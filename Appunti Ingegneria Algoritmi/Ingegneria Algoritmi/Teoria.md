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