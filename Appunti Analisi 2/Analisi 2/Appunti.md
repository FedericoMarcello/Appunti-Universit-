# Capitolo 1: Introduzione:
## Funzioni a più variabili:
Possiamo definire una funzione ad una variabile come $\sigma:R\rightarrow R,~y=f(x),~\sigma:A\subset R\rightarrow R$, mentre una funzione a più variabili come $\delta:A\subseteq R^{n}\rightarrow R^n,~con~n\ge1$. 
In questo caso y sarà definito $y:\omega(x_{1},x_{2},…,x_{n})$, con le n-uple x numeri reali. Opereremo inoltre in un sistema in $R^{3}$ del tipo: $$~\delta:A\subseteq R^{n}\rightarrow R$$
Che rappresentato graficamente è il il piano in tre dimensioni:
![[Pasted image 20241023142401.png]]
<div class="page-break" style="page-break-before: always;"></div>


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
Essendo questa una successione che tende all'infinito, prendiamo come casi di studio quando $x=4$ e quando $x\rightarrow +\infty$ 
- Il punto $(\frac{1}{4},\frac{1}{4})$ è un punto esterno e di frontiera poichè non esiste una sfera che coinvolga i punti di A, però posso crearne una che prenda sia elementi di A, se stesso, sia elementi di $A^C$ 
- Il punto $(0,0)$ è ottenuto se tendo n a infinito, $\frac{1}{+\infty} =0$, ed è un punto di accumulazione e di frontiera. Questo poiché per ogni sfera attorno a (0,0) potrò trovare punti del dominio di A.

<div class="page-break" style="page-break-before: always;"></div>
# Capitolo 2 Integrali multipli:
## Integrali doppi:
### Definizione:
Dalla seguente formula
$$\int_ D\int f(x,y)dxdy$$
possiamo individuare il grafico che ha come base il dominio sugli assi $x$ ed $y$ e la sua proiezione  sull'asse z fino ai punti individuati dalla funzione, in questo modo:
![[Pasted image 20241210152937.png]]

---
Ora ipotizziamo di prendere un rettangolo R intorno a D:
![[Pasted image 20241210153532.png]]
E si scrive la funzione $\overline{f}(x,y)=\cases{f(x,y)~~~se~(x,y)\in D \\0~~~~~~se~(x,y)\in R\D~~(complementare)}$  
Che va a definire i punti all'interno di D come dipendenti dalla funzione $f(x,y)$ e gli altri, cioè quelli al di fuori di D ma compresi in R, come 0.
Questa funzione può essere spiegata attraverso lo studio della sezione del grafico visto in precedenza:
![[Pasted image 20241210154204.png]]

---
Definiamo il rettangolo come $[a,b]$x$[c,d]$, il singolo quadratino come $R_{ij}$. L'area del rettangolino vale $|R_{ij}|=(x_{i}-x_{i-1})*(y_{n}-y_{n-1})$. 
L'altezza del parallelepipedo è data sia dall'estremo inferiore: $$m_{ij}=\inf f (x,y)$$
Sia dall'estremo superiore:
$$M_{ij}=sup f(x,y)$$
Questa divisione è data dal fatto che se prendiamo gli estremi inferiori andiamo a considerare tutti quei parallelepipedi che sono leggermente sotto la funzione e al contrario per l'estremo superiore 

---
A questo punto per trovare il volume "inferiore e superiore" dobbiamo trovare le rispettive somme, ricordandoci che con P intendiamo la "partizione" del rettangolo R, ovvero in quanti blocchi è diviso e l'ordine di questi.
- Per la somma inferiore:
$$s(f,P)= \sum\limits_{i=1}^{m}\sum\limits_{j=1}^{n}m_{ij}|R_{ij}|$$
- Per la somma superiore :
$$S(f,P)= \sum\limits_{i=1}^{m}\sum\limits_{j=1}^{n}M_{ij}|R_{ij}|$$
### Teoremi:
#### Teorema Integrabilità
Solo adesso possiamo dire che una funzione è integrabile due volte se:
$sup\{s(f,P),~per~ogni~partizione~di~R\}=inf\{S(f,P),~per~ogni~partizione~di~R\}$
Quindi se l'estremo superiore delle somme inferiori è equivalente all'estremo inferiore delle somme superiori.

---
#### Teorema Condizioni di integrabilità
##### Enunciato:
Data una funzione $f:D\subset R^{2}\longrightarrow R$,
Se D è limitato e misurabile ed $f$ è limitata e continua su D allora $f$ è integrabile su D.

#### Criterio geometrico di Misurabilità:
##### Enunciato:
- D è misurabile se $$X_{D}(x,y)=\cases{1~~~~se~(x,y)\in D \\ 0~~se~(x,y)\notin D}$$
e se $X_{D}$ è integrabile, ovvero se $|\partial D|= 0$, cioè la misura del bordo è = 0.
- La misura (| |) di un insieme è l'area del dominio. 
- Il bordo è definito come:$$\partial D=\{\forall \varepsilon>0 \cases{B(x,y)\cap D \neq \emptyset \\ B(x,y)\cap D^C\neq \emptyset}$$
dove $B(x,y)$ è il disco aperto di centro ($x,y$) e raggio $\varepsilon > 0$
###  Domini semplici e formule di riduzione:
#### Quali sono?
Un sottoinsieme $D\cap R^{2}$ si dice **dominio semplice rispetto all'asse y** se $$\exists~\Phi_{1}~\Phi_{2} \in X([a,b]):~\phi_{1}\le ~\phi_{2}$$ e $$D=\{x,y\in R^2:x\in[a,b]~e~y\in [\Phi_1(x),\Phi_{2}(x)]\}$$  ![[Pasted image 20241210181729.png]]

---
mentre si dice dominio semplice rispetto all'asse x se $\exists \phi_{1}, \phi_{2} \in C([c,d]):\phi_{1}\le\phi_{2}$ e $D=\{x,y\in R^2:x\in[c,d]~e~y\in [\Phi_1(y),\Phi_{2}(y)]\}$
![[Pasted image 20241210182126.png]]

---
Dato che la frontiera è costituita da grafici di funzioni continue si dimostra che i domini semplici sono misurabili.
Inoltre un dominio semplice è chiuso e limitato.

---
#### Teorema formule di riduzione:
Il seguente teorema illusa come il calcolo di un integrale doppio si può ridurre al calcolo di due integrali ordinari.
##### Enunciato:
Sia D un dominio semplice di $R^{2}$ e sia $f$ continua in D.
##### Formule:
- Se D è semplice rispetto all'asse x, allora:$$\int_ D\int f(x,y)dxdy = \int_{x=a}^{b}(\int_{y=\phi_{1}(x)}^{\phi_{2}(x)}f(x,y)dx)dy$$
- Se D è semplice rispetto all'asse delle y invece:
$$\int_ D\int f(x,y)dxdy = \int_{y=c}^{d}(\int_{x=\phi_{1}(x)}^{\phi_{2}(y)}f(x,y)dx)dy$$
##### Rappresentazioni Grafiche:
![[Pasted image 20241210184131.png]]
#### Esempi:
##### Esempio 1:
Data la seguente funzione:
$$\int_{D}\int xy~dxdy$$
Dove D è il triangolo chiuso dai vertici:$$(0,0),(1,0),(1,1)$$
In questo caso il dominio D è semplice sia rispetto a x sia rispetto a y:
![[Pasted image 20241212125722.png]]
svolgiamo il calcolo rispetto a y:
1) $$\int_{x=0}^{1}(\int_{y=0}^{y=x}xy dy)dx=\int_{0}^{1}x(\int_{y=0}^{y=x}y dy)dx=\int_{0}^{1}x*[\frac{y^{2}}{2}]_{0}^{x}dx={\int_{0}^{1}\frac{x^{3}}{2}dx}=\frac{1}{8}[x^4]_{0}^{1}=\frac{1}{8}$$ il calcolo rispetto a x si svolge in modo specchiato.
2) ![[Pasted image 20241212130855.png]]
---
##### Esempio 2:
ipotizziamo di avere:
$$\int_{D}\int e^{y^{3}}dxdy$$
con il seguente dominio:
![[Pasted image 20241212131041.png]]
Visto che l'integrale interno $\int e^{y^3}$ non si riesce a risolvere, proviamo a ridurre rispetto a x:
$$\int_{y=0}^{1}(\int_{x=0}^{y^{2}}e^{y^{3}}dx)dy=\int_{y=0}^{1} e^{y^{3}}(\int_{x=0}^{y^{2}}dx)dy=\int_{0}^{1}e^{y^{3}}[x]_{0}^{y^{2}}dy=\int_{0}^{1} y^{2}e^{y^{3}}dy=[\frac{e^{y^{3}}}{3}]_{0}^{1}=\frac{{e-1}}{3}$$
---
<div class="page-break" style="page-break-before: always;"></div>

##### Esempio 3
![[Pasted image 20241212132733.png]]
![[Pasted image 20241212132935.png]]

---
##### Esempio 4:
![[Pasted image 20241212133000.png]]

---
### Valore medio:
#### Cos'è?
Il valore medio di una funzione $f:D\rightarrow R$ su D di misura non nulla si definisce come: $$\overline{f_{D}}=\frac{1}{|D|}~~~~\int_{D}\int f(x,y)dxdy$$
#### Esempio:
Calcolare il valore medio della funzione:$$f(x,y)=(1-2x)y$$
sull'insieme $D=D_1\cup D_2$:
![[Pasted image 20241212133814.png]]
$$|D|=|D_{1}|+|D_{2}|=\int_{0}^{1}\sqrt xdx+\int_{1}^{2}\frac{1}{x^{2}}dx=[\frac{2}{3}x^{\frac{3}{2}}+[-\frac{1}{x}]_{1}^{2}=\frac{7}{6}$$
e ora ci studiamo $\int_{D}\int f(x,y)dxdy$:
1) prima studiamo $D_{1}$   $$\int_{D_{1}}\int(1-2x)ydxdy=\int_{0}^{1}(1-2x)(\int_{0}^{\sqrt{x}}ydy)dx=\int_{0}^{1}(1-2x)\frac{x}{2}dx=[\frac{{x^{2}}}{4}-\frac {x^{3}}{3}]=-\frac{1}{12}$$
2) poi studiamo $D_{2}$
   $$\int_{D_{2}}\int(1-2x)ydxdy=\int_{1}^{2}(1-2x)(\int_{0}^{\frac{1}{x^{2}}}ydy)dx=\int_{1}^{2}(1-2x)\frac{1}{2x^{4}}dx=[-\frac{{1}}{6x^{3}}+\frac{1}{2x^2}]=-\frac{11}{48}$$
Quindi:$$\overline {f_{D}}=\frac{1}{\frac{7}{6}}*(\frac{-1}{12}-\frac{11}{48})=\frac{-15}{56}$$
#### Cambiamento di variabili:
##### Introduzione:
Alcune volte in un integrale doppio le variabili originali (x,y) possono rendere il calcolo complicato.
In questo caso può essere utile un cambio di variabili in un nuovo sistema di coordinate $(u,v)$. 
##### Spiegazione:
Indichiamo con $$\Phi : \Omega \rightarrow R^{2}$$
$$\Phi (u,v)=(x(u,v),~y(u,v))~~per~~(u,v)\in \Omega$$

l'applicazione che realizza il cambiamento dove $\Omega$ è un insieme aperto di $R^{2}$:
![[Pasted image 20241212141500.png]]
Supponiamo che $\Phi$ sia biunivoca tra $\Omega$ e $\Phi(\Omega)$ e che le sue componenti $x(y,v)$ e $y(u,v)$ siano continue con le derivate parziali continue in $\Omega$ .
Inoltre indichiamo con $$J_{\Phi}(u,v)=\begin{bmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v}\end{bmatrix}$$
la **Matrice Jacobiana** di $\Phi$, e con 
$$\frac{\partial (x,y)}{\partial(u,v)}$$
Il determinante: $$det(J_\Phi(u,v))$$
Ora supponiamo che $$\frac{\partial (x,y)}{\partial(u,v)}\neq0 \forall(u,v)\in \Omega$$ allora vale il seguente risultato.
#### Teorema 5:
##### Enunciato:
Se D è misurabile e f è l'integrale su D, allora: $$\int_{D}\int f(x,y)=\int_{\Phi^{-1}(D)}\int f(x(u,v), y(u,v))|\frac{\partial (x,y)}{\partial (u,v)}|$$
rappresenta il fattore di trasformazione dall'elemento infinitesimo d'area $dudv$ a $dxdy$: $$dxdy=|\frac{\partial(x,y)}{\partial(u,v)}|dudv$$

---
Ad esempio, se $\Phi$ è l'applicazione lineare:$$\Phi(u,v)=(au+bv,~cu+dv)$$ con $ad-bc\neq0$, ricordandoci che $\Phi$ deve essere iniettiva, allora il quadrato $Q=[0,1]$x$[0,1]$ viene trasformato in un parallelogramma $D$:
![[Pasted image 20241212144636.png]]
Anche se $\Phi$ realizza una corrispondenza biunivoca tra i punti di Q e quelli di D, in generale $\Phi$ "non conserva le aree":
|Q|=1 e $|\Phi (Q)|=|D|=|(a,c)$x$(b, d)|=|det\begin {bmatrix} a & b\\ c & d\end{bmatrix}|=|ad-bc|$.
È facile verificare dalla definizione che in questo caso $|\frac{\partial(x,y)}{\partial(u,v)}|$ è costante ed uguale al rapporto delle due aree $\frac{|D|}{|Q|}$.
##### Coordinate polari
Un altro esempio importante è il caso delle coordinate polari.
![[Pasted image 20241212223742.png]]
Quindi: $$|\frac{\partial(x,y)}{\partial(\rho,\theta)}|=|det \begin{bmatrix}\frac{\partial x}{\partial \rho} & \frac{\partial x}{\partial \theta} \\ \frac{\partial y}{\partial \rho} & \frac{\partial y}{\partial \theta} \end{bmatrix}|=|det \begin{bmatrix}cos\theta&-\rho sen\theta \\sin\theta & \rho cos\theta\end{bmatrix}|=\rho$$
##### Esempio:
Calcolare: $$\int_{D}\int\frac{dxdy}{xy}$$
dove:
![[Pasted image 20241213112805.png]]
ossia:
$$D=\{(x,y)\in R^{2}:~0<x\le y \le 2x,~1\le x+y \le 3\}$$
A questo punto poniamo $n =\frac{y}{x}$ e $v=x+y$ $(*)$
In questo modo il dominio nelle nuove coordinate è il rettangolo $[1,2]$x$[1,3]$.
Per calcolare: $|\frac{\partial(x,y)}{\partial(u,v)}|$ abbiamo de possibilità:
###### 1˚ Caso
Trovare $x$ e $y$ in funzione di $u$ e $v$ dal cambio di variabile visto in precedenza $(*)$
   $$x = \frac{v}{u+1},~~y=\frac{u~v}{u+1}$$
e ci troviamo anche 
   $$|\frac{\partial(x,y)}{\partial(u,v)}|=|det \begin{bmatrix}-\frac{v}{(u+1)^{2}} & \frac{1}{u+1} \\ \frac{v}{(u+1)^{2}} & \frac{u}{u+1} \end{bmatrix}|=\frac{v}{(u+1)^{2}}$$
quindi andando a sostituire nella equazione principale sia :
$$\int_{D}\int\frac{dxdy}{xy}=\int_{u=1}^2\int_{v=1}^{3}\frac{(u+1)^2}{(uv^{2})}*\frac{v}{(u+1)^{2}}=$$$$\int_{u=1}^2\int_{v=1}^{3}\frac{1}{u*v}dudv=\int_{u=1}^{2}\frac{1}{u}(\int_{v=1}^{3}\frac{1}{v}dv)du=[log~u]_{1}^{2}~[log~v]_{1}^{3}=log(2)*log(3)$$
---
###### 2° Caso:
![[Pasted image 20241213131351.png]]

---
##### altri esempi:
...
### Integrali tripli