(content:VibeCoding)=
# Some good Vibes... Coding!

The previous section was quite technical, but essential in order to have a clean Python environment to code. Let's have a bit of fun now, with some **vibe coding**! 😁 In this section we are going to deal with a non scientific example, but the main conclusions apply to any problem, including the chemistry related things we are going to investigate in the following of the lecture.

Vibe Coding is a term coined in 2025 by Andrej Karpathy, co-founder of OpenAI (company behind ChatGPT), which refers to generating working code by providing a natural language description of the program rather than manually writing it (definition from [Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding)).

## 2mn Tetris

As an example of the power of Vibe Coding, let's try to program the famous Tetris game. A few years back, that would be a rather advanced exercise, and for a non professionnal programmer like I am, it would probably takes a few hours to get something functionnal. But nowadays, this can be achieved in a few minutes (even seconds...) using AI. For this example, I will use the AI ChatGPT, and in particular the free model based on *GPT-5 mini*. Note that I will use the library `pygame` installed in our Python environment in the previous section, which allow to display graphical stuffs.

In vibe coding, everything starts with a **prompt**, which is the question you are asking to the AI chatbot. Here is the prompt I am using:

*"Give me a simple python program, that fits in a file, and that code the famous tetris game. For the graphical part, use the pygame library"*

Below is the answer of the chatbot (March 9, 2026):

````{tip} See the code
:class: dropdown

```python
import pygame, random

# Initialize pygame
pygame.init()

# Screen dimensions
WIDTH, HEIGHT = 300, 600
BLOCK_SIZE = 30
ROWS, COLS = HEIGHT // BLOCK_SIZE, WIDTH // BLOCK_SIZE

# Colors
BLACK = (0,0,0)
WHITE = (255,255,255)
COLORS = [(0,255,255),(0,0,255),(255,165,0),(255,255,0),(0,255,0),(128,0,128),(255,0,0)]

# Tetris shapes
SHAPES = [
    [[1,1,1,1]],                # I
    [[1,1],[1,1]],              # O
    [[0,1,0],[1,1,1]],          # T
    [[1,0,0],[1,1,1]],          # J
    [[0,0,1],[1,1,1]],          # L
    [[0,1,1],[1,1,0]],          # S
    [[1,1,0],[0,1,1]]           # Z
]

class Piece:
    def __init__(self, x, y, shape):
        self.x, self.y = x, y
        self.shape = shape
        self.color = random.choice(COLORS)
        self.rotation = 0

    def image(self):
        return self.shape[self.rotation % len(self.shape)]

def create_grid(locked={}):
    grid = [[BLACK for _ in range(COLS)] for _ in range(ROWS)]
    for i in range(ROWS):
        for j in range(COLS):
            if (j,i) in locked:
                grid[i][j] = locked[(j,i)]
    return grid

def convert_shape_format(piece):
    positions = []
    shape = piece.shape
    for i, line in enumerate(shape):
        for j, column in enumerate(line):
            if column:
                positions.append((piece.x + j, piece.y + i))
    return positions

def valid_space(piece, grid):
    accepted = [[(j,i) for j in range(COLS) if grid[i][j]==BLACK] for i in range(ROWS)]
    accepted = [j for sub in accepted for j in sub]
    for pos in convert_shape_format(piece):
        if pos not in accepted:
            return False
    return True

def check_lost(positions):
    for pos in positions:
        x, y = pos
        if y < 1:
            return True
    return False

def get_shape():
    return Piece(COLS//2 - 2, 0, random.choice(SHAPES))

def draw_grid(surface, grid):
    for i in range(ROWS):
        for j in range(COLS):
            pygame.draw.rect(surface, grid[i][j],
                             (j*BLOCK_SIZE, i*BLOCK_SIZE, BLOCK_SIZE, BLOCK_SIZE),0)
    for i in range(ROWS):
        pygame.draw.line(surface, WHITE, (0,i*BLOCK_SIZE),(WIDTH,i*BLOCK_SIZE))
    for j in range(COLS):
        pygame.draw.line(surface, WHITE, (j*BLOCK_SIZE,0),(j*BLOCK_SIZE,HEIGHT))

def clear_rows(grid, locked):
    increment = 0
    for i in range(ROWS-1,-1,-1):
        if BLACK not in grid[i]:
            increment += 1
            for j in range(COLS):
                try:
                    del locked[(j,i)]
                except:
                    continue
            for key in sorted(list(locked), key=lambda x: x[1])[::-1]:
                x, y = key
                if y < i:
                    locked[(x,y+1)] = locked.pop((x,y))
    return increment

def draw_window(surface, grid, score=0):
    surface.fill(BLACK)
    draw_grid(surface, grid)
    font = pygame.font.SysFont('comicsans', 30)
    label = font.render(f"Score: {score}",1,WHITE)
    surface.blit(label,(10,10))
    pygame.display.update()

def main():
    locked_positions = {}
    grid = create_grid(locked_positions)
    change_piece = False
    run = True
    current_piece = get_shape()
    next_piece = get_shape()
    clock = pygame.time.Clock()
    fall_time = 0
    fall_speed = 0.5
    score = 0

    screen = pygame.display.set_mode((WIDTH, HEIGHT))
    pygame.display.set_caption('Tetris')

    while run:
        grid = create_grid(locked_positions)
        fall_time += clock.get_rawtime()
        clock.tick()

        if fall_time/1000 > fall_speed:
            fall_time = 0
            current_piece.y += 1
            if not valid_space(current_piece, grid) and current_piece.y > 0:
                current_piece.y -= 1
                change_piece = True

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                run = False
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    current_piece.x -=1
                    if not valid_space(current_piece, grid):
                        current_piece.x +=1
                if event.key == pygame.K_RIGHT:
                    current_piece.x +=1
                    if not valid_space(current_piece, grid):
                        current_piece.x -=1
                if event.key == pygame.K_DOWN:
                    current_piece.y +=1
                    if not valid_space(current_piece, grid):
                        current_piece.y -=1
                if event.key == pygame.K_UP:
                    current_piece.shape = [list(row) for row in zip(*current_piece.shape[::-1])]
                    if not valid_space(current_piece, grid):
                        current_piece.shape = [list(row) for row in zip(*current_piece.shape)][::-1]

        shape_pos = convert_shape_format(current_piece)
        for x,y in shape_pos:
            if y>=0:
                grid[y][x] = current_piece.color

        if change_piece:
            for pos in shape_pos:
                locked_positions[pos] = current_piece.color
            current_piece = next_piece
            next_piece = get_shape()
            change_piece = False
            score += clear_rows(grid, locked_positions) * 10

        draw_window(screen, grid, score)
        if check_lost(locked_positions):
            run = False

    pygame.display.quit()

if __name__ == "__main__":
    main()
```
````

To run this code, do the following step:
- Open an Anaconda terminal and activate the environment we have created in the previous section.
- In this terminal, go to any folder on your computer where you want to store your tetris game.
- Create a new python file (with extension .py) called `tetris.py`. Copy/paste the code given by ChatGPT in this file, save it.
- In the terminal, type `python tetris.py` and then press Enter to execute the Python code written in the `tetris.py` file

You should obtain a working game that looks like the following picture:

:::{figure} images/fig_tetris_v1.png
:align: center
:width: 50%

A python tetris game programmed by an AI
:::

Amazing, isn't it?! Now, you can continue vibe code by asking the AI to refine the program. For instance, here is a second prompt I submitted to the AI:

*"Upgrade the code so that we have a next piece preview, and the Score is not written on the game grid"*

Here is the AI answer:

````{tip} See the improved code
:class: dropdown

```python

import pygame, random

# Initialize pygame
pygame.init()

# Screen dimensions
GRID_WIDTH, GRID_HEIGHT = 300, 600
SIDE_PANEL = 150
WIDTH, HEIGHT = GRID_WIDTH + SIDE_PANEL, GRID_HEIGHT
BLOCK_SIZE = 30
ROWS, COLS = GRID_HEIGHT // BLOCK_SIZE, GRID_WIDTH // BLOCK_SIZE

# Colors
BLACK = (0,0,0)
WHITE = (255,255,255)
COLORS = [(0,255,255),(0,0,255),(255,165,0),(255,255,0),(0,255,0),(128,0,128),(255,0,0)]

# Tetris shapes
SHAPES = [
    [[1,1,1,1]],                # I
    [[1,1],[1,1]],              # O
    [[0,1,0],[1,1,1]],          # T
    [[1,0,0],[1,1,1]],          # J
    [[0,0,1],[1,1,1]],          # L
    [[0,1,1],[1,1,0]],          # S
    [[1,1,0],[0,1,1]]           # Z
]

class Piece:
    def __init__(self, x, y, shape):
        self.x, self.y = x, y
        self.shape = shape
        self.color = random.choice(COLORS)

def create_grid(locked={}):
    grid = [[BLACK for _ in range(COLS)] for _ in range(ROWS)]
    for (x,y), color in locked.items():
        if y >= 0:
            grid[y][x] = color
    return grid

def convert_shape_format(piece):
    positions = []
    for i, row in enumerate(piece.shape):
        for j, val in enumerate(row):
            if val:
                positions.append((piece.x + j, piece.y + i))
    return positions

def valid_space(piece, grid):
    accepted = [(j,i) for i in range(ROWS) for j in range(COLS) if grid[i][j]==BLACK]
    for pos in convert_shape_format(piece):
        if pos not in accepted:
            return False
    return True

def check_lost(positions):
    for x, y in positions:
        if y < 1:
            return True
    return False

def get_shape():
    return Piece(COLS//2 - 2, 0, random.choice(SHAPES))

def draw_grid(surface, grid):
    for i in range(ROWS):
        for j in range(COLS):
            pygame.draw.rect(surface, grid[i][j],
                             (j*BLOCK_SIZE, i*BLOCK_SIZE, BLOCK_SIZE, BLOCK_SIZE),0)
    for i in range(ROWS):
        pygame.draw.line(surface, WHITE, (0,i*BLOCK_SIZE),(GRID_WIDTH,i*BLOCK_SIZE))
    for j in range(COLS):
        pygame.draw.line(surface, WHITE, (j*BLOCK_SIZE,0),(j*BLOCK_SIZE,GRID_HEIGHT))

def clear_rows(grid, locked):
    cleared = 0
    for i in range(ROWS-1,-1,-1):
        if BLACK not in grid[i]:
            cleared += 1
            for j in range(COLS):
                del locked[(j,i)]
            for (x,y) in sorted(list(locked), key=lambda k:k[1])[::-1]:
                if y < i:
                    locked[(x,y+1)] = locked.pop((x,y))
    return cleared

def draw_window(surface, grid, score, next_piece):
    surface.fill(BLACK)
    draw_grid(surface, grid)

    # Draw side panel background
    pygame.draw.rect(surface, (50,50,50), (GRID_WIDTH, 0, SIDE_PANEL, HEIGHT))

    # Draw score
    font = pygame.font.SysFont('comicsans', 30)
    label = font.render(f"Score: {score}",1,WHITE)
    surface.blit(label,(GRID_WIDTH + 20, 20))

    # Draw next piece preview
    label_next = font.render("Next:",1,WHITE)
    surface.blit(label_next,(GRID_WIDTH + 20, 60))
    for i, row in enumerate(next_piece.shape):
        for j, val in enumerate(row):
            if val:
                pygame.draw.rect(surface, next_piece.color,
                                 (GRID_WIDTH + 50 + j*BLOCK_SIZE//2,
                                  100 + i*BLOCK_SIZE//2,
                                  BLOCK_SIZE//2, BLOCK_SIZE//2))
    pygame.display.update()

def main():
    locked_positions = {}
    grid = create_grid(locked_positions)
    change_piece = False
    run = True
    current_piece = get_shape()
    next_piece = get_shape()
    clock = pygame.time.Clock()
    fall_time = 0
    fall_speed = 0.5
    score = 0

    screen = pygame.display.set_mode((WIDTH, HEIGHT))
    pygame.display.set_caption('Tetris')

    while run:
        grid = create_grid(locked_positions)
        fall_time += clock.get_rawtime()
        clock.tick()

        if fall_time/1000 > fall_speed:
            fall_time = 0
            current_piece.y += 1
            if not valid_space(current_piece, grid) and current_piece.y > 0:
                current_piece.y -= 1
                change_piece = True

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                run = False
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    current_piece.x -=1
                    if not valid_space(current_piece, grid):
                        current_piece.x +=1
                if event.key == pygame.K_RIGHT:
                    current_piece.x +=1
                    if not valid_space(current_piece, grid):
                        current_piece.x -=1
                if event.key == pygame.K_DOWN:
                    current_piece.y +=1
                    if not valid_space(current_piece, grid):
                        current_piece.y -=1
                if event.key == pygame.K_UP:
                    current_piece.shape = [list(row) for row in zip(*current_piece.shape[::-1])]
                    if not valid_space(current_piece, grid):
                        current_piece.shape = [list(row) for row in zip(*current_piece.shape)][::-1]

        shape_pos = convert_shape_format(current_piece)
        for x,y in shape_pos:
            if y>=0:
                grid[y][x] = current_piece.color

        if change_piece:
            for pos in shape_pos:
                locked_positions[pos] = current_piece.color
            current_piece = next_piece
            next_piece = get_shape()
            change_piece = False
            score += clear_rows(grid, locked_positions) * 10

        draw_window(screen, grid, score, next_piece)
        if check_lost(locked_positions):
            run = False

    pygame.display.quit()

if __name__ == "__main__":
    main()
```
````

This new code will give you the following updated version of the game:

:::{figure} images/fig_tetris_v2.png
:align: center
:width: 50%

An improved version of tetris
:::

## Thoughts on AI and programming

I hope this small tetris example has convinced you of the power of AI when it comes to coding! You can take some times here to play with vibe coding and try to build any program you are dreaming of. Have some fun, and at the same time this will be an opportunity to discover the nearly limitless possibilities of Python.

Actually, if you are interested in using Python for "basic" tasks such as plotting figures for publication, it might be that vibe coding is just enough for you and you don't need to go further in this lecture. Yet, at the time of writing (2026) I am convinced that it is still important to learn Python for the following reasons:

- For the tetris example, any AI will succeed in giving you a nice working code without any adjustment required from your side. The reason behind this is that there are so many publicly available tetris code online, that were probably used at some point in the AI training (I believe this is also the reason why all the AI I have tested gave me basically the very same tetris game, in term of colors, shapes, play style...) But if you want to build a large program with very specific functionnalities, it might be that the AI gives a code with some bugs (even if it is becoming increasingly rare); in that case you need to know Python in order to understand the errors you will get, and to find ways to solve them.

- For specific problems again, it might be that the AI doesn't really know "what to do". You will need to guide it precisely with a detailed prompt that specifies all the steps in order to solve the problem. Writing the good prompt is becoming a real technical skill, the so-called **prompt engineering**. The more familiar you are with Python and programming in general, the better will be your prompt.

- AI are really awesome, *but they still have limits*. First, they have some **hallucinations**, meaning they tend to make things up when they don't know the answer, or they just "lie" about things sometimes. In addition, they have a **limited context window**, meaning that they will forget the beginning of the conversation they are having with you if the chat gets too long. All together, if you build a large program with AI and let it do everything from scratch, without understanding anything, at some points you will run into problems for sure. At some points the program will start crashing, you will get lost and spend days trying to fix things by asking again and again the AI to repair the program, but it it just too late.

- Knowing Python and its libraries allows you to be creative and find ways to solve complex problems, sometimes more efficiently than AI.

- For a scientific publication including modeling with a Python program, you definitely need to know exactly how the program works to be 100% sure that it does what it is supposed to!

- Using an AI to write two lines of code is a bit overkill, especially at a time when energy and technological frugality are becoming increasingly important... use it wisely.

- Finally, it is so satisfying to build some working program by yourself, even if you get some helps from AI! 😎

## Final advise

To conclude this section, here is my personnal view on how you should learn and use Python in 2026, especially for sciences:

- The main point is to learn how a program is structured, what is the logic behind, and what type of problems can be solved with programming: it is about getting familiar with a particular "mindset" if you like.

- At the beginning, don't spend too much time learning the precise syntax of the Python langage (even though the very fundamentals must be known). This will come naturally with practicing, and Internet and AI are here to help you find the name of a function when needed.

- Start with solving programming problems only by yourself, and progressively include the use of AI as an assistant.

- You are free to follow this advise or not, but here are the rules I impose on myself: use AI to write code that you could write by yourself, and do not have pieces of code that you have never reviewed in your program! 