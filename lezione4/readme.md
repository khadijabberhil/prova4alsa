# Lezione 4
Il ciclo while running: è il cuore del gioco. Continua a girare finché la variabile running è True. Questo ciclo esegue le seguenti operazioni in ogni frame:

# Controllo del Framerate:
clock.tick(60) limita il gioco a 60 frame per secondo (FPS). Questo assicura che il gioco si muova a una velocità costante, indipendentemente dall'hardware su cui è eseguito.

# Svuotamento dello Schermo:
screen.fill((30, 30, 30)) riempie lo schermo con un colore grigio scuro. Questo cancella il frame precedente, preparandolo per il nuovo frame da disegnare.

# Gestione degli Eventi:
Il blocco for event in pygame.event.get(): gestisce gli eventi, come i tasti premuti e i movimenti del mouse.

if event.type == pygame.QUIT:: Se l'utente chiude la finestra, running viene impostato su False, interrompendo il ciclo e terminando il gioco.

if event.type == pygame.MOUSEBUTTONDOWN and event.button == 1:: Se il tasto sinistro del mouse viene premuto, viene calcolato l'angolo tra la posizione del giocatore e la posizione del mouse, e un nuovo proiettile viene aggiunto alla lista bullets.

# Movimento del Giocatore:
Il blocco keys = pygame.key.get_pressed() controlla quali tasti sono premuti. Le istruzioni if spostano il giocatore in base ai tasti premuti (W, A, S, D), assicurandosi che il giocatore non esca dai bordi dello schermo.

# Disegno del Giocatore:
pygame.draw.rect(...) disegna un rettangolo blu che rappresenta il giocatore nella sua posizione corrente.

# Gestione dei Proiettili:
Il ciclo for bullet in bullets[:] itera attraverso ogni proiettile nella lista bullets. L'uso di [:] crea una copia della lista, permettendo di rimuovere elementi dalla lista originale durante l'iterazione senza causare errori.
bullet[0] += bullet_speed \* math.cos(bullet[2]) e bullet[1] += bullet_speed \* math.sin(bullet[2]) aggiornano la posizione di ogni proiettile in base alla sua velocità e all'angolo di direzione.
Se un proiettile esce dallo schermo, viene rimosso dalla lista bullets.
pygame.draw.circle(...) disegna un cerchio giallo per ogni proiettile.

# Spawn dei Nemici:
enemy_timer += 1 incrementa un timer.
if enemy_timer >= enemy_spawn_delay:: Quando il timer raggiunge il valore di enemy_spawn_delay (60 frame), viene chiamata la funzione spawn_enemy() per creare un nuovo nemico. Il timer viene poi resettato.

# Movimento dei Nemici:
Il ciclo for enemy in enemies[:] itera attraverso ogni nemico nella lista enemies.
Vengono calcolate la distanza e la direzione tra il nemico e il giocatore.
Il nemico si muove verso il giocatore.
pygame.draw.rect(...) disegna un rettangolo rosso per ogni nemico.
Il codice verifica se un proiettile colpisce un nemico. Se lo colpisce, sia il proiettile che il nemico vengono rimossi dalle rispettive liste.

# Aggiornamento dello Schermo:
pygame.display.flip() aggiorna l'intero schermo, mostrando tutto ciò che è stato disegnato nel frame corrente.
