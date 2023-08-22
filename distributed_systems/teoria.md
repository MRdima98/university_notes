# Introduzione

Il materia per lo studio è composto da slides. 
Libri di riferimento per materiale aggiuntivo:
- Distributed Systems: Principles and Paradigms

#### Esame

Progetto + discussione orale. È necessario prima completare delle attività di laboratorio
e avere la conferma dal prof. L'esame si prende tramite appuntamento quasi ogni settimana.

# C1
### Availability, Consistency, Failure
Il beneficio principale di un sistema distribuito è essere capace di nascondere 
un fallimento quando avviene. Se un sistema è in grado di nascondere gran parte 
del fallimento allora si dice che è *highly available*.

È possibile avere solo 2 delle 3 caratteristiche: consistency (C), availability (A), 
partition tollerance (P).

Un sistema consistent ha operazioni atomiche che avvengono in uno specifico tempo. 
Ogni operazione lettura avviene quindi dopo una scrittura, facendo in modo che il 
ritorno sia sempre corretto.

Availability significa che il sistema riesce a rispondere, non è però garantito 
che contenga il write più recente.

Consistency che il sistema ritorni la risposta corretta, ovvero che è l'ultimo
write e il messaggio di ritorno non è un errore.

Network partition che non c'è un singolo punto di fallimento, due nodi che falliscono 
la comunicazione non impediscono il corretto funzionamento del restante sistema.

ACID => atomic, consistency, isolation, durability

BASE: 
- basically available: risponderà sempre ma non è detta che mi dia il dato più recente,
perché richiede varie duplicazioni lungo vari nodi
- soft state: i dati cambiano nel tempo, non è garantita la consistency
- eventually consistent: sarai aggiornato con il dato più recente in tempi brevi

# M1 
### Replication and consistency
Il problema dei sistemi distribuiti è la consistency dei dati. Il nostro obietto è 
ridurre questo problema il più possibile.

Conit sta per consistency unit, e viene usato per misurare la consistency: 
 - deviazione numerica: la differenze tra il valore del conit e il valore relativo 
 dell'ultimo aggiornamento 
 - deviazione di ordine: differenza tra l'ordine di scrittura locale e quella del 
 immagine vera
 - deviazione in stallness: differenza tra il tempo di adesso e l'ultima scrittura 
 di un conit non locale

 Ci deve essere un ordine di scrittura globale, è possibile raggiungerlo tramite 2 
 modelli: 
  - squential consistency: ogni operazione segue lo stesso ordine di scrittura 
  - casual consistency: sono in ordine di cause effetto

Eventual consistency può essere un grosso sistema, che di solita ha solo un grosso 
centro che scrive gli aggiornamenti e tanti repliche da cui vengono letti. L'unico 
possibile conflitto avviene quando si tenda di leggere e scrivere in una risorsa 
in contemporanea. Il sistema non serve i dati più aggiornati ma di solito è 
accettabile in questi casi (tipo sito web), se per un tempo sufficiente non ci sono 
aggiornamenti il sistema diventare consistent.

Monotonic reads: data una lettura di un dato x, ogni successiva lettura garantisce 
x oppure un dato più recente di x, esempio un sistema di mail

Monotonic writes: la scrittura è completata prima di ogni altra operazione

Ready your writes: l'effetto di una scrittura sarà sempre visto dalla prossima 
lettura dello stesso processo

Write follow reads: una scrittura dopo una lettura di un dato garantisce che verrà 
salvato sul dato più recente oppure sullo stesso

Può essere necessario creare sia repliche dei dati ma anche repliche dei servizi 
oppure processi.

# M2 
### Dependability
