## Funzioni a più variabili:
Possiamo definire una funzione ad una variabile come $\sigma:R\rightarrow R,~y=f(x),~\sigma:A\subset R\rightarrow R$, mentre una funzione a più variabili come $\delta:A\subseteq R^{n}\rightarrow R^n,~con~n\ge1$. 
In questo caso y sarà definito $y:\omega(x_{1},x_{2},…,x_{n})$, con le n-uple x numeri reali. Opereremo inoltre in un sistema in $R^{3}$ del tipo: $$~\delta:A\subseteq R^{n}\rightarrow R$$
Che rappresentato graficamente è il il piano in tre dimensioni:
![[Pasted image 20241023142401.png]]
## Topologia di R:
### Distanze
Per facilità di scrittura, possiamo utilizzare la seguente notazione:$$\underline{x^0}=(x_{1}^{0},…,x_{n}^{0})$$ Possiamo calcolare la distanza fra n numeri, osserviamo due casi: 
- $n=1,~x_{0}:=(x_{0}^{0},x_{0}^{1})$ la cui distanza sarà $\sqrt{(x_{0}^{1}-x_{0}^{0})^2}=|x_{1}^{0}-x_{0}^{0}|$ 
- $n=2,~avrò~x_{0}:=(x_{0}^{0},x_{0}^{1})~e~x_{1}=(x_{1}^0,x_{1}^{1})$ la cui distanza sarà $\sqrt{(x_{0}^{1}-x_{0}^{0})^{2}+(x_{1}^{1}-x_{1}^{0})^{2}}$ 
### Equazioni e Nozioni Fondamentali:
#### Sfera Aperta:
- Sfera Aperta in $R^3$ dove con $\underline{x^{0}}$ indichiamo il centro e con r il raggio
  $B_{r}(\underline{x^{0}})=${$x\in R^{3}:C(x,\underline{x^{0}})<r$}
- E la frontiera è: 
  $\partial{B_{r}}(\underline{x^{0}})=${$x\in R^{3}:d(x,\underline{x^{0}})=r$}
#### Sfera Chiusa:
- Sfera Chiusa in $R^3$ dove con $\underline{x^{0}}$ indichiamo il centro e con r il raggio
  $B_{r}(\underline{x^{0}})=${$x\in R^{3}:C(x,\underline{x^{0}})\le r$} 
- E la frontiera è: 
  $\partial{B_{r}}(\underline{x^{0}})=${$x\in R^{3}:d(x,\underline{x^{0}})=r$}
#### Punto Interno:
$A\subset R^{n},x$ interno aD A se $\exists r>0~t.c.~B_{r}(\underline{x^{0}})\subset A$ quindi se almeno una sfera è contenuta in A.
##### Esempio:
A={$x\in R^{2}:x_{1}>0,x_{2}>0$} 
Ogni punto compreso nell’area A si dice punto interno 
![[Pasted image 20241023190536.png]]
In questo caso essendo maggiore stretto di 0, i punti delle rette y=0 e x=0 non sono punti interni.

#### Punto Isolato:
$\underline{x^{0}}$ è un punto isolato se $\exists~r:B_{r}(\underline{x^{0}})\cap A$ \ {$x_{0}$} = 0, cioè se non l’intersezione di almeno una sfera attorno a $\underline{x^{0}}$ è l’insieme vuoto
##### Esempio:
Riprendiamo l’esempio precedente e aggiungiamo oltre all’insieme di partenza, anche il punto $(-1,-1)$: 
			A = {$x\in R^{2}:x_{1}>0,x_{2}>0$} $\cup~(-1,-1)$  
Dunque il punto $(-1,-1)$ è un punto isolato, visto che esiste almeno una sfera di raggio r qualsiasi tale che essa non si intersechi col dominio.
### Insiemistica:
#### Insieme Aperto:
Un insieme si dice aperto SE E SOLO SE tutti i suoi punti sono interni:
##### Esempio:
$$B=\{x \in R^{2}:x_{1}\ge 0, x_{2}\ge 0\}$$
La cui rappresentazione è del tipo:
![[Pasted image 20241024121555.png]]
E on si tratta di un insieme aperto poiché i punti in corrispondenza di $x_{1}=0$ e $x_{2}=0$ non sono interni
#### Insieme Chiusi:
Un insieme si dice chiuso se il suo complementare $A^{C}$ è aperto
#### Frontiera di un insieme:
Dato un insieme A, OA è l’insieme dei punti non necessariamente $\in A$ t.c. $\forall r : B_{r}(\underline{x^{0}})\cap A$ $\neq 0$ e$B_{r}(\underline{x^{0}})\cap A^C\neq0$ 
##### Esempio:
Riprendendo l’esempio studiato in precedenza 			$$A = \{ x\in R^{2}:x_{1}>0,x_{2}>0\} \cup~(-1,-1)$$![[Pasted image 20241024132440.png]]
In questo caso il punto {-1,-1} è di frontiera, poiché una qualsiasi sfera costruita attorno a esso, comprende un punto dell’insieme A, cioè se stesso, e i punti del complementare $A^{C}$
#### Punto di Accumulazione:
$\underline{x^{0}}$ è detto punto di accumulazione se $\forall~r:B(\underline{x^{0}})\cap A$\ $\underline{x^{0}}\neq \emptyset$  (Non è detto che $\underline{x^{0}} \in A$) 
##### Esempio:
$A:=\{x\in R^{2}:x_{1}=\frac{1}{n_{1}},~x_{2}=\frac{1}{n_{2}},…,x_{n}=\frac{1}{n_{n}}, n\ge 1\}$ 
![[Pasted image 20241024145014.png]]
Essendo questa una successione che tende all’infinito, prendiamo come casi di studio quando $x=4$ e quando $x\rightarrow +\infty$ 
- Il punto $(\frac{1}{4},\frac{1}{4})$ è un punto esterno e di frontiera poichè non esiste una sfera che coinvolga i punti di A, però posso crearne una che prenda sia elementi di A, se stesso, sia elementi di $A^C$ 
- Il punto $(0,0)$ è ottenuto se tendo n a infinito, $\frac{1}{+\infty} =0$, ed è un punto di accumulazione e di frontiera. Questo poiché per ogni sfera attorno a (0,0) potrò trovare punti del dominio di A.