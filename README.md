# Progetto Reti Logiche
Prova Finale del corso di Reti Logiche del Prof. Salice Fabio effettuato durante l'anno accademico A.A 2020/2021 al Politecnico di Milano.
## Descrizione generale
La specifica della Prova finale (Progetto di Reti Logiche) 2020 è ispirata al metodo di
equalizzazione dell’istogramma di una immagine .

Il metodo di equalizzazione dell’istogramma di una immagine è un metodo pensato per
ricalibrare il contrasto di una immagine quando l’intervallo dei valori di intensità sono molto
vicini effettuandone una distribuzione su tutto l’intervallo di intensità, al fine di incrementare il
contrasto.

Il modulo da implementare dovrà leggere l’immagine da una memoria in cui è memorizzata,
sequenzialmente e riga per riga, l’immagine da elaborare. Ogni byte corrisponde ad un pixel
dell’immagine.
La dimensione della immagine è definita da 2 byte, memorizzati a partire dall’indirizzo 0. Il
byte all’indirizzo 0 si riferisce alla dimensione di colonna; il byte nell’indirizzo 1 si riferisce
alla dimensione di riga. La dimensione massima dell’immagine è 128x128 pixel.
L’immagine è memorizzata a partire dall’indirizzo 2 e in byte contigui. Quindi il byte
all’indirizzo 2 è il primo pixel della prima riga dell’immagine.

L’immagine equalizzata deve essere scritta in memoria immediatamente dopo l’immagine
originale

### Dati
Le dimensioni dell’immagine, ciascuna di dimensione di 8 bit, sono memorizzati in una
memoria con indirizzamento al Byte partendo dalla posizione 0: il byte in posizione 0 si
riferisce al numero di colonne (N-COL), il byte in posizione 1 si riferisce al numero di righe
(N-RIG).
I pixel del’immagine, ciascuno di un 8 bit, sono memorizzati in memoria con indirizzamento
al Byte partendo dalla posizione 2.
I pixel della immagine equalizzata, ciascuno di un 8 bit, sono memorizzati in memoria con
indirizzamento al Byte partendo dalla posizione 2+(N-COL*N-RIG)+1.

#### Note ulteriori sulla specifica
1. Si noti che nel modulo da implementare, FLOOR(LOG2( X )) è un numero intero con
valori tra 0 e 7 facilmente ricavabile da controlli a soglia.
2. Si faccia attenzione al numero di bit necessari in ogni passaggio.
3. Il modulo deve essere progettato per poter codificare più immagini, ma l’immagine da
codificare non verrà mai cambiata all’interno della stessa esecuzione, ossia prima
che il modulo abbia segnalato il completamento tramite il segnale DONE. Si veda il
prossimo punto per il protocollo di re-start.
4. Il modulo partirà nella elaborazione quando un segnale START in ingresso verrà
portato a 1. Il segnale di START rimarrà alto fino a che il segnale di DONE non verrà
portato alto; Al termine della computazione (e una volta scritto il risultato in memoria),
il modulo da progettare deve alzare (portare a 1) il segnale DONE che notifica la fine
dell’elaborazione. Il segnale DONE deve rimanere alto fino a che il segnale di START
non è riportato a 0. Un nuovo segnale start non può essere dato fin tanto che DONE
non è stato riportato a zero. Se a questo punto viene rialzato il segnale di START, il
modulo dovrà ripartire con la fase di codifica.
5. Il modulo deve essere progettato considerando che prima della prima codifica verrà
sempre dato il reset al modulo. Invece, come descritto nel protocollo precedente, una
seconda elaborazione non dovrà attendere il reset del modulo.
