import pygame
import math
import random

pygame.init()

WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Tower Defense (base)")
clock = pygame.time.Clock()

# Percorso dei nemici (lista di punti da seguire)
path = [
    (0, 300), (200, 300), (200, 100),
    (400, 100), (400, 500), (600, 500),
    (600, 200), (800, 200)
]

# Nemici
enemies = []
enemy_speed = 1
spawn_delay = 120
spawn_timer = 0
lives = 10

# Torri
towers = []
tower_radius = 120
tower_fire_delay = 45

# Proiettili
bullets = []
bullet_speed = 6

def spawn_enemy():
    enemies.append({
        "x": path[0][0],
        "y": path[0][1],
        "path_index": 0,
        "health": 100
    })

running = True
while running:
    clock.tick(60)
    screen.fill((50, 50, 50))

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

        if event.type == pygame.MOUSEBUTTONDOWN and event.button == 1:
            mx, my = pygame.mouse.get_pos()
            towers.append({
                "x": mx,
                "y": my,
                "cooldown": 0
            })

    spawn_timer += 1
    if spawn_timer >= spawn_delay:
        spawn_enemy()
        spawn_timer = 0

    for enemy in enemies[:]:
        i = enemy["path_index"]
        if i < len(path) - 1:
            ex, ey = enemy["x"], enemy["y"]
            tx, ty = path[i+1]
            dx = tx - ex
            dy = ty - ey
            dist = math.hypot(dx, dy)
            if dist != 0:
                enemy["x"] += enemy_speed * dx / dist
                enemy["y"] += enemy_speed * dy / dist
            if dist < 2:
                enemy["path_index"] += 1
        else:
            enemies.remove(enemy)
            lives -= 1

        pygame.draw.circle(screen, (200, 50, 50),
                           (int(enemy["x"]), int(enemy["y"])), 15)

    for tower in towers:
        if tower["cooldown"] > 0:
            tower["cooldown"] -= 1

        found = None
        closest_dist = tower_radius

        for enemy in enemies:
            dx = enemy["x"] - tower["x"]
            dy = enemy["y"] - tower["y"]
            dist = math.hypot(dx, dy)
            if dist < closest_dist:
                closest_dist = dist
                found = enemy

        if found and tower["cooldown"] == 0:
            angle = math.atan2(found["y"] - tower["y"],
                               found["x"] - tower["x"])
            bullets.append([tower["x"], tower["y"], angle])
            tower["cooldown"] = tower_fire_delay

        pygame.draw.circle(screen, (100, 100, 255),
                           (int(tower["x"]), int(tower["y"])), 10)
        pygame.draw.circle(screen, (80, 80, 120),
                           (int(tower["x"]), int(tower["y"])),
                           tower_radius, 1)

    for bullet in bullets[:]:
        bullet[0] += bullet_speed * math.cos(bullet[2])
        bullet[1] += bullet_speed * math.sin(bullet[2])

        bx, by = bullet[0], bullet[1]
        remove_bullet = False

        if bx < 0 or bx > WIDTH or by < 0 or by > HEIGHT:
            remove_bullet = True
        else:
            for enemy in enemies:
                if math.hypot(enemy["x"] - bx,
                              enemy["y"] - by) < 15:
                    enemy["health"] -= 50
                    remove_bullet = True
                    break

        if remove_bullet:
            bullets.remove(bullet)
        else:
            pygame.draw.circle(screen, (255, 255, 0),
                               (int(bullet[0]), int(bullet[1])), 5)

    for enemy in enemies[:]:
        if enemy["health"] <= 0:
            enemies.remove(enemy)

    font = pygame.font.SysFont(None, 36)
    text = font.render(f"Lives: {lives}", True, (255, 255, 255))
    screen.blit(text, (10, 10))

    if lives <= 0:
        running = False

    pygame.display.flip()

pygame.quit()
