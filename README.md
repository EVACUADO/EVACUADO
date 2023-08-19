import pygame
import sys

# Initialize Pygame
pygame.init()

# Constants
SCREEN_WIDTH = 640
SCREEN_HEIGHT = 480
BLACK = (0, 0, 0)
YELLOW = (255, 255, 0)
PACMAN_RADIUS = 20

# Create the screen
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Pac-Man")

# Load Pac-Man image
pacman_img = pygame.image.load("pacman.png")
pacman_img = pygame.transform.scale(pacman_img, (PACMAN_RADIUS * 2, PACMAN_RADIUS * 2))

# Pac-Man's position
pacman_x = SCREEN_WIDTH // 2
pacman_y = SCREEN_HEIGHT // 2

# Main game loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        pacman_x -= 5
    if keys[pygame.K_RIGHT]:
        pacman_x += 5
    if keys[pygame.K_UP]:
        pacman_y -= 5
    if keys[pygame.K_DOWN]:
        pacman_y += 5

    # Clear the screen
    screen.fill(BLACK)

    # Draw Pac-Man
    screen.blit(pacman_img, (pacman_x - PACMAN_RADIUS, pacman_y - PACMAN_RADIUS))

    # Update the screen
    pygame.display.update()
