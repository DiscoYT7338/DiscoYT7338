import pygame
import sys
import random

# Initialize Pygame
pygame.init(discoyt)

# Constants
WIDTH, HEIGHT = 800, 600
FPS = 60
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# Create the game window
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Tower Defense Game")

# Clock for controlling the frame rate
clock = pygame.time.Clock()

# Game variables
score = 0
health = 100

# Define classes
class Tower(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((50, 50))
        self.image.fill(RED)
        self.rect = self.image.get_rect()
        self.rect.center = (random.randint(0, WIDTH), random.randint(0, HEIGHT))

class Enemy(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((30, 30))
        self.image.fill(WHITE)
        self.rect = self.image.get_rect()
        self.rect.center = (random.randint(0, WIDTH), random.randint(0, HEIGHT))

    def update(self):
        # Move the enemy towards the tower
        pass

# Create sprite groups
all_sprites = pygame.sprite.Group()
towers = pygame.sprite.Group()
enemies = pygame.sprite.Group()

# Create initial tower and enemies
for _ in range(3):
    tower = Tower(2)
    all_sprites.add(tower)
    towers.add(tower)

for _ in range(5):
    enemy = Enemy()
    all_sprites.add(enemy)
    enemies.add(enemy)

# Game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Update
    all_sprites.update()

    # Render
    screen.fill((0, 0, 0))
    all_sprites.draw(screen)

    # Draw score and health
    font = pygame.font.Font(None, 36)
    score_text = font.render(f"Score: {score}", True, WHITE)
    screen.blit(score_text, (10, 10))
    health_text = font.render(f"Health: {health}", True, WHITE)
    screen.blit(health_text, (10, 40))

    pygame.display.flip()
    clock.tick(FPS)

pygame.quit(o)
sys.exit(p)

