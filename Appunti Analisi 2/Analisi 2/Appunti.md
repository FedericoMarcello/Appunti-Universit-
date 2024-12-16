# Capitolo 1: Introduzione:
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
<div class="page-break" style="page-break-before: always;"></div>

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
$A\subset R^{n},x$ interno a D A se $\exists r>0~t.c.~B_{r}(\underline{x^{0}})\subset A$ quindi se almeno una sfera è contenuta in A.
##### Esempio:
A={$x\in R^{2}:x_{1}>0,x_{2}>0$} 
Ogni punto compreso nell'area A si dice punto interno 
![[Pasted image 20241023190536.png]]
In questo caso essendo maggiore stretto di 0, i punti delle rette y=0 e x=0 non sono punti interni.

#### Punto Isolato:
$\underline{x^{0}}$ è un punto isolato se $\exists~r:B_{r}(\underline{x^{0}})\cap A$ \ {$x_{0}$} = 0, cioè se non l’intersezione di almeno una sfera attorno a $\underline{x^{0}}$ è l’insieme vuoto
##### Esempio:
Riprendiamo l’esempio precedente e aggiungiamo oltre all’insieme di partenza, anche il punto $(-1,-1)$: 
			A = {$x\in R^{2}:x_{1}>0,x_{2}>0$} $\cup~(-1,-1)$  
Dunque il punto $(-1,-1)$ è un punto isolato, visto che esiste almeno una sfera di raggio r qualsiasi tale che essa non si intersechi col dominio.
<div class="page-break" style="page-break-before: always;"></div>

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
$$\large \int_ D\int f(x,y)dxdy$$
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
L'altezza del parallelepipedo è data sia dall'estremo inferiore: $$\large m_{ij}=\inf f (x,y)$$
Sia dall'estremo superiore:
$$\large M_{ij}=sup f(x,y)$$
Questa divisione è data dal fatto che se prendiamo gli estremi inferiori andiamo a considerare tutti quei parallelepipedi che sono leggermente sotto la funzione e al contrario per l'estremo superiore 

---
A questo punto per trovare il volume "inferiore e superiore" dobbiamo trovare le rispettive somme, ricordandoci che con P intendiamo la "partizione" del rettangolo R, ovvero in quanti blocchi è diviso e l'ordine di questi.
- Per la somma inferiore:
$$\large s(f,P)= \sum\limits_{i=1}^{m}\sum\limits_{j=1}^{n}m_{ij}|R_{ij}|$$
- Per la somma superiore :
$$\large S(f,P)= \sum\limits_{i=1}^{m}\sum\limits_{j=1}^{n}M_{ij}|R_{ij}|$$
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
<div class="page-break" style="page-break-before: always;"></div>

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
![[Pasted image 20241213151747.png]]![[Pasted image 20241213151806.png]]

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
Indichiamo con $\Phi : \Omega \rightarrow R^{2}$ ed in particolare con:
$$\large\Phi (u,v)=(x(u,v),~y(u,v))~~per~~(u,v)\in \Omega$$

l'applicazione che realizza il cambiamento dove $\Omega$ è un insieme aperto di $R^{2}$:
![[Pasted image 20241212141500.png]]
Supponiamo che $\Phi$ sia biunivoca tra $\Omega$ e $\Phi(\Omega)$ e che le sue componenti $x(y,v)$ e $y(u,v)$ siano continue con le derivate parziali continue in $\Omega$ .
Inoltre indichiamo con $$\large J_{\Phi}(u,v)=\begin{bmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v}\end{bmatrix}$$
la **Matrice Jacobiana** di $\Phi$, e con 
$$\large\frac{\partial (x,y)}{\partial(u,v)}$$
Il determinante: $$det(J_\Phi(u,v))$$
Ora supponiamo che $$\frac{\partial (x,y)}{\partial(u,v)}\neq0 \forall(u,v)\in \Omega$$ allora vale il seguente risultato.
#### Teorema 5:
##### Enunciato:
Se D è misurabile e f è l'integrale su D, allora: $$\large\int_{D}\int f(x,y)=\int_{\Phi^{-1}(D)}\int f(x(u,v), y(u,v))|\frac{\partial (x,y)}{\partial (u,v)}|$$
rappresenta il fattore di trasformazione dall'elemento infinitesimo d'area $dudv$ a $dxdy$: $$\large dxdy=|\frac{\partial(x,y)}{\partial(u,v)}|dudv$$

---
Ad esempio, se $\Phi$ è l'applicazione lineare:$$\Phi(u,v)=(au+bv,~cu+dv)$$ con $ad-bc\neq0$, ricordandoci che $\Phi$ deve essere iniettiva, allora il quadrato $Q=[0,1]$x$[0,1]$ viene trasformato in un parallelogramma $D$:
![[Pasted image 20241212144636.png]]
Anche se $\Phi$ realizza una corrispondenza biunivoca tra i punti di Q e quelli di D, in generale $\Phi$ "non conserva le aree":
|Q|=1 e $|\Phi (Q)|=|D|=|(a,c)$x$(b, d)|=|det\begin {bmatrix} a & b\\ c & d\end{bmatrix}|=|ad-bc|$.
È facile verificare dalla definizione che in questo caso $|\frac{\partial(x,y)}{\partial(u,v)}|$ è costante ed uguale al rapporto delle due aree $\frac{|D|}{|Q|}$.
##### Coordinate polari
Un altro esempio importante è il caso delle coordinate polari.
![[Pasted image 20241212223742.png]]
Quindi: $$|\large\frac{\partial(x,y)}{\partial(\rho,\theta)}|=|det \begin{bmatrix}\frac{\partial x}{\partial \rho} & \frac{\partial x}{\partial \theta} \\ \frac{\partial y}{\partial \rho} & \frac{\partial y}{\partial \theta} \end{bmatrix}|=|det \begin{bmatrix}cos\theta&-\rho sen\theta \\sin\theta & \rho cos\theta\end{bmatrix}|=\rho$$
##### Esempio:
Calcolare: $$\large\int_{D}\int\frac{dxdy}{xy}$$
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
###### esempio

## Integrali tripli:
### Introduzione:
Le considerazioni fatte per gli integrali doppi si possono estendere agli integrali tripli. 
Utilizziamo gli elementi più importanti per il calcolo, ovvero il [[#Teorema formule di riduzione]] 

### Come si integra?
Esistono due modi per svolgere un integrale triplo.
Sia D un dominio di $R^{3}$ e sia $f: D \rightarrow R$ una funzione continua:
#### Integrazione per fili:
Se $\large D=\{(x,y,z): (x,y)\in D',~z \in [\varphi_{1}(x,y)],[\varphi_{2}(x,y)] \}$
dove $\varphi_{!},\varphi_{2}\in C(D')$, allora:
$$\large\iiint_{D}f(x,y,z)dxdydz=\iint_{D'}(\int_{\varphi_{1}(x,y)}^{\varphi_{2}(x,y)}f(x,y,z)dz)dxdy$$
![[Pasted image 20241213154604.png]]
Quindi prima si integra in $dz$ lungo i "fili": $[\varphi_{1}(x,y),\varphi_{2}(x,y)]$ e poi si calcola l'integrale doppio in $dxdy$ su D.
<div class="page-break" style="page-break-before: always;"></div>

#### Integrazione per sezioni:
Se $D=\{(x,y,z):z\in[a,b]~e~(x,y) \in D(z) \}$
dove $D(z)$ è un insieme misurabile piano, allora: $$\large\iiint_{D}f(x,y,z)dxdydz=\int_{b}^{a}(\iint_{D(z)}f(x,y,z)dxdy)dz$$
![[Pasted image 20241213180400.png]]
Quindi si calcola prima l'integrale doppio in $dxdy$ sulle sezioni $D(z)$ e infine si integra in $dz$ su $[a, b]$.
<div class="page-break" style="page-break-before: always;"></div>


#### Esempi:
##### Esempio 10
Calcolare $\iiint_{D}|x|z~dxdydz$ dove D è il paraboloide troncato delimitato dalle superfici $z=1$ e $z=x^{2}+y^{2}$.
![[Pasted image 20241213181202.png]]
###### Calcolo per fili:
Svolgiamo il calcolo per fili:
$$\large\iiint_{D}|x|z~dxdydz=\iint_{\{x^{2}+y^{2}\le 1\}}|x|(\int_{x^{2}+y^{2}}^1zdz)dxdy=$$$$\large\iint_{\{x^{2}+y^{2}\le 1\}}|x|*\frac{1}{2}(1-(x^{2}+y^{2})^{2})dxdy=$$e, passando a coordinate polari,$$\large\int_{\rho = 0}^{1}\int_{\theta=0}^{2\pi}\rho|cos\theta|\frac{1-\rho^{4}}{2}\rho ~d\rho d\theta$$dato che $\int_{0}^{2\pi}|cos\theta|d\theta=4\int_{0}^{\frac{\pi}{2}}|cos\theta d\theta=4[sin\theta]_{0}^{\frac{\pi}{2}}=4$  lo sostituisco nell'equazione precedente:$$\large\int_{0}^{1}2\rho^{2}(1-\rho^{4})d\rho=2[\frac{\rho^{3}}{3}-\frac{\rho^7}{7}]_{0}^{1}=\frac{8}{21}$$
###### Calcolo per sezioni:
Svolgiamo lo stesso calcolo per le sezioni 
$$\large\iiint_{D}|x|z~dxdydz=\int_{z=0}^{1}(\iint_{x^{2}+y^{2}\le z}|x|dxdy)dz =\int_{z=0}^{1}z(\int_{\rho=0}^{\sqrt z}\int_{\theta=0}^{2\pi})\rho |cos\theta|\rho d\rho d\theta)dz=$$ $$\large =4\int_{z=0}^{1}z[\frac{\rho^{3}}{3}]_{0}^{\sqrt z}=\frac{4}{3}[\frac{z^\frac{7}{2}}{\frac{7}{2}}]=\frac{8}{21}$$
<div class="page-break" style="page-break-before: always;"></div>


##### Altri Esempi:
![[Pasted image 20241213194138.png]]![[Pasted image 20241213194152.png]]
### Teorema Cambiamento di variabili:
Sia D un dominio misurabile di $R^3$ e sia $f:D\rightarrow R$$ una funzione continua.
Se $\Phi:D'\rightarrow D$ è un'applicazione biunivoca:$$\Phi(x,y,z)=(x(u,v,w),y(u,v,w),z(u,v,w))$$tale che le componenti $x,y,z$ e le loro derivate parziali sono continue in un aperto $\Omega \supset D'$ allora: $$\large\iiint_D f(x,y,z)dxdydz= \iiint_{\Phi^{-1}(D)}f((x(u,v,w),y(u,v,w),z(u,v,w))|\frac{\partial(x,y,z)}{\partial(u,v,w)}dudvdw|$$
dove con $\large\frac{\partial(x,y,z)}{\partial(u,v,w)}$ indichiamo il **determinante della matrice jacobiana**:
$$\LARGE\begin{bmatrix}\frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} & \frac{\partial x}{\partial w} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} & \frac{\partial y}{\partial w} \\ \frac{\partial z}{\partial u} &\frac{\partial z}{\partial v} & \frac{\partial z}{\partial w}\end{bmatrix}$$
#### Coordinate cilindriche:
![[Pasted image 20241213201348.png]]
#### Coordinate sferiche:
![[Pasted image 20241213201404.png]]
#### Altri esempi:
...
# Capitolo 3: Integrali Curvilinei:
## Curve nel piano:
### Cos'è?
Una **Curva nel piano** è una funzione $\gamma:I\rightarrow \mathbb R^2$ dove I è un intervallo di $\mathbb R$:
![[Pasted image 20241214093909.png]]

---
### Caratteristiche::
#### Curve chiuse e semplici:
- Una curva si dice _chiusa_ se $I=[a,b]$ e se $\gamma(a)=\gamma (b)$ 
- Una curva si dice _semplice_ se $\gamma$ è iniettiva.
- Il sostegno della curva $\gamma$ è l'insieme $\{(x(t),y(t)):t\in I\}$. 
Graficamente si intende:
![[Pasted image 20241214094347.png]]
Le frecce sul sostegno indicano il verso di percorrenza della curva al variare del parametro $t \in I$
### Esempi:
#### Esempio 1:
Ipotizziamo di avere: $$\large\begin{cases}x(t)= 2+t \\ y(t)= 1-2t \end{cases}~~~~con~t\in\mathbb R$$
Questo sono le equazione parametriche della retta:
![[Pasted image 20241214094715.png]]
"portando" in evidenza il parametro t, nel seguente modo:
$t=x-2 \longrightarrow y=1-2(x-2)=y=5-2x$

Quindi se si fa variare il parametro $t$ nell'intervallo $[0, \frac{1}{2}]$ il sostegno corrispondente è dato dal segmento che unisce i punti $(2,1)$ e $(\frac{5}{2},0)$.
#### Esempio 2:
![[Pasted image 20241214102126.png]]
#### Esempio 3:
![[Pasted image 20241214102144.png]]
### Altre Definizioni:
#### Vettore tangente:
Una curva si dice regolare se le componenti $x(t)$ e $y(t)$ sono derivabili con le derivate continue in $I$ e $$\large\gamma':=(x'(t),y'(t))\neq(0,0)~~~~\forall t\in I$$
è il vettore che si chiama **Vettore Tangente**.
Se $\gamma(t_{0})\neq0$ allora la retta tangente (parametrica) alla curva, nel punto $\gamma(t_{0})$, è data da:$$\begin{cases}x=x(t_{0})+x'(t_0)(t-t_0) \\ y=y(t_0)~+y'(t_0)(t-t_0)\end{cases}~~~~per~t\in\mathbb R$$
e la sua rappresentazione grafica è:
![[Pasted image 20241214104628.png]]
## Integrali curvilinei del primo tipo:
### Cosa sono?
Sia $f:\Omega \rightarrow \mathbb R$ una funzione continua in $\Omega$ (insieme aperto di $\mathbb R^{2}$).
Sia $\gamma(t):[a,b]\rightarrow \Omega$ una curva regolare e semplice:$$\large\gamma(t)=(x(t),y(t))$$ per $t\in[a,b]$.
Allora **l'integrale curvilineo** di $f$ lungo $\gamma$ è definito come:$$\large\int_{a}^{b}f(x(t),y(t))\sqrt{{x'(t)}^2+{y'(t)}^2}dt$$
Possiamo anche utilizzare i seguenti simboli per indicarlo:
$$\large\int_r fds~~~oppure~~~~\int_a^bf(\gamma(t))\|\gamma'(t)\|dt$$
### Esempio semplice:
#### Esempio 3:
Calcolare $\int_{\gamma}fds$ dove $\large f(x,y)=\frac{xyseny}{\sqrt {1+x^{2}}}$ e $\gamma$ è il ramo di parabola  $\gamma(t)= (t,\frac{t^{2}}{2})$ per $t \in [0,\sqrt{2\pi}]$.
Il vettore tangente è ($1,t$) e $\|(1,t)\|=\sqrt{1+t^{2}}$.
Dunque andando a sostituire: 	
$$\large\int_\gamma fds=\int_0^\sqrt{2\pi}\frac{t*\frac{t^2}{2}sin(\frac{t^2}{2})}{\sqrt{1+t^2}}*\sqrt{1+t^2}=_{u=\frac{t^2}{2}}\int_0^\pi u~sin(u)du=[sin(u)-u cos(u)]_0^\pi=\pi$$
### Definizioni:
Due curve $\gamma_{1}:I_{1}\rightarrow \mathbb R^{2}$ e $\gamma_{2}:I_{2}\rightarrow \mathbb R^{2}$ si dicono **equivalenti** se $\exists \varphi:I_{2}\rightarrow I_{1}$ biunivoca, derivabile con derivata continua in $I_{2}$ e tale che $\varphi(t)\neq 0$ in $I_{2}$ per cui:$$\gamma_1 (\varphi(t))=\gamma_2(t)~~\forall~t\in I_2$$
Due curve equivalenti hanno lo stesso sostegno, inoltre hanno lo stesso verso di percorrenza se $\varphi'>0$ in $I_{2}$ oppure hanno verso opposto se $\varphi'<0$.
Ad esempio:

$\gamma_{1}(t)=(cos (t),sin (t))$ per $t\in[0,2\pi]$
$\gamma_{2}(t)=(cos (2t),-sin (2t))$ per $t\in[0,\pi]$![[Pasted image 20241214195500.png]]
Sono equivalenti e sono due parametrizzazioni diverse dalla circonferenza di centro (0,0) e raggio unitario. $\gamma_{1}$ e $\gamma_{2}$ hanno verso opposto:
### Teoremi:
#### Teorema 1:
##### Enunciato:
Se $\gamma_{1}~e~\gamma_{2}$ sono due curve equivalenti allora: $$\large\int_{\gamma_1}fds=\int_{\gamma_2}fds$$
Ossia l'integrale curvilineo non dipende dalla parametrizzazione scelta per la curva ma solo dal suo sostegno:
Se $\gamma:[a,b]\rightarrow \mathbb R^{2}$ è una curva lungo la quale è distribuita della massa con densità lineare $\delta(x,y)$ allora il **centro di massa** ($\overline{x},\overline{y}$) è dato da: $$\overline{x}=\frac{\int_\gamma x~\delta~ds}{\int_\gamma \delta~ds},~~~~~~\overline{y}=\frac{\int_\gamma y~\delta~ds}{\int_\gamma \delta~ds}$$ 
##### Esempio:
![[Pasted image 20241214201045.png]]

##### Caso Particolare (coordinate polari):
Se la curva $\gamma$ è data in coordinate parametriche polari $\rho(t), \theta (t)$ per $t\in I$, allora è necessario qualche calcolo in più per scrivere il vettore tangente:
$$\large x(t)=\rho(t)cos(\theta(t)),~~~y(t)=\rho(t)sin(\theta(t))$$
Se lo deriviamo rispetto a t otteniamo:
$\large x'(t)=\rho'(t)cos(\theta(t))+\rho(t)(-sin(\theta(t)))*\theta'(t)$
$\large y'(t)=\rho'(t)sin(\theta(t))+\rho(t)cos(\theta(t))*\theta'(t)$
e cosi:$$\large\sqrt{x'(t)^2+y'(t)^2}=\sqrt{\rho'(t)^2+(\rho(t)*\theta'(t))^2}$$
###### 1°Esempio Caso Particolare:
![[Pasted image 20241214210417.png]]
![[Pasted image 20241214210432.png]]
###### 2° Esempio Caso Particolare:
![[Pasted image 20241214210519.png]]
## Integrali curvilinei del secondo tipo:
### Cosa sono?
#### Introduzione:
Sia $F:\Omega \rightarrow \mathbb R^{2}$ un **campo vettoriale** in $\Omega$ (insieme aperto di $\mathbb R^{2}$):$$\large F(x,y)=(A(x,y),B(x,y))$$
Con le componenti $A(x,y),B(x,y)$ continue.
Ad F associamo l'espressione formale $$\large \omega(x,y)=A(x,y)dx+B(x,y)dy$$
detta **forma differenziale**.
#### Definizione:
Sia$\gamma:[a,b]\rightarrow \Omega$ una curva regolare e semplice, definita come:$\gamma(t)=(x(t),y(t))$ per $t\in[a,b]$.
Allora **l'integrale curvilineo** di F lungo $\gamma$ è definita come:
$$\large\int_a^b(A(x(t),y(t))*x'(t)+B(x(t),y(t))*y'(t))dt$$
I simboli usati per indicarlo possono essere:
$$\int_\gamma\omega~~~~~~oppure~~~~~~\int_\gamma F*d\gamma$$

---
Se F rappresenta un campo di forze piano allora il suo integrale curvilineo lungo $\gamma$ rappresenta il lavoro compiuto per muoversi da $\gamma(a)$ a $\gamma(b)$ lungo $\gamma$ 
#### Esempi:
##### Esempio 7:
![[Pasted image 20241214212619.png]]![[Pasted image 20241214212629.png]]
![[Pasted image 20241214213658.png]]
##### Esempio 8:
![[Pasted image 20241214214004.png]]
![[Pasted image 20241214214043.png]]
### Differenze tra 1° e 2° tipo:
A differenza dell'integrale curvilineo del primo tipo, l'integrale del secondo tipo dipende dal verso in cui viene percorso il sostegno della curva $\gamma$.
### Teoremi:
#### Teorema 2:
Se $\gamma_1$ e $\gamma_{2}$ sono due curve equivalenti allora:
1) $\large\int_{\gamma_1}Fd\gamma_{1}=\int_{\gamma_{2}}Fd\gamma_{2}$ se $\gamma_1$ e $\gamma_{2}$ hanno lo stesso verso
2) $\large\int_{\gamma_1}Fd\gamma_{1}=-\int_{\gamma_{2}}Fd\gamma_{2}$ se $\gamma_1$ e $\gamma_{2}$ hanno verso opposto
##### Esempio:
![[Pasted image 20241214215408.png]]
![[Pasted image 20241214215420.png]]
## Forme differenziali esatte e chiuse:
### Introduzione:
#### Connessione per archi:
Un insieme $\rho \subset \mathbb R^{2}$ si dice **connesso (per archi)** se $\forall P,Q \in \rho\exists~una~curva~\gamma:[a,b]\rightarrow\rho$ tale che $\gamma(a)=P$ e $\gamma(b)=Q$.
Ad esempio:
![[Pasted image 20241214215939.png]]

---
### Forme esatte:
#### Cosa sono?
Sia $\Omega$ un insieme aperto e connesso di $\mathbb R^{2}$, una forma differenziale: $\large \Omega(x,y)=A(x,y)dx+B(x,y)dy$
(con le componenti $A,B$ continue in $\Omega$) si dice **Esatta** in $\Omega$ se esiste una funzione, detta **potenziale**, $U:\Omega\rightarrow \mathbb R^{2}$ differenziabile con le derivate continue tale:
$$\frac{\partial U}{\partial x}(x,y)=A(x,y)~e~\frac{\partial U}{\partial y}=B(x,y)~~\forall(x,y)\in \Omega$$

#### Teorema 3 (caratterizzazione delle forme esatte):
Il seguente teorema riporta una caratterizzazione delle forme differenziali esatte.
##### Enunciato
$\omega$ è esatta in $\Omega\subset\mathbb R^{2}$ (aperto e connesso se):$$\int_{\gamma_1}\omega=\int_{\gamma_2}\omega$$
graficamente è del tipo:
![[Pasted image 20241216113040.png]]
Per ogni coppia di curve $\gamma_{1}\gamma_{2}$ contenute in $\Omega$ e con gli stessi punti iniziali e finali.
##### Dimostrazione:
Se $\Omega$ è esatta allora per ogni curva $\gamma:[a,b]\rightarrow \Omega$
$$\large \int_{\gamma}=\int_{a}^{b}(\frac{\partial U}{\partial x}x'(t)+\frac{\partial U}{\partial y}y'(t))dt=\int_{a}^{b}\frac{d(U(x(t),y(t)))}{dt}dt=[U(x(t),y(t))]_{a}^{b}=U(\gamma(b)-\gamma(a))$$
##### Conclusioni:
Questo significa che $\int_{\gamma}\omega$ dipende solo dal punto iniziale e finale e non dalla particolare curva in $\Omega$ che li congiunge.
Ora supponiamo che $\int_{\gamma_{1}}\omega=\int_{\gamma_{2}}\omega~~~\forall\gamma_{1},\gamma_{2} (*)$ con gli stessi punti iniziali e finali e dimostriamo che $\omega$ è esatta.
Fissiamo un punto ($x_{0},y_{0}$) $\in \Omega$ e definiamo una funzione $U(x,y)$ nel seguente modo $$U(x,y)=\int_{\gamma}\omega$$
dove $\gamma$ è una qualunque curva in $\Omega$ che parte da ($x_{0},y_{0}$) e arriva in ($x,y$).
Tale funzione U è ben definita perché per ipotesi $\Omega$ è aperto e connesso e quindi esiste almeno una curva che congiunge ($x_{0},y_{0}$) a ($x,y$).
Inoltre dato $(*)$ il valore di $\int_{\gamma}\omega$ non dipende dalla particolare curva scelta:
![[Pasted image 20241216114814.png]]
In questo modo:
$$\large U(x,y)=\int_{\gamma}\omega~~~~~~~~~~~e~~~~~~~~~U(x+h,y)=\int_{\gamma\cup\gamma_{h}}\omega=\int_{\gamma}\omega+\int_{\gamma_{h}}\omega$$
dove $\gamma$ è una curva da ($x_{0},y_{0}$) a ($x,y$) e $\gamma_{h}=(x+t,y)~~per~~t\in[0,h]$
(h>0 è scelto sufficiente piccolo in modo che il sostegno di $\gamma_{h}$, cioè un segmento, sia contenuto in $\Omega$). Quindi: $$\frac{U(x+h,y)-U(x,y)}{h}=\frac{1}{h}\int_{\gamma_{h}}\omega=\frac{1}{h}\int_{t=0}^{h}A(x+t,y)dt\rightarrow{\text{per il teorema della media integrale}}=A(x+t_{h},y)$$per qualche $t_{h}\in [0,h]$. 
Passando cosi al limite per $h\rightarrow 0$ abbiamo che $t_{h}\rightarrow 0$. Così per la continuità di A:
$$\large\frac{\partial U}{\partial x}(x,y)=\lim_{h\to 0}\frac{U(x+h,y)-U(x,y)}{h}=\lim{h\to0}A(x+t_{h},y)=A(x,y).$$
In modo simile si può dimostrare che:$$\frac{\partial U}{\partial y}(x,y)=B(x,y)$$

---
##### Osservazioni:
1) Se U è una funzione potenziale di $\omega$ allora lo è anche $U + \text{costante}$

2) Se $\gamma$ è una curva chiusa e $\omega$ è esatta allora $$\int_{\gamma}\omega=\int_{\gamma_1\cup\gamma_{2}^-}\omega=\int_{\gamma_1}\omega-\int_{\gamma_{2}}\omega=0~~~~~~~~~~\text{dove }\gamma=\gamma_1\cup\gamma_2^-,$$![[Pasted image 20241216130354.png]]
$$\text{ con }\gamma_2^- \text{ è la curva }\gamma_2 \text{ con il senso di percorrenza invertito}  $$
##### Esempi:
###### Esempio 10:
![[Pasted image 20241216130632.png]]
###### Esempio 11:
![[Pasted image 20241216130659.png]]
##### Difficoltà:
La difficoltà di riconoscere una forma differenziale esatta sta nella costruzione della funzione potenziale. Le seguenti definizioni permettono di stabilire dei criteri di esattezza:
- Una forma differenziale  $\omega(x,y)=A(x,y)dx+B(x,y)dy$ 
  con A e B differenziabili e con le loro derivate parziali continue in $\Omega$ aperto e connesso, si dice **chiusa** se $$\large\frac{\partial A}{\partial y}(x,y)=\frac{\partial B}{\partial x}(x,y)~~~\forall(x,y)\in\Omega$$
- Un insieme aperto connesso $\omega$ si dice **semplicemente connesso** se ogni curva chiusa contenuta in $\Omega$ può essere ridotta mediante una deformazione continua a un punto senza uscire da $\Omega$.
  ![[Pasted image 20241216131502.png]]

#### Teorema 4 (Quando le forme sono esatte):
##### Enunciato:
Sia $\Omega$ un insieme aperto connesso e $\omega$ una forma differenziale differenziabile in $\Omega$ con le derivate continue.
1) Se $\omega$ è esatta in $\Omega$ allora $\omega$ è chiusa in $\Omega$ 
2) Se $\omega$ è chiusa in $\Omega$ e $\Omega$ è semplicemente connesso allora $\omega$ è esatta in $\Omega$
##### Dimostrazione:
Dimostrazione del punto 1):
Se $\omega$ è esatta allora $\exists~U:\Omega\to\mathbb R$: $$\omega=Adx+Bdy~~~e~~~\frac{\partial^2U}{\partial x\partial y}=\frac{\partial B}{\partial x}$$
##### Altri esempi:
###### Esempio 12
![[Pasted image 20241216133400.png]]
![[Pasted image 20241216133413.png]]
###### Esempio 13:
![[Pasted image 20241216134530.png]]
###### Esempio 14:
![[Pasted image 20241216134556.png]]
![[Pasted image 20241216134605.png]]
###### Esempio 15:
![[Pasted image 20241216134632.png]]
![[Pasted image 20241216134701.png]]![[Pasted image 20241216134716.png]]

---
## Teorema di Gauss Green nel piano:
### Teorema 5:
#### Enunciato:
Sia $D\subset \mathbb R^2$ un dominio semplice rispetto a x e a y. Sia $$\omega(x,y)=A(x,y)dx+B(x,y)dy$$
una forma differenziale con A,B e le loro derivate continue in un insieme aperto $\Omega\supset D$.
Allora vale la formula di **Gauss-Green**:
$$\iint_D(\frac{\partial B}{\partial x}-\frac{\partial A}{\partial y})dxdy=\int_{\partial D^{+}}(Adx+Bdy)$$
dove $\partial D^{+}$ indica la curva chiusa che ha per sostegno la frontiera di D percorsa in senso antiorario.
#### Dimostrazione:
![[Pasted image 20241216140044.png]]![[Pasted image 20241216140321.png]]
![[Pasted image 20241216140329.png]]

---
#### Osservazioni:
Il teorema di Gauss-Green vale per domini più generali. È sufficiente che il dominio sia decomponibile in domini per cui valgono le ipotesi del teorema precedente.
Ad esempio il dominio $D=D_{1}\cup D_{2}\cup D_{3}\cup D_{4}$
![[Pasted image 20241216140708.png]]
è unione dei 4 domini ($D_{i}$) che sono semplici rispetto ad entrambi gli assi. Quindi $$\iint_D(\frac{\partial B}{\partial x}-\frac{\partial A}{\partial y})dxdy=\sum_{k=1}^4\iint_{D_k}\iint_D(\frac{\partial B}{\partial x}-\frac{\partial A}{\partial y})dxdy$$ che attraverso il teorema di Gauss-Green:
$=\sum\limits_{k=1}^{4}\int_{\partial D^{+}} (Adx+Bdy)=$
sapendo che i segmenti vengono percorsi in entrambe le direzioni dunque il loro contributo è nullo. Quindi: $$\int_{\gamma_1}Adx+Bdy~~+\int_{\gamma_2}Adx+Bdy$$
Si noti che la frontiera di $\partial D$ è data da $\gamma_{1}$ orientata in senso antiorario e da $\gamma_{2}$ orientata in senso orario.
#### Esempi:
##### Esempio 16:
![[Pasted image 20241216141815.png]]
![[Pasted image 20241216141850.png]]
![[Pasted image 20241216141915.png]]
##### Esempio 17:
![[Pasted image 20241216141946.png]]
##### Esempio 18:
![[Pasted image 20241216142005.png]]
![[Pasted image 20241216142017.png]]
##### Esempio 19:
![[Pasted image 20241216142041.png]]
![[Pasted image 20241216142059.png]]
![[Pasted image 20241216142121.png]]
##### Esempio 20:
![[Pasted image 20241216142159.png]]
![[Pasted image 20241216142208.png]]
##### Esempio 21:
![[Pasted image 20241216142232.png]]
![[Pasted image 20241216142243.png]]

---
# Capitolo 4: Analisi Complessa:
## Introduzione  alle funzione olomorfe:
sia $\Omega$ un sottoinsieme di $\mathbb C$. Una funzione $f(z)$ che associa ad ogni numero complesso $z\in\Omega$ un numero complesso $f(z)$ si dice **Funzione di variabile complessa** e si indica con $$\Omega\ni z\rightarrow f(z)\in\mathbb C$$
Ogni funzione di questo tipo può essere pensata come una funzione da un sottoinsieme di $\mathbb R^{2}~in~\mathbb R^{2}$: posto $z=x+iy\in\Omega$ (con $x,y$ numeri reali) si ha che:$$f(z)=u(x,y)+iv(x,y)$$
dove:$$u(x,y)=Re(f(z)),~~~e~~~v(x,y)=Im(f(z))$$
sono rispettivamente la funzione **Parte reale** e la funzione **Parte immaginaria** associate a $f$. Ad esempio la funzione reciproco $f(z)=\frac{1}{z}$ è definita in $\mathbb C$ \ $\{0\}$
e si può scrivere come: $$\large  f(z)=\frac{1}{z}=\frac{1}{x+iy}=\frac{{x-iy}}{{x^{2}+y^{2}}}=\frac{x}{x^{2}+y^{2}}-i \frac{y}{x^{2}+y^{2}}$$
 
 ---
 Altri esempi di funzione di variabile complessa che possono essere considerate "elementari" sono:
 1) il coniugio:$$f(z)=\overline{z}=x-iy,~~~~~per~z\in \mathbb C$$
 2) I polinomi: $$f(z)=a_nZ^n+a_{n-1}Z^{n-1}+...+a_{0},~~~per z\in \mathbb C$$
 3) Le funzioni razionali:$$f(z)=\frac{P(z)}{Q(z)},~~~~~~per~z\in\mathbb C-\{z\in \mathbb C:Q(z)=0\}$$con P e Q polinomi a coefficienti in $\mathbb C$
 4) L'esponente complesso: $$f(z)=e^{z}=e^{x+iy}=e^{x}(cos y+isiny),~~~per~z\in\mathbb C$$
 5) Il seno complesso e il coseno complesso:$$f(z)=sinz=\frac{e^{iz}-e^{-iz}}{2i}=\frac{e^{ix-y}-e^{-ix-y}}{2i}=e^{-y}(cosx+isinx)\frac{1}{2i}-e^{y}(cosx-isinx)\frac{1}{2i}=$$$$sin(x)cosh(y)+icos(x)~sinh(y)$$dove: $$cos(h)y=\frac{e^y+e^{-y}}{2}~~~e~~~sin(h)y=\frac{e^y-e^{-y}}{2}$$sono rispettivamente il coseno iperbolico ed il seno iperbolico (ricordandoci che sono funzioni reali e che: $\large cos^{2}x+sin^{2}x=1~~e~~cosh^{2}x-sinh^{2}x=1$
 6) Il logaritmo complesso:
    L'idea della definizione è di estendere il logaritmo reale. Se $4=|z|e^{i\theta}\neq 0$ allora "formalmente":
    $$\large logz=log(|z|e^{i\theta})=log|z|+i\theta$$
    Il termine $log|z|$ è il solito logaritmo reale valutato in $|z|>0$. La parte immaginaria è invece uguale a 0. Nella notazione esponenziale $z=|z|e^{i\theta}$ l'angolo $\theta$ ha infiniti valore possibili: $$\theta=\theta_0+2k\pi\text{ con k}\in\mathbb Z$$ dove $\theta_0=arg(z)\in(-\pi,\pi]$ si dice **argomento principale**.
    Questo comporta ci sono infiniti modi di definire il logaritmo complesso. Uno di questi è attraverso il **logaritmo principale**:
    $$log z=log|z|+iarg(z),~~~~per~z~\in~\mathbb C-\{0\}$$
7) La radice n-esima complessa:
   Anche in questo caso il problema è che dato un numero complesso $z\neq 0$ ci sono n radici n-sime distinte (se z=0 c'è una sola radice ossia 0): 
   Le soluzioni dell'equazione $W^{n}=z=|z|e^{iarg(z)}$ sono:$$\large W_k=\sqrt{|z|}e^{i(\frac{arg(z)}{n}+\frac{2\pi k}{n}}),~~~per~k=0,1,2,3, ...,n-1$$
   Si definisce la radice n-esima complessa **principale** come $$\large f(z)=\sqrt[n]{|z|}e^{i(\frac{arg(z)}{n})}=\sqrt[n]{|z|},~~~per~z\in\mathbb C$$   
---
### Limiti, Continuità e Derivabilità
   Sia $\Omega$ un insieme aperto di $\mathbb C$ e sia $f:\Omega\rightarrow \mathbb C$. Se $z_0\in\Omega$ si dice che $$\lim_{z\to z_0}f(z)=w$$
   Se $\forall \varepsilon>0, \exists~\delta>0$  tale che se $0<|z-z_{0}|<\delta$ e $z\in\Omega$ allora $|f(z)-w|<\varepsilon$. Questo è l'equivalente a dire che se $z=x+iy,z_{0}=x_{0}+iy_{0}$ e $w=a+ib$ allora: $$\large\lim_{x,y\to(x_0,y_0}u(x,y)=a~~~e~~~\lim_{x,y\to x_{0},y_{0}}v(x,y)=b$$
   
   
   