## Lezione 2: Sistema di sparo
## Analisi tecnica passo per passo
## a) rappresentazione dei proiettili

Ogni proiettile è rappresentato come una lista di tre valori:  
[x,y,angle]  
x,y = coordinate attuali del proiettile sullo schermo  
angle = direzione del moto ( in radianti), calcolata rispetto al giocatore e alla posizione del mouse


## b) Creazione del proiettile ( sparo) 
Quando l'utente clicca col tasto sinistro del mouse:  
``` python
if event.type == pygame.MOUSEBUTTONDOWN and event.button == 1:
    mx, my = pygame.mouse.get_pos()
```
mx,my sono le coordinate del mouse sullo schermo

Poi si calcola il vettore direzionale fra il giocatore e il mouse: 
dx = mx - player_pos[0]
dy = my - player_pos[1]

Da qui, si ottiene l'angolo di tiro:  
angle= math.atan2(dy,dx)

math.atan2(dy,dx) restituisce l'angolo ( in radianti) fra l'asse X e la linea che unisce il giocatore al puntatore, gestendo automaticamente i segni di dx/dy ( quindi anche i quadranti giusti).

Infine si crea e salva il proiettile nella lista:

```
bullets.append([player_pos[0], player_pos[1], angle])
```
Il proiettile parte dalla posizione attuale del giocatore e si muoverà nella direzione angle. 

## c) Movimento del proiettile
Si aggiorna posizione 







