# Trump PyGame (2020)

[English](README.md) | [Русский](README.ru.md)

A small 2D game built with Python and Pygame. Move an animated character, jump and fire projectiles across a fixed scene.

This learning project explores keyboard input, sprite animation and a game loop. The game code is in [app/game.py](app/game.py), with its background and character sprites in [images/](images/).

![Game preview](images/gameplay.png)

## Gameplay

- Move left and right with a six-frame walking animation for each direction.
- Jump with the space bar.
- Fire in the last movement direction, with up to five projectiles on screen.
- Play in a 500 × 500 window with a game loop capped at 30 frames per second.

## Controls

| Key | Action |
| --- | --- |
| `←` | Move left |
| `→` | Move right |
| `Space` | Jump |
| `F` | Fire a projectile |
| Close the window | Exit the game |

## Run locally

Use Python 3.12 and a desktop session where Pygame can open a window. The commands below use Bash and install Pygame 2.6.1 in a virtual environment.

```bash
git clone https://github.com/ivan-zamula/trump-pygame-2020.git
cd trump-pygame-2020
python3 -m venv .venv
source .venv/bin/activate
python -m pip install pygame==2.6.1
python app/game.py
```

To start the game again, activate the same environment and run `python app/game.py` from the project root.

## Project files

| Path | Purpose |
| --- | --- |
| [app/game.py](app/game.py) | Input handling, movement, jumping, animation, projectiles and drawing |
| [images/bg.jpg](images/bg.jpg) | Background image |
| [images/idle.png](images/idle.png) | Standing character sprite |
| [images/gameplay.png](images/gameplay.png) | Game screenshot |
| [images/](images/) | Walking frames: `left_1.png`–`left_6.png` and `right_1.png`–`right_6.png` |

The script resolves image paths from its own location, so resource loading does not depend on the current working directory.

## How it works

Each frame reads the keyboard state, updates the character and projectiles, and redraws the scene. Walking cycles through six sprites; releasing the movement keys displays the standing sprite. A jump follows a simple counter-based trajectory. Projectiles travel horizontally and are removed when they leave the window.

The project uses Python's `pathlib` module for resource paths and Pygame for the window, input, image loading, drawing and frame timing.
