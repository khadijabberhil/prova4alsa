## SEZIONE 1 — Inizializzazione del gioco
Questa parte serve per preparare l’ambiente di Pygame, cioè creare lo schermo, impostare titolo e clock.
```import pygame
import random
import math

pygame.init()
```

# Schermo
WIDTH, HEIGHT = 1360, 800
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Arena Shooter")

clock = pygame.time.Clock()
## SPIEGAZIONE DEL CODICE
# pygame.init() 
avvia tutte le funzioni di Pygame (audio, grafica, ecc.).
# WIDTH e HEIGHT :
definiscono la grandezza della finestra.
# screen 
è la superficie su cui disegniamo tutto.
# clock 
serve per controllare il numero di frame al secondo (FPS), così il gioco è fluido.

# “Questa parte serve per creare la finestra del gioco e impostare le dimensioni dello schermo dove si muoverà il mio giocatore.”
## 🎮 SEZIONE 2 — Creazione del giocatore
Qui crei il giocatore, cioè un semplice rettangolo blu.
# Giocatore
```player_size = 40
player_pos = [WIDTH // 2, HEIGHT // 2]
player_speed = 5
```
## SPIEGAZIONE DELLA CREAZIONE DEL GIOCO 
# player_size 
è la grandezza del quadrato.
# player_pos 
è una lista con le coordinate (x, y).
Usi WIDTH // 2 e HEIGHT // 2 per posizionarlo al centro dello schermo.
# player_speed 
definisce quanto si muove ad ogni frame.

## “Qui creo il mio giocatore come un quadrato di 40 pixel, posizionato al centro dello schermo, con una velocità di movimento pari a 5 pixel per frame.”
## SEZIONE 3 — Movimento del giocatore!!!
Permette al giocatore di muoversi con i tasti W, A, S, D e non uscire dai bordi.
```keys = pygame.key.get_pressed()
if keys[pygame.K_w] and player_pos[1] > 0:
    player_pos[1] -= player_speed
if keys[pygame.K_s] and player_pos[1] < HEIGHT:
    player_pos[1] += player_speed
if keys[pygame.K_a] and player_pos[0] > 0:
    player_pos[0] -= player_speed
if keys[pygame.K_d] and player_pos[0] < WIDTH:
    player_pos[0] += player_speed
```
## Spiegazione sul come fare il movimento:
# pygame.key.get_pressed()
controlla quali tasti sono premuti.
K_w, K_s, K_a, K_d corrispondono ai tasti W, S, A, D.
# Ogni riga sposta il giocatore in una direzione:
W: su → diminuisce la coordinata y
S: giù → aumenta y
A: sinistra → diminuisce x
D: destra → aumenta x
Le condizioni con i bordi (> 0 e < WIDTH / HEIGHT) impediscono di uscire dallo schermo.
## “Ogni volta che premo un tasto, il programma aggiorna la posizione del giocatore. Le condizioni di controllo assicurano che il giocatore non esca mai dallo schermo: per esempio, non posso andare oltre il bordo sinistro se la x è già 0.”

## SEZIONE 4 — Disegno del giocatore sullo schermo
Dopo aver aggiornato la posizione, serve ridisegnare il giocatore.
```pygame.draw.rect(screen, (0, 150, 255),
                 (player_pos[0] - player_size // 2,
                  player_pos[1] - player_size // 2,
                  player_size, player_size))
```
# Spiegazione su come disegnare il giocatore sullo schermo :
pygame.draw.rect() disegna un rettangolo:
screen → dove disegnarlo
(0,150,255) → colore (blu)
le coordinate (x, y, width, height) → definiscono la posizione e la grandezza.
Usi player_pos[0] - player_size // 2 per centrare il rettangolo rispetto alle coordinate del giocatore.

## “Questa funzione disegna il mio giocatore come un rettangolo blu, centrato sulla sua posizione. Ad ogni frame, viene ridisegnato nella nuova posizione aggiornata.”

##  CONCLUSIONE 

# “In questa parte del codice ho creato il giocatore e il suo movimento. Ho impostato la posizione iniziale al centro dello schermo e ho gestito i movimenti con i tasti W, A, S, D. Ho aggiunto condizioni per evitare che il giocatore esca fuori dai bordi dello schermo. Infine, disegno il rettangolo che rappresenta il mio personaggio ad ogni frame, così si aggiorna visivamente.”
