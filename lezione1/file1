import pygame
import random
import math

pygame.init()

# Schermo
WIDTH, HEIGHT = 1360, 800
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Arena Shooter")

clock = pygame.time.Clock()

# Giocatore
player_size = 40
player_pos = [WIDTH // 2, HEIGHT // 2]
player_speed = 5

# Liste per proiettili e nemici
bullets = []
enemies = []

# Parametri
enemy_spawn_delay = 60
enemy_timer = 0
enemy_speed = 2
bullet_speed = 10

# Funzione per spawnare nemici ai bordi
def spawn_enemy():
    side = random.choice(["top", "bottom", "left", "right"])
    if side == "top":
        pos = [random.randint(0, WIDTH), 0]
    elif side == "bottom":
        pos = [random.randint(0, WIDTH), HEIGHT]
    elif side == "left":
        pos = [0, random.randint(0, HEIGHT)]
    else:
        pos = [WIDTH, random.randint(0, HEIGHT)]
    enemies.append(pos)

running = True
while running:
    clock.tick(60)
    screen.fill((30, 30, 30))

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

        # Sparo col tasto sinistro
        if event.type == pygame.MOUSEBUTTONDOWN and event.button == 1:
            mx, my = pygame.mouse.get_pos()
            dx = mx - player_pos[0]
            dy = my - player_pos[1]
            angle = math.atan2(dy, dx)
            bullets.append([player_pos[0], player_pos[1], angle])

    # Movimento player
    keys = pygame.key.get_pressed()
    if keys[pygame.K_w] and player_pos[1] > 0:
        player_pos[1] -= player_speed
    if keys[pygame.K_s] and player_pos[1] < HEIGHT:
        player_pos[1] += player_speed
    if keys[pygame.K_a] and player_pos[0] > 0:
        player_pos[0] -= player_speed
    if keys[pygame.K_d] and player_pos[0] < WIDTH:
        player_pos[0] += player_speed

    # Disegna giocatore
    pygame.draw.rect(screen, (0, 150, 255),
                     (player_pos[0] - player_size // 2,
                      player_pos[1] - player_size // 2,
                      player_size, player_size))

    # Gestione proiettili
    for bullet in bullets[:]:
        bullet[0] += bullet_speed * math.cos(bullet[2])
        bullet[1] += bullet_speed * math.sin(bullet[2])

        if bullet[0] < 0 or bullet[0] > WIDTH or bullet[1] < 0 or bullet[1] > HEIGHT:
            bullets.remove(bullet)
        else:
            pygame.draw.circle(screen, (255, 255, 0), (int(bullet[0]), int(bullet[1])), 5)

    # Spawn nemici
    enemy_timer += 1
    if enemy_timer >= enemy_spawn_delay:
        spawn_enemy()
        enemy_timer = 0

    # Movimento nemici
    for enemy in enemies[:]:
        dx = player_pos[0] - enemy[0]
        dy = player_pos[1] - enemy[1]
        dist = math.hypot(dx, dy)
        if dist != 0:
            enemy[0] += enemy_speed * (dx / dist)
            enemy[1] += enemy_speed * (dy / dist)

        pygame.draw.rect(screen, (200, 50, 50),
                         (enemy[0] - 20, enemy[1] - 20, 40, 40))

        for bullet in bullets[:]:
            if abs(bullet[0] - enemy[0]) < 20 and abs(bullet[1] - enemy[1]) < 20:
                enemies.remove(enemy)
                bullets.remove(bullet)
                break

    pygame.display.flip()

pygame.quit()
