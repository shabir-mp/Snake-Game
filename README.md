<p align="center">
<img src="https://github.com/shabir-mp/Snake-Game/assets/133546000/28a05d47-ddbd-4376-bf17-1a163438da91" width="170" />
<h1 align="center">Snake Game v1.0.0</h1>
</p>

This Snake Game is a classic arcade game implemented using Python and the Pygame library. The game involves controlling a snake to eat food and grow longer while avoiding collisions with the walls and the snake's own body. It is a single-player game where the objective is to achieve the highest possible score by consuming as much food as possible. Enjoy playing the Snake Game, a classic arcade experience brought to life with Python and Pygame! Challenge yourself to beat your high score and master the art of controlling the ever-growing snake.

## About
[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)
[![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg)](https://github.com/shabir-mp/Image-Background-Remover/blob/main/LICENSE)

- **Developer:** Shabir Mahfudz Prahono - @shabir-mp
- **Application creation date:** 28 June 2024

## Features
- Simple Graphics: The game uses basic rectangular graphics for the snake and food, with different colors to distinguish them.
- Keyboard Controls: The snake is controlled using the arrow keys on the keyboard.
- Score Tracking: The game keeps track of and displays the player's score based on the number of food items consumed.
- Game Over and Restart: When the game is over, the player can choose to quit or restart the game.

## Requirements

To play the Snake Game, you need:

- **Python 3.x**: Python is the programming language used to run the game.
- **Pygame Library**: This Python library is required for handling graphics, events, and sound in the game.

## Installation Steps

1. **Install Python**:
   - Download and install Python 3.x from the [official website](https://www.python.org/).

2. **Install Pygame**:
   - Open a command prompt or terminal.
   - Use the following command to install Pygame using pip, Python's package installer:

     ```bash
     pip install pygame
     ```

## How to Play

1. **Download the Snake Game Code**:
   - Save the provided Python code in a file, e.g., `snake_game.py`.

2. **Run the Game**:
   - Open a command prompt or terminal.
   - Navigate to the directory where `snake_game.py` is saved.
   - Run the game by executing the following command:

     ```bash
     python snake_game.py
     ```

3. **Game Controls**:
   - Use the arrow keys on your keyboard to control the snake:
     - **Up Arrow**: Move the snake upwards.
     - **Down Arrow**: Move the snake downwards.
     - **Left Arrow**: Move the snake to the left.
     - **Right Arrow**: Move the snake to the right.

4. **Game Objective**:
   - Guide the snake to eat the green food squares that randomly appear on the screen.
   - Each time the snake eats food, it grows longer.
   - Avoid collisions with the walls and the snake's own body, as these will end the game.

5. **Scoring**:
   - The score increases with each piece of food consumed.
   - Try to achieve the highest possible score before the snake collides with an obstacle.

6. **Game Over**:
   - The game ends when the snake collides with a wall or its own body.
   - Upon game over, you can press **Q** to quit the game or **C** to play again.

## Application Preview
![SNKGM 1](https://github.com/shabir-mp/Snake-Game/assets/133546000/9b493b86-9a4d-4e19-94bc-de716ce9376d)
#### 1. View of the game. User can move the snake (black box) by clicking the up, down, right, left keys on the keyboard. The target is the green box.
![SNKGM 2](https://github.com/shabir-mp/Snake-Game/assets/133546000/554fd670-3bc2-4d6c-b730-78f4af052909)
#### 2. Game over display. User can press `Q` key on keyboard to exit, and `U` to restart the game.

## Code Explanation
### 1. Imports and Initialization
```python
import pygame
import time
import random

pygame.init()
```
- **Explanation:**
  - `pygame` is a Python library used for game development.
  - `time` and `random` are standard Python libraries.
  - `pygame.init()` initializes all the imported pygame modules and must be called before using any other Pygame functions.

### 2. Colors
```python
white = (255, 255, 255)
yellow = (255, 255, 102)
black = (0, 0, 0)
red = (213, 50, 80)
green = (0, 255, 0)
blue = (50, 153, 213)
```
- **Explanation:**
  - These variables store RGB tuples representing different colors used in the game interface.
  - For example, `white` is pure white `(255, 255, 255)` and `black` is pure black `(0, 0, 0)`.

### 3. Screen Setup
```python
dis_width = 800
dis_height = 600
dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption('Snake Game')
```
- **Explanation:**
  - `dis_width` and `dis_height` set the dimensions of the game window to 800 pixels wide and 600 pixels high.
  - `pygame.display.set_mode((dis_width, dis_height))` creates a Pygame display surface with the specified dimensions.
  - `pygame.display.set_caption('Snake Game')` sets the title of the game window to 'Snake Game'.

### 4. Clock and Game Parameters
```python
clock = pygame.time.Clock()
snake_block = 10
snake_speed = 15
```
- **Explanation:**
  - `clock` is an instance of `pygame.time.Clock()` used to control the game's frame rate.
  - `snake_block` determines the size of each segment of the snake.
  - `snake_speed` controls how fast the snake moves; it represents the number of pixels the snake moves per frame update.

### 5. Fonts
```python
font_style = pygame.font.SysFont("bahnschrift", 25)
score_font = pygame.font.SysFont("comicsansms", 35)
```
- **Explanation:**
  - `font_style` and `score_font` are Pygame Font objects created using `pygame.font.SysFont`.
  - They are used for rendering text on the game screen with specified fonts ("bahnschrift" and "comicsansms") and sizes (25 and 35, respectively).

### 6. Functions
- **Your_score(score):**
  ```python
  def Your_score(score):
      value = score_font.render("Your Score: " + str(score), True, black)
      dis.blit(value, [0, 0])
  ```
  - **Explanation:**
    - `Your_score()` function renders and displays the player's current score on the game screen.
    - `score_font.render("Your Score: " + str(score), True, black)` creates a text surface with the score rendered in black color.
    - `dis.blit(value, [0, 0])` draws the rendered text (`value`) at the top-left corner of the screen.

- **our_snake(snake_block, snake_List):**
  ```python
  def our_snake(snake_block, snake_List):
      for x in snake_List:
          pygame.draw.rect(dis, black, [x[0], x[1], snake_block, snake_block])
  ```
  - **Explanation:**
    - `our_snake()` function draws the snake on the game screen based on its current segments.
    - It iterates through `snake_List`, which contains coordinates of each segment of the snake.
    - `pygame.draw.rect(dis, black, [x[0], x[1], snake_block, snake_block])` draws a rectangle (snake segment) at position `(x[0], x[1])` with dimensions `snake_block x snake_block` in black color (`black`) on the `dis` surface.

- **message(msg, color):**
  ```python
  def message(msg, color):
      mesg = font_style.render(msg, True, color)
      dis.blit(mesg, [dis_width / 6, dis_height / 3])
  ```
  - **Explanation:**
    - `message()` function displays a message on the game screen.
    - It renders the text `msg` using the `font_style` and with the specified `color`.
    - `dis.blit(mesg, [dis_width / 6, dis_height / 3])` draws the rendered message (`mesg`) at a specific position on the screen, which is `(dis_width / 6, dis_height / 3)`.

### 7. GameLoop Function
```python
def gameLoop():
    game_over = False
    game_close = False

    x1 = dis_width / 2
    y1 = dis_height / 2

    x1_change = 0
    y1_change = 0

    snake_List = []
    Length_of_snake = 1

    foodx = round(random.randrange(0, dis_width - snake_block) / 10.0) * 10.0
    foody = round(random.randrange(0, dis_height - snake_block) / 10.0) * 10.0

    while not game_over:
        while game_close == True:
            dis.fill(blue)
            message("You Lost! Press Q-Quit or C-Play Again", red)
            Your_score(Length_of_snake - 1)
            pygame.display.update()

            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_c:
                        gameLoop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change = -snake_block
                    y1_change = 0
                elif event.key == pygame.K_RIGHT:
                    x1_change = snake_block
                    y1_change = 0
                elif event.key == pygame.K_UP:
                    y1_change = -snake_block
                    x1_change = 0
                elif event.key == pygame.K_DOWN:
                    y1_change = snake_block
                    x1_change = 0

        if x1 >= dis_width or x1 < 0 or y1 >= dis_height or y1 < 0:
            game_close = True
        x1 += x1_change
        y1 += y1_change
        dis.fill(white)
        pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
        snake_Head = []
        snake_Head.append(x1)
        snake_Head.append(y1)
        snake_List.append(snake_Head)
        if len(snake_List) > Length_of_snake:
            del snake_List[0]

        for x in snake_List[:-1]:
            if x == snake_Head:
                game_close = True

        our_snake(snake_block, snake_List)
        Your_score(Length_of_snake - 1)

        pygame.display.update()

        if x1 == foodx and y1 == foody:
            foodx = round(random.randrange(0, dis_width - snake_block) / 10.0) * 10.0
            foody = round(random.randrange(0, dis_height - snake_block) / 10.0) * 10.0
            Length_of_snake += 1

        clock.tick(snake_speed)

    pygame.quit()
    quit()
```
- **Explanation:**
  - `gameLoop()` function manages the main game logic and loop.
  - **Initialization:**
    - `game_over` and `game_close` control the game state (running or ended).
    - `x1` and `y1` represent the initial position of the snake's head.
    - `x1_change` and `y1_change` store the velocity of the snake in the x and y directions.
    - `snake_List` keeps track of the snake's body segments.
    - `Length_of_snake` tracks the current length of the snake.
    - `foodx` and `foody` store the coordinates of the food that the snake eats.
  - **Main Loop:**
    - `while not game_over:` runs the game until the player quits or loses.
    - `while game_close == True:` manages the game over screen:
      - Fills the screen with blue (`dis.fill(blue)`).
      - Displays a message indicating the player lost and instructions to quit or play again.
      - Updates the display and waits for player input (`pygame.event.get()`).
    - Event handling (`for event in pygame.event.get()`):
      - Processes events such as quitting the game (`pygame.QUIT` event) or controlling the snake's direction (`pygame.KEYDOWN` events).
    - **Game Logic:**
      - Checks if the snake collides with boundaries (`if x1 >= dis_width or x1 < 0 or y1 >= dis_height or y1 < 0:`) and sets `game_close` to `True` if true.
      - Updates the snake's position (`x1 += x1_change`, `y1 += y1_change`) based on user input

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

-----------------------------------------------------------------------------------------
![Github Footer](https://github.com/shabir-mp/Kereta-Api-Indonesia-Booking-System/assets/133546000/c1833fe4-f470-494f-99e7-d583421625be)
