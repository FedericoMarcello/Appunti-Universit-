# Capitolo 1: Complessità Computazionale:
 Esempio di istruzioni su quantità scalari:
![[Pasted image 20241003161425 1.png]]

#### Studio dei cicli:
Ciclo:
$$ \sum_{i=0}^n C(i) $$
-  i è una iterazione
- I è l'insieme di tutte le iterazioni
- C(i) è il costo della i-esima iterazione
Spesso (ma non sempre) il costo delle iterazioni è costante.
A cicli innestati corrispondono somme multiple:
![[Pasted image 20241003161911 1.png]]
ciò può essere rappresentato come:
$$ \sum_ {i=1}^m \sum_{j=1}^n C(statement_{i,j}) $$
##### Esempi:
###### Somma scalata di vettori di dimensione n: $c=a+ alpha * b$
![[Pasted image 20241003162829 1.png]]
Dove il costo è:
$$\sum_{i=1} ^n 2 = 2\sum_{i=1} ^n 1= 2n $$
###### Prodotto matrice vettore $y=y+Ax$ (matrice m x n):
![[Pasted image 20241003163322 1.png]]
Dove il costo è:
$$ \sum_{i=1}^m \sum_{j=1}^n2 =2mn $$
###### Matrice per matrice $C= C + A * B$ (con matrici m x k x n):
![[Pasted image 20241003163714 1.png]]
Dove il costo è:
$$ \sum_{i=1}^m \sum_{j=1}^n \sum_{l=1}^k 2 = 2mnk$$
###### Risoluzione di un sistema triangolare:
Se la matrice dei coefficienti di un sistema è triangolare inferiore L, il sistema Lx si risolve facilmente per sostituzione in avanti:
![[Pasted image 20241003164039 1.png]]
Se la diagonale è unitaria, il passo di divisione può essere saltato. Andiamo ora a dimostrare che il numero di operazioni è $O(n^2)$ :
Quale è il costo?
- Ad ogni iterazione del ciclo esterno i= 1, ..., n abbiamo un ciclo interno, una assegnazione e una divisione,
- Il ciclo interno j=1,...,i-1 è un prodotto scalare e contiene due operazioni per iterazione.
- Ogni iterazione del jcì



##### Algoritmo di inserzione:
![[Pasted image 20241003170210 1.png]]
Abbiamo una struttura simile a quella del sistema triangolare, ma per il ciclo interno:
- nel caso migliore il ciclo while esegue un controllo ed esce immediatamente
- Nel caso peggiore viene eseguito i-1 volte:
- Abbiamo quindi la complessità $\Omega$(n) e $O(n^2)$ 


##### Algoritmo di ricerca binaria:
![[Pasted image 20241003170916 1.png]]
- alla prima invocazione di BinarySearch la dimensione del vettore è n;
- Ad ogni invocazione ricorsiva la dimensione si dimezza
- nel caso peggiore bisogna eseguire un numero di chiamate ricorsive k:
$$\frac{n}{2^k} \le 1 => k = log_2(n)$$
- quindi BinarySearch è $O(log(n))$
##### Funzioni Ricorsive:
Ciascuna istanza di una funzione ricorsiva applicata ad un problema è una istanza in base n = 1, oppure divide il problema corrente di dimensione n in un certo numero di sottoproblemi di dimensione più piccola, le cui soluzioni saranno poi combinate per costruire la soluzione complessiva.
In questa analisi si usano spesso delle relazioni di ricorrenza, ossia delle equazioni del tipo:
$$T(n)=G(T(n-n_1), T(n-n_2),T(n-n_3),...,T(n-n_k))$$
Con $n_j < n$
###### Esempio con lineare a termini costanti del tipo:
$$T(n)=(\sum_{i=1}^k a_i * T(n-i))+c*n^\beta,n> k $$
#### Teorema sulle Ricorrenze Lineari:
Siano $a_1, a_2,...,a_k$ costanti intere non negative, $c >0,\beta \ge 0$ e sia T(n) definito dalla ricorrenza:
![[Pasted image 20241003172400 1.png]]
##### Dimostrazione:
Si supponga che solo 1 dei coefficienti $a_i$ non sia nullo. Allora $a=a_j$, supponendo $n=m+p*j$ con $1 \le m \le k$
Sostituendo otterrò:![[Pasted image 20241003172625 1.png]]
A questo punto abbiamo due casi:
1) 
![[Pasted image 20241003172714 1.png]]

2) 
![[Pasted image 20241003172749 1.png]]

Nel caso generale di più di un coefficiente non nullo, necessariamente $a \ge 2$  
![[Pasted image 20241003173013 1.png]]
che si riconduce al caso precedente.








#### Trasformata di Fourier Discreta:
DFT opera su sequenze (campionamenti di una funzione).
$$f_j,j=0,...,N-1 $$
e si definisce come $$\sum_{j=0}^{N-1} e^{\frac{2\pi ijk},{}} $$
E' evidente che a



# Capitolo 2: Introduzione C
# Capitolo 3: Dati elementari, operatori e strutture di controllo:
### Dati di base:

Per i tipi di dati elementari, possiamo dire che ne esistono di diversi tipi:
#### Caratteri:
- char: minimo tipo intero, dimensione minima 8 bit
#### Interi:
- short int: dimensione minima 16 bit
- int: dimensione $\ge$ short int, quindi $\ge 16$ 
- long int: dimensione minima di 32 bit, $\ge$ int
- long long int: dimensione minima 64 bit;
#### Variabili a virgola mobile:
- float/ double/long double
#### Informazione aggiuntive:
![[Pasted image 20241115163707.png]]
![[Pasted image 20241115163719.png]]
#### Tipi booleani:
Nel linguaggio C non esiste un tipo booleano, cioè i valori logici vengono gestiti con gli interi 1 e 0 (true e false)
Nel C11 viene definito il tipo $\_Boo1$ (da utilizzare con il rispettivo header : stdbool.h)
E vengono utilizzate le seguenti keywords:
- bool, true, false
#### Corso C
Per vedere a livello informatico:
[[Corso#Lezione 2 (variabili)]]
[[Corso#Lezione 3 (costanti)]]

### Operatori:
#### Cosa sono?
Sulle variabili agiscono degli operatori per costruire delle espressioni, ne esistono di diverso tipo:
- Operatori di assegnazione: =
- Operatori aritmetici: $~+,~-,~*,~/$
- Operatori relazionali: $<,~>,~==,~!=$
- Operatori di incremento: $++,~--$
- Operatori logici: $|,~||,~\&,~\&\&$
Bisogna prestare attenzione agli operatori interi:
```c title:"Operatori interi"
int main(int argc, char *argv[]) { 
		double result = 1 / 2 * 2; 
		printf("Result is %lf\n", result); 
		return 0;
```
Operatori di cast:
```c title:"Operatori interi"
int main(int argc, char *argv[]) { 
		double result = (double 1) / 2 * 2; 
		printf("Result is %lf\n", result); 
		return 0;
```

#### Riassunto:
![[Pasted image 20241115164302.png]]
#### Corso C:
[[Corso#Numeri interi]]
[[Corso#Operazioni]]
[[Corso#Operatori di Assegnazione]]
[[Corso#Operatori di comparazione]]
[[Corso#Operatori Logici]]

### Strutture di Controllo:
#### Cosa sono?
è un modo per alterare il flusso delle istruzioni ed imporre delle condizioni:
##### Cicli:
1) If:
![[Pasted image 20241115161351.png]]
2) while: Quando il numero di iterazioni non è prevedibile, si usa while
![[Pasted image 20241115161519.png]]
##### Interruzione dei cicli:
1) break: 
Con l'istruzione break si esce dal ciclo circostante:
![[Pasted image 20241115161803.png]]
2) continue: 
Con l'istruzione continue si passa alla prossima iterazione del ciclo
![[Pasted image 20241115161915.png]]
#### Corso C:
[[Corso#If, Else, Else if]]
[[Corso#Lezione 11 ( cicli while)]]
[[Corso#While]]
[[Corso#While do]]
[[Corso#Lezione 13 (break e continue)]]
### Chiamate a funzioni:
#### Cosa sono?
Una funzione racchiude un insieme di istruzioni da eseguire su dati di volta in volta diversi:
![[Pasted image 20241115162116.png]]
Ci sono dei vantaggi nello scrivere una funzione:
- C'è la possibilità di riusarla più volte;
- C'è la possibilità di separare interfaccia da implementazione;
Gli argomenti di una funzione vengono normalmente passati per _valore_
![[Pasted image 20241115162407.png]]
#### Corso C:
[[Corso#Lezione 17 (funzioni)]]
[[Corso#Chiamata di Funzioni]]
[[Corso#Funzioni Ricorsive]]
...
### Variabili:
Ogni variabile ha un ambito (scope) e una conseguente _visibilità_
Esistono diversi tipi di variabile:
- Globale 
- Locali
- Statiche
Nel C89 le variabili devono essere dichiarate all'inizio di una funzione. Nelle versioni successive no.
Bisogna ricordarsi 
- di dichiarare le variabili importanti della procedura all'inizio (per aver subito idea della complessità)
- di dichiarare le variabili di uso locale e temporaneo nel blocco di codice che le usa (o dentro un ciclo).
#### Corso C:
[[Corso#Lezione 2 (variabili)]]
[[Corso#Lezione 14 (Variabili globali)]]
# Capitolo 4 (Dati derivati: Array)
#### Cosa sono?
Possiamo specificare dei tipi derivati dai tipi appena visti. 
#### Array:
Un _array_ è un tipo di dato aggregato costituito da molteplici dati elementari i quali:
- hanno tutti lo stesso tipo di base
- sono identificati da un indice numerico 
Il numero di indici necessari per identificare un elemento si dice **dimensione**. Quindi esisteranno array monodimensionali, bidimensionali etc..
##### Esempi:
###### Array monodimensionale:
```c title:"array monodimensionale"
#include <stdio.h>
#define N100 3 
int main(int argc, char *argv[])
{ 
int a[N],i; 
for (i=0; i<N; i++)
a[i]=i;
}
```
Il primo elemento corrisponde all'elemento di indice 0 (e l'ultimo a N-1);
L'indirizzo in memoria dell'elemento i si trova aggiungendo $I*s$ all'indirizzo base di a, dove s è la dimensione in bytes di ciascun elemento.
![[Pasted image 20241115165420.png]]
###### Array bidimensionale:
```c title:"array bidimensionale"
#include <stdio.h>
#define N100 3 
int main(int argc, char *argv[])
{ 
int a[N],i; 
for (i=0; i<N; i++)
a[i]=i;
}
```
Il primo elemento corrisponde all'indice  $[0][0]$ e l'ultimo a $[M-1][N-1]$
La memorizzazione avviene per righe;
L'indirizzo in memoria dell'elemento i,j si trova aggiungendo $((i*N)+j)*S$
![[Pasted image 20241115172212.png]]
#### Array e funzioni:
Come si fa a passare da un array ad una funzione?
##### Modo tradizionale:
Il modo "tradizionale" consiste nell'usare un puntatore
![[Pasted image 20241115172550.png]]
##### Modo moderno
Il modo "moderno" consiste nell'usare lo standard C99 e seguenti
![[Pasted image 20241115172404.png]]
Nel linguaggio C una stringa è semplicemente un array di caratteri, terminato con il carattere '\0'
![[Pasted image 20241115172458.png]]
#### Corso C:
[[Corso#Lezione 15 (array)]]
# Capitolo 5 (Dati derivati: Puntatori):
#### Cosa sono?
Un puntatore in C è una variabile che contiene un indirizzo:
![[Pasted image 20241024161337 1.png]] 
L’operatore **_&_** consente di **accedere all'indirizzo di un’altra variabile**, quindi di assegnarlo ad un puntatore. I puntatori hanno normalmente un tipo associato, ma ne esistono anche di generici:![[Pasted image 20241024161633 1.png]]
#### Come si usano?
- per dichiarare una varibile:
		type * ptr,
- Accedere al valore “puntato”(ossia, all’indirizzo corrispondente)
		val= * ptr
- Accedere ad un indirizzo
		Type * ptr
- Aritmetica dei puntatori:
		vs = * (ptr+i)
		ptr++
#### Incrementare un puntatore:
Cosa vuol dire incrementare un puntatore?
$$ptr++$$
Aumentare il valore dell’indirizzo di un numero di byte pari alla dimensione del tipo di base.
In altre parole significa aggiungere il valore corrispondente al numero di byte che il tipo di dato di riferimento occupa. Per esempio visto che l'intero occupa 4 byte, per ogni +1 al puntatore, andrò ad aggiungere +4 all'indirizzo.
##### Esempi:
```c title:"Esempio incremento puntatore"
int * prt=1000; /se “sizeof(int)“ == 4 allora: (ptr+2) == 1008>
char * cp=2000; /se ”sizeof(int)” == 1, allora *\(cp+3) == 2003>
```
#### Operazioni valide con puntatori:
- somma e sottrazioni con interi
- Sottrazione tra puntatori
- Confronto per uguaglianza di puntatori
N.B _incrementare_ un puntatore void con _$*$  è un operazione illegale_
#### Memoria dinamica:
Come gestire necessità di memoria di dimensioni non prevedibili al momento della scrittura del programma? Quindi come posso decidere la memoria da utilizzare al momento dell'esecuzione del programma?
- ottenere memoria con $malloc$:
```c title:"malloc"
void * malloc(size_t size)
```
- Rilasciare la memoria con 
```c title:"free"
Void free(void* ptr)
```
##### Esempio:
Se abbiamo bisogno di un array di K numeri interi, possiamo eseguire:![[Pasted image 20241024172634 1.png]]
dove vengono usati:
- funzione `malloc` per allocare dinamicamente memoria per un array di `K` interi.
- `malloc` accetta come argomento il numero di byte da allocare. La quantità di memoria necessaria viene calcolata moltiplicando `K` (il numero di elementi) per `sizeof(int)`, che rappresenta la dimensione in byte di un intero.
- Il cast `(int *)` converte il puntatore restituito da `malloc` (che è di tipo `void *`) in un puntatore a intero `int *`, adatto al tipo della variabile `a`
#### Errori con puntatori:
Quali errori vanno evitati?
- controllare sempre che malloc sia andata a buon fine:
![[Pasted image 20241024172908 1.png]]
- tentare di rilasciare un puntatore non allocato:
![[Pasted image 20241024173001 1.png]]
- creare una memory leak:
![[Pasted image 20241024173156 1.png]]
fare attenzione all’uso delle stringe
- quando si alloca una stringa, ricordare sempre il carattere di terminazione: ‘\0’
- Usare le funzioni di copia strcpy, strncpy
- Concatenazione e “tokenizzazione” di stringhe sono una fonte di errori
#### Passaggio di parametri:
Partendo dall'esempio di codice, vediamo come utilizzare i parametri nella dichiarazione di una funzione:
![[Pasted image 20241115185451.png]]
Nel linguaggio C i parametri vengono passati per valore, ossia la funzione ne riceve una copia.
Per risparmiare il tempo della copia, ovvero per modificare l’argomento, occorre passare il parametro per riferimento, ovvero passarne un puntatore
![[Pasted image 20241115190938.png]]
Analogamente se si vuole modificare un puntatore in una funzione:![[Pasted image 20241115191029.png]]
#### Corso C:
[[Corso#Lezione 18 (puntatori)]]

# Capitolo 6 (Dati derivati: Strutture)
#### Cos'è?
Una struttura è un tipo di dato derivato costituito da una collezione di dati potenzialmente disomogenei tra di loro; i singoli elementi vengono acceduti per nome
##### Esempi:
1° esempio
![[Pasted image 20241115191755.png]]
2° esempio![[Pasted image 20241115191904.png]]
![[Pasted image 20241115191949.png]]
#### Uso delle strutture:
Le strutture sono fondamentali:
- nella realizzazione di qualunque complesso
- come livello di astrazione necessario a ragionare sui dati
- per incapsulare funzionalità, per rendere possibile miglioramenti futuri
Una struttura può, inoltre, contenere un puntatore (o anche diversi puntatori) ad una variabile del suo stesso tipo:
##### Esempio:
![[Pasted image 20241115200604.png]]
#### Corso C:
[[Corso#Lezione 19 (strutture)]]
# Capitolo 9: (Tipi e strutture dati)
### Definizioni:
- Un dato è un valore appartenente ad un insieme. 
- Un tipo di Dato (astratto) è costituito da un in insieme di valori e dagli operatori che su questi valori
- Una struttura dati è una collezione di dati così come memorizzati nel calcolatore, insieme con i programmi che su di loro agiscono. In altre parole, è una particolare realizzazione di un tipo di dato astratto, ma ad un tipo di dato astratto possono corrispondere più realizzazioni diverse.
Per l'analisi generale conviene prima conoscere l'identità dei dati e sulle operazioni, solo successivamente la rappresentazione.
### Tipi di Dati Astratti: (SEQUENZA)
Una sequenza è un'insieme di elementi caratterizzati da una posizione $pos_i$ $$S=s_{1},s_{2},...,s_{n}$$
Esisteranno inoltre due posizioni speciali, $pos_{0}$ e $pos_{n+1}$ che marcano l'inizio e la fine della sequenza.
#### Metodi per Sequenza:
![[Pasted image 20241116114725.png]]

#### Insiemi "SET"
Un insieme è una collezione di elementi identificabili (i "membri" dell'insieme).
- il numero di elementi di un insieme è la sua cardinalità |$A$|
- Un insieme che non contiene elementi si dice vuoto $s$
- La relazione fondamentale è l'_appartenenza_  $x\in A$ di un elemento x ad un insieme A
- Dalla appartenenza deriva la relazione di inclusione $A\subseteq B$ che è vera se tutti gli elementi di A appartengono anche a B
Sugli insiemi si applicano gli operatori di unione e differenza simmetrica
##### Operatori sugli insiemi:
![[Pasted image 20241116162715.png]]
#### Altri esempi di dati Astratti:
**Dizionario**: Insieme di coppie chiave valore dove la ricerca si effettua per chiave allo scopo di recuperare il valore.
**Grafo**: Una collezione di due insiemi, i vertici o nodi $V$ e gli archi $\epsilon\subseteq V~$x$~V$ 
**Albero**: Un grafo che, escludendo l'orientamento, non contiene cicli
**Matrici**: Insieme di elementi (coefficienti) identificati da due indici numerici.
# Capitolo 10: (Liste, Pile e Code)
### Liste:
#### Cosa sono?
Le liste sono delle strutture che realizzano il tipo di dato astratto "Sequence"
La lista con puntatori singoli consente di realizzare gli operatori:
- Empty
- Head
- Next
- Insert
con una complessità $O(1)$. 
La complessità degli operatori `prev` e `remove` è $O(n)$, mentre quella dell'operatore `tail` dipende dall'implementazione.
Si noti che le aree di memoria occupate dai dati non hanno in generale alcuna relazione ovvia tra di loro.
Ciascun nodo della lista ha due componenti
- Un campo **`value`**;
- Un campo **`next`** che contiene il puntatore al prossimo elemento;
La stessa lista è realizzata con un puntatore al primo elemento (se esiste, sennò nil). Ciò avverrà in modo specchiato anche alla fine della lista, infatti l'ultimo elemento di essa avrà un campo `next` che vale **nil**. 
#### Liste con puntatore singolo:
Questi sono due esempi equivalenti di lista, con la differenza che nella seconda variante si mantiene esplicitamente un puntatore all'ultima posizione della lista.
![[Pasted image 20241118173634.png]]
La prima cella è indirizzata da una variabile L di tipo puntatore
#### Metodi (funzioni) per liste.
![[Pasted image 20241118173849.png]]
#### Liste con puntatore doppio:
In questo caso ciascun nodo della lista ha tre componenti:
- Un campo `value`
- Un campo `next` che contiene il puntatore al prossimo elemento
- un campo `prev` che contiene il puntatore al precedente elemento
![[Pasted image 20241118174019.png]]
Il vantaggio è che il metodo `prev` ha ora costo O(1).
#### Metodi per le liste con puntatore doppio:
![[Pasted image 20241118180345.png]]
#### Liste con vettori:
#### Cosa sono?
Una realizzazione alternativa consiste nel memorizzare gli elementi della sequenza in un vettore. In questo caso la posizione di un elemento è un indice del vettore e $pos_{i}$ 
è proprio uguale ad i, per $1\le i\le n$. In altri termini, alla contiguità tra elementi della sequenza, corrisponde una contiguità di memorizzazione. Questa realizzazione permette agevolmente, cioè in tempo $O(1)$ di passare da un elemento al successivo (precedente), di rendersi conto se si tenta di superare un estremo della sequenza, di leggere o modificare il valore di un elemento, anche tramite un accesso diretto e non sequenziale.
Graficamente, si può vedere l'aggiornamento dei puntatori nelle procedure `remove()` ed `insert()`:
![[Pasted image 20241118184111.png]]
Se implementiamo la lista con un vettore, la posizione di riferimento corrisponde all'indice dell'elemento nel vettore. In questo caso la lista conterrà:
- Un vettore V atto a contenere i valori
- La dimensione del vettore D
- Il numero di elementi attualmente presenti K, ovvero l'indice dell'ultimo elemento attualmente occupato S (con valore iniziale -1)
Attraverso questa implementazione si può rappresentare la coda della lista come:
![[Pasted image 20241118183734.png]]
#### Problemi:
##### Problema 1.0
L'inserimento di un vettore in una posizione arbitraria costa $O(N)$, poiché occorre traslare i contenuti del vettore:
![[Pasted image 20241118184151.png]]
Supponiamo quindi che gli inserimenti avvengano sempre in coda, ossia $P=L.S+1$; cosi da far sembrare che il costo sia $O(1)$
Da questa risposta, sorge il
##### Problema 1.1
Occorre gestire la dimensione del vettore V:
![[Pasted image 20241118184446.png]]
consideriamo dunque l'operazione di `realloc`:![[Pasted image 20241118185559.png]]
##### Problema 1.2
Come scegliere `newsize`?
La scelta più ovvia è:
$$newsize\leftarrow oldsize+d$$
##### Costo medio
Consideriamo ora il costo di N inserimenti con incremento d costante:
- gli eventi di riallocazione avverranno ogni d inserimenti
- ad ogni riallocazione $i=d*k$ si pagherà un costo lineare $d*(k-1)$
Quindi il costo di $N = d*p$ sarà $$\sum\limits_{k=1}^{P}d*(k-1)=d\sum\limits_{k=0}^{P}k*\frac{P*(P-1)}{2}$$ che è circa uguale a $$d*\frac{P^2}{2}=\frac{N^{2}}{2d}=O(N^{2})$$
e dunque il costo medio di ogni singolo inserimento è $$O(N)$$
#### Altri casi:
![[Pasted image 20241118191251.png]]

### Pile
#### Cosa sono?
Una pila è una sequenza di elementi di un certo tipo in cui è possibile aggiungere o togliere elementi soltanto ad un estremo (la "testa") della sequenza. Può essere vista come un caso speciale di sequenza in cui l'ultimo elemento inserito è anche il primo ad essere rimosso e non è possibile accedere ad alcun elemento che non sia quello in testa. Tale meccanismo di accesso è detto LIFO (Last In First Out), cioè il primo elemento ad essere analizzato è l'ultimo ad essere "arrivato".
Inoltre, sia gli inserimenti che le cancellazioni avvengono ad un estremo della struttura dati, ovvero:
- Gli inserimenti avvengono solo dopo l’ultimo elemento 
- La cancellazione avviene solo sull'ultimo elemento
Un esempio di uso delle pile si ha nella gestione delle procedure ricorsive. 
Nella terminologia, quando si parla di pile, si utilizzano i seguenti nomi:
- push(P,v) per l'operazione di inserimento
- pop(P) per l'operazione di cancellazione (che restituisce il contenuto dell'elemento cancellato)
- top(P) per l'operazione che legge l'elemento in cima alla pila.
### Code:
Analogamente una coda, (_queue_) è una sequenza di elementi di un certo tipo, in cui possibile aggiungere elementi ad un estremo (il "fondo") e togliere elementi dall'altro estremo (la "testa").
Può essere considerata come una particolare sequenza il cui il primo elemento inserito è anche il primo ad essere rimosso e non è possibile accedere ad alcun elemento che non sia quello in testa o quello in fondo. Differentemente questo meccanismo è detto FIFO ("First In First Out").
Questo tipo di dato è possibile intenderlo come una specializzazione della lista, in cui:
- Gli eventi di inserimento avvengono solo ad un estremo della lista (prima della testa, o dopo la coda)
- Gli eventi di cancellazione avvengono solo all'altro estremo (o coda o testa)
- In questo contesto prendono il nome le due funzioni:
- enqueue (Q, v) per l'operazione di inserimento;
- dequeue(Q) per l'operazione di cancellazione (che restituisce il contenuto dell'elemento cancellato)
- 
### Differenze:
Anche se le operazioni della pile e delle code possano essere simulate con le operazioni di liste, è utile utilizzare nomi diversi. Per esempio, nel caso del tipo di dato pila (stack), l'operazione di lettura per il punto sul punto più alto top() e 
# Capitolo 11: (Alberi)
## Strutture ad albero:
### Introduzione:
Gli alberi sono un tipo di struttura dati presente in moltissime applicazioni in informatica. Per esempio, una ragione per usare gli alberi potrebbe essere perché si desidera memorizzare informazioni che forma naturalmente una gerarchia.
Ogni albero è costituito da un insieme di _Nodi_ (nodes) collegati fra di loro. Ognuno di questi contiene informazioni e presenta (tranne la <span style="color:rgb(185, 88, 24)">radice</span> (root) che non lo ha proprio) uno ed un solo nodo <span style="color:rgb(255, 0, 0)">padre</span>. Può avere degli antenati e può avere dei <span style="color:rgb(225, 137, 188)">figli</span> (children) e discendenti, in caso contrario, si dice <span style="color:rgb(0, 176, 80)">foglia</span>.
Una ragione per usare gli alberi potrebbe essere perché si desidera memorizzare informazioni che forma naturalmente una gerarchia
Da ogni nodo parte un <span style="color:rgb(0, 112, 192)">sottoalbero</span> (che potrebbe contenere solo il nodo) di cui il nodo è radice.
![[Pasted image 20241121152241.png]]
L'ordine in cui compaiono i figli è significativo, possiamo infatti dire che un albero è una generalizzazione di una lista, ma anche che una lista può essere un caso particolare di albero.
Concettualmente un nodo e una radice di un sottoalbero sono la stessa cosa.
### Tipi di alberi:
![[Pasted image 20241121135857.png]]

## Alberi ordinati:
L'albero ordinato possiede due caratteristiche:
- **L'ordine dei figli di ogni nodo è significativo.**
    - Ad esempio, se un nodo ha tre figli, l'ordine di questi (primo figlio, secondo figlio, terzo figlio) è importante.
    - Cambiare l'ordine dei figli cambierebbe il significato dell'albero.
- **I figli di ciascun nodo sono ordinati da sinistra a destra.**
    - Questa proprietà consente di distinguere il "primo figlio", "secondo figlio", ecc.
![[Pasted image 20241121121153.png]]
## Albero Binario:
### Caratteristiche:
#### Cos'è?
Un albero binario è un tipo specifico di albero (ordinato) in cui ogni nodo può avere un massimo di due figli collegati ad esso. Alcuni tipi comuni di alberi binari includono alberi binari completi, alberi binari incompleti, alberi binari bilanciati e alberi binari degenerati o patologici.
Un albero binario può essere memorizzato in un vettore: se il padre è in posizione i i due fili sono nelle posizioni $2i$ e $2i+1$. Prendiamo come esempio il seguente albero
![[Pasted image 20241104104512.png]]
Se volessimo creare un vettore di riferimento, dovremmo utilizzare questa tabella per assegnare i valori:

| figli     | 2   | 3   | 6   | 4   | 7   | 1   | 5   |
| --------- | --- | --- | --- | --- | --- | --- | --- |
| posizione | 1   | 2   | 3   | 4   | 5   | 6   | 7   |

#### Funzioni di riferimento:
##### Introduzione:
L'immagine seguente mostra un'implementazione di base delle operazioni per la gestione di un **albero binario**. Ogni nodo dell'albero contiene:
- Un riferimento al **genitore** (`Node parent`).
- Due puntatori ai suoi figli, a sinistra (`Node left`) e a destra (`Node right`).
- Un **valore** associato al nodo (`Item value`).
![[Pasted image 20241121185722.png]]
##### Analisi:
[(Per un'analisi migliore)](https://chatgpt.com/c/673f6cf0-5d10-800c-a0b0-ef34d25818b7)
###### 1. Function `Tree(item v)`
Questa funzione crea un nuovo nodo dell'albero con un valore specificato (`v`).  
**Passaggi**:
1. Crea un nuovo nodo `t`.
2. Imposta il valore di `t` uguale a `v`.
3. Inizializza i puntatori del nodo:
    - `t.left` e `t.right` sono impostati a `nil` (nessun figlio iniziale).
    - `t.parent` è anch'esso impostato a `nil` (nessun genitore iniziale).
4. Restituisce il nodo appena creato.

---

###### 2. Function `insertLeft(Tree t)`

Inserisce un nodo come **figlio sinistro** del nodo corrente.  
**Passaggi**:

1. Imposta il campo `parent` del nodo `t` al nodo corrente (`this`).
2. Aggiorna il puntatore sinistro (`left`) del nodo corrente per farlo puntare a `t`.

---

###### 3. Function `insertRight(Tree t)`

Inserisce un nodo come **figlio destro** del nodo corrente.  
**Passaggi**:

1. Imposta il campo `parent` del nodo `t` al nodo corrente (`this`).
2. Aggiorna il puntatore destro (`right`) del nodo corrente per farlo puntare a `t`.

---
###### 4. Function `deleteLeft()`

Elimina il sottoalbero radicato nel **figlio sinistro** del nodo corrente. **Passaggi**:

1. Controlla se il figlio sinistro (`left`) esiste.
    - Se esiste:
        - Chiama ricorsivamente `deleteLeft()` sul sottoalbero sinistro.
        - Chiama ricorsivamente `deleteRight()` sul sottoalbero sinistro per eliminare eventuali figli del nodo sinistro.
        - Elimina il nodo sinistro.
2. Alla fine, imposta `left` a `nil`.

---

###### 5. Function `deleteRight()`

Elimina il sottoalbero radicato nel **figlio destro** del nodo corrente.  
**Passaggi**:

1. Controlla se il figlio destro (`right`) esiste.
    - Se esiste:
        - Chiama ricorsivamente `deleteLeft()` sul sottoalbero destro.
        - Chiama ricorsivamente `deleteRight()` sul sottoalbero destro per eliminare eventuali figli del nodo destro.
        - Elimina il nodo destro.
2. Alla fine, imposta `right` a `nil`.



##### Esempio di funzioni di riferimento:
![[Pasted image 20241104104934.png]]

#### Altezza (massima) di un albero binario:
#### Cos'è?
L'altezza di un albero è il numero di collegamenti verticali dalla radice all'ultima foglia.
Ad esempio, l'altezza del seguente albero è 2, poiché ci sono due collegamenti dalla radice alle ultime foglie.
![[Pasted image 20241124202933.png]]
Vediamo ora  una modalità per trovare l'altezza di un albero 
##### Utilizzando la ricorsione: $O(n)$ per il tempo e $O(h)$ per lo spazio
L'idea è quella di calcolare l'altezza dei sottoalberi di sinistra e di destra e assegnare come altezza dell'albero il valore massimo tra le due altezze +1, in formule potrebbe essere:$$heightTree=max(height(leftSubtree),~height(rightSubtree))+1$$

---

##### Codice:
```c title:"Ricorsione Calcolo altezza"
// C program to find the height of a binary 
// tree using depth-first search (DFS) approach.
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
}; 

// Returns "height" which is the number of edges 
// along the longest path from the root node down 
// to the farthest leaf node.
int height(struct Node* root) {
    if (root == NULL)
        return -1;

    // compute the height of left and right subtrees
    int lHeight = height(root->left);
    int rHeight = height(root->right);

    return (lHeight > rHeight ? lHeight : rHeight) + 1;
}

struct Node* createNode(int val) {
    struct Node* node 
        = (struct Node*)malloc(sizeof(struct Node));
    node->data = val;
    node->left = NULL;
    node->right = NULL;
    return node;
}

int main() {
  
    // Representation of the input tree:
    //     1
    //    / \
    //   2   3
    //  / \
    // 4   5
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);
    
    printf("%d\n", height(root));
    
    return 0;
}
```
il cui output sarà 2.

---

Questo è un esempio di come funziona il codice. Ricordiamoci che se l'albero (o il sottoalbero) è vuoto la funzione _height_ tornerà _-1_
![[Pasted image 20241125115635.png]]
height(’12’) = max(height(‘8′), height(’18’)) + 1 = 1 + 1 = 2. Questo perché, in modo ricorsivo:
height(‘8’) = max(height(‘5′), height(’11’)) + 1 = 0 + 1 = 1
height(’18’) = max(height(NULL), height(‘NULL’)) + 1 = (-1) + 1 = 0 
height(“5”) = max(height(NULL), height(‘NULL’)) + 1 = (-1) + 1 = 0
height(“11”) = max(height(NULL), height(‘NULL’)) + 1 = (-1) + 1 = 0
 
***Complessità temporale:*** O(n), dove ***n*** è il numero di nodi nell'albero binario, come ogni nodo viene visitato una volta.
***Spazio ausiliario:*** O(h) dove ***h*** è l'altezza dell'albero binario.

---
#### Livello di un nodo:
##### Cos'è?
Dato un albero binario e un valore, l'obiettivo è di trovare il livello in cui si trova il valore dato.
Ad esempio, se l'input è key = 4 e l'albero da analizzare è:
![[Pasted image 20241125122512.png]]
l'output sarà 3, infatti 4 si trova al 3 livello dell'albero.
Se la chiave fosse stata 10, l'output sarebbe stato -1, poiché non è un valore presente nell'albero.
##### Come fare?:
###### 1. Utilizzando la ricorsione: $O(n)$ per il tempo e $O(h)$ per lo spazio:
```c title:"Livello di un nodo in un Albero Binario"
// C code to find level of a Node in Binary Tree

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

int getLevel(struct Node* root, int target, int level) {
    if (root == NULL) {
        return -1;
    }

    // If the target key matches the current node's data, return the level
    if (root->data == target) {
        return level;
    }

    // Recursively call for left and right subtrees
    int leftLevel = getLevel(root->left, target, level + 1);
    if (leftLevel != -1) {
        return leftLevel;
    }

    return getLevel(root->right, target, level + 1);
}

struct Node* createNode(int val) {
    struct Node* newNode = 
      (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->left = newNode->right = NULL;
    return newNode;
}

int main() {
  
    // Creating a sample binary tree:
    //       1
    //      / \
    //     2   3
    //    / \ / \
    //   4  5 6  7
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);
    root->right->left = createNode(6);
    root->right->right = createNode(7);

    int target = 5;
    printf("%d\n", getLevel(root, target, 1));

    return 0;
}
```
dove l'output sarà 3.

---
#### Ricerca di un nodo:
##### Introduzione:
Dato un albero binario ed un nodo, l'obiettivo è quello di trovare se il valore affiliato al nodo è presente o meno in un albero.
Ad esempio, dato il seguente albero, il valore da trovare è 4:
![[Pasted image 20241125134234.png]]
L'output sarà True.
##### Come fare?
L'idea è quella di utilizzare una delle visite degli alberi e mentre si sta analizzando punto per punto, controllare se il nodo corrente ha valore equivalente a quello dato, se ciò avviene, il programma tornerà "True" e bloccherà la visita, viceversa la completerà e tornerà False.
###### Codice:
```c title:"Nodo in un albero"
// C program to check if a node exists
// in a binary tree
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *left, *right;
};

// Function to traverse the tree in preorder
// and check if the given node exists in it
int ifNodeExists(struct Node* root, int key) {
    if (root == NULL)
        return 0;

    if (root->data == key)
        return 1;

    // then recur on left subtree
    int res1 = ifNodeExists(root->left, key);

    // node found, no need to look further
    if (res1) return 1;

    // node is not found in left, 
    // so recur on right subtree
    int res2 = ifNodeExists(root->right, key);

    return res2;
}

struct Node* createNode(int x) {
    struct Node* newNode = 
        (struct Node*)malloc(sizeof(struct Node));
    newNode->data = x;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

int main() {
    
    // Binary tree  
    //          0
    //        /  \
    //       1    2
    //      / \   / \
    //     3   4 5   6
    //    /   / \
    //   7   8   9
    struct Node* root = createNode(0);
    root->left = createNode(1);
    root->left->left = createNode(3);
    root->left->left->left = createNode(7);
    root->left->right = createNode(4);
    root->left->right->left = createNode(8);
    root->left->right->right = createNode(9);
    root->right = createNode(2);
    root->right->left = createNode(5);
    root->right->right = createNode(6);

    int key = 4;

    if (ifNodeExists(root, key))
        printf("True");
    else
        printf("False");

    return 0;
}
```
L'output sarà True
#### Trovare il genitore:
##### Introduzione:
Dato un albero binario e un nodo, l'obiettivo è di trovare il genitore del nodo, tornando -1 se il nodo dato è la radice.
Ad esempio, se dovessi avere il seguente albero e l'input di trovare il padre di 3,
![[Pasted image 20241125134943.png]]
l'output sarà 1.
##### Come fare?:
L'idea è quella di scrivere una funzione ricorsiva che prende il nodo corrente e il suo genitore come argomento. Se il nodo corrente è uguale al nodo richiesto, restituire il suo genitore e finire il ciclo, altrimenti continuare fino alla fine dell'albero.
```c title:"Trovare il genitore"
#include <stdio.h>
#include <stdlib.h>

// Struttura per rappresentare un nodo dell'albero binario
typedef struct Node {
    int data;
    struct Node* left;
    struct Node* right;
} Node;

// Funzione per creare un nuovo nodo
Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    if (newNode == NULL) {
        fprintf(stderr, "Errore nella creazione del nodo\n");
        exit(1);
    }
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Funzione ricorsiva per trovare il genitore di un nodo target
int findParent(Node* root, int target, int parent) {
    if (root == NULL) {
        return -1;
    }
    
    // Se il nodo corrente è il target, restituisci il suo genitore
    if (root->data == target) {
        return parent;
    }
    
    // Cerca ricorsivamente nel sottoalbero sinistro
    int leftSearch = findParent(root->left, target, root->data);
    if (leftSearch != -1) {
        return leftSearch;
    }
    
    // Cerca ricorsivamente nel sottoalbero destro
    return findParent(root->right, target, root->data);
}

int main() {
    // Rappresentazione dell'albero dato
    //         1
    //        / \
    //       2   3
    //      / \
    //     4   5
    Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    int target = 3;
 
    int parent = findParent(root, target, -1);

    printf("Il genitore del nodo %d è: %d\n", target, parent);

    return 0;
}

```






#### Inserimento di un nodo:
##### Introduzione
Dato un albero binario e una chiave, l'obiettivo è inserire la chiave nell'albero binario, con la regola di immetterlo nella prima posizione disponibile seguendo la visita in ampiezza.
Ad esempio, dato come input il seguente albero e il valore 12,
![[Pasted image 20241125145315.png]]
L'output sarà:
![[Pasted image 20241125145352.png]]
##### Come fare?
L'idea è quella di fare una visita in ampiezza iterativa di un albero dato utilizzando la coda. Se troviamo un nodo il cui figlio di sinistra è vuoto, ne creiamo uno al posto suo, altrimenti se il figlio di destra è vuoto, faremo la stessa cosa. In caso ancora contrario, la ricerca continuerà fino alla fine o fino a quando non ci sarà uno spazio di un figlio vuoto.
###### Codice Online:
```c title:"Inserimento nodi"
#include <stdio.h>
#include <stdlib.h>

// Definizione del nodo dell'albero binario
typedef struct Node {
    int data;
    struct Node* left;
    struct Node* right;
} Node;

// Funzione per creare un nuovo nodo
Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Definizione di una coda per il livello di attraversamento
typedef struct QueueNode {
    Node* treeNode;
    struct QueueNode* next;
} QueueNode;

typedef struct Queue {
    QueueNode* front;
    QueueNode* rear;
} Queue;

// Funzioni della coda
Queue* createQueue() {
    Queue* q = (Queue*)malloc(sizeof(Queue));
    q->front = q->rear = NULL;
    return q;
}

int isEmpty(Queue* q) {
    return q->front == NULL;
}

void enqueue(Queue* q, Node* treeNode) {
    QueueNode* temp = (QueueNode*)malloc(sizeof(QueueNode));
    temp->treeNode = treeNode;
    temp->next = NULL;
    if (q->rear == NULL) {
        q->front = q->rear = temp;
        return;
    }
    q->rear->next = temp;
    q->rear = temp;
}

Node* dequeue(Queue* q) {
    if (isEmpty(q)) return NULL;
    QueueNode* temp = q->front;
    Node* treeNode = temp->treeNode;
    q->front = q->front->next;
    if (q->front == NULL) q->rear = NULL;
    free(temp);
    return treeNode;
}

// Funzione per inserire un nodo in ordine di livello
Node* InsertNode(Node* root, int data) {
    if (root == NULL) {
        return createNode(data);
    }

    Queue* q = createQueue();
    enqueue(q, root);

    while (!isEmpty(q)) {
        Node* curr = dequeue(q);

        if (curr->left != NULL) {
            enqueue(q, curr->left);
        } else {
            curr->left = createNode(data);
            break;
        }

        if (curr->right != NULL) {
            enqueue(q, curr->right);
        } else {
            curr->right = createNode(data);
            break;
        }
    }

    free(q); // Pulizia della memoria della coda
    return root;
}

// Traversata in-order dell'albero binario
void inorder(Node* curr) {
    if (curr == NULL) return;
    inorder(curr->left);
    printf("%d ", curr->data);
    inorder(curr->right);
}

int main() {
    // Costruzione dell'albero binario iniziale
    Node* root = createNode(10);
    root->left = createNode(11);
    root->right = createNode(9);
    root->left->left = createNode(7);
    root->right->left = createNode(15);
    root->right->right = createNode(8);

    int key = 12;
    root = InsertNode(root, key);

    // Dopo l'inserimento di 12
    inorder(root);

    return 0;
}
```




#### Eliminazione di un nodo:
##### Introduzione:
Dato un albero binario, l'obiettivo è quello di eliminare un nodo da esso rimanendo sicuri che l'albero si riduca dal basso, cioè bisogna "rimpiazzare" il nodo che andiamo ad eliminare con il nodo più in basso e più a destra.
Ad esempio, dato come input il nodo 10 da eliminare e il seguente albero
![[Pasted image 20241125161951.png]]
sappiamo che l'output sarà:
![[Pasted image 20241125162012.png]]
poiché il nodo con valore 10 sarà sostituito dal nodo più a destra e più in basso.

---

Un altro esempio può essere questo albero a cui dobbiamo rimuovere il nodo contenente il valore 20:
![[Pasted image 20241125163540.png]]
L'output sarà:
![[Pasted image 20241125163604.png]]

---
##### Come fare?
L'idea è di attraversare l'albero in ampiezza. Bisogna seguire questi tre input
- A partire dalla radice, trovare il nodo più profondo e più a destra nell'albero binario e nel nodo che vogliamo eliminare. 
- Sostituire i dati del nodo più profondo con il nodo da cancellare. 
- Quindi cancellare il nodo più profondo più a destra.
###### Codice Online:
```c title:"Eliminazione di un Nodo"
#include <stdio.h>
#include <stdlib.h>

// Definizione del nodo dell'albero binario
typedef struct Node {
    int data;
    struct Node* left;
    struct Node* right;
} Node;

// Funzione per creare un nuovo nodo
Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Definizione di una coda per attraversare l'albero
typedef struct QueueNode {
    Node* treeNode;
    struct QueueNode* next;
} QueueNode;

typedef struct Queue {
    QueueNode* front;
    QueueNode* rear;
} Queue;

// Funzioni per la gestione della coda
Queue* createQueue() {
    Queue* q = (Queue*)malloc(sizeof(Queue));
    q->front = q->rear = NULL;
    return q;
}

int isEmpty(Queue* q) {
    return q->front == NULL;
}

void enqueue(Queue* q, Node* treeNode) {
    QueueNode* temp = (QueueNode*)malloc(sizeof(QueueNode));
    temp->treeNode = treeNode;
    temp->next = NULL;
    if (q->rear == NULL) {
        q->front = q->rear = temp;
        return;
    }
    q->rear->next = temp;
    q->rear = temp;
}

Node* dequeue(Queue* q) {
    if (isEmpty(q)) return NULL;
    QueueNode* temp = q->front;
    Node* treeNode = temp->treeNode;
    q->front = q->front->next;
    if (q->front == NULL) q->rear = NULL;
    free(temp);
    return treeNode;
}

// Funzione per eliminare il nodo più profondo
void deleteDeepest(Node* root, Node* dNode) {
    Queue* q = createQueue();
    enqueue(q, root);

    Node* curr;
    while (!isEmpty(q)) {
        curr = dequeue(q);

        if (curr->right) {
            if (curr->right == dNode) {
                curr->right = NULL;
                free(dNode);
                free(q);
                return;
            } else {
                enqueue(q, curr->right);
            }
        }

        if (curr->left) {
            if (curr->left == dNode) {
                curr->left = NULL;
                free(dNode);
                free(q);
                return;
            } else {
                enqueue(q, curr->left);
            }
        }
    }

    free(q);
}

// Funzione per eliminare un nodo con un valore specifico
Node* deleteNode(Node* root, int key) {
    if (root == NULL) return NULL;

    if (root->left == NULL && root->right == NULL) {
        if (root->data == key) {
            free(root);
            return NULL;
        } else {
            return root;
        }
    }

    Queue* q = createQueue();
    enqueue(q, root);

    Node* keyNode = NULL;
    Node* curr;

    while (!isEmpty(q)) {
        curr = dequeue(q);

        if (curr->data == key) keyNode = curr;

        if (curr->left) enqueue(q, curr->left);
        if (curr->right) enqueue(q, curr->right);
    }

    if (keyNode != NULL) {
        int x = curr->data;
        keyNode->data = x;
        deleteDeepest(root, curr);
    }

    free(q);
    return root;
}

// Traversata in-order dell'albero binario
void inorder(Node* curr) {
    if (curr == NULL) return;
    inorder(curr->left);
    printf("%d ", curr->data);
    inorder(curr->right);
}

int main() {
    // Costruzione dell'albero binario
    //       10         
    //      /  \       
    //    11    9
    //   / \   / \     
    //  7  12 15  8     
    Node* root = createNode(10);
    root->left = createNode(11);
    root->right = createNode(9);
    root->left->left = createNode(7);
    root->left->right = createNode(12);
    root->right->left = createNode(15);
    root->right->right = createNode(8);

    int key = 11;
    root = deleteNode(root, key);

    // Stampa dell'albero dopo la cancellazione
    inorder(root);
    return 0;
}

```


#### Trovare tutte le foglie:
##### Introduzione:
Dato un albero binario, dobbiamo far restituire ogni foglia dell'albero in ordine da come appaiono da sinistra a destra, quindi se avessi come input questo albero:
![[Pasted image 20241125171737.png]]
il cui output sarà 4, 6, 7, 9, 10.
##### Come fare?
1) Controllare se il nodo è nullo, se è tale return dalla funzione
2) Sennò guardare se è una foglia, se è tale scrivere il suo valore
3) Sennò controllare a sinistra e a destra e ripetere l'algoritmo che permette di cercare se il nodo ha figli, se non ce li ha, scrivere il valore
###### Codice Online:
```c title:"Foglie"
#include <stdio.h>
#include <stdlib.h>

// Definizione del nodo dell'albero binario
typedef struct Node {
    int data;
    struct Node* left;
    struct Node* right;
} Node;

// Funzione per creare un nuovo nodo
Node* createNode(int val) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = val;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Funzione per stampare i nodi foglia da sinistra a destra
void printLeafNodes(Node* root) {
    // Se il nodo è nullo, ritorna
    if (!root)
        return;

    // Se il nodo è una foglia, stampa il dato
    if (!root->left && !root->right) {
        printf("%d ", root->data);
        return;
    }

    // Se il figlio sinistro esiste, controlla ricorsivamente
    if (root->left)
        printLeafNodes(root->left);

    // Se il figlio destro esiste, controlla ricorsivamente
    if (root->right)
        printLeafNodes(root->right);
}

// Funzione principale
int main() {
    // Costruzione dell'albero binario
    Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->right->left = createNode(5);
    root->right->right = createNode(8);
    root->right->left->left = createNode(6);
    root->right->left->right = createNode(7);
    root->right->right->left = createNode(9);
    root->right->right->right = createNode(10);

    // Stampa dei nodi foglia
    printLeafNodes(root);

    return 0;
}
```


### Suddivisioni:
#### Prima suddivisione:
In funzione del numero di figli, possiamo distinguere: 
- **Albero Binario Completo**
- **Albero Binario Degenere**
##### Albero Binario Pieno: 
Un albero binario completo è un albero binario con zero o due nodi infantili per ogni nodo.
![[Pasted image 20241121135647.png]]
##### Albero Binario Degenere:
Un **albero binario degenere** è un caso particolare di **albero binario** in cui ogni nodo ha **al massimo un figlio** (cioè o un figlio sinistro o un figlio destro, ma non entrambi contemporaneamente). In pratica, un albero binario degenere si comporta come una **lista concatenata** (linked list)
![[Pasted image 20241121140507.png]]
#### Seconda suddivisione:
In base la comportamento dei livelli invece, possiamo suddividere 
- **Albero Binario Completo**
- **Albero Binario Perfetto**
- **Albero Binario Bilanciato** 
  (che presenta diversi tipologie:
	- Alberi AVL 
	- B-alberi 
	- Alberi 2-3
	- Alberi rosso-neri)
##### Albero Binario Completo:
Un **albero binario completo** è un albero in cui tutti i livelli, eccetto l'ultimo, sono **completamente riempiti** con nodi.
Nell'ultimo livello, se non pieno, tutti i nodi sono **posizionati il più a sinistra possibile**.
![[Pasted image 20241121144042.png]]
##### Albero Binario Perfetto:
Esso è un tipo speciale di albero binario nel quale tutti i nodi fogliari hanno la stessa profondità, e tutti i nodi che non siano foglie hanno due figli, questo significa che tutti i nodi che non siano foglie sono alla stessa profondità dell'albero e che l'albero è completo senza gap.
![[Pasted image 20241121142038.png]]
###### Codice:



##### Albero Binario Bilanciato
L'albero binario Bilanciato è un tipo particolare di albero binario in cui l'altezza del sottoalbero di sinistra non differenzi più di uno da quello di destra o viceversa.
![[Pasted image 20241121143156.png]]
###### Codice:
Il seguente codice mi dice se l'albero è bilanciato:
```c title:"Alberi Binari Bilanciati"
/* C program to check if a tree is height-balanced or not */
#include <stdio.h>
#include <stdlib.h>
#define bool int

/* A binary tree node has data, pointer to left child
   and a pointer to right child */
struct node {
    int data;
    struct node* left;
    struct node* right;
};

/* Returns the height of a binary tree */
int height(struct node* node);

/* Returns true if binary tree with root as root is
 * height-balanced */
bool isBalanced(struct node* root)
{
    /* for height of left subtree */
    int lh;

    /* for height of right subtree */
    int rh;

    /* If tree is empty then return true */
    if (root == NULL)
        return 1;

    /* Get the height of left and right sub trees */
    lh = height(root->left);
    rh = height(root->right);

    if (abs(lh - rh) <= 1 && isBalanced(root->left)
        && isBalanced(root->right))
        return 1;

    /* If we reach here then tree is not height-balanced */
    return 0;
}

/* UTILITY FUNCTIONS TO TEST isBalanced() FUNCTION */

/* returns maximum of two integers */
int max(int a, int b) { return (a >= b) ? a : b; }

/*  The function Compute the "height" of a tree. Height is
   the number of nodes along the longest path from the root
   node down to the farthest leaf node.*/
int height(struct node* node)
{
    /* base case tree is empty */
    if (node == NULL)
        return 0;

    /* If tree is not empty then height = 1 + max of left
      height and right heights */
    return 1 + max(height(node->left), height(node->right));
}

/* Helper function that allocates a new node with the
   given data and NULL left and right pointers. */
struct node* newNode(int data)
{
    struct node* node
        = (struct node*)malloc(sizeof(struct node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;

    return (node);
}

// Driver code
int main()
{
    struct node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);
    root->left->left->left = newNode(8);

    if (isBalanced(root))
        printf("Tree is balanced");
    else
        printf("Tree is not balanced");

    getchar();
    return 0;
}
```






### Alberi Binari di ricerca:
#### Cosa sono?
Sono una struttura dati utilizzata nell'informatica per organizzare e posizionare i dati in una maniera specifica. Gli alberi di ricerca binari seguono tutte le proprietà degli alberi binari e hanno la caratteristica di avere, per ogni nodo, il successivo sottoalbero sinistro contenente valori inferiori al nodo, mentre quello destro conterrà valori (keys) maggiori:
![[Pasted image 20241121191029.png]]
##### Esempio:
Cosa succede se si inserisce la sequenza:$$V=[1,2,3,4,5,6]$$Essendo questi valori l'uno maggiore dell'altro, c'è una sola possibile configurazione:
![[Pasted image 20241121195126.png]]
A sinistra non avremo alcun elemento perché nella configurazione vanno posizionati gli elementi minori del nodo.
#### Esempio pratico:
Un esempio pratico è la realizzazione di un _dizionario_, ovvero il mantenimento di un insieme di dati ordinato per chiavi:
- A ciascun nodo è associato un record, con la sua chiave del nodo corrente
- Per ciascun nodo, tutte le chiavi nel sottoalbero radicato nel figlio sinistro sono minori della chiave del nodo corrente 
- Per ciascun nodo, tutte le chiavi nel sottoalbero radicato nel figlio destro sono maggiori della chiave del nodo corrente
#### Funzioni principali:
![[Pasted image 20241121194829.png]]
![[Pasted image 20241121194843.png]]
![[Pasted image 20241121194902.png]]

#### Inserimento (o insertion):
##### Obiettivo:
immaginiamo di avere un albero binario nel quale dobbiamo inserire un nuovo nodo, in questo modo:
![[Pasted image 20241122142703.png]]
Sappiamo che nell'inserire un nuovo valore, esso si posiziona sempre alle foglie, mantenendo le proprietà.
##### Step per l'inserimento:
###### 1. Inizializzare il nodo corrente:
Bisogna inizializzare il nodo utilizzando, per esempio, ("currNode", "node") con il la radice 
![[Pasted image 20241122202333.png]]

---
###### 2. Comparazione:
Bisogna comparare la chiave con il nodo corrente, cioè devo controllare il valore della chiave che sto aggiungendo e quello del nodo 
![[Pasted image 20241122202343.png]]

---
###### 3. Muoversi a..
Si continua nell'analisi 
- a sinistra se il valore è minore o uguale al valore del nodo che stiamo analizzando
- a destra se è maggiore rispetto a valore del nodo che stiamo analizzando
![[Pasted image 20241122202404.png]]

---
###### 4. Ripetizione
Bisogna ripetere gli step 2 e 3 fino a che non raggiungi una foglia.
![[Pasted image 20241122202414.png]]

---
###### 5. Fine
Una volta trovato una foglia, attaccare il nodo a destra o a sinistra in funzione del valore (rispettivamente a destra se la foglia possiede valore minore del nostro nodo o viceversa)
![[Pasted image 20241122202426.png]]

---
##### Implementazione in C:
###### Codice non iterativo ():
```c title:"Inserimento nodo"
#include <stdio.h>
#include <stdlib.h>

// Define the structure for a BST node
struct Node {
    int key;
    struct Node* left;
    struct Node* right;
};

// Function to create a new BST node
struct Node* newNode(int item) {
    struct Node* temp = 
       (struct Node*)malloc(sizeof(struct Node));
    temp->key = item;
    temp->left = temp->right = NULL;
    return temp;
}


// Function to insert a new node with the given key
struct Node* insert(struct Node* node, int key) {
  
    // If the tree is empty, return a new node
    if (node == NULL)
        return newNode(key);
    
    // If the key is already present in the tree,
    // return the node
    if (node->key == key)
        return node;
    
    // Otherwise, recur down the tree. If the key 
    // to be inserted is greater than the node's key,
    // insert it in the right subtree
    if (node->key < key)
        node->right = insert(node->right, key);
  
    // If the key to be inserted is smaller than 
    // the node's key,insert it in the left subtree
    else
        node->left = insert(node->left, key);

    // Return the (unchanged) node pointer
    return node;
}

// Function to perform inorder tree traversal
void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%d ", root->key);
        inorder(root->right);
    }
}

// Driver program to test the above functions
int main() {
    // Creating the following BST
    //      50
    //     /  \
    //    30   70
    //   / \   / \
    //  20 40 60 80

    struct Node* root = newNode(50);
    root = insert(root, 30);
    root = insert(root, 20);
    root = insert(root, 40);
    root = insert(root, 70);
    root = insert(root, 60);
    root = insert(root, 80);

    // Print inorder traversal of the BST
    inorder(root);

    return 0;
}
```
***Output***: 20 30 40 50 60 70 80
***Complessità***: La complessità del caso sarà $O(h)$ dove con $h$ indichiamo la profondità dell'albero.
###### Codice iterativo:
Si basa sull'utilizzo di un loop _while_ :
```c title:"Iterativo"
#include <stdio.h>
#include <stdlib.h>

// Define the structure for a BST node
struct Node {
    int key;
    struct Node* left;
    struct Node* right;
};

// Function to create a new BST node
struct Node* newNode(int item) {
    struct Node* temp = 
       (struct Node*)malloc(sizeof(struct Node));
    temp->key = item;
    temp->left = temp->right = NULL;
    return temp;
}


struct Node* insert(struct Node* root, int x)
{

    struct Node* temp = newNode(x);

    // If tree is empty
    if (root == NULL)
        return temp;

    // Find the node who is going
    // to have the new node temp as
    // it child. The parent node is
    // mainly going to be a leaf node
    struct Node *parent = NULL, *curr = root;
    while (curr != NULL) {
        parent = curr;
        if (curr->key > x)
            curr = curr->left;
        else if (curr->key < x)
            curr = curr->right;
        else
            return root;
    }

    // If x is smaller, make it
    // left child, else right child
    if (parent->key > x)
        parent->left = temp;
    else
        parent->right = temp;
    return root;
}

// Function to perform inorder tree traversal
void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%d ", root->key);
        inorder(root->right);
    }
}

// Driver program to test the above functions
int main() {
    // Creating the following BST
    //      50
    //     /  \
    //    30   70
    //   / \   / \
    //  20 40 60 80

    struct Node* root = newNode(50);
    root = insert(root, 30);
    root = insert(root, 20);
    root = insert(root, 40);
    root = insert(root, 70);
    root = insert(root, 60);
    root = insert(root, 80);

    // Print inorder traversal of the BST
    inorder(root);

    return 0;
}
```
***Output*** 20 30 40 50 60 70 80
***Complessità***: la complessità è $O(n)$ 











#### Ricerca Valore:
##### Obiettivo:
Dato un albero binario di ricerca l'obiettivo è quello di trovare se un determinato valore è presente o meno. 
Ad esempio, nel seguente albero se la key da trovare è 8, il programma tornerà true:
![[Pasted image 20241124161016.png]]
Invece se la key da trovare fosse stata 4, il programma avrebbe avuto come output false.
##### Step per la ricerca:
Immaginiamo di dover cercare un numero generico X:
###### 1. Comparazione con la radice:
Per prima cosa compariamo il valore X con il valore della radice:
- Se i due valori sono uguali il ciclo è finito. 
Se la condizione non è verificata, si prosegue cosi:
![[Pasted image 20241124165526.png]]

---
###### 2. Comparazione con i sottoalberi:
- Se X è minore, essendo un albero di ricerca binario, ci spostiamo a sinistra continuando con la comparazione
- Se X è maggiore, viceversa, ci sposteremo a destra proseguendo con la ricerca.
![[Pasted image 20241124165549.png]]

---
###### 3. Ripetizione:
Se al primo nodo dopo la radice l'uguaglianza è rispettata, il ciclo finisce, sennò ripeteremo il punto [[#2. Comparazione con i sottoalberi]].
![[Pasted image 20241124165741.png]]

---
###### 4. Fine:
Se ad una qualsiasi iterazione il valore è stato trovato, il programma ritornerà "True", altrimenti "False"
![[Pasted image 20241124165759.png]]

---
##### Codice:
```c title:"Ricerca Valore in BST"
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int key;
    struct Node* left;
    struct Node* right;
};

// Constructor to create a new BST node
struct Node* newNode(int item)
{
    struct Node* temp
        = (struct Node*)malloc(sizeof(struct Node));
    temp->key = item;
    temp->left = temp->right = NULL;
    return temp;
}

// function to search a key in a BST
struct Node* search(struct Node* root, int key)
{

    // Base Cases: root is null or key is
    // present at root
    if (root == NULL || root->key == key)
        return root;

    // Key is greater than root's key
    if (root->key < key)
        return search(root->right, key);

    // Key is smaller than root's key
    return search(root->left, key);
}

// Driver Code
int main()
{
    // Creating a hard coded tree for keeping 
    // the length of the code small. We need 
    // to make sure that BST properties are 
    // maintained if we try some other cases.
    struct Node* root = newNode(50);
    root->left = newNode(30);
    root->right = newNode(70);
    root->left->left = newNode(20);
    root->left->right = newNode(40);
    root->right->left = newNode(60);
    root->right->right = newNode(80);

    printf(search(root, 19) != NULL ? "Found\n"
                                    : "Not Found\n");
    printf(search(root, 80) != NULL ? "Found\n"
                                    : "Not Found\n");

    return 0;
}
```



#### Vista:
##### Generale:
Ipotizziamo di avere un albero di ricerca binario:
![[Pasted image 20241123003709.png]]
di conseguenza, i singoli output saranno:
- Visita in inorder : 10 20 30 100 150 200 300 
- Visita in preordine: 100 20 10 30 200 150 300  
- Visita in postorder : 10 30 20 150 300 200 100
#### Eliminazione:
Esistono 3 casi di eliminazione dei nodi:
##### 1. Eliminazione di una foglia:
![[Pasted image 20241124191955.png]]

---
##### 2. Eliminazione di un nodo con un figlio solo:
Per l'eliminazione di un nodo che però possiede un figlio bisogna sostituire il valore del figlio al posto del padre e viceversa, a questo punto agire come era stato scritto per la foglia. ([[#1. Eliminazione di una foglia]])
![[Pasted image 20241124192325.png]]

---
##### 3. Eliminazione di un nodo con entrambi i figli:
Se un nodo ha due figli, bisogna seguire la procedura di visita in preordine ([[#Visita in inordine]]) in modo tale da sostituire il valore con quello del suo successore. Analizziamo il seguente esempio:
![[Pasted image 20241124193516.png]]
Devo eliminare il valore 50, quindi utilizzo la visita in "inordine" per trovare il giusto valore con cui rimpiazzarlo. Quest'ultimo sarà proprio 60, quindi posso rimpiazzare 50 con 60 e viceversa, lasciando inalterata la proprietà dell'albero BS poiché le disuguaglianze dei valori rimangono inalterate.
- **Nota 1**:
	può essere utilizzato anche il predecessore.
- **Nota 2**:
	il valore successivo è richiesto solamente quando il figlio di destra non è vuoto. In questo caso particolare, il successore del nodo da utilizzare è ottenibile trovare il valore minimo del sottoalbero di destra.
---
##### Codice online:
```c title:"Eliminazione di un nodo"
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int key;
    struct Node* left;
    struct Node* right;
};

// Note that it is not a generic inorder successor
// function. It mainly works when the right child
// is not empty, which is  the case we need in
// BST delete.
struct Node* getSuccessor(struct Node* curr) {
    curr = curr->right;
    while (curr != NULL && curr->left != NULL)
        curr = curr->left;
    return curr;
}

// This function deletes a given key x from the
// given BST  and returns the modified root of 
// the BST (if it is modified)
struct Node* delNode(struct Node* root, int x) {
  
    // Base case
    if (root == NULL)
        return root;

    // If key to be searched is in a subtree
    if (root->key > x)
        root->left = delNode(root->left, x);
    else if (root->key < x)
        root->right = delNode(root->right, x);
    else {
        // If root matches with the given key

        // Cases when root has 0 children or 
        // only right child
        if (root->left == NULL) {
            struct Node* temp = root->right;
            free(root);
            return temp;
        }

        // When root has only left child
        if (root->right == NULL) {
            struct Node* temp = root->left;
            free(root);
            return temp;
        }

        // When both children are present
        struct Node* succ = getSuccessor(root);
        root->key = succ->key;
        root->right = delNode(root->right, succ->key);
    }
    return root;
}

struct Node* createNode(int key) {
    struct Node* newNode = 
       (struct Node*)malloc(sizeof(struct Node));
    newNode->key = key;
    newNode->left = newNode->right = NULL;
    return newNode;
}

// Utility function to do inorder traversal
void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%d ", root->key);
        inorder(root->right);
    }
}

// Driver code
int main() {
    struct Node* root = createNode(10);
    root->left = createNode(5);
    root->right = createNode(15);
    root->right->left = createNode(12);
    root->right->right = createNode(18);
    int x = 15;

    root = delNode(root, x);
    inorder(root);
    return 0;
}
```



### Alberi AVL
#### Introduzione:
##### Cosa sono?
Gli alberi di Adel’son-Vel’skii e Landis sono degli alberi 1-bilanciati. Sono un tipo particolare di alberi binari di ricerca.
In un albero AVL ogni nodo contiene un campo aggiuntivo che distingue tre situazioni possibili.
- -1 il sottoalbero sinistro è più profondo (di un livello, -1) del destro.
- 0 Il sottoalbero sinistro ha la stessa profondità del destro.
- 1 Il sottoalbero destro è più profondo (di un livello, 1) del sinistro.
Come per tutti gli alberi bilanciati, la ricerca procede come per un albero binario semplice, mentre l'inserimento richiede delle considerazione più sofisticate. 
Un esempio di albero AVL può essere:
![[Pasted image 20241125190709.png]]
##### Vantaggi dell'uso degli Alberi AVL:
1. Gli alberi AVL possono auto-bilanciarsi e quindi forniscono complessità di tempo come O (Log n) per la ricerca, l'inserimento e l'eliminazione.
2. Sono un tipo di BST (con bilanciamento), quindi gli elementi possono essere attraversati in ordine ordinato.
3. Poiché le regole di bilanciamento sono più severe, gli alberi AVL in generale hanno relativamente meno altezza e quindi la ricerca è più veloce.
4. L'albero AVL è relativamente meno complesso da comprendere e implementare rispetto agli alberi neri rossi.
##### Svantaggi dell'uso degli alberi AVL:
1. È difficile da implementare rispetto al normale BST e più facile rispetto al Red Black
2. Meno utilizzato rispetto agli alberi rosso-neri.
3. A causa del loro equilibrio piuttosto rigido, gli alberi AVL richiedono operazioni di inserimento e rimozione complesse man mano che vengono eseguite più rotazioni.


##### Applicazioni dell'albero AVL:
- La maggior parte dei set e dei dizionari in memoria vengono memorizzati utilizzando alberi AVL.
- Anche le applicazioni di database, in cui inserimenti ed eliminazioni sono meno comuni ma sono necessarie frequenti ricerche di dati, utilizzano spesso alberi AVL.
- Oltre alle applicazioni di database, viene utilizzato in altre applicazioni che richiedono una ricerca migliore.
- La maggior parte delle implementazioni STL dei contenitori associativi ordinati (set, multiset, mappe e multimap) utilizzano alberi rosso-neri anziché alberi AVL.
#### Rotazioni:
##### Rotazione a Sinistra:
Ipotizziamo di avere un albero AVL e che un nodo venga aggiunto nel sottoalbero di destra di un albero che presenta una radice e un figlio di destra. Affinché esso non perda la sua natura di albero AVL, quindi che ci sia una disparità di altezza di massimo 1, bisogna effettuare una rotazione a sinistra, come mostrato in figura:
![[Pasted image 20241125194725.png]]

---
##### Rotazione a Destra:
Immaginiamo che avvenga la contrario rispetto a come abbiamo impostato il problema nel caso precedente, ovvero in questo modo:
![[Pasted image 20241125200921.png]]
##### Rotazione "Left-Right":
Una rotazione Sinistra-Destra è un tipo di combinazione in cui avviene prima una rotazione a sinistra e poi una destra
![[Pasted image 20241125212836.png]]

---
##### Rotazione "Right-Left"
E' la rotazione che avviene al contrario della rotazione Left-Right.
![[Pasted image 20241125213040.png]]








##### Codice Tutor:
```c title:"Rotazione alberi AVL"
// Funzione per la rotazione a destra

struct Node *rightRotate(struct Node *y) {

struct Node *x = y->left;

struct Node *T2 = x->right;

  

x->right = y;

y->left = T2;

  

y->height = max(height(y->left), height(y->right)) + 1;

x->height = max(height(x->left), height(x->right)) + 1;

  

return x; //ritorna la nuova root

}

  

// Funzione per la rotazione a sinistra

struct Node *leftRotate(struct Node *x) {

struct Node *y = x->right;

struct Node *T2 = y->left;

  

y->left = x;

x->right = T2;

  

x->height = max(height(x->left), height(x->right)) + 1;

y->height = max(height(y->left), height(y->right)) + 1;

  

return y; //ritorna la nuova root

}
```



#### Inserzione:
##### Introduzione:
La seguente foto rappresenta l'inserimento di un nodo, con uno studio iniziale sul bilanciamento dei sottoalberi. Nell'albero iniziale, il nodo radice **13** ha un fattore di bilanciamento di **-1**, poiché il suo sottoalbero destro è più alto di 1 rispetto al sinistro.
Quando viene inserito il nodo **14**, il fattore di bilanciamento di alcuni nodi cambia per riflettere la nuova altezza dei loro sottoalberi.
![[Pasted image 20241126195654.png]]
Questo però è il caso più semplice in cui il nodo che andiamo ad aggiungere non crea instabilità nell'albero.

---

##### Casi singola rotazione:
La seguente immagine rappresenta lo stesso albero precedente ma nel caso in cui i nodi creano instabilità e costringono a compiere una rotazione:
![[Pasted image 20241126201320.png]]

---

Un altro esempio potrebbe essere:
![[Pasted image 20241126201459.png]]
Fino ad ora però abbiamo visto solo i casi in cui c'è una sola rotazione.

---
##### Casi doppia rotazione:
La seguente immagine presenta una doppia rotazione, causata dal fatto che dopo la prima, come visualizzato, rimane uno sbilanciamento
![[Pasted image 20241126202258.png]]

---
##### Come fare?
L'idea è quella di usare l'inserimento ricorsivo BST e dopo averlo fato utilizziamo i puntatori ad ogni antenato uno per uno, svolgendo questo procedimento salendo dal basso verso l'alto. Facendo questo, non necessitiamo di un puntatore che punta ai genitori e sale uno alla volta.

---
Vediamo i singoli step dell'algoritmo:
- Eseguire il normale inserimento degli BST
- Il nodo attuale deve essere uno degli antenati del nodo appena inserito. Aggiornare ***l'altezza*** del nodo corrente.
- Ottenere il fattore di equilibrio ****(altezza del sottoalbero sinistro – altezza del sottoalbero destro)**** del nodo corrente.
- Se il fattore di equilibrio è maggiore di ***1,*** allora il nodo corrente non è sbilanciato e siamo nel ***caso di sinistra sinistra*** o ***nella custodia destra sinistra***. Per verificare se è ***lasciato o*** meno, confrontare la chiave appena inserita con la chiave nella ***radice del sottoalbero sinistro***.
- Se il fattore di equilibrio è inferiore a ***-1***, allora il nodo attuale non è sbilanciato e siamo nel caso giusto o nel caso destro-sinistra. Per verificare se si tratta del caso Right Right o meno, confrontare la chiave appena inserita con la chiave nella radice del sottoalbero giusto.
##### Codice Online:
```c title:"Inserimento nodo AVL"
// C program to insert a node in AVL tree
#include<stdio.h>
#include<stdlib.h>

// An AVL tree node
struct Node
{
    int key;
    struct Node *left;
    struct Node *right;
    int height;
};

// A utility function to get the height of the tree
int height(struct Node *N)
{
    if (N == NULL)
        return 0;
    return N->height;
}

// A utility function to get maximum of two integers
int max(int a, int b)
{
    return (a > b)? a : b;
}

/* Helper function that allocates a new node with the given key and
    NULL left and right pointers. */
struct Node* newNode(int key)
{
    struct Node* node = (struct Node*)
                        malloc(sizeof(struct Node));
    node->key   = key;
    node->left   = NULL;
    node->right  = NULL;
    node->height = 1;  // new node is initially added at leaf
    return(node);
}

// A utility function to right rotate subtree rooted with y
// See the diagram given above.
struct Node *rightRotate(struct Node *y)
{
    struct Node *x = y->left;
    struct Node *T2 = x->right;

    // Perform rotation
    x->right = y;
    y->left = T2;

    // Update heights
    y->height = max(height(y->left),
                    height(y->right)) + 1;
    x->height = max(height(x->left),
                    height(x->right)) + 1;

    // Return new root
    return x;
}

// A utility function to left rotate subtree rooted with x
// See the diagram given above.
struct Node *leftRotate(struct Node *x)
{
    struct Node *y = x->right;
    struct Node *T2 = y->left;

    // Perform rotation
    y->left = x;
    x->right = T2;

    //  Update heights
    x->height = max(height(x->left),   
                    height(x->right)) + 1;
    y->height = max(height(y->left),
                    height(y->right)) + 1;

    // Return new root
    return y;
}

// Get Balance factor of node N
int getBalance(struct Node *N)
{
    if (N == NULL)
        return 0;
    return height(N->left) - height(N->right);
}

// Recursive function to insert a key in the subtree rooted
// with node and returns the new root of the subtree.
struct Node* insert(struct Node* node, int key)
{
    /* 1.  Perform the normal BST insertion */
    if (node == NULL)
        return(newNode(key));

    if (key < node->key)
        node->left  = insert(node->left, key);
    else if (key > node->key)
        node->right = insert(node->right, key);
    else // Equal keys are not allowed in BST
        return node;

    /* 2. Update height of this ancestor node */
    node->height = 1 + max(height(node->left),
                        height(node->right));

    /* 3. Get the balance factor of this ancestor
          node to check whether this node became
          unbalanced */
    int balance = getBalance(node);

    // If this node becomes unbalanced, then
    // there are 4 cases

    // Left Left Case
    if (balance > 1 && key < node->left->key)
        return rightRotate(node);

    // Right Right Case
    if (balance < -1 && key > node->right->key)
        return leftRotate(node);

    // Left Right Case
    if (balance > 1 && key > node->left->key)
    {
        node->left =  leftRotate(node->left);
        return rightRotate(node);
    }

    // Right Left Case
    if (balance < -1 && key < node->right->key)
    {
        node->right = rightRotate(node->right);
        return leftRotate(node);
    }

    /* return the (unchanged) node pointer */
    return node;
}

// A utility function to print preorder traversal
// of the tree.
// The function also prints height of every node
void preOrder(struct Node *root)
{
    if(root != NULL)
    {
        printf("%d ", root->key);
        preOrder(root->left);
        preOrder(root->right);
    }
}

/* Driver program to test above function*/
int main()
{
  struct Node *root = NULL;

  /* Constructing tree given in the above figure */
  root = insert(root, 10);
  root = insert(root, 20);
  root = insert(root, 30);
  root = insert(root, 40);
  root = insert(root, 50);
  root = insert(root, 25);

  /* The constructed AVL Tree would be
            30
           /  \
         20   40
        /  \     \
       10  25    50
  */

  printf("Preorder traversal : \n");
  preOrder(root);

  return 0;
}

```
L'output mi darà il risultato con la visita in preordine: 
30 20 10 25 40 50
##### Codice professore:
![[Pasted image 20241122105217.png]]








#### Bilanciamento su Inserzione
##### Bilanciamento su inserzione: (Rotate Left)
Consideriamo il caso l’inserimento e avvenuto nel sottoalbero di destra di un nodo il cui bilanciamento diventa +2, mentre la radice del sottoalbero ha bilanciamento +1 come è riportato nell'immagine:
![[Pasted image 20241122105451.png]]
Effettuando una rotazione a sinistra si ripristina il bilanciamento (in tempo O(1)) in modo tale da ottenere:
![[Pasted image 20241122105607.png]]
##### Bilanciamento su inserzione: (Rotate Right)
![[Pasted image 20241127162204.png]]



##### Codice Prof: (Rotate)
![[Pasted image 20241122105809.png]]
##### Bilanciamento su inserzione: doppia rotazione
Ora invece consideriamo il caso l’inserimento è avvenuto nel sottoalbero di destra di un nodo il cui bilanciamento diventa +2, mentre la radice del sottoalbero ha bilanciamento −1. Come nel seguente caso:
![[Pasted image 20241127162349.png]]
E necessaria una sequenza di due rotazioni, con un costo che comunque è O(1).
per vedere il codice: [[#Bilanciamento su inserzione (Rotate Right)]]
#### Cancellazione:
##### Introduzione:
Analizziamo direttamente il problema della cancellazione di un nodo x che ha al più un figlio, poiché, in caso contrario, si cerca il predecessore immediato muovendosi una volta a sinistra e poi sempre a destra.
Il nuovo nodo y non può avere un figlio destro. Sostituiamo y dove era x, poi cancelliamo y utilizzandolo sempre al posto di x. Ora colleghiamo il genitore di x con il singolo figlio di x, il relativo sottoalbero si è accorciato e lo tracciamo con una variabile "shorter" che inizialmente è impostata su true.
#### Bilanciamento su Cancellazione:
Si ripetono i passi seguenti per tutti i nodi p dal genitore di x fino alla radice, ma se shorter diventa false, si esce:
##### Caso 1:
Il nodo p ha bilanciamento 0: si fa diventare +1 o-1 a seconda di quale sottoalbero si era accorciato e shorter = false;
![[Pasted image 20241127192127.png]]
##### Caso 2:
Il nodo p è sbilanciato, ma è stato accorciato il sottoalbero più alto, il bilanciamento diventa 0 e shorter = True
![[Pasted image 20241127192537.png]]
##### Caso 3:
Il nodo p è sbilanciato ed è stato accorciato il sottoalbero più basso; sia q la radice del sottoalbero più alto:
###### Caso 3a: 
 Il nodo q è bilanciato: si applica una rotazione singola, si aggiusta il bilanciamento di p e q e shorter=FALSE;
![[Pasted image 20241127192623.png]]

---
###### Caso 3b: 
Il nodo q è sbilanciato come p: si applica una rotazione singola, si aggiusta il bilanciamento di p e q e shorter=TRUE
![[Pasted image 20241127192639.png]]
###### Caso 3c:
Il nodo q è sbilanciato in modo opposto di p: si applica una rotazione doppia, si aggiusta il bilanciamento della nuova radice a 0 e gli altri opportunamente, e shorter=TRUE
![[Pasted image 20241127192652.png]]








##### Codice Online:
```c title:"Eliminazione"
// C program to delete a node from AVL Tree
#include<stdio.h>
#include<stdlib.h>

// An AVL tree node
struct Node
{
    int key;
    struct Node *left;
    struct Node *right;
    int height;
};

// A utility function to get maximum of two integers
int max(int a, int b);

// A utility function to get height of the tree
int height(struct Node *N)
{
    if (N == NULL)
        return 0;
    return N->height;
}

// A utility function to get maximum of two integers
int max(int a, int b)
{
    return (a > b)? a : b;
}

/* Helper function that allocates a new node with the given key and
    NULL left and right pointers. */
struct Node* newNode(int key)
{
    struct Node* node = (struct Node*)
                        malloc(sizeof(struct Node));
    node->key   = key;
    node->left   = NULL;
    node->right  = NULL;
    node->height = 1;  // new node is initially added at leaf
    return(node);
}

// A utility function to right rotate subtree rooted with y
// See the diagram given above.
struct Node *rightRotate(struct Node *y)
{
    struct Node *x = y->left;
    struct Node *T2 = x->right;

    // Perform rotation
    x->right = y;
    y->left = T2;

    // Update heights
    y->height = max(height(y->left), height(y->right))+1;
    x->height = max(height(x->left), height(x->right))+1;

    // Return new root
    return x;
}

// A utility function to left rotate subtree rooted with x
// See the diagram given above.
struct Node *leftRotate(struct Node *x)
{
    struct Node *y = x->right;
    struct Node *T2 = y->left;

    // Perform rotation
    y->left = x;
    x->right = T2;

    //  Update heights
    x->height = max(height(x->left), height(x->right))+1;
    y->height = max(height(y->left), height(y->right))+1;

    // Return new root
    return y;
}

// Get Balance factor of node N
int getBalance(struct Node *N)
{
    if (N == NULL)
        return 0;
    return height(N->left) - height(N->right);
}

struct Node* insert(struct Node* node, int key)
{
    /* 1.  Perform the normal BST rotation */
    if (node == NULL)
        return(newNode(key));

    if (key < node->key)
        node->left  = insert(node->left, key);
    else if (key > node->key)
        node->right = insert(node->right, key);
    else // Equal keys not allowed
        return node;

    /* 2. Update height of this ancestor node */
    node->height = 1 + max(height(node->left),
                           height(node->right));

    /* 3. Get the balance factor of this ancestor
          node to check whether this node became
          unbalanced */
    int balance = getBalance(node);

    // If this node becomes unbalanced, then there are 4 cases

    // Left Left Case
    if (balance > 1 && key < node->left->key)
        return rightRotate(node);

    // Right Right Case
    if (balance < -1 && key > node->right->key)
        return leftRotate(node);

    // Left Right Case
    if (balance > 1 && key > node->left->key)
    {
        node->left =  leftRotate(node->left);
        return rightRotate(node);
    }

    // Right Left Case
    if (balance < -1 && key < node->right->key)
    {
        node->right = rightRotate(node->right);
        return leftRotate(node);
    }

    /* return the (unchanged) node pointer */
    return node;
}

/* Given a non-empty binary search tree, return the
   node with minimum key value found in that tree.
   Note that the entire tree does not need to be
   searched. */
struct Node * minValueNode(struct Node* node)
{
    struct Node* current = node;

    /* loop down to find the leftmost leaf */
    while (current->left != NULL)
        current = current->left;

    return current;
}

// Recursive function to delete a node with given key
// from subtree with given root. It returns root of
// the modified subtree.
struct Node* deleteNode(struct Node* root, int key)
{
    // STEP 1: PERFORM STANDARD BST DELETE

    if (root == NULL)
        return root;

    // If the key to be deleted is smaller than the
    // root's key, then it lies in left subtree
    if ( key < root->key )
        root->left = deleteNode(root->left, key);

    // If the key to be deleted is greater than the
    // root's key, then it lies in right subtree
    else if( key > root->key )
        root->right = deleteNode(root->right, key);

    // if key is same as root's key, then This is
    // the node to be deleted
    else
    {
        // node with only one child or no child
        if( (root->left == NULL) || (root->right == NULL) )
        {
            struct Node *temp = root->left ? root->left :
                                             root->right;

            // No child case
            if (temp == NULL)
            {
                temp = root;
                root = NULL;
            }
            else // One child case
             *root = *temp; // Copy the contents of
                            // the non-empty child
            free(temp);
        }
        else
        {
            // node with two children: Get the inorder
            // successor (smallest in the right subtree)
            struct Node* temp = minValueNode(root->right);

            // Copy the inorder successor's data to this node
            root->key = temp->key;

            // Delete the inorder successor
            root->right = deleteNode(root->right, temp->key);
        }
    }

    // If the tree had only one node then return
    if (root == NULL)
      return root;

    // STEP 2: UPDATE HEIGHT OF THE CURRENT NODE
    root->height = 1 + max(height(root->left),
                           height(root->right));

    // STEP 3: GET THE BALANCE FACTOR OF THIS NODE (to
    // check whether this node became unbalanced)
    int balance = getBalance(root);

    // If this node becomes unbalanced, then there are 4 cases

    // Left Left Case
    if (balance > 1 && getBalance(root->left) >= 0)
        return rightRotate(root);

    // Left Right Case
    if (balance > 1 && getBalance(root->left) < 0)
    {
        root->left =  leftRotate(root->left);
        return rightRotate(root);
    }

    // Right Right Case
    if (balance < -1 && getBalance(root->right) <= 0)
        return leftRotate(root);

    // Right Left Case
    if (balance < -1 && getBalance(root->right) > 0)
    {
        root->right = rightRotate(root->right);
        return leftRotate(root);
    }

    return root;
}

// A utility function to print preorder traversal of
// the tree.
// The function also prints height of every node
void preOrder(struct Node *root)
{
    if(root != NULL)
    {
        printf("%d ", root->key);
        preOrder(root->left);
        preOrder(root->right);
    }
}

/* Driver program to test above function*/
int main()
{
  struct Node *root = NULL;

  /* Constructing tree given in the above figure */
    root = insert(root, 9);
    root = insert(root, 5);
    root = insert(root, 10);
    root = insert(root, 0);
    root = insert(root, 6);
    root = insert(root, 11);
    root = insert(root, -1);
    root = insert(root, 1);
    root = insert(root, 2);

    /* The constructed AVL Tree would be
            9
           /  \
          1    10
        /  \     \
       0    5     11
      /    /  \
     -1   2    6
    */

    printf("Preorder traversal of the constructed AVL "
           "tree is \n");
    preOrder(root);

    root = deleteNode(root, 10);

    /* The AVL Tree after deletion of 10
            1
           /  \
          0    9
        /     /  \
       -1    5     11
           /  \
          2    6
    */

    printf("\nPreorder traversal after deletion of 10 \n");
    preOrder(root);

    return 0;
}
```
Che avrà come complessità $O(log(h))$
##### Output:
l'output sarà:
"Preorder traversal of the constructed AVL tree is 
5 1 0 -1 2 9 6 10 11 
Preorder traversal after deletion of 10 
5 1 0 -1 2 9 6 11"
#### Teoremi
##### Altezza massima di un AVL:
Alberi AVL Teorema (Massima altezza di un albero AVL) L’altezza h di un albero bilanciato con N nodi interni è limitata da $$log(N + 1) < h < 1.4404 log(N + 2) − 0.3277$$

###### Dimostrazione (Parte 1). 
l numero di nodi esterni (foglie) di un albero di altezza h è chiaramente ≤ $2^h$, per cui 
$N + 1 ≤ 2h$ ovvero: $$h ≥ ⌈log(N + 1)⌉.$$

---
###### Dimostrazione (Parte 2).
Si consideri un albero bilanciato di altezza h con il minimo numero possibile di nodi; allora un sottoalbero della radice (p.es. il sinistro) deve avere altezza h − 1, e l’altro h − 2, e devono essere entrambi con numero minimo di nodi; quindi Nh = Nh−1 + Nh−2 + 1, ossia si ha un albero di Fibonacci; pertanto $$N ≥ F_{h+2} − 1 > \frac{\phi^{h+2}}{√5}−2??$$

---
### Alberi Rosso-Neri:
#### Introduzione:
##### Cosa sono?
Gli alberi rosso-neri (Red-Black) utilizzano un attributo (colore) aggiuntivo per ogni nodo, attributo che può appunto prendere i valori rosso oppure nero.
![[Pasted image 20241127195716.png]]
##### Proprietà:
- La **radice** è **Nera**
- Tutte le **foglie** sono **Nere**
- _Entrambi_ i **figli** di un *nodo rosso* sono **neri** (quindi un nodo rosso non può avere figli rossi)
- Tutti i collegamenti da un nodo ad una foglia contengono lo stesso numero di nodi neri.
![[Pasted image 20241129101101.png]]
---

La presentazione e le dimostrazioni di correttezza si semplificano assumendo che
- Tutte le foglie sono memorizzate esplicitamente,
- Le foglie non contengono dati; 
- Sono in numero tale che tutti i nodi (interni) abbiano esattamente due figli (che possono anche essere foglie).

---
Altri punti interessanti:
- l'altezza nera di un albero è data dl numero di foglie nere dalla radice alle foglie (considerate, visto che esse sono contate come nodi neri). Quindi un albero rosso-nero con altezza h avrà altezza nera $\ge \frac{h}{2}$
- L'altezza di un albero con n nodi è $h \le 2log_{2}(n+1)$
questi punti saranno visti meglio nei capitoli immediatamente successivi.
---
##### Definizione:
L'altezza nera $b(u)$ è il numero di nodi neri da u (escluso) ad una (qualsiasi) foglia

---
##### Lemma:
Il sottoalbero di radice u contiene almeno $N = 2^{b(u)} − 1$ nodi interni.
###### Dimostrazione:
Per induzione sulla altezza h (totale) dell’albero. Se h = 0, allora siamo su una foglia, ed il numero di nodi interni è $N = 0 = 20 − 1$. Se $h > 0$ allora siamo su un nodo interno che ha 2 figli; se il figlio è rosso allora la sua altezza nera è eguale a b(u), altrimenti è $b(u) − 1$ per induzione, il numero di nodi interni del sottoalbero radicato in ciascun figlio è almeno $2^{b(u)−1} − 1$, e quindi il numero totale di nodi interni (contando anche u) è $$N ≥ 2^{b(u)−1} − 1 + 2^{b(u)−1} − 1 + 1 = 2 × 2^{b(u)−1} − 1 = 2^{b(u)} − 1.$$

---
##### Teorema Cammino radice-foglia:
La lunghezza del cammino radice-foglia più lungo non supera il doppio di quella del più corto $$max\{l(u) : u.left = u.right = nil\} ≤ 2 min\{l(u) : u.left = u.right = nil\}$$
###### Dimostrazione:
- Tutti i cammini dalla radice alle foglie hanno la stessa altezza nera b(r ); 
- Nessun cammino può contenere due nodi rossi consecutivi; 
- Pertanto, i nodi rossi sul cammino più lungo sono al più tanti quanti quelli neri; 
- Il cammino più corto ha lo stesso numero di nodi neri del più lungo; 
- Pertanto il cammino più lungo è al più il doppio del più corto.

---
##### Lemma Altezza:
L’altezza di un albero rosso-nero con N nodi interni è al più $2log(N + 1)$
###### Dimostrazione:
Dai lemmi precedenti: 
- Altezza
- da cui $2^ \frac{h}{2} ≤ N + 1$
- $h/2 ≤ log(N + 1)$
- $h ≤ 2 log(N + 1)$
---
##### Resoconto:
Quindi, gli alberi rosso-neri possono essere sbilanciati di un fattore 2, ma vale comunque che la ricerca in un albero rosso-nero ha una complessità $O(log(N))$ nel numero di nodi N. 
Le operazioni di ricerca di un nodo, del successore, del massimo o del minimo sono realizzabili esattamente con lo stesso codice che per un albero binario. 
###### Altre operazioni:
Le operazioni di inserimento e cancellazione possono alterare la struttura dati; il nostro problema è di trovare dei metodi che ripristino le proprietà di un albero rossonero, con una complessità accettabile $O(log(N))$.

---
Dopo una qualsiasi modifica, bisogna ripristinare l'albero, attraverso due opzioni:
- Cambio di colore dei un nodo
- Rotazione
![[Pasted image 20241128193949.png]]
---
#### Inserzione:
##### Introduzione:
bisogna eseguire l'inserzione utilizzata per gli alberi di ricerca binaria (BST).
![[Pasted image 20241128194132.png]]
##### Ripristino su inserzione:
###### Codice Prof:
![[Pasted image 20241128195043.png]]
###### Casi 1-2
Nei primi due casi: 
1. Il nuovo nodo (che nasce rosso) è il primo (non ha un genitore) quindi basta colorarlo di nero; 
2. Il nuovo nodo (che nasce rosso) ha un genitore nero, quindi tutti i vincoli sono rispettati e non si deve fare niente

---
###### Caso 3:
![[Pasted image 20241128195218.png]]
Il cui albero si aggiusta trasformando in:
![[Pasted image 20241128195258.png]]
Che però potrebbe necessitare di ulteriore aggiustamento, la procedura deve proseguire dal nodo n.

---
###### Caso 4:
Se dovessimo avere:
![[Pasted image 20241128195337.png]]
Si aggiusta trasformando in:
![[Pasted image 20241128195404.png]]
Si ricomincia con t ← p e ci si ritrova al caso successivo che necessita di una modifica:
Poiché tra le proprietà di un albero rosso-nero, c'è quella per la quale i figli di un nodo rosso devono essere neri, allora sarà necessario una doppia rotazione a destra. Otterremo dunque:
![[Pasted image 20241128195436.png]]

---
##### Codice Online:
```c title:"Inserimento"
#include <stdio.h>
#include <stdlib.h>

// Nodo per l'albero rosso-nero
typedef struct Node {
    int data;
    struct Node* left;
    struct Node* right;
    struct Node* parent;
    char colour; // 'R' per rosso, 'B' per nero
} Node;

// Struttura dell'albero
typedef struct RedBlackTree {
    Node* root;
    int ll; // Flag per rotazione sinistra-sinistra
    int rr; // Flag per rotazione destra-destra
    int lr; // Flag per rotazione sinistra-destra
    int rl; // Flag per rotazione destra-sinistra
} RedBlackTree;

// Funzione per creare un nuovo nodo
Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    newNode->parent = NULL;
    newNode->colour = 'R'; // Nuovi nodi sono sempre rossi
    return newNode;
}

// Funzione per eseguire una rotazione a sinistra
Node* rotateLeft(Node* node) {
    Node* x = node->right;
    Node* y = x->left;
    x->left = node;
    node->right = y;
    if (y != NULL) y->parent = node;
    x->parent = node->parent;
    node->parent = x;
    return x;
}

// Funzione per eseguire una rotazione a destra
Node* rotateRight(Node* node) {
    Node* x = node->left;
    Node* y = x->right;
    x->right = node;
    node->left = y;
    if (y != NULL) y->parent = node;
    x->parent = node->parent;
    node->parent = x;
    return x;
}

// Funzione di supporto per inserire un nodo
Node* insertHelp(Node* root, RedBlackTree* tree, int data) {
    int f = 0; // Flag per il conflitto rosso-rosso

    if (root == NULL)
        return createNode(data);

    if (data < root->data) {
        root->left = insertHelp(root->left, tree, data);
        root->left->parent = root;
        if (root != tree->root && root->colour == 'R' && root->left->colour == 'R')
            f = 1;
    } else {
        root->right = insertHelp(root->right, tree, data);
        root->right->parent = root;
        if (root != tree->root && root->colour == 'R' && root->right->colour == 'R')
            f = 1;
    }

    // Eseguire le rotazioni
    if (tree->ll) {
        root = rotateLeft(root);
        root->colour = 'B';
        root->left->colour = 'R';
        tree->ll = 0;
    } else if (tree->rr) {
        root = rotateRight(root);
        root->colour = 'B';
        root->right->colour = 'R';
        tree->rr = 0;
    } else if (tree->rl) {
        root->right = rotateRight(root->right);
        root->right->parent = root;
        root = rotateLeft(root);
        root->colour = 'B';
        root->left->colour = 'R';
        tree->rl = 0;
    } else if (tree->lr) {
        root->left = rotateLeft(root->left);
        root->left->parent = root;
        root = rotateRight(root);
        root->colour = 'B';
        root->right->colour = 'R';
        tree->lr = 0;
    }

    // Gestione del conflitto rosso-rosso
    if (f) {
        if (root->parent->right == root) {
            if (root->parent->left == NULL || root->parent->left->colour == 'B') {
                if (root->left != NULL && root->left->colour == 'R')
                    tree->rl = 1;
                else if (root->right != NULL && root->right->colour == 'R')
                    tree->ll = 1;
            } else {
                root->parent->left->colour = 'B';
                root->colour = 'B';
                if (root->parent != tree->root)
                    root->parent->colour = 'R';
            }
        } else {
            if (root->parent->right == NULL || root->parent->right->colour == 'B') {
                if (root->left != NULL && root->left->colour == 'R')
                    tree->rr = 1;
                else if (root->right != NULL && root->right->colour == 'R')
                    tree->lr = 1;
            } else {
                root->parent->right->colour = 'B';
                root->colour = 'B';
                if (root->parent != tree->root)
                    root->parent->colour = 'R';
            }
        }
        f = 0;
    }

    return root;
}

// Funzione per l'inserimento
void insert(RedBlackTree* tree, int data) {
    if (tree->root == NULL) {
        tree->root = createNode(data);
        tree->root->colour = 'B'; // La radice è sempre nera
    } else {
        tree->root = insertHelp(tree->root, tree, data);
    }
}

// Funzione per la visita in ordine
void inorderTraversal(Node* root) {
    if (root != NULL) {
        inorderTraversal(root->left);
        printf("%d ", root->data);
        inorderTraversal(root->right);
    }
}

// Funzione per stampare l'albero
void printTree(Node* root, int space) {
    if (root != NULL) {
        space += 10;
        printTree(root->right, space);
        printf("\n");
        for (int i = 10; i < space; i++) printf(" ");
        printf("%d\n", root->data);
        printTree(root->left, space);
    }
}

// Main
int main() {
    RedBlackTree tree = {NULL, 0, 0, 0, 0};

    int arr[] = {1, 4, 6, 3, 5, 7, 8, 2, 9};
    for (int i = 0; i < 9; i++) {
        insert(&tree, arr[i]);
        printf("\nInorder Traversal: ");
        inorderTraversal(tree.root);
    }

    printf("\n\nTree structure:\n");
    printTree(tree.root, 0);

    return 0;
}

```
La complessità temporale sarà $O(log(n))$ dove con n intendiamo il numero totale di nodi nell'albero.
###### Output:
L'output sarà:
1 
1 4 
1 4 6 
1 3 4 6 
1 3 4 5 6 
1 3 4 5 6 7 
1 3 4 5 6 7 8 
1 2 3 4 5 6 7 8 
1 2 3 4 5 6 7 8 9 
                              9

                    8

                              7

          6

                    5

4

                    3

          2

                    1


#### Cancellazione:
##### Introduzione:
Consiste nell'eliminazione di un nodo come negli alberi BST, per poi procedere a ripristinare eventuali errori.
Bisogna però essere coscienti del fatto che il nodo da eliminare non può avere figli.
Gli step per l'eliminazione sono:
###### Step:
1. se il nodo non ha figli, eliminarlo semplicemente e aggiornare il nodo genitore

---
2. Se ha un solo figlio, rimpiazzare il nodo con il figlio ed eliminarlo

---
3.  Se il nodo ha due figli, allora rimpiazzare il nodo con il primo figlio seguendo la visita in inordine, quindi eliminare il nodo (che ora è diventato il figlio).

---
4. Dopo che il nodo è stato eliminato, le proprietà dell'albero rosso-nero potrebbero essere violate, bisogna utilizzare la rotazione e la colorazione:

---
##### Ripristino su cancellazione:
###### Codice Prof:
![[Pasted image 20241128200814.png]]
###### Caso 1:
![[Pasted image 20241128202218.png]]
che si aggiusta trasformando in:
![[Pasted image 20241128202242.png]]
###### Caso 2:
Ipotizzando di riprendere l'esempio di prima e ruotarlo ancora a destra, otteniamo:
![[Pasted image 20241128202718.png]]
Il cambiamento di colore di p è dato dal fatto che per una delle proprietà dell'albero rosso-nero la radice deve essere nera.
###### Caso  3:
![[Pasted image 20241129084333.png]]
che si trasforma in:
![[Pasted image 20241129084634.png]]
###### Caso 4:
![[Pasted image 20241129085615.png]]
che si aggiusta in:
![[Pasted image 20241129085706.png]]
e si pone t = T.


##### Codice Online:
```c title:"Cancellazione"
#include <stdio.h>
#include <stdlib.h>

// Enum per i colori
typedef enum { RED, BLACK } COLOR;

// Nodo dell'albero
typedef struct Node {
    int val;
    COLOR color;
    struct Node *left, *right, *parent;
} Node;

// Albero rosso-nero
typedef struct RBTree {
    Node *root;
} RBTree;

// Creazione di un nodo
Node* createNode(int val) {
    Node *newNode = (Node*)malloc(sizeof(Node));
    if (!newNode) {
        perror("Errore nell'allocazione del nodo");
        exit(EXIT_FAILURE);
    }
    newNode->val = val;
    newNode->color = RED;
    newNode->left = newNode->right = newNode->parent = NULL;
    return newNode;
}

// Funzione per ruotare a sinistra
void leftRotate(RBTree *tree, Node *x) {
    Node *y = x->right;
    x->right = y->left;

    if (y->left)
        y->left->parent = x;

    y->parent = x->parent;

    if (!x->parent)
        tree->root = y;
    else if (x == x->parent->left)
        x->parent->left = y;
    else
        x->parent->right = y;

    y->left = x;
    x->parent = y;
}

// Funzione per ruotare a destra
void rightRotate(RBTree *tree, Node *x) {
    Node *y = x->left;
    x->left = y->right;

    if (y->right)
        y->right->parent = x;

    y->parent = x->parent;

    if (!x->parent)
        tree->root = y;
    else if (x == x->parent->left)
        x->parent->left = y;
    else
        x->parent->right = y;

    y->right = x;
    x->parent = y;
}

// Funzione per correggere la violazione rosso-rosso
void fixRedRed(RBTree *tree, Node *x) {
    while (x != tree->root && x->parent->color == RED) {
        Node *parent = x->parent;
        Node *grandparent = parent->parent;

        if (parent == grandparent->left) {
            Node *uncle = grandparent->right;

            if (uncle && uncle->color == RED) {
                // Caso 1: Lo zio è rosso (Recoloring)
                parent->color = BLACK;
                uncle->color = BLACK;
                grandparent->color = RED;
                x = grandparent;
            } else {
                if (x == parent->right) {
                    // Caso 2: Triangolazione
                    leftRotate(tree, parent);
                    x = parent;
                    parent = x->parent;
                }
                // Caso 3: Lineare
                rightRotate(tree, grandparent);
                parent->color = BLACK;
                grandparent->color = RED;
                break;
            }
        } else {
            Node *uncle = grandparent->left;

            if (uncle && uncle->color == RED) {
                // Caso 1: Lo zio è rosso (Recoloring)
                parent->color = BLACK;
                uncle->color = BLACK;
                grandparent->color = RED;
                x = grandparent;
            } else {
                if (x == parent->left) {
                    // Caso 2: Triangolazione
                    rightRotate(tree, parent);
                    x = parent;
                    parent = x->parent;
                }
                // Caso 3: Lineare
                leftRotate(tree, grandparent);
                parent->color = BLACK;
                grandparent->color = RED;
                break;
            }
        }
    }
    tree->root->color = BLACK;  // La radice deve essere sempre nera
}

// Funzione per inserire un nodo nell'albero
void insert(RBTree *tree, int val) {
    Node *newNode = createNode(val);

    if (!tree->root) {
        newNode->color = BLACK;
        tree->root = newNode;
        return;
    }

    Node *temp = tree->root;
    Node *parent = NULL;

    while (temp) {
        parent = temp;
        if (val < temp->val)
            temp = temp->left;
        else if (val > temp->val)
            temp = temp->right;
        else
            return;  // Evitare duplicati
    }

    newNode->parent = parent;
    if (val < parent->val)
        parent->left = newNode;
    else
        parent->right = newNode;

    fixRedRed(tree, newNode);
}

// Funzione per cercare un nodo con un valore specifico
Node* search(Node *root, int val) {
    while (root) {
        if (val < root->val)
            root = root->left;
        else if (val > root->val)
            root = root->right;
        else
            return root;
    }
    return NULL;
}

// Funzione per stampare l'albero in ordine
void inorder(Node *node) {
    if (!node)
        return;

    inorder(node->left);
    printf("%d(%s) ", node->val, node->color == RED ? "R" : "B");
    inorder(node->right);
}

// Funzione per stampare l'albero per livelli
void levelOrder(Node *root) {
    if (!root)
        return;

    Node *queue[100];
    int front = 0, rear = 0;

    queue[rear++] = root;

    while (front < rear) {
        Node *current = queue[front++];
        printf("%d(%s) ", current->val, current->color == RED ? "R" : "B");

        if (current->left)
            queue[rear++] = current->left;
        if (current->right)
            queue[rear++] = current->right;
    }
}

// Funzione per inizializzare l'albero
RBTree* createRBTree() {
    RBTree *tree = (RBTree*)malloc(sizeof(RBTree));
    if (!tree) {
        perror("Errore nell'allocazione dell'albero");
        exit(EXIT_FAILURE);
    }
    tree->root = NULL;
    return tree;
}

// Funzione per deallocare l'albero
void freeTree(Node *node) {
    if (!node)
        return;

    freeTree(node->left);
    freeTree(node->right);
    free(node);
}

// Main
int main() {
    RBTree *tree = createRBTree();

    // Inserimento di nodi
    int values[] = {7, 3, 18, 10, 22, 8, 11, 26, 2, 6, 13};
    for (int i = 0; i < sizeof(values) / sizeof(values[0]); i++) {
        insert(tree, values[i]);
    }

    printf("Inorder Traversal:\n");
    inorder(tree->root);
    printf("\n");

    printf("Level Order Traversal:\n");
    levelOrder(tree->root);
    printf("\n");

    // Liberazione della memoria
    freeTree(tree->root);
    free(tree);

    return 0;
}

```
###### Output:
---
**1. Visita in inordine**
L'output della traversata **inorder** stampa i valori in ordine crescente, con il colore del nodo indicato tra parentesi (`R` per rosso, `B` per nero). Questo mostra come l'albero è strutturato.
`2(B) 3(B) 6(R) 7(B) 8(B) 10(R) 11(B) 13(R) 18(B) 22(B) 26(R)`

---
**2. Visita in ampiezza**
La traversata **level order** stampa i valori livello per livello (BFS - Breadth First Search). Questo mostra la struttura dell'albero in ordine gerarchico.

---
#### Rotazioni:
##### A sinistra:
###### Codice professore:
![[Pasted image 20241128194045.png]]

---
![[Pasted image 20241129085819.png]]

---
##### Codice Online:
```c title:"Rotazione"
#include <stdio.h>
#include <stdlib.h>

// Definizione della struttura Node
typedef struct Node {
    int key; // opzionale, dipende dall'uso
    struct Node* left;
    struct Node* right;
    struct Node* parent;
} Node;

// Nodo NIL rappresentato come sentinella
Node* NIL;

// Radice dell'albero
Node* root;

// Funzione di rotazione a sinistra
void leftRotate(Node* x) {
    Node* y = x->right;
    x->right = y->left;
    if (y->left != NIL) {
        y->left->parent = x;
    }
    y->parent = x->parent;
    if (x->parent == NIL) {
        root = y;
    } else if (x == x->parent->left) {
        x->parent->left = y;
    } else {
        x->parent->right = y;
    }
    y->left = x;
    x->parent = y;
}

// Funzione di rotazione a destra
void rightRotate(Node* x) {
    Node* y = x->left;
    x->left = y->right;
    if (y->right != NIL) {
        y->right->parent = x;
    }
    y->parent = x->parent;
    if (x->parent == NIL) {
        root = y;
    } else if (x == x->parent->right) {
        x->parent->right = y;
    } else {
        x->parent->left = y;
    }
    y->right = x;
    x->parent = y;
}

// Funzione per creare un nuovo nodo
Node* createNode(int key) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->key = key;
    newNode->left = NIL;
    newNode->right = NIL;
    newNode->parent = NIL;
    return newNode;
}

int main() {
    // Inizializzazione del nodo NIL
    NIL = (Node*)malloc(sizeof(Node));
    NIL->left = NIL->right = NIL->parent = NULL;

    // Esempio d'uso
    root = createNode(10);
    root->left = createNode(5);
    root->left->parent = root;

    rightRotate(root); // Esegue una rotazione a destra su root

    // Debug
    printf("Nuova radice: %d\n", root->key);
    printf("Figlio destro della radice: %d\n", root->right->key);

    return 0;
}


```










## Albero Ternario:
è una struttura di dati degli alberi in cui ogni nodo ha al massimo tre nodi figli, solitamente intesi come il figlio di "sinistra", quello di "mezzo" e quello di "destra".
## Albero Generico:
### Cosa sono?
Gli **alberi generici** sono una collezione di nodi in cui ogni nodo è una struttura dati che consiste in record e una lista di riferimenti ai suoi figli (i riferimenti duplicati non sono consentiti). A differenza delle liste concatenate, ogni nodo memorizza l'indirizzo di più nodi.
Ogni nodo memorizza gli indirizzi dei suoi figli e l’indirizzo del primo nodo sarà memorizzato in un puntatore separato chiamato root.
Gli alberi generici sono alberi N-ari che hanno le seguenti proprietà: 
1. Molti figli in ogni nodo.
 2. Il numero di nodi per ciascun nodo non è noto in anticipo.
### Codice:
```c title:"Albero Generico"
//Node declaration
struct Node{
   int data;
   struct Node *firstchild;
   struct Node *secondchild;
   struct Node *thirdchild;
   struct Node *fourthchild;
   struct Node *fifthchild;
   struct Node *sixthchild;
}
```
Il codice però possiede due svantaggi:
1. ***Spreco di memoria*** – Non tutti i puntatori sono richiesti in tutti i casi. Quindi, c'è molto spreco di memoria.
2. ***Numero sconosciuto di figli*** : il numero di figli per ciascun nodo non è noto in anticipo.
Quindi il miglior codice sarà quello utilizzato usando gli Array dinamici:
```c title:"Miglior Codice"
//Node declaration
struct Node{
    int data;
    struct Node *firstChild;
    struct Node *nextSibling;
}
```
Questa rappresentazione presenta diversi vantaggi:
- ***Efficienza della memoria***: non sono richiesti collegamenti aggiuntivi, quindi viene risparmiata molta memoria.
- Li trattiamo come  ***alberi binari*** – Poiché siamo in grado di convertire qualsiasi albero generico in rappresentazione binaria, possiamo trattare tutti gli alberi generici con una rappresentazione primo figlio/fratello successivo come alberi binari. Invece di puntatori sinistro e destro, utilizziamo solo firstChild e nextSibling.
- Molti algoritmi possono essere espressi più facilmente perché si tratta semplicemente di un albero binario.
- Ogni nodo ha una ***dimensione fissa***, quindi non è necessario alcun array o vettore ausiliario.

## Visita:
#### Cos'è?
L'esame di un albero è l'esame di tutti i nodi di un albero secondo un ordine prestabilito.
Durante la “visita” di ciascun nodo si possono intraprendere azioni, quali Stampare il contenuto del nodo; Accodare il contenuto del nodo ad un insieme di dati.
#### Principali tipi di visita:
Esistono due principali tipi di visita, uno dei quali racchiude altri 3 metodi:
- In **profondità:**
	- _Preordine_
	- _Postordine_
	- _Inordine_
- In **ampiezza**
#### Visita in preordine:
##### Cos'è?
La visita **in preordine** è una modalità di attraversamento di un albero dove i nodi vengono visitati seguendo quest'ordine:
1. **Visita il nodo corrente (radice)**.
2. **Visita ricorsivamente i figli del nodo** (partendo dal figlio più a sinistra fino all'ultimo).
In altre parole, si visita prima un nodo, poi i suoi figli uno per uno, spostandosi sempre più in profondità prima di passare ai fratelli del nodo.
![[Pasted image 20241121155949.png]]
##### Codice Online:
```c title: "Vista in Preordine"
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Function to perform preorder traversal
void preorderTraversal(struct Node* root) {
  
    // Base case
    if (root == NULL)
        return;
  
    // Visit the current node
    printf("%d ", root->data);
  
    // Recur on the left subtree
    preorderTraversal(root->left);
  
    // Recur on the right subtree
    preorderTraversal(root->right);
}

struct Node* newNode(int data) {
    struct Node* node = 
      (struct Node*)malloc(sizeof(struct Node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;
    return node;
}

int main() {
    struct Node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);
    preorderTraversal(root);
    return 0;
}
```

##### Codice Professore:
![[Pasted image 20241104100407.png]]
###### Analisi del codice:
- `visitaProfondità(Tree t);` 
    Questo è il nome della funzione ricorsiva che implementa la visita in profondità dell'albero, in modalità preordine. L'argomento `t` rappresenta un nodo dell'albero che stiamo visitando.
    
- `t ≠ nil;`  
    Questa condizione verifica se il nodo attuale `t` esiste (cioè non è nullo). Se `t` è nullo, significa che non c'è nulla da visitare e la funzione termina.
- `visita la radice di t;`  
    Qui viene eseguita un'operazione sul nodo corrente `t`. Questo potrebbe includere, ad esempio, la stampa del valore del nodo, l'elaborazione di un dato associato al nodo, ecc.
    
- `Tree u ← t.leftmostChild();`  
    Questa istruzione assegna alla variabile `u` il figlio più a sinistra del nodo `t`. Se il nodo `t` non ha figli, `u` sarà nullo.
    
- `while u ≠ nil do`  
    Questo ciclo `while` è eseguito fino a quando esiste un figlio (o un fratello) da visitare. In particolare, serve a iterare tra tutti i figli del nodo corrente.
- `visitaProfondità(u);`  
    All'interno del ciclo, viene chiamata ricorsivamente la funzione `visitaProfondità` sul figlio corrente `u`. Questo permette di visitare ricorsivamente tutti i discendenti del figlio.
- `u ← u.rightSibling();`  
    Una volta completata la visita del sottoalbero radicato in `u`, la variabile `u` viene aggiornata per puntare al fratello destro del nodo `u` (se esiste). In questo modo, si prosegue la visita degli altri figli del nodo `t`


#### Visita in postordine:
##### Cos'è?
La visita **in postordine** è una modalità di attraversamento di un albero che segue questo ordine:
1. **Visita tutti i figli del nodo corrente** (da sinistra a destra).
2. **Visita il nodo corrente (la radice)**.
Quindi, a differenza della visita in preordine (dove si visita prima il nodo e poi i figli), nella postordine si visitano **prima i figli** e **poi la radice**.![[Pasted image 20241121170921.png]]
##### Codice Online:
```c title:"Postorder"
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Function to perform postorder traversal
void postorderTraversal(struct Node* node) {
  
    // Base case
    if (node == NULL)
        return;
  
    // Recur on the left subtree
    postorderTraversal(node->left);
  
    // Recur on the right subtree
    postorderTraversal(node->right);
  
    // Visit the current node
    printf("%d ", node->data);
}

struct Node* newNode(int data) {
    struct Node* node = 
      (struct Node*)malloc(sizeof(struct Node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;
    return node;
}

int main() {
    struct Node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);
    postorderTraversal(root);
    return 0;
}
```

##### Codice Professore:
![[Pasted image 20241104100503.png]]
###### Spiegazione:
1. **Condizione iniziale**:

    - L'algoritmo parte dalla chiamata `visitaProfonditaˋ(t)` dove t è la radice.
    - Se $t\neq nil$, esiste un nodo da visitare.
2. **Preparazione**:
    - Si ottiene il **figlio più a sinistra** del nodo t con il metodo `t.leftmostChild()`, che viene assegnato alla variabile `u`.
3. **Visita dei figli (while loop)**:
    - Si itera finché $u\neq nil$, visitando ricorsivamente ogni figlio u:
        - Si chiama `visitaProfondita` per visitare i figli di `u` in profondità.
        - Dopo la visita, `u` viene aggiornato al **fratello destro**: 
		 `(u ← u.rightSibling())`.
1. **Visita della radice**:
    
    - Dopo aver visitato tutti i figli del nodo t, si visita la radice di t.




#### Visita in inordine:
##### Cos'è?
E' un tipo di visita che segue il seguente ordine:
- Prima viene analizzato il sottoalbero sinistro.
- Successivamente viene analizzata la radice.
- Infine il sottoalbero destro.
![[Pasted image 20241121174042.png]]
##### Codice Online:
```c title:"Visita in Inordine"
#include <stdio.h>
#include <stdlib.h>

// Structure of a Binary Tree Node
struct Node {
    int data;
    struct Node *left, *right;
};

// Function to print inorder traversal
void printInorder(struct Node* node) {
    if (node == NULL)
        return;

    // First recur on left subtree
    printInorder(node->left);

    // Now deal with the node
    printf("%d ", node->data);

    // Then recur on right subtree
    printInorder(node->right);
}

// Function to create a new node
struct Node* newNode(int v) {
    struct Node* node = 
      (struct Node*)malloc(sizeof(struct Node));
    node->data = v;
    node->left = node->right = NULL;
    return node;
}

// Driver code
int main() {
    struct Node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);
    root->right->right = newNode(6);

    // Function call
    printf("Inorder traversal of binary tree is: \n");
    printInorder(root);

    return 0;
}
```
##### Codice professore:
![[Pasted image 20241104100524.png]]
###### Spiegazioni:
1. Condizione iniziale: 
   - Se il nodo $t\neq nil$, allora esiste un nodo da visitare.
	- Si ottiene il figlio più a sinistra del nodo `t` con il metodo `t.leftmostChild()` e si assegna a `u`.
	- Si inizializza un contatore `l` a 1.
2. Prima iterazione (while loop):
   - Si visitano ricorsivamente i figli $T_1,…,T_i$​, ovvero i primi ii figli.
   - Dopo ogni visita:
	- Si sposta `u` al fratello destro (`u←u.rightSibling()`).
	- Si incrementa il contatore `l`.
3. Visita della radice:
   - Una volta visitati i primi ii figli, si visita la radice del nodo `t`.
4. Seconda iterazione (while loop):
   - Si visitano ricorsivamente i figli $Ti+1,…,Tk$​ (gli ultimi $k−i$ figli), con lo stesso meccanismo del primo ciclo.
#### Visita in ampiezza:
##### Cos'è?
E' un tipo di visita che utilizza l'analisi di ogni nodo presente sullo stesso livello per poi passare al livello successivo.
![[Pasted image 20241121181247.png]]



##### Codice Online:
```c title "Visita in Ampiezza"
#include <stdio.h>
#include <stdlib.h>

// Tree Node
struct Node {
    int data;
    struct Node *left;
    struct Node *right;
};

// Queue is implemented using singly 
// Linked List
struct QNode {
    struct Node *tNode;
    struct QNode *next;
};

struct QNode *front = NULL;
struct QNode *rear = NULL;

// The following functions are defined later
// in this code
void enqueue(struct Node *tNode);
struct Node *dequeue();

// Function to do level order traversal of given
// Binary Tree using a Queue
void levelOrderTraversal(struct Node* root) {
    if (root == NULL) return; 

    enqueue(root);
    
    while (front != NULL) {
        struct Node* curr = dequeue();
        printf("%d ", curr->data);
        if (curr->left != NULL) enqueue(curr->left);
        if (curr->right != NULL) enqueue(curr->right);
    }
}

struct Node* newNode(int x) {
    struct Node* node = 
     (struct Node*)malloc(sizeof(struct Node));
    node->data = x;
    node->left = node->right = NULL;
    return node;
}
struct QNode* newQNode(struct Node* tNode) {
    struct QNode* qNode = 
     (struct QNode*)malloc(sizeof(struct QNode));
    qNode->tNode = tNode;
    qNode->next = NULL;
    return qNode;
}
void enqueue(struct Node *tNode) {
    struct QNode* qNode = newQNode(tNode);
    
    if (rear == NULL) {
        front = rear = qNode;
    } else {
        rear->next = qNode;
        rear = qNode;
    }
}
struct Node* dequeue() {
    if (front == NULL) return NULL; 
    struct Node* tNode = front->tNode;
    struct QNode* temp = front;
    front = front->next;
    if (front == NULL) rear = NULL; 
    free(temp);
    return tNode;
}
int main() {
    struct Node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);
    root->right->right = newNode(6);
    levelOrderTraversal(root);
    return 0;
}
```
##### Codice Professore:
![[Pasted image 20241104100548.png]]
###### Spiegazione:
1. **Condizione iniziale**:
    
    - Se $t\neq nil$, esiste un nodo da visitare.
    - Si crea una **coda ausiliaria Q**, inizialmente vuota, utilizzata per memorizzare i nodi da visitare.
    - Si aggiunge il nodo radice `t` alla coda con il comando `Q.enqueue(t)`
2. **Ciclo principale (while not `Q.isEmpty()`)**:
    
    - Finché la coda non è vuota:
        1. Estrai il nodo `u` in testa alla coda con `Q.dequeue()`
        2. Visita `u` (ad esempio, stampandolo o eseguendo un'operazione su di esso).
3. **Gestione dei figli di u**:
    - Si ottiene il **figlio più a sinistra** di `u` con il metodo `u.leftmostChild()`.
    - Si avvia un ciclo per processare **tutti i fratelli del figlio corrente**:
        - Aggiungi ogni figlio di `u` alla coda con `Q.enqueue(u)`
        - Passa al fratello destro del figlio corrente con 
         `u ← u.rightSibling()`
4. Il processo continua finché tutti i nodi sono stati visitati e la coda è vuota.



## Operatori:
#### Operatori principali:
##### Operatore di creazione: tree(v):
crea un albero nuovo con un solo nodo
##### Operazione di scrittura: write(Item v):
scrive informazioni in un nodo
##### Operatore di lettura: item read ():
legge il  contenuto di un solo nodo
##### Operazione genitore: Tree parent():
restituisce il nodo genitore
##### Operatore primo figlio: Tree leftmostChild():
restituisce il primo figlio oppure nil
##### Operatore primo figlio: Tree leftmostChild():
restituisce il prossimo figlio oppure nil
##### Operatore inserimento primo figlio: 
insertChild(Tree t):
inserisce il sottoalbero t come primo figlio (t.parent deve essere nil)
##### Operatore inserimento prossimo figlio: insertSibiling(Tree t):
inserisce il sottoalbero t come prossimo figlio (t.parent deve essere nil)
##### Operatore eliminazione primo figlio: deleteChild():
elimina il sottoalbero con radice il primo figlio corrente
##### Operatore eliminazione prossimo figlio: deleteChild():
elimina il sottoalbero con radice il prossimo figlio 
#### Esempio in codice C:
##### Codice:
```c title:"Operatori Alberi"
#include <stdio.h>
#include <stdlib.h>

// Definizione del nodo dell'albero
typedef struct TreeNode {
    int value;                 // Valore del nodo
    struct TreeNode* parent;   // Puntatore al nodo genitore
    struct TreeNode* leftmostChild; // Puntatore al primo figlio
    struct TreeNode* rightSibling; // Puntatore al fratello destro
} TreeNode;

// Funzione per creare un nuovo albero con un solo nodo
TreeNode* Tree(int value) {
    TreeNode* newNode = (TreeNode*)malloc(sizeof(TreeNode));
    newNode->value = value;
    newNode->parent = NULL;
    newNode->leftmostChild = NULL;
    newNode->rightSibling = NULL;
    return newNode;
}

// Funzione per leggere il valore di un nodo
int read(TreeNode* node) {
    if (node == NULL) {
        printf("Errore: Nodo nullo!\n");
        return -1; // Valore di errore
    }
    return node->value;
}

// Funzione per scrivere (aggiornare) il valore di un nodo
void write(TreeNode* node, int value) {
    if (node == NULL) {
        printf("Errore: Nodo nullo!\n");
        return;
    }
    node->value = value;
}

// Funzione per ottenere il genitore del nodo
TreeNode* parent(TreeNode* node) {
    if (node == NULL) {
        printf("Errore: Nodo nullo!\n");
        return NULL;
    }
    return node->parent;
}

// Funzione per ottenere il primo figlio del nodo
TreeNode* leftmostChild(TreeNode* node) {
    if (node == NULL) {
        printf("Errore: Nodo nullo!\n");
        return NULL;
    }
    return node->leftmostChild;
}

// Funzione per ottenere il fratello destro del nodo
TreeNode* rightSibling(TreeNode* node) {
    if (node == NULL) {
        printf("Errore: Nodo nullo!\n");
        return NULL;
    }
    return node->rightSibling;
}

// Funzione per aggiungere un figlio a un nodo
void addChild(TreeNode* parent, TreeNode* child) {
    if (parent == NULL || child == NULL) {
        printf("Errore: Nodo nullo!\n");
        return;
    }
    child->parent = parent;
    if (parent->leftmostChild == NULL) {
        // Se il nodo non ha figli, aggiungilo come primo figlio
        parent->leftmostChild = child;
    } else {
        // Trova l'ultimo fratello e aggiungi il nuovo nodo come fratello destro
        TreeNode* sibling = parent->leftmostChild;
        while (sibling->rightSibling != NULL) {
            sibling = sibling->rightSibling;
        }
        sibling->rightSibling = child;
    }
}

// Esempio di utilizzo
int main() {
    // Crea un albero con radice 10
    TreeNode* root = Tree(10);

    // Aggiungi figli alla radice
    TreeNode* child1 = Tree(20);
    TreeNode* child2 = Tree(30);
    addChild(root, child1);
    addChild(root, child2);

    // Aggiungi un figlio al primo figlio
    TreeNode* grandchild = Tree(40);
    addChild(child1, grandchild);

    // Test degli operatori
    printf("Valore della radice: %d\n", read(root));
    printf("Primo figlio della radice: %d\n", read(leftmostChild(root)));
    printf("Fratello destro del primo figlio: %d\n", read(rightSibling(leftmostChild(root))));
    printf("Genitore del nipote: %d\n", read(parent(grandchild)));

    // Aggiorna un valore
    write(child1, 25);
    printf("Nuovo valore del primo figlio: %d\n", read(child1));

    // Libera la memoria (da fare in pratica per evitare memory leaks)
    free(root);
    free(child1);
    free(child2);
    free(grandchild);

    return 0;
}

```
###### Spiegazione: 
- **Creazione di un nodo:** La funzione `Tree(int value)` crea un nodo con il valore specificato e inizializza i puntatori a `NULL`.
    
- **Lettura e scrittura:** `read` legge il valore del nodo e `write` aggiorna il valore del nodo.
    
- **Navigazione:**
    
    - `parent` restituisce il genitore del nodo.
    - `leftmostChild` restituisce il primo figlio del nodo.
    - `rightSibling` restituisce il fratello destro del nodo.
- **Aggiunta di figli:** La funzione `addChild` aggiunge un figlio a un nodo, aggiornando i puntatori `leftmostChild` e `rightSibling`.
    
- **Esempio:** Mostriamo come creare un albero, navigare tra i nodi e aggiornare i valori.
#### Realizzazione:
![[Pasted image 20241104104213.png]]
Questa immagine rappresenta una **struttura dati ad albero** organizzata su più livelli (indicati a destra: 0, 1, 2) e mostra come i nodi dell'albero sono collegati tramite puntatori. Ecco una spiegazione dettagliata:

---

##### 1. Struttura dell'albero:

- L'albero è composto da **nodi**. Ogni nodo contiene:
    - Un valore (ad esempio, `2`, `3`, `6`, ecc.).
    - **Puntatori**:
        - Verso il **primo figlio** (indica il nodo più a sinistra tra i figli).
        - Verso il **fratello destro** (indica il nodo successivo sullo stesso livello).
        - Eventualmente un puntatore al **genitore** (se non mostrato direttamente, lo si deduce dalla struttura).

---

##### 2. Analisi del livello e dei collegamenti:

###### Livello 0 (Radice dell'albero):

- Il nodo `2` è la **radice** dell'albero.
    - Non ha un genitore (indicato da `nil`).
    - Ha due figli:
        - Il primo figlio è `3`.
        - Il fratello destro del primo figlio è `6`.

---

###### Livello 1 (Figli della radice):

- Il nodo `3`:
    - È il **primo figlio** della radice `2`.
    - Ha due figli: `4` (primo figlio) e `7` (fratello destro di `4`).
    - Ha un fratello destro, il nodo `6`.
- Il nodo `6`:
    - È il fratello destro di `3` e quindi un altro figlio della radice `2`.
    - Ha un solo figlio, `5`.
    - Non ha un fratello destro (il puntatore è `nil`).

---

###### Livello 2 (Foglie o figli dei nodi di livello 1):

- Il nodo `4`:
    
    - È il **primo figlio** del nodo `3`.
    - Non ha figli (puntatori a `nil`).
- Il nodo `7`:
    
    - È il **fratello destro** del nodo `4`.
    - Non ha figli (puntatori a `nil`).
- Il nodo `5`:
    
    - È il **unico figlio** del nodo `6`.
    - Non ha figli (puntatori a `nil`).

---

##### 3. Significato dei collegamenti**

- I **puntatori** tra i nodi permettono di:
    1. Navigare verso il primo figlio (freccia verso il basso).
    2. Passare al fratello destro (freccia orizzontale a destra).
    3. Risalire verso il genitore, se necessario (freccia verso l'alto, se mostrata o dedotta).

Questa struttura consente di organizzare i dati gerarchicamente e facilita operazioni come la ricerca, l'inserimento, la cancellazione, o il passaggio tra livelli.

---

##### 4. Interpretazione numerica

- I numeri nei nodi rappresentano **valori o dati** associati ai nodi.
- I livelli a destra (`0`, `1`, `2`) indicano la **profondità** nell'albero:
    - Livello 0: Radice.
    - Livello 1: Figli della radice.
    - Livello 2: Figli dei nodi di livello 1 (foglie o ulteriori sotto-alberi).

---
##### Sintesi:
In sintesi, questa immagine rappresenta un albero gerarchico con radice `2`, che ha due sottoalberi principali (uno radicato in `3` e l'altro in `6`). I collegamenti visualizzati mostrano come i nodi sono strutturati e interconnessi tramite puntatori, utili per navigare tra i vari livelli e nodi.






# Capitolo 12: (Ordinamento)
## Problema dell'ordinamento:
### Introduzione:
Abbiamo una collezione di oggetti (records) $R_{i}$ ciascuno con una chiave $K_{i}$ con $i = 1,..., n$.
Le chiavi ammettono una **relazione di ordinamento**:
1. Ogni coppia di chiavi $K_{i},K_{j}$ soddisfa esattamente una delle tre relazioni (tricotomia)
- $K_{i}<K_{j}$ 
- $K_{i}= K_{j}$
- $K_{j}<K_{i}$
2. Se $K_{i}<K_{q}$ e $K_{q}<K_{j}$ allora $K_{i}< K_{j}$ (transitività) 
Vogliamo modificare l’insieme dei record in modo tale che $i < j \rightarrow Ki \le Kj$
Ricordiamo che la ricerca in un insieme ordinato ha un costo $O(log n)$, quindi avere una sequenza in ordine può far risparmiare tempo. 
Stiamo assumendo di saper soltanto confrontare chiavi tra loro. Consideriamo quindi un esempio contenente le chiavi, possiamo passare da$$V=[1,5,3,9,4,8,-1,12]$$
a$$VS=[-1,1,3,4,5,8,9,12]$$
Con un metodo che vedremo successivamente.
## Permutazioni:
### Introduzione:
#### Cosa sono?
Una permutazione è una sequenza di n oggetti distinguibili tra loro in uno specifico ordine. $$(a, c, b, d)$$ 
Se l’insieme degli oggetti è l’insieme {0, 1, 2, 3, . . . } possiamo usarli come indici per accedere un altro insieme di oggetti. Per esempio la permutazione : $$P = [6, 0, 2, 4, 1, 5, 3, 7]$$
consente di accedere al vettore V nel seguente modo:$$V [P[0]] == −1$$ $$V [P[1]] == 1$$$$V [P[2]] == 3$$e quindi di accedere a tutti gli elementi in ordine (per poi verificare che sia effettivamente così).
Dunque, ordinare una sequenza può essere considerato formalmente equivalente a trovare una permutazione che accede ai suoi elementi in ordine.
## Modi per ordinare i dati:
### Simple Sort:
#### Cos'è?
è il primo metodo utilizzabile per risolvere il problema dell'ordinamento di n oggetti:
![[Pasted image 20241130115628.png]]
E come si generano? 
![[Pasted image 20241130121832.png]]
Problema dell’ordinamento Il metodo sicuramente funziona, in quanto almeno una delle NP permutazioni mette in ordine l’input.
#### Costo:
Ci sono tre possibilità di costo dell'intera operazione:
- Nel caso migliore, la prima permutazione funziona ed il costo sarà $O(n)$ (solo quello della verifica).
- Nel caso peggiore solo l'ultima funziona, andando a costare $O(NP)$
- Nel caso intermedio, ci si fermerà in una posizione intermedia, dove il costo sarà circa $O(NP/2)$, che però è uguagliabile a $O(NP)$.
Dunque quante sono le permutazioni?
$$NP=n!\approx (\frac{n}{e})^n*\sqrt{2\pi n}(\frac{1+1}{12n}+O(\frac{1}{n^{2}}))$$
che, matematicamente, è improponibile.

---
Dunque il metodo è improponibile.
### Bubble Sort:
#### Cos'è?
è il primo metodo avvicinabile, ma non utilizzabile
![[Pasted image 20241130124951.png]]
L’algoritmo funziona perchè a forza di scambiare di posto, non ci saranno più elementi fuori ordine.
### Insertion Sorting:
#### Cos'è?
Il primo metodo utilizzabile è l'ordinamento per inserzione:
![[Pasted image 20241201132721.png]]
#### Utilizzo:
Dobbiamo verificare che 
- L'algoritmo effettivamente produce in uscita una sequenza ordinata.
- Valutare la sua complessità
##### Verifica della Correttezza:
- Prima dell'esecuzione del ciclo `for` la sotto-sequenza V[0] è sicuramente ordinata in quanto contiene un solo elemento.
- L'esecuzione del ciclo `while` all'iterazione i-esima del ciclo `for` trasferisce un elemento nella sua posizione corretta. 
- All'ultimo passo della iterazione i-esima del ciclo For, la sotto-sequenza V [0], . . . , V [i] è quindi ordinata.
- Quando il ciclo `for` termina definitivamente, questa proprietà è valida per V[0],..,V[n-1]
##### Costo:
Ad ogni iterazione del ciclo `for` i = 0 . . . n − 1, abbiamo un ciclo interno, ed un paio di assegnazioni. 
Il ciclo interno viene eseguito per valori di j che possono andare da i a 0 o, nel migliore dei casi, non sarà eseguita alcuna operazione.
Ogni iterazione del ciclo esterno ha un costo potenzialmente diverso, calcoliamo però il caso peggiore:
$$opcnt = (\sum\limits_{i=0}^{n-1}1+1)+(\sum\limits_{i=0}^{n-1}\sum\limits_{i=0}^{j-1}1)\le2n+\sum\limits_{i=0}^{n-1}=3n+\frac{(n-1)n}{2}=O(n^2)$$

---
Mentre nel caso migliore sopravvive solo il ciclo esterno e quindi il costo è $\Omega (n)$

---
#### Espressioni utili:
![[Pasted image 20241202155953.png]]
#### Limiti dell'ordinamento:
##### Quali sono?
Andiamo ad analizzare tutto ciò che abbiamo raccolto fino ad adesso:
- Dobbiamo distinguere tra n! configurazioni possibili; 
- Stiamo effettuando delle scelte binarie (ossia, ad ogni passo ci chiediamo se V [k] ≷ V [j] per qualche coppia k, j); 
- Possiamo quindi assumere di stare esaminando un albero binario; ma bisogna che il numero delle foglie dell’albero sia almeno n!; 
- Per arrivare dalla radice alle foglie si percorrono k livelli; 
- Ogni livello i contiene $2^i$ nodi, quindi il numero di livelli k è eguale al logaritmo (in base 2) del numero delle foglie; 
Quindi quanti livelli ci vogliono per distinguere n! foglie? $$log(n!) ≈ log(n^n) = n log (n).$$
Vediamo ora un primo algoritmo ricorsivo che raggiunge una complessità $O(nlog(n))$
### QuickSort
#### Introduzione:
![[Pasted image 20241202161231.png]]
#### Codici Prof:
![[Pasted image 20241202161318.png]]
![[Pasted image 20241202162047.png]]
#### Esempio Prof:
![[Pasted image 20241202162507.png]]
#### Complessità Computazionale:
Usiamo il teorema sulle ricorrenze lineari con partizione bilanciata. Nella partizione, ci aspettiamo che la posizione del perno k cada a metà del vettore, ossia che si stia partizionando il vettore iniziale in due metà eguali: 
$$T(n)=\begin{cases} 1~~~~~~~~~~~~~~~~~~~~n=1\\2T(\frac{n}{2})+n~~~~n>1\end{cases}$$ e allora avremo un tempo di esecuzione $T (n) = O(n log(n))$.
### MergeSort:
##### Introduzione:
Vediamo ora un secondo algoritmo ricorsivo che raggiunge una complessità $O(n log(n))$:
![[Pasted image 20241202163932.png]]
##### Codice Prof:
![[Pasted image 20241202164021.png]]
![[Pasted image 20241202164035.png]]
##### Complessità Computazionale:
La complessità computazionale del Mergesort è analoga a quella del Quicksort, dato che ad ogni passo ricorsivo sto spezzando la sequenza iniziale in due sottosequenze eguali, dunque:
$$T(n)=\begin{cases} 1~~~~~~~~~~~~~~~~~~~~n=1\\2T(\frac{n}{2})+n~~~~n>1\end{cases}$$e allora avremo un tempo di esecuzione $T (n) = O(n log(n))$.
### Confronto tra Mergesort e Quicksort:
##### Introduzione:
Sappiamo che i records sono una collezione di oggetti ($R_{i}$) ciascuno con una chiave $K_{i}$, con i che va da 1 a n. Ad esempio, immaginiamo di trovarci in una biblioteca e di dover ordinare dei libri, ed ognuno di questi possiamo rappresentarlo come un record. Ad ogni record (quindi ad ogni libro) associamo una chiave (ovvero, per esempio, il numero di pagine). Dunque per ordinare i libri, possiamo raggruppare le chiavi in ordine crescente
Possiamo dunque dire che un ordinamento è stabile se ogni volta che due chiavi sono eguali $K_{i}==K_{j}$ e se i record $R_{i}$ ed $R_{j}$ vengono mantenuti nello stesso ordine tra loro con cui comparivano nella sequenza iniziale.
Quindi se volessimo usare l'esempio di prima potremmo dire che l'ordinamento sarebbe stato stabile se due libri con la stessa chiave (quindi con lo stesso numero di pagine) fossero stati mantenuti nello stesso ordine nella sequenza iniziale.
- Possiamo infine dire che Mergesort è un algoritmo stabile, Quicksort no, e questo è un problema per alcune applicazioni.
##### Altre Osservazioni:
- Quicksort e Mergesort sono in qualche senso speculari, in quanto il lavoro di “sistemazione” viene effettuato da Quicksort prima delle chiamate ricorsive, mentre invece Mergesort lo effettua dopo. 
- Nel descrivere il comportamento di Quicksort abbiamo detto che ci aspettiamo una partizione bilanciata a metà; tuttavia questo non è garantito, mentre per Mergesort è garantito essere bilanciato
- Mergesort richiede uno spazio aggiuntivo di memoria $O(n)$, Quicksort $O(1)$
##### Complessità nel caso peggiore:
- Quicksort: $O(n^2);$ 
- Mergesort: $O(n log(n))$.
##### Complessità nel caso medio:
E tuttavia, nel caso “medio” (per una qualche definizione di “medio”), Quicksort è più veloce
### Coda con priorità:
#### Cosa sono?
Abbiamo un insieme di elementi ciascuno con assegnata una priorità (un valore intero, p.es. priorità massima per valori piccoli). 
Vogliamo poter eseguire le operazioni: 
- `min` restituisce l’elemento con priorità di valore numerico più basso; 
- `DeleteMin` come `min` ma elimina l’elemento dall'insieme; 
- `insert(t,p)` Aggiunge un oggetto in una coda con priorità
- `decrease(t,p)` Diminuisce la priorità di un oggetto portandola a p
Immaginiamo d realizzare la coda con una semplice lista (per esempio con i puntatori), che tempi otteniamo per queste operazioni?
---
- Per le **liste non ordinate**:
	- `insert` $O(1)$;
	- `min` $O(N)$
	-  `deleteMin` $O(N)$
---
- Per le **liste ordinate**:
	- `insert` $O(1)$;
	- `min` $O(N)$
	-  `deleteMin` $O(N)$
---
Si noti che una complessità $O(N)$ sulla singola operazione comporta una complessità totale $O(N^2)$ se l’operazione viene iterata N volte.
#### Heapsort:
##### Introduzione
Una particolare struttura dati adatta per la rappresentazione delle code con priorità ci consente di definire un metodo di ordinamento con complessità $O(nlog(n))$
Il metodo usa la struttura dati di supporto:
![[Pasted image 20241202182147.png]]

---
Una definizione grafica può essere:
Un albero binario in cui la chiave associata con ciascun nodo è minore della chiave associata con ciascuno dei due figli:

#### Caratteristiche:
In sostanza, si tratta di un albero binario memorizzato in un array lineare. La descrizione migliore se assumiamo un indirizzamento dell'array a partire dall'indice 0:
- l'elemento in posizione i è minore degli elementi in posizione i è minore degli elementi in posizione $2i+1$ e $2i+2$;
- L'elemento in posizione o è il più piccolo (radice dell'albero)
- Vale sempre la seguente formula:
$$K_{[\frac{j}{2]}}\le K_{j}~~~~~~~~~~~~~~~~~per~1\le[j/2]<j<N$$
Ossia l'elemento in posizione $[(j-1)/2]$ è il padre.
#### Proprietà:
L'heap ha come caratteristica quella di essere "pieno" escluse le foglie.
#### Esempio:
Un esempio di una heap memorizzata in un vettore:
$$[3, 5,9,6,8,9,10,10,18,9]$$
![[Pasted image 20241202182817.png]]
Per esempio, in questo caso, 6 si trova in posizione 4. Ciò significa che il padre di 6 è in posizione 1, cioè è 5. Questo corrisponde alla realtà.
#### Operazioni fondamentali:
##### DeleteMin:
![[Pasted image 20241202191854.png]]
###### Codice Prof:
![[Pasted image 20241202191718.png]]

---
**Esempio:**
![[Pasted image 20241202191831.png]]

---
##### HeapInsert:
Si occupa dell'inserimento nella Heap di un nuovo elemento.
###### Codice prof:
![[Pasted image 20241202192046.png]]

---
##### HeapSort:
###### Codice prof:
![[Pasted image 20241202192148.png]]
###### Problemi:
L’ordinamento presenta particolari problemi quando si debbano ordinare grosse quantità di dati, tali da NON poter essere memorizzate nella RAM. Si tratta di una argomento specializzato che non tratteremo oltre, ma che è estremamente rilevante per applicazioni con database di grandi dimensioni.
#### Altri algoritmi:
##### Quali sono?
`Straight selection`Ricerca sequenziale del minimo corrente ad ogni passo $O(N^2)$; `tree selection` Ricerca usando alberi (binari) “normali”; dipende dalla struttura dell’albero, e nel caso peggiore $O(N^2)$;[[#Albero Binario]] 
`shellsort` Simile ad insertion sort, scelta della distanza tra i termini da confrontare; è possibile una implementazione $O(N^1.5)$;
##### Shellsort:
Uno dei problemi di insertion sort è che gli scambi tra chiavi avvengono tra posizioni adiacenti, quindi una chiave “viaggia” a velocità bassa. Se invece scegliessimo di confrontare tra loro elementi “lontani” allora si potrebbe migliorare:
![[Pasted image 20241202192747.png]]
###### Codice Prof:
![[Pasted image 20241202192834.png]]
#### Esistono algoritmi **$O(n)$**?
##### Risposta:
Si esistono algoritmi lineari **se** abbiamo a disposizione **più** informazioni, in particolare se si può fare qualcosa di più che semplicemente confrontare due chiavi tra loro.
##### Esempio:
![[Pasted image 20241202193050.png]]
# Capitolo 40: Tabelle
## Vettori ed array:
### Introduzione:
#### Tipi di dati:
Possiamo accedere e recuperare informazioni in tempo O(1)?
La risposta è quello che accade quando accediamo degli array mono-dimensionali 
$$rv = V [k]$$
o multi-dimensionali: $$ra = A[i][j] $$Quindi, se le informazioni sono indirizzate da indici numerici, e se l’indice numerico è calcolabile in tempo O(1), allora possiamo accedere in tempo O(1).
Ma cosa accade quando quando il compilatore traduce il codice che abbiamo appena visto?

---
#### Caso monodimensionale:

##### Esempio:
![[Pasted image 20241202201927.png]]
##### Come accede a $v[i]$:
Per accedere a v[i] il compilatore ha bisogno di conoscere:
- l'indirizzo di partenza del vettore v
- Le dimensioni di ciascun elemento (per un  `double`: 8 byte)
- L'indice del primo elemento xb(in C e nei linguaggi derivati: 0);
Il compilatore allora può calcolare l'indirizzo di memoria dell'elemento da accedere:
```
addr = start(v) + size*(i-xb)
(in particolare, nei dati presi come esempio: start(v)+ 8*(4-0))
```

---
#### Caso multidimensionale:
##### Cos'è?
Una collezione di oggetti, tutti dello stesso tipo, identificati da un insieme di indici; potremmo visualizzare un array 2D come una collezione di array 1D, anche se va parzialmente contro la interpretazione normale del compilatore che sarebbe:
- **Compiler view**
	Un array è una collezione di oggetti tale che sia possibile identificare la posizione in memoria di ciascuno di essi dati i suoi indici (ed un insieme di dati ausiliari di cardinalità limitata).
##### Esempio:
![[Pasted image 20241202204508.png]]

###### Problema:
- Come viene memorizzato l'array 2D
	Il problema è che si deve tradurre una struttura multidimensionale in una memoria che è monodimensionale (la memoria RAM è sostanzialmente un vettore, ogni locazione è identificata da uno ed un solo indirizzo). In C, e nei linguaggi derivati, si usa la memorizzazione per righe.
##### Come accede a $a[i][j]$ ?
il compilatore ha bisogno di conoscere:
- L'indirizzo di partenza in memoria dell'array a;
- La dimensione di ciascun elemento dell'array (per un double 8 byte)
- L'indirizzo iniziale in ciascuna dimensione xb (in C = 0);
- Il numero di elementi NC in ciascuna riga (in questo caso 20)

Allora il compilatore può calcolare 
```
addr = start(a) + size * ( (i - xb)*NC + (j-xb) )
(che nel caso equivale a = start(a) + 8*( (4-0)*20+(3-0)))
```
Questo è un esempio di una funzione di indice:
##### Rappresentazione:
![[Pasted image 20241202204920.png]]
##### Altri metodi di memorizzazione:
###### Per colonne:
Il primo indice potrebbe essere 1 invece che 0! Questo schema è utilizzato nei linguaggi Matlab, Fortran e Julia; la funzione di indice deve essere modificata usando il numero di righe invece che il numero di colonne:
```
addr = start(a) + size * ( (j - xb)*NR + (i -xb)) = start(a) + 8*( (3-1)*10+(4-1))
``` 
Matlab (e Julia) richiede che il primo indice sia 1; 
Fortran consente di scegliere l’indice iniziale xb, e 1 è il default.
![[Pasted image 20241203132013.png]]
##### Problema
Cosa succede se il numero di righe/colonne non è noto a tempo di compilazione? 
Per esempio, possiamo scrivere una funzione che accetta una variabile `a`: 
potremmo voler passare dinamicamente alla funzione il numero di righe e colonne, per interpretare correttamente la variabile. Se si può fare, allora il linguaggio che si sta usando supporta gli array bi- e multi-dimensionali.
Questo non accade in C perché in questo linguaggio di programmazione il compilatore interpreta l'espressione:$$x=mat[i][j]$$
in due modi completamente diversi, a seconda che le dimensioni della variabile `mat` siano note o meno al tempo di compilazione.

---
 Se le dimensioni sono note solo a runtime
 Il compilatore interpreta $$x=mat[i][j]$$
come:
- mat è un puntatore ad un array di puntatori; con `mat[i` si seleziona l'elemento (puntatore all'indice $[i]$)
- Ciascun puntatore identifica un distinto array di riga, gli elementi di ciascuna riga sono indirizzati da [j]
- Ciascuna riga è allocata indipendentemente e non c'è alcuna ovvia relazione tra le posizioni in memoria degli elementi di due qualsiasi righe.
###### tipi di tabelle hash:
![[Pasted image 20241203141334.png]]
L'immagine mostra due versioni di rappresentazione di una **tabella hash** (o **hash table**) con **liste di collisione**, utilizzata per gestire le collisioni in una struttura dati basata su hashing.

---
**Versione 1: Singola lista concatenata**

- Qui tutti i valori che si "mappano" agli stessi indici dell'array principale (il cosiddetto "array di bucket") sono memorizzati in un'unica **lista concatenata globale**.
- Ogni indice del bucket array punta a una posizione nella lista concatenata che contiene le informazioni relative ai valori memorizzati.
- **Caratteristiche**:
    - Tutti i dati sono organizzati in **un'unica struttura condivisa** (una lista concatenata globale).
    - Ogni indice (come 0, 4, 8, 11) punta all'inizio del sottoinsieme che appartiene a quell'indice.
---
**Versione 2: Liste concatenate separate**
- Qui ogni bucket (cella dell'array principale) ha la propria **lista concatenata separata** per memorizzare i dati che si mappano a quel bucket.
- Ogni bucket dell'array punta direttamente alla propria lista, che contiene tutti gli elementi con la stessa chiave hash.
- **Caratteristiche**:
    - Più semplice da gestire: ogni bucket è responsabile esclusivamente dei propri elementi.
    - Non c'è una lista concatenata unica: ogni bucket può essere trattato indipendentemente dagli altri.

---
**Confronto tra le due versioni**
1. **Gestione della memoria**:
    - Nella **Versione 1**, la lista concatenata globale è una struttura unica, il che può ridurre il numero di puntatori necessari.
    - Nella **Versione 2**, ogni bucket ha la propria lista, quindi ci sono più puntatori ma una maggiore modularità.
2. **Efficienza di accesso**:
    - Nella **Versione 1**, per accedere a un elemento specifico, è necessario attraversare la lista concatenata fino a trovare il sottoinsieme corrispondente.
    - Nella **Versione 2**, accedere a un bucket specifico è più diretto, perché ogni bucket ha la sua lista dedicata.
3. **Modularità e semplicità**:
    - La **Versione 2** è più intuitiva per la gestione delle collisioni, poiché ogni bucket è isolato.
    - La **Versione 1** può essere più complessa da implementare, ma può risultare vantaggiosa in termini di utilizzo della memoria per scenari specifici.

---
##### Linguaggi di programmazione ed array multidimensionali:
###### Difformità
![[Pasted image 20241203142836.png]]

---
In C/C++/Java come abbiamo visto il codice 
```
void compute(double a[][])
``` 
comporta che a sia interpretato come Un array 1-D di puntatori (ad array 1-D) e naturalmente questi puntatori (anche nel caso in cui le righe abbiano tutte la stessa lunghezza) possono puntare ad una qualunque posizione di memoria, per cui per sapere dove trovare `mat[2][3]` bisogna esaminare il puntatore contenuto in `mat[2]`, e poi accedere gli elementi puntati, all'indice 3.
###### Come fare? (caso 1)

```c
void compute(int nr, int nc, double mat[]) 
x = mat[my2Dindex(i,j,nr,nc)] 
int my2Dindex(i,j,nr,nc) {
return(i*nc+j);
}
```
il precedente codice illustra come in **C** o **C++** si possano simulare gli **array multidimensionali** utilizzando un **array monodimensionale** e calcolando manualmente l'indice corrispondente tramite una funzione di indirizzamento.

---

**1. Dichiarazione di un array come monodimensionale**

- L'array `mat[]` viene dichiarato come monodimensionale, anche se in realtà si vuole utilizzarlo come un array bidimensionale.
- La dimensione effettiva del "matrice" è definita dalle variabili:
    - `nr`: numero di righe.
    - `nc`: numero di colonne.

In pratica, si tratta di memorizzare gli elementi di una matrice bidimensionale in una sequenza lineare.

---
**2. Funzione di indirizzamento manuale**
La funzione `my2Dindex(i, j, nr, nc)` calcola l'indice lineare corrispondente a una posizione (i,j)(i, j) della matrice bidimensionale.
La formula è:  
indice lineare=i⋅nc+j

- `i`: Indice della riga.
- `j`: Indice della colonna.
- `nc`: Numero di colonne (utile per sapere quanti elementi occupa ogni riga).

**Esempio:** Se la matrice è:

```
1  2  3
4  5  6
7  8  9
```

Rappresentata linearmente:  
`[1, 2, 3, 4, 5, 6, 7, 8, 9]`

- Per accedere a (1,2)(1, 2) (seconda riga, terza colonna): 
indice lineare=$1*3+3=5$ che corrisponde a 6 nell'array lineare

---

**3. Uso nella funzione `compute`**

- Nella funzione `compute`, la riga `x = mat[my2Dindex(i, j, nr, nc)]` usa la funzione di indirizzamento per accedere all'elemento desiderato nell'array monodimensionale come se fosse bidimensionale.
- Questo approccio permette di simulare il comportamento di un array bidimensionale senza dichiararlo esplicitamente.

---

**4. Inlining**
- Il commento sull'**inlining** sottolinea che è preferibile che il compilatore trasformi la funzione `my2Dindex` in una **funzione inline**.
    - Una funzione inline viene "espansa" direttamente nel codice, evitando il costo della chiamata a funzione.
    - Dato che la funzione `my2Dindex` è semplice, fare inlining migliora le prestazioni.

---

**Vantaggi di questo approccio**

1. **Flessibilità nella gestione della memoria**: La matrice è memorizzata in un blocco continuo di memoria.
2. **Compatibilità con librerie o funzioni che supportano solo array monodimensionali**.
3. **Maggiore controllo sugli indici**: È possibile calcolare l'indirizzo manualmente.

---

**Quando si usa questo approccio?**

- Quando la dimensione dell'array non è nota a tempo di compilazione.
- Per ottimizzare l'accesso alla memoria in contesti come il calcolo numerico.
- In linguaggi come C o C++ dove gli array bidimensionali standard hanno delle limitazioni o overhead.
---
###### Caso 2:
![[Pasted image 20241203145211.png]]

---
### Tabella bidimensionale: 
#### Introduzione:
##### Cos'è?
Supponiamo di avere una certa quantità di dati, con chiavi numeriche, e che possano avere delle ripetizioni (ossia diversi record possono contenere la stessa chiave) Si potrebbero memorizzare i puntatori ai record in una tabella bidimensionale
![[Pasted image 20241204124633.png]]
##### Spiegazione ed esempio:
###### Esempio:
**Archivio di dati per studenti in una scuola**
Supponiamo di voler gestire informazioni su studenti di diverse classi e sezioni, ma non tutte le combinazioni di classe e sezione hanno studenti associati. Utilizziamo una tabella bidimensionale per memorizzare puntatori ai record degli studenti.

---
**Struttura:**

- Ogni riga rappresenta una **classe** (ad esempio 1ª, 2ª, 3ª).
- Ogni colonna rappresenta una **sezione** (ad esempio A, B, C).
- In ogni cella, memorizziamo un puntatore a un record che contiene informazioni sugli studenti (oppure `nil` se non ci sono studenti in quella combinazione).

---
**Tabella bidimensionale:**

| Classe/Sezione | A   | B   | C   | D   |
| -------------- | --- | --- | --- | --- |
| **1ª**         | R1  | nil | nil | nil |
| **2ª**         | R2  | nil | R3  | nil |
| **3ª**         | nil | R4  | nil | R5  |

- `R1`, `R2`, ecc., sono puntatori ai record che memorizzano i dati sugli studenti.

---
**Record degli studenti:**

- **R1**: `{ "Classe": 1, "Sezione": "A", "Studenti": ["Alice", "Bob"] }`
- **R2**: `{ "Classe": 2, "Sezione": "A", "Studenti": ["Carlos"] }`
- **R3**: `{ "Classe": 2, "Sezione": "C", "Studenti": ["David", "Eve"] }`
- **R4**: `{ "Classe": 3, "Sezione": "B", "Studenti": ["Frank"] }`
- **R5**: `{ "Classe": 3, "Sezione": "D", "Studenti": ["Grace", "Hannah"] }`

---
**Accesso ai dati:**

Con questa struttura, possiamo accedere facilmente ai record:

1. Per trovare gli studenti della **2ª classe, sezione C**:
    
    - Consultiamo la tabella: posizione (2ª riga, 3ª colonna) → `R3`.
    - Seguiamo il puntatore `R3` per accedere al record: `{ "Classe": 2, "Sezione": "C", "Studenti": ["David", "Eve"] }`.
2. Per controllare se ci sono studenti nella **3ª classe, sezione A**:
    
    - Consultiamo la tabella: posizione (3ª riga, 1ª colonna) → `nil`.
    - Risultato: Nessun record presente.

---

###### Vantaggi di questa rappresentazione:

- **Efficienza:** Accediamo ai record in tempo costante O(1)O(1)O(1) con gli indici della tabella.
- **Risparmio di memoria:** Non usiamo spazio per celle vuote (`nil`).
- **Semplicità:** Separiamo la logica della matrice dalla gestione dei dati nei record.

---
##### Altro esempio:
###### Introduzione:
Supponiamo ora di avere una certa quantità di dati, con chiavi memorizzate su 8 bytes, quindi con valori nell'insieme $[1 : 26^4].$ Usare le chiavi come indici in una tabella consente di fare ricerche in tempo O(1); 
l’idea potrebbe essere generalizzata al caso di chiavi non numeriche (p.es. stringhe di caratteri), semplicemente usando la loro rappresentazione binaria. 

---
###### Qual è il problema fondamentale di questo schema? 
Predisporre una tabella accessibile per tutti i valori possibili della chiave comporta l’uso di una grande quantità di memoria. Ad esempio, con chiavi da 8 caratteri ci sono $26^8 ≈ 2 × 10^{11}$ valori possibili, e quindi righe della tabella.
Se l’insieme dei valori delle chiavi che si presentano in pratica è più piccolo dell’insieme dei valori teoricamente possibili, si ha uno spreco di memoria.

---
#### Indirizzamento diretto:
##### Funzioni indice:
![[Pasted image 20241204212027.png]]
Ecco una spiegazione passo per passo:

1. **Definizione di una funzione indice**:
    
    - Dato un elemento $K \in U$(dove K è una **chiave** appartenente a un universo U),
    - Si vuole costruire una funzione $h(K) : U \to \{1, \dots, m\}$ .
    - Questa funzione h deve essere **iniettiva**, ovvero soddisfare la seguente condizione: $K1≠K2  ⟹  h(K1)≠h(K2)$. Significa che chiavi diverse ($K_1, K_2$) devono essere associate a valori distinti tramite h.
2. **Cardinalità di mm**:
    
    - Affinché la funzione h sia iniettiva, il numero dei possibili valori di $h(K)$ (ovvero il numero di elementi in $\{1, \dots, m\}$ deve essere **almeno pari alla cardinalità di U**, cioè al numero di elementi in U.
    - In simboli: $m = |U|$, dove $|U|$ rappresenta la cardinalità dell'universo U.
3. **Significato pratico**:
    
    - Una funzione indice è utile per mappare in modo unico ogni chiave K dell'universo U a un valore numerico (nell'intervallo $\{1, \dots, m\}$.
    - Questa proprietà di unicità è fondamentale in contesti come tabelle hash, dove si cerca di rappresentare un insieme di dati in uno spazio ridotto senza collisioni (quando possibile).
### Tabelle Hash:
#### Funzioni di hashing:
##### Introduzione:
La dimensione della tabella può essere $m << |U|$ dove occasionalmente si può avere una collisione.
$K_{1}\neq K_{2},~h(K_1) = h(K_{2})$
Sarà necessario avere un meccanismo per la risoluzione delle collisioni; se queste sono sufficientemente rare, la loro gestione potrebbe non costare troppo.
La funzione $h(K)$ viene normalmente detta hash o funzione di hashing
##### Requisiti per una tabella hash:
- Che sia disponibile una funzione h() calcolabile velocemente (O(1))
- Che la funzione h() sia tale che i valori calcolati sull'insieme delle chiavi (attese) siano ben distribuiti
- Che sia disponibile un metodo per la risoluzione delle collisioni.
- Che la dimensione m della tabella sia una sovrastima della cardinalità dell'insieme delle chiavi da gestire, in modo da evitare un riempimento completo. (questo è necessario per almeno una tipologia di tabelle hash).
##### La funzione h:
Dovrebbe essere uniforme, ossia la probabilità che una chiave qualsiasi K venga inserita alla posizione i nella tabella (di dimensione m) dovrebbe corrispondere ad una distribuzione uniforme:$$Q(i)=\sum\limits_{K:h(K)=i}P(K,i)≈\frac{1}{m}$$
E quindi come si costruisce una funzione di hashing?
- **troncamento**
- **folding**
###### Troncamento:
Spesso si usa un solo sottoinsieme della chiave.
In molte applicazioni si usano degli identificatori con parti comuni e parti varianti, come Type1, Type2, Type3 etc., si cerca di eliminare la parte comune, p.es. estraendo da una stringa solo la sua porzione centrale.
###### Folding:
Si spezza una chiave in più parti e queste vengono combinate attraverso una funzione ausiliaria.
###### Esempi di funzioni di hash:

---
1. Estrazione:$$h(K)=int(b)$$dove b è un sottoinsieme dei bit della rappresentazione binaria di K, di solito la parte centrale
---
2. XOR:
   $$h(K)=int(b),b=p_{1}(K)⊕ p_2(K ) ⊕ · · · ⊕ p_n(K)$$
   dove p(K) è una partizione della chiave K e ⊕ è l'operatore OR-esclusivo bit a bit
---
3. Moltiplicazione:
   $$h(K)=[m(iC-[iC])]$$
   dove m è un numero intero qualsiasi, i è $int(bin(K))$, C è un numero reale $0<C<1$. In questo caso va scelto un valore m arbitrario, e Knuth propone $\frac{\sqrt 5 - 1}{2}$ che è l'opposto del numero di Bernoulli normalmente utilizzato
---
4. Divisione:
   si usa il resto della divisione $$h(k)=int(bin(K))~mod~m$$
Nel metodo della divisione serve un valore di m dispari; infatti, assumendo la rappresentazione binaria dei dati, con $m=2^p$ tutti i valori che abbiano gli stessi p bit finali andranno a collidere.
In particolare, si usano spesso dei valori primi distanti dalle potenze di due; ad esempio, 13, 23, 47, 97, 193, 383, 769, 1531, 6143, 12289

---
##### Funzione:
###### Immagine:
![[Pasted image 20241205123356.png]]
###### Descrizione dell'algoritmo

1. **Input**:
    - k[]: un array di caratteri (può rappresentare una chiave, come una stringa).
    - l: la lunghezza della chiave k[]k[]k[].
    - m: il modulo, ovvero il numero massimo di valori distinti che la funzione hash può assumere (tipicamente m è la dimensione di una tabella hash).
2. **Calcolo**:
    
    - Si inizializza una variabile intera b con il valore della funzione **`ord`** applicata al primo carattere di k[].
        - **`ord(c)`** è una funzione che restituisce il valore ASCII (o Unicode) di un carattere ccc.
    - Poi si iterano i caratteri di k[]k[]k[], a partire dal secondo carattere (j=2) fino all'ultimo (l):
        - Ad ogni passo, si aggiorna b con questa formula: $$b←(b⋅256+ord(k[j]))~mod~m$$
        - Qui 256 rappresenta il numero di valori possibili per un byte (da 0 a 255).
3. **Output**:
    
    - La funzione restituisce b, che è il valore hash calcolato.

###### Come funziona?

L'algoritmo costruisce l'hash combinando i valori dei caratteri di k[], trattandoli come una sequenza di byte. La formula:
$$(b⋅256+ord(k[j]))mod  m$$
significa che ogni carattere successivo di k[] contribuisce a costruire un numero che viene ridotto tramite il modulo m. Questo garantisce che il risultato rimanga entro i limiti desiderati ([0,m−1]).

###### Esempio reale:
- Input:
	- k[]="abc" (stringa con i caratteri 'a', 'b', 'c'),
	- l = 3 (lunghezza della stringa),
	- m=10 (ad esempio, vogliamo che l'hash sia compreso tra 0 e 9).

- Calcolo:
	1. Inizializzazione:
	    - $b=ord(’a’)=97$ (valore ASCII del carattere 'a').
	    
	2. Iterazione:
	    - Per $j=2 (k[2])= b:$ $$b←(97⋅256+ord(’b’))~~~~mod 10=(97⋅256+98)~~~mod 10=24930~~~mod10=0$$
	    - Per $j=3 k[3]=c$ : $$b←(0⋅256+ord(’c’)) mod  10=(0+99) mod  10=9$$
	3. Risultato:
	    - La funzione restituisce b=9b = 9b=9.

###### Applicazione pratica

Questo algoritmo viene usato in:

- **Tabelle hash**: per generare un indice unico per chiavi diverse.
- **Gestione delle collisioni**: dato che il modulo m riduce il range di valori hash, questo può creare collisioni (due chiavi diverse con lo stesso hash). Tuttavia, la combinazione di 256 e il modulo aiuta a distribuire uniformemente gli hash.
#### Risoluzione delle collisioni: 
##### Come fare?
Ci sono due classi di metodi principali per la risoluzione delle collisioni:
- metodi interni: una scansione interna, _open addressing_
- metodi esterni: le liste di trabocco (_chaining_)
##### Scansione interna lineare:
###### Cos'è?
Si estende la funzione h con un secondo argomento:
$$h(K, i), ~~i=0,...,m-1$$
se l'elemento della tabella indirizzato da h(K,i) è occupato, si passa la valore successivo di i fin quando si sia scandita tuta la tabella. Se la ricerca di una posizione libera non trova risultati, la tabella è piena.
Una versione molto comune è la scansione lineare in cui $$h(K , i) = (h(k) + s · i)~mod~m$$se s = 1 si sta semplicemente incrementando il risultato del precedente calcolo di h. Se si cancella un elemento, non si può marcare una posizione come “libera”.
###### Esempio:
![[Pasted image 20241205131932.png]]
###### Vantaggi e svantaggi:
- **Vantaggi**:
	- Semplicità dell'algoritmo
	- Memorizzazione delle sole chiavi
- **Svantaggi**:
	- Creazione di _cluster_ che tendono ad espandersi;
	- Necessità di sovradimensionamento della tabella
L'algoritmo va in crisi quando la tabella è vicina ad essere totalmente riempita, quindi si tende a sovradimensionarla opportunamente. Una regola "empirica" è che le tabelle con scansione interna tendono a funzionare bene fino ad una occupazione di circa il 60% dello spazio disponibile.
##### Le liste di trabocco:
###### Cosa sono?
Per ogni indice della tabella, si memorizza una lista, a cui vengono via via aggiunge le chiavi reinviatie in quella posizione dalla funzione h(K).
###### Esempio:
![[Pasted image 20241205132425.png]]
###### Vantaggi:
- La tabella richiede solo una lista di puntatori,
- La tabella principale può essere allocata alla dimensione minima
- Non ci sono limiti al numero di entità memorizzate.
Tuttavia, se le chiavi sono di piccole dimensioni, si ha un aggravo di memoria dovuto ai puntatori.
##### Complessità
###### Nei due metodi:
Nel caso peggiore la ricerca di un elemento in una tabella hash ha un costo lineare nella dimensione della stessa tabella:
- Nella scansione interna, la ricerca può avere costo O(m) dove m è la dimensione della tabella; 
- Nella implementazione con liste di trabocco, la ricerca può avere costo O(n) dove n è il numero di chiavi memorizzate.
###### Definizioni:
![[Pasted image 20241205134234.png]]I tempi di inserzione e cancellazione sono determinati da I (α) e S(α). Per inserire un nuovo elemento in una tabella, bisogna prima cercare la sua chiave: Se la ricerca è infruttuosa, si otterrà la posizione in cui inserire il nuovo elemento; Se la ricerca è fruttuosa, ossia si trova la chiave, bisogna gestire la collisione. 
Per cancellare un elemento bisogna prima cercare la posizione della sua chiave.

---
###### Complessità media:
![[Pasted image 20241205134443.png]]
##### Insiemi e dizionari:
![[Pasted image 20241205134525.png]]
# Capitolo 50 (i grafi):
## I grafi:
### Introduzione:
#### Cosa sono?
Un grafo è una collezione di due insieme, i _vertici_ (o nodi) V e gli archi $\epsilon$ (ossia coppie di nodi (I,J)):
Esistono diversi tipi grafi:
#### Definizioni:
##### Grafi e nodi:
---
- Grafi **Orientati**:
  Sono grafi in cui gli archi (I, J) e (J, I) sono distinti (in particolare uno dei due potrebbe non esistere);
---
- Grafi **Non orientati**:
  Sono dei grafi in cui non si considera l'ordine dei nodi in un arco, ossia [I, J] corrisponde sia a (I, J) che a (J, I).
---
- Nodi **adiacenti**:
  Due nodi i e j si dicono adiacenti se esiste un arco che li connette (i, j) $\in \epsilon$ 
---
- Arco **Incidente**:
  l’arco (i, j) si dice incidente su j (da i); 
---
- **Grado** di un nodo: 
  il grado in entrata è il numero di archi incidenti su di un nodo (in uscita: archi incidenti da un nodo)
---
- **Cammino**:
  Dato un grafo orientato $G$, un cammino di lunghezza k è una sequenza di nodi $u_0, u_1, . . . , u_k$ tale che ($u_{i}, u_{i+1}\in \epsilon$).
  Se non ci sono nodi ripetuti si dice semplice, se $u_{o}=u_{k}$ si dice chiuso, se è entrambi si chiama "Ciclo"
---
- Grafi **orientati aciclici**:
  Sono grafi in cui non esiste alcun ciclo $(I_{1},I_{2}), (I_2, I_3), . . . (I_n, I_1).$
---
- **Catena**:
  In un grafo non orientato G, una catena è una sequenza di nodi "$u_{0}, u_{1},...,u_{k}$" tale che $[u_i , u_{i+1}]\in$  $\varepsilon$;  analogamente con la definizione per grafi orientati, una catena semplice e chiusa è un circuito.
---
##### Connessioni:
---
- **Connessione** (semplice):
  Se G= ($V, \varepsilon$) è un grafo _non orientato_, dunque G è connesso se per ogni coppia di nodi u,v esiste una catena da u a v
---
- **Componenti connesse**
  Si dice componente connessa un sottografo connesso e massimale.
---
- **Connessione forte**: 
  Se G = (V, E) è un grafo orientato, allora G è fortemente connesso se per ogni coppia di nodi u, v esiste un cammino da u a v , ed un cammino da v a u. 
---
- **Componenti fortemente connesse** 
  Si dice componente fortemente connessa un sottografo fortemente connesso e massimale: 
	- Un grafo G′ è un sottografo di G se e solo se V′ ⊆ V e E′ ⊆ E; 
	- Un sottografo G′ è massimale se non esiste nessun sottografo fortemente connesso di G che lo contiene strettamente, ossia non esiste G′′ tale che G′ ⊂ G′′ ⊆ G;
---
- **Albero libero**:
  Un grafo non orientato è un albero libero se è connesso e per ogni coppia di nodi esiste una e una sola catena semplice. 
---
- **Albero Radicato**:
  Un albero radicato si ottiene da un albero libero fissando arbitrariamente un nodo come radice, e poi ordinando i rimanenti per livelli.
---
### Operatori su Grafi:
![[Pasted image 20241205142306.png]]
### Implementazioni:
denotiamo con m = |$\varepsilon$|, n = |$V$|
#### Implementazione con matrice di adiacenza:
![[Pasted image 20241205143859.png]]
- Verificare l’appartenenza di un arco al grafo ha costo O(1); 
- adj(u) ha costo Θ(n). 
- Se gli archi sono pesati, allora si memorizza il peso (oppure ∞) nell'elemento corrispondente
---
#### Implementazione con matrice di incidenza
![[Pasted image 20241205143948.png]]
E' utile in problemi di programmazione lineare, ma costosa in memoria e in tempo.

---
#### Implementazione con liste di adiacenza:
![[Pasted image 20241205144242.png]]
- Occupazione della memoria ottimale: Θ(n + m);
- Scansione della lista di adiacenza ottimale;
- Scansione degli archi ottimale
- Verifica dell'appartenenza di un arco $O(|adj(u)|)$ (non ottimale).
---
### Visita di un grafo:
Definiamo una generica “visita” di un grafo, in cui vengono esaminati tutti i nodi e tutti gli archi:
#### Algoritmi:
##### Visita semplice:
![[Pasted image 20241205144629.png]]

---
##### Visita BFS di un grafo:
Visita per livelli:
![[Pasted image 20241205144742.png]]

---
##### Il numero di Erdos:
![[Pasted image 20241205144906.png]]La procedura restituisce anche un vettore contenente una lista dei “padri” che consente di ricostruire il percorso da Erdos al nodo desiderato

---
##### Componenti connesse:
Una visita in profondità in preordine può essere impiegata per il calcolo delle componenti connesse di un grafo:
###### Algoritmi:
![[Pasted image 20241205145008.png]]

---
##### Albero ricoprente:
![[Pasted image 20241205145159.png]]
Si può costruire una _procedura DFS_ generica che serve come schema per diversi scopi; si usano i vettori `dt` e `ft` per registrare quando vengono visitati i vari nodi:
![[Pasted image 20241205145500.png]]

---
##### Verifica ciclicità di un grafo:
![[Pasted image 20241205145536.png]]
Un grafo orientato aciclico ammette un ordinamento topologico, ossia una sequenza $v_1, v_2, . . . , v_n$ dove $i < j$ implica che vi precede $v_k$.
###### Esempio:
![[Pasted image 20241205145650.png]]
##### Ordinamento topologico:
![[Pasted image 20241205145826.png]]

---
#### Alberi di copertura minimo:
Dato un grafo $G=(V, \varepsilon)$ con pesi w(u,v) non negativi, trovare un albero $G$' = ($V,T$), quindi con n-1 archi, tale che la funzione:$$\sum_{(u,v)\in T}w(u,v)$$
sia minimizzata:
##### Algoritmi:
![[Pasted image 20241205150352.png]]
#### Cammini minimi:
Dato G = (V, E), un costo associato ad ogni arco w (u,v). ed un cammino $c = v_1, . . . , v_k$ definiamo il costo del cammino:$$w(c)=\sum\limits_{i=2}^{k}w(v_{i-1},v_{i})$$
##### Problema dei cammini minimi:
Dato un grafo orientato G ed un nodo r, trovare per ogni nodo u un cammino di costo minimo.
Una soluzione ammissibile consiste nel trovare un albero di ricopertura T.
![[Pasted image 20241205150711.png]]
##### Algoritmo:
![[Pasted image 20241205150733.png]]
![[Pasted image 20241205150759.png]]![[Pasted image 20241205150813.png]]
##### Algoritmo di Dijkstra:
Nell’algoritmo di Dijkstra per S si usa una coda con priorità:
![[Pasted image 20241205150853.png]]![[Pasted image 20241205150901.png]]
##### Algoritmo di Bellman-For-Moore:
Nell’algoritmo di Bellman-Ford-Moore per S si usa una coda (semplice):
![[Pasted image 20241205151002.png]]
##### Calcolo dei cammini minimi All-Pairs:
Dato un grafo $G = (V,\varepsilon)$, dobbiamo trovare la lunghezza del cammino minimo tra ogni possibile coppia di nodi. Possimao utilizzare un algoritmo che si sviluppa in modo simile tra un classico prodotto tra matrici ma è generalizzato su (R, min, +) invece che (R, +, * )
![[Pasted image 20241205151255.png]]
# Capitolo 55: (problemi di flusso e di accoppiamento)
## Problema del flusso in una rete:
### Introduzione:
#### Definizione:
Una rete di flusso ($V,\varepsilon,s,p,c$) è data da un grafo G = (V, E), due vertici s e p detti rispettivamente sorgente e pozzo ed una funzione di capacità a valori interi positivi c : $$V × V → Z^+ ∪~{0},~~~ tale~che~~~c(u, v) = 0~se~(u, v) \notin \varepsilon$$, allora:
Un flusso in G è una funzione a valori interi F : V × V → Z che soddisfa: 
- Simmetria opposta: $f (u, v ) = −f (v , u)$ per ogni u, v ∈ V; 
- Vincolo di capacità: $f (u, v ) ≤ c(u, v )$ per ogni u, v ∈ V; 
- Conservazione del flusso: $\sum\limits_{v} f (u, v ) = 0$ per ogni nodo $u ∈ V − {s, p}.$ Il valore del flusso è la somma dei flussi in uscita dalla sorgente (o in entrata nel pozzo):$$|f|=\sum\limits_{v}f(s,v)$$
#### Flusso massimo:
Data una rete di flusso ($V, \varepsilon,s,p,c$) trovare il flusso ottimale f* che massimizza $|f$* $|$ su tutti i flussi possibili.
#### Taglio:
Un taglio è una partizione dei nodi (S, P) tale che: 
1. s ∈ S; 
2. p ∈ P; 
3. S ∪ P = V; 
4. S ∩ P = ∅; 
La capacità del taglio è $\sum\limits_{u\in S,v\in P} c(u, v)$
#### Problema del flusso in una rete:
![[Pasted image 20241205153705.png]]
##### Capacità residua e cammino aumentante:
- Capacità residua: $r (u, v ) = c(u, v ) − f (u, v )$, cioè capacità dell'arco meno il flusso; 
- Rete di flusso residua R: La rete contenente il sottoinsieme degli archi tale che $r(u, v) > 0$
- Cammino aumentante: un cammino da s a p in R; la sua capacità residua è il più piccolo degli r (u, v ) sugli archi (u, v ) che appartengono al cammino.
##### Teorema:
Il flusso massimo è uguale alla capacità del taglio minimo. Inoltre le seguenti condizioni sono equivalenti:
1. f è un flusso massimo; 
2. Non esiste alcun cammino aumentante; 
3. Esiste un taglio (S, P) tale che $|f | = c(S, P)$.
![[Pasted image 20241205161255.png]]
##### Algoritmo:
![[Pasted image 20241205154132.png]]
##### Altri algoritmi:
- Algoritmo Ford-Fulkerson: si usa un cammino aumentante qualsiasi; costo nel caso peggiore O((n + m) · |f*|); 
- Algoritmo di Edmonds-Karp: Ricerca i cammini aumentanti con una visita in ampiezza BFS; complessità: $O(nm^2)$; 
- Algoritmo dei tre indiani: Aumentare lungo i cammini aumentanti più corti.
##### Esempio:
abbinamento in un grafo bipartito:
![[Pasted image 20241205154401.png]]

---
- **Risoluzione**
![[Pasted image 20241205154440.png]]

---
L’abbinamento può essere: 
- Pesato (esiste una funzione w (u, v )); 
- Su grafo non bipartito
#### Problema del circuito Meltoniano ed Euleriano:
Dato il seguente grafo, c'è la possibilità di attraversare ogni nodo una volta sola e tornare al punto di partenza: (anche detto commesso viaggiatore)
![[Pasted image 20241205162649.png]]
La risposta è no
# Capitolo 60: (progettazione di algoritmi)
## Considerazioni generali:
### Introduzione:
Poiché la progettazione degli algoritmi non ammette una formula universale.
#### Analisi:
Esistono diverse fasi nell'analisi di un problema:
1) Classificazione del problema: decisionale, ricerca, ottimizzazione;
2) Caratterizzazione della soluzione; 
3) Tecnica specifica di progettazione divide et impera, programmazione dinamica, greedy, ricerca locale, backtrack, probabilistica; 
4) Strutture di dati.
#### Dividi et Impera:
Suddividere un problema in sottoproblemi, risolverli e combinare le soluzioni in una soluzione del problema principale:
Alcuni esempi di questa tecnica sono
- QuickSort
- Mergesort
### Programmazione dinamica:
#### Cos'è?
La programmazione dinamica è un modo per cui essere sicuri che il calcolo di un sotto-problema venga svolto una volta sola.
#### Rappresentazione Grafica:
![[Pasted image 20241205173054.png]]

---
#### Condizioni di applicabilità:
- è possibile combinare soluzioni di sottoproblemi per risolvere un problema più grande; 
- Le decisioni ottime di un sottoproblema sono ottime anche quando è parte di un problema più grande;
La programmazione dinamica è conveniente quando divide-et-impera risolve più volte gli stessi sottoproblema.

---
#### Condizioni per complessità polinomiale
1. Il numero dei sottoproblemi deve essere (non più che) polinomiale; 
2. Si può usare una tabella per memorizzare tutte le soluzioni dei sottoproblemi; 
3. Il tempo di ricombinazione dei sottoproblemi è polinomiale.

---
#### Esempi:
##### Coefficiente binomiale:
![[Pasted image 20241205173129.png]]

---
##### Successione Fibonacci:
![[Pasted image 20241205173441.png]]

---
##### Prodotto tra matrici:
###### Introduzione al problema:
![[Pasted image 20241205173731.png]]
![[Pasted image 20241205173742.png]]
###### Ricerca soluzione ottima
![[Pasted image 20241205173753.png]]
###### Algoritmo:
![[Pasted image 20241205173803.png]]

---
##### Problema dello zaino:
###### Introduzione al problema
Immaginare di essere in una casa che sta andando a fuoco, avere uno zaino e dover salvare gli oggetti dal maggior valore possibile.
![[Pasted image 20241205174143.png]]
Definendo S(i, c) la soluzione ottima del problema P(i, c) con i primi i oggetti e capacità c, allora:
![[Pasted image 20241205174210.png]]
###### Algoritmo:
![[Pasted image 20241205174228.png]]
##### La più lunga sottosequenza comune:
