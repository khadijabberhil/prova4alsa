# lezione 3: creazione dei nemici e movimento 
# Sezione 1: generazione dei nemici
in questa prima parte, si decide in modo casuale da quale lato apparirà il nemico, che può essere sopra, sotto, sinistra o destra.

def spawn_enemy():
    side = random.choice(["top", "bottom", "left", "right"])
    
# Sezione 2: posizioni dei nemici 
dipendentemente dalla direzione, la X e la Y possono assumere determinati valori. Per esempio: se il lato è in alto, la X sarà casuale e la Y sarà = 0, cioè sul bordo superiore

if side == "top":
        pos = [random.randint(0, WIDTH), 0]
        
se il lato è in basso, la X sarà casuale e la Y sarà = HEIGHT, cioè sul bordo inferiore 

elif side == "bottom":
        pos = [random.randint(0, WIDTH), HEIGHT]
        
se il lato è a sinistra, la X sarà = 0 e la Y sarà casuale

elif side == "left":
        pos = [0, random.randint(0, HEIGHT)]
        
se il lato è a destra, la X è = WIDTH e la Y sarà casuale

else:
        pos = [WIDTH, random.randint(0, HEIGHT)]
        
La posizione generata [x, y] viene aggiunta alla lista enemies, così il nemico potrà essere gestito nel gioco

enemies.append(pos)

# Sezione 3: movimento base dei nemici
questa parte serve a sapere in che direzione il nemico deve muoversi. dx è la distanza orizzontale tra giocatore e nemico, mentre dy è la distanza verticale 

for enemy in enemies[:]:
    dx = player_pos[0] - enemy[0]
    dy = player_pos[1] - enemy[1]
    
inoltre viene anche calcolata la distanza reale tra giocatore e nemico con il teorema di Pitagora, in modo da mantenere la velocità del nemico costante 

dist = math.hypot(dx, dy)

# Sezione 4: movimento diagonale e disegno 
per riuscire a muovere i nemici diagonalmente e ad una velocità costante, si utilizza di nuovo il teorema di Pitagora 

if dist != 0:
        enemy[0] += enemy_speed * (dx / dist)
        enemy[1] += enemy_speed * (dy / dist)
        
il nemico viene disegnato come un quadrato rosso centrato nella posizione [enemy[0], enemy[1]]

pygame.draw.rect(screen, (200, 50, 50),
                     (enemy[0] - 20, enemy[1] - 20, 40, 40))
