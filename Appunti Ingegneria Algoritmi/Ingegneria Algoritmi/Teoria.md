### Complessità Computazionale:

#### Esempio di istruzioni su quantità scalari:
![[Pasted image 20241003161425.png]]
#### Studio dei cicli:
Ciclo:
$$ \sum_{i=0}^n C(i) $$
-  i è una iterazione
- I è l'insieme di tutte le iterazioni
- C(i) è il costo della i-esima iterazione
Spesso (ma non sempre) il costo delle iterazioni è costante.
A cicli innestati corrispondono somme multiple:
![[Pasted image 20241003161911.png]]
ciò può essere rappresentato come:
$$ \sum_ {i=1}^m \sum_{j=1}^n C(statement_{i,j}) $$
##### Esempi:
###### Somma scalata di vettori di dimensione n: $c=a+ alpha * b$
![[Pasted image 20241003162829.png]]
Dove il costo è:
$$\sum_{i=1} ^n 2 = 2\sum_{i=1} ^n 1= 2n $$
###### Prodotto matrice vettore $y=y+Ax$ (matrice m x n):
![[Pasted image 20241003163322.png]]
Dove il costo è:
$$ \sum_{i=1}^m \sum_{j=1}^n2 =2mn $$
###### Matrice per matrice $C= C + A * B$ (con matrici m x k x n):
![[Pasted image 20241003163714.png]]
Dove il costo è:
$$ \sum_{i=1}^m \sum_{j=1}^n \sum_{l=1}^k 2 = 2mnk$$
###### Risoluzione di un sistema triangolare:
Se la matrice dei coefficienti di un sistema è triangolare inferiore L, il sistema Lx si risolve facilmente per sostituzione in avanti:
![[Pasted image 20241003164039.png]]
Se la diagonale è unitaria, il passo di divisione può essere saltato. Andiamo ora a dimostrare che il numero di operazioni è $O(n^2)$ :
Quale è il costo?
- Ad ogni iterazione del ciclo esterno i= 1, ..., n abbiamo un ciclo interno, una assegnazione e una divisione,
- Il ciclo interno j=1,...,i-1 è un prodotto scalare e contiene due operazioni per iterazione.
- Ogni iterazione del jcì



##### Algoritmo di inserzione:
![[Pasted image 20241003170210.png]]
Abbiamo una struttura simile a quella del sistema triangolare, ma per il ciclo interno:
- nel caso migliore il ciclo while esegue un controllo ed esce immediatamente
- Nel caso peggiore viene eseguito i-1 volte:
- Abbiamo quindi la complessità $\Omega$(n) e $O(n^2)$ 


##### Algoritmo di ricerca binaria:
![[Pasted image 20241003170916.png]]
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
![[Pasted image 20241003172400.png]]
##### Dimostrazione:
Si supponga che solo 1 dei coefficienti $a_i$ non sia nullo. Allora $a=a_j$, supponendo $n=m+p*j$ con $1 \le m \le k$
Sostituendo otterrò:![[Pasted image 20241003172625.png]]
A questo punto abbiamo due casi:
1) 
![[Pasted image 20241003172714.png]]

2) 
![[Pasted image 20241003172749.png]]

Nel caso generale di più di un coefficiente non nullo, necessariamente $a \ge 2$  
![[Pasted image 20241003173013.png]]
che si riconduce al caso precedente.








#### Trasformata di Fourier Discreta:
DFT opera su sequenze (campionamenti di una funzione).
$$f_j,j=0,...,N-1 $$
e si definisce come $$\sum_{j=0}^{N-1} e^{\frac{2\pi ijk},{}} $$
E' evidente che a



### Capitolo 5:
#### Puntatori:
##### Cosa sono?
Un puntatore in C è una variabile che contiene un indirizzo:
![[Pasted image 20241024161337.png]] 
L’operatore & consente di accedere all’indirizzo di un’altra variabile, quindi di assegnarlo ad un puntatore. I puntatori hanno normalmente un tipo associato, ma ne esistono anche di generici:![[Pasted image 20241024161633.png]]
##### Come si usano?
- per dichiarare una varibile:
		type * ptr,
- Accedere al valore “puntato”(ossia, all’indirizzo corrispondente)
		val= * ptr
- Accedere ad un indirizzo
		Type * ptr
- Aritmetica dei puntatori:
		vs = * (ptr+i)
		ptr++
##### Incrementare un puntatore:
Cosa vuol dire incrementare un puntatore?
		ptr++
Aumentare il valore dell’indirizzo di un numero di byte pari alla dimensione del tipo di base:

	int * prt=1000; /se “sizeof(int)“ == 4 allora: *\(ptr+2) == 1000>
	
    char * cp=2000; /se ”sizeof(int)” == 1, allora *\(cp+3) == 2003>
Operazioni valide con puntatori:
- somma e sottrazioni con interi
- Sottrazione tra puntatori
- Confronto per uguaglianza di puntator
N.B incrementare un puntatore void * è un operazione illegale
#### Memoria dinamica:
Come gesitre necessità di memoria di dimensioni non prevedibili al momento della scrittura del programma?
- ottenere memoria con malloc:
		void * malloc(size_t size)
- Rilasciare la memoria con 
		Void free(void* ptr)
##### Esempio:
Se abbiamo bisogno di un array di K numeri interi, possiamo eseguire:![[Pasted image 20241024172634.png]]
#### Errori con puntatori:
Quali errori vanno evitati?
- controllare sempre che malloc sia andata a buon fine:
![[Pasted image 20241024172908.png]]
- tentare di rilasciare un puntatore non allocato:
![[Pasted image 20241024173001.png]]
- creare una memory leak:
![[Pasted image 20241024173156.png]]
- fare attenzione all’uso delle stringe
	- quando si alloca una stringa, ricordare sempre il carattere di terminazione: ‘\0’
	- Usare le funzioni di copia strcpy, strncpy
	- Concatenazione e “tokenizzazione” di stringhe sono una fonte di errori