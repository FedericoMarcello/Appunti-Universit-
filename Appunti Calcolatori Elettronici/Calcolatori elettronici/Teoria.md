## Capitolo 2 Rappresentazioni:
### Conversione da base decimale a una base di destinazione qualsiasi:
#### Se ho parte intera:
1) Divisioni intere per la base di destinazione
2) Fermarsi quando si è arrivati al valore 0
3) Si ordinano i resti dall'ultimo al primo
##### Esempio
(10) in base decimale a base due:
10 |5, Resto= 0
5   |2, resto = 1
2   |1, resto = 0
1   |0, resto = 1
quindi 10 in base 2 si scrive (0,11)

#### Se ho parte decimale:
1) Moltiplicare per la base di destinazione
2) Si sottrae la parte intera 
3) Ci si ferma quando si è arrivati al valore 0 o un periodo
4) Si ordinano le parti intere sottratte dalla prima all'ultima dopo 

##### Esempio
(0.75) in base decimale a base due:
0,75|1.5 unità = 1
0,5  |1 , unità  = 1
0
quindi 0.75 in base 2 si scrive (0,11)


### Sistemi più comuni
esistono diversi sistemi di codifica, i più comuni sono
#### Sistema Binario:
- Base 2
- Alfabeto I = {0, 1}
#### Sistema Ottale
- Base 8
- Alfabeto I = {0,1,2,3,4,5,6,7}
#### Sistema Esadecimale
- Base 16
- Alfabeto I = {0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F}
#### Sistema Decimale
- Base 10
- Alfabeto I = {0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15}

### Scorciatoie per la conversione:
- Se parto da una base 2 ed arrivo ad una base 8, varranno le seguenti corrispondenze, o viceversa.
![[Pasted image 20240927161949.png]]

- Se parto da una base 2 ed arrivo ad una base 16, varranno le seguente corrispondenze, o viceversa:
![[Pasted image 20240927163327.png]] 
### Intervalli rappresentabili con la notazione posizionale
Dato un numero k di cifre di un alfabeto associato al sistema numerico in base b, è possibile rappresentare tutti i valori nell'intervallo: 
$${[0, b^k-1]}$$
 allo stesso modo per rappresentare n elementi, sono necessarie un numero di cifre pari a:
$$k=log_{b}(n)$$
è importante quindi conoscere gli intervalli rappresentabili perché le codifiche funzionano su insiemi finiti, questo perché un computer è in grado di interpretare informazioni a dimensione prefissata.

### Operazioni aritmetiche in altre basi:
Sono simili a quelle in base 10, ma introduciamo i concetti di riporto e prestiti:
![[Pasted image 20240927171217.png]]
questo è un esempio in base 2.
Analizzando la prima operazione, 
- 0+0 = 0, 
- 1+1=2, visto che esso non esiste in binario, lo trasformo e mi viene (10), e la prima cifra significativa la riporto
- allo steso modo per la terza operazione
- non avendo riporti, l'ultima è 1
Analizzando la seconda operazione,
- 0-1=-1, non esistendo il -1 devo prendere un prestito dalla cifra più vicina a sinistra, che avrà valore di 2 unità. Riducendo però il valore di 1 a 0,
- 0-1=-1, ""
- 0-0=0
- 1-0=1
### Numeri negativi in base 2:
Per studiare come si rappresenta il numero negativo esistono diversi metodi:
#### La rappresentazione in modulo e segno:
vado quindi a inserire nel primo bit significativo il valore opposto a quello iniziale.
![[Pasted image 20240927174102.png]]
Attraverso questa operazione però otterrò due zeri:
![[Pasted image 20240927174149.png]]
E' una rappresentazione inefficiente però, quindi non sarà quella utilizzata.
#### Complemento a uno:
Questo metodo consiste nell'invertire tutti i bit.
![[Pasted image 20240927175528.png]]
Il nome deriva dal fatto che sommando ogni valore otterremo una sequenza di tutti 1. Rimangono però due zeri.
Con n cifre, si rappresentano i numeri nell'intervallo:
$$[-(2^{n-1}-1), 2^{n-1}-1]$$
Ciò significa che il complemento a 1 di x è quel valore x' tale che se sommato a x mi restituisce una sequenza n di 1, ovvero:
$$x+x'=2^n-1$$
Questo tipo di rappresentazione, però, crea problemi quando svolgo operazioni di somma fra numeri negativi:
![[Pasted image 20240927180033.png]]
- Il risultato è sbagliato
- Il fenomeno si chiama end-around carry (riporto di fine giro)
- Per ottenere il risultato corretto, è necessario sommare al risultato ottenuto anche il bit di riporto.

#### Complemento a due:
La rappresentazione più efficiente è data dal complemento a 2, una rappresentazione ad n cifre, il complemento a due di un numero x è definita come il complemento a 2^n
$$2^n-x$$
Per calcolare il complemento a due di x possiamo ragionare sulla proprietà fondamentale del complemento a 1. 
([[Teoria#Complemento a uno]])
essendo il complemento a 1:
$$x+x'=2^n-1$$
invertendo l'1 e x, otterrò:
$$x'+1=2^n-x$$
##### Esempio:
- ho x=(0110) in base 2 = 6
- x' -> (1001) in base 2
- x'+1=(1010) in base 2 = -6
Osservando con attenzione notiamo che le due cifre meno significative di x e x'+1 sono entrambe 10, questo non è un caso:
- nel calcolo di x' tutti gli zeri meno significativi sono stati trasformati in uno
- sommando 1, si ripristina la configurazione delle cifre meno significative fino al primo 1
Quindi, in modo più generale, per calcolare il complemento a due di un numero, si parte dal bit meno significativo. Si lasciano inalterati tutti i bit fino a quando non si trova il primo 1. A questo punto, si invertono tutti i bit rimanenti.
##### Organizzazione della codifica: 
L'esempio di un caso di 4 cifre binarie:
![[Pasted image 20240927183515.png]] 
Notiamo che vi è un solo zero, ma si può codificare -8 e non 8 (chiamato per questo numero strano)

Con n cifre, si rappresentano i numeri nell'intervallo:
$$[-2^{n-1}, 2^{n-1}-1]$$
##### Somma e Differenza in complemento a 2:
Può essere svolta ignorando il segno:
![[Pasted image 20240927184618.png]]
- questo significa che per effettuare le sottrazioni basta negare il sottraendo ed effettuare la somma
- in questo modo utilizzo lo stesso circuito per implementare due operazioni differenti.
- Il riporto può essere tralasciato.
##### Condizioni di overflow:
Si parla di overflow quando il risultato non è compreso nell'intervallo di riferimento. 
Esso non avviene quando i due operandi hanno segno discorde.
Viceversa, esistono due casi in cui il risultato di una somma (in complemento a due) non è corretto ovvero se
- somma algebrica di due numeri positivi A e B. Si ha un overflow se $$ A + B >=  2^{n-1} $$
- somma algebrica di due numeri negativi A e B. Si ha overflow se  $$ A + B >= 2^{n-1} $$
Tali due condizioni si verificano se gli ultimi due riporti sono discordi:
![[Pasted image 20241012170320.png]]

Guardando l'immagine orizzontalmente, i primi due numeri sono entrambi somme di numeri positivi, mentre gli altri due sono numeri negativi (presenza dell'1 davanti al vero numero).
##### Rappresentazione in eccesso:
Chiamata anche offset binary o biased. Consiste nel selezionare un numero k nell'intervallo rappresentabile. Viene utilizzata la codifica binaria di k per rappresentare lo zero. 
Quando si utilizzano n bit , tipicamente si pone $k=2^{n-1}$ 
con due caratteristiche principali: 
- lo zero è rappresentato con un valore con la sola cifra più significativa pari a 1, essa è unica.
- viene conservato l'ordinamento dei numeri(non è vero con il complemento a 2)
- la codifica è estremamente semplice:$$x'=x+k,~~~x = x'-k$$
- Vi è una sola rappresentazione dello zero
- L'intervallo rappresentabile è $[-2^{n-1},2^{n-1}-1]$
### Numeri in virgola mobile:
Esistono molte quantità di numeri reali che possono essere memorizzate in numeri interi:
- lunghuezza
- prezzi
- temperature
- frequenze delle note musicali
- velocità
Cosa succede se dovessimo rappresentare un numero che è più alto del numero massimo rappresentato attraverso i bit?
Attraverso la Floating Point Unit possiamo manipolare numeri reali.
#### Caratteristiche:
- la rappresentazione dei numeri in virgola mobile si base su una uguaglianza del tipo: $12,345 = 1,2345 * 10^{1}$
  dove 
  $1,2345~è~la~mantissa,~10~è~la~base,~1~è~l'esponente$
  
- il nome virgola mobile si riferisce al fatto che la virgola può muoversi avanti e indietro 

- sono state proposte diverse rappresentazioni nel tempo, ma studieremo lo standard IEEE 754 a 32 bit:
#### Rappresentazione IEEE 754 a 32 bit:
![[Pasted image 20241014113848.png]]
Un numero reale (float) ha dimensione 32 bit così utilizzati:
- segno s: 1 bit
- esponente e: 8 bit
- mantissa m: 23 bit
#### Caratteristiche:
L'esponente decimale E è rappresentato in eccesso a 127:$$e= E +127
$$
La mantissa rappresenta il valore binario $$(1.m)_2$$
- dove la parte intera viene omessa nella rappresentazione
Il valore decimale può essere calcolato come $$(-1)^{s}*2^{è-127}*(1.m)$$ questa viene chiamata rappresentazione _normalizzata_
##### Tipologie di numero:
- numeri normalizzati: sono la maggior parte dei numeri rappresentabili dallo standard
- numeri denormalizzati: valori molto prossii allo zero. Generano alcuni problemi nella gestione degli errori di arrotondamento.
	- la parte intera omessa non è 1, bensì 0
- zeri: è possibile rappresentare ±0
	- la maggior parte delle operazioni ignora il segno, ma dividere per ±0 può dare come risultato $\pm\infty$ 
- infiniti: $\pm\infty$. Sono il risultato di una divisione per zero, o di un'operazione che genera un _overflow_
- NaNs(not a number): sono il risultato di un'operazione che non ha significato: $(\infty - \infty, \frac{0}{0},\sqrt{-1},...)$ 

Attraverso questa tabella possiamo individuare il  tipo di valore corrispondente grazie al valore della mantissa e dell'esponente:
![[Pasted image 20241014132810.png]]
##### Eccezioni:
In alternativa a NaNs e infiniti, è possibile richiedere alla FPU di sollevare delle eccezioni:
- **Invalid Operation**: generata quando si calcola un'operazione non matematicamente corretta
- **Overflow** : indica che il risultato di un'operazione è troppo grande per essere rappresentato da un numero in virgola mobile.
- **Division by Zero**: viene alzata quando si calcola $\frac{x}{\pm0}$ se $x \neq 0$
- **Underflow**: analoga all'overflow, per risultati troppo piccoli
- **Inexact**: i risultato reale non può essere rappresentato (vi è un errore di arrotondamento)
#### Massimo e minimo numero positivo rappresentabile:
##### Caso dei numeri normalizzati:
La mantissa rappresenta i numeri nell'intervallo:
$[(1.00000000000000000000000)_2,(1,11111111111111111111111)_2]$
###### Caratteristiche:
- Gli esponenti minimo e massimo sono 127 e -126
- minimo $2^{-126}\approx 1.1754943508 * 10^{-38}$ 
- massimo $2^{-126} * (1-2^{-23}\approx 3.4028234664*10^{38}$ 
##### Caso dei numeri denormalizzati:
La mantissa rappresenta i numeri nell'intervallo:
$[(0.00000000000000000000001)_2,(1,11111111111111111111111)_2]$
###### Caratteristiche:
- L'esponente è -126
- minimo $2^{-126} *2^{-23}=2^{-149}\approx 1.4012984643 * 10^{-45}$ 
- massimo $2^{-126} * (1-2^{-23}\approx 1.1754943508*10^{-38}$ 
#### Errori di approssimazione:
Sappiamo che numeri reali sono infiniti, ma i bit utilizzati per la rappresentazione in virgola mobile sono finiti, dunque:
- Ogni volta che effettuiamo un'operazione su un numero in virgola mobile, commettiamo un errore di operazione su un numero in virgola mobile
- Il risultato è che, anche se l'insieme dei reali è totalmente _connesso_, l'insieme dei numeri in virgola mobile è _sparso_
![[Pasted image 20241014155605.png]]
La presenza di numeri massimi e minimi rappresentabili, crea dei buchi nella linea dei numeri rappresentabili.
Altri buchi piccoli si creano tra la rappresentazione normalizzata quella denormalizzata.
Se un numero non è rappresentabile in alcun modo:
- **Overflow**:numero troppo grande o troppo piccolo (negativo)
- **Underflow**: arrotondamento allo zero
![[Pasted image 20241014163515.png]]
La divisione in mantissa/esponente fa nascere un ulteriore peculiarità del formato
quando siamo vicini allo zero, l'esponente è piccolo, quindi un incremento nella mantissa di 1 provoca un "salto" piccolo.
Viceversa, per numeri grandi, questo numero sarà migliore.
La densità dei numeri in virgola mobile non è quindi costante.
- con 32 bit, circa la metà dei numeri rappresentabili sono compresi tra -1 e 1
- vi è la stessa quantità di numeri rappresentabili tra 65536 e 131072
![[Pasted image 20241014173928.png]]
##### Come misurare l'errore:
è possibile quantificare l'errore di approssimazione commesso nella rappresentazione di un numero in virgola mobile:
- si può utilizzare la nozione di errore assoluto:
$$\varepsilon_A=x-x'$$
e ci dice quanto è stato perso dell'informazione originale.
Volendo si può utilizzare anche la nozione di errore relativo:
$$\varepsilon_{R}= \frac{x-x'}{x} $$
esso è una quantità adimensionale che indica se l'errore commesso è grande o piccolo.
La quantità $\log_{10}(\varepsilon_R)$ indica il numero di cifre non affette da errore.
###### Esempio:
![[Pasted image 20241014174950.png]]
### Altri tipi di codifica:
Volendo se definiamo un alfabeto e un tipo di codifica, possiamo far corrispondere questo linguaggio a quello che vogliamo.
#### Esempio:
![[Pasted image 20241014192459.png]]
#### Codifiche arbitrarie:
Non esiste una sola codifica per ciascun elemento degli elementi che si vogliono rappresentare. Ipotizziamo di avere N elementi da rappresentare, n cifre binarie disponibili per la codifica e $m=[\log_{2}N]$, ci sono due possibilità:
- Se $n=m$, allora il codice è irridondante
-  Se $n>m$, allora il codice è ridondante
Ecco alcuni Esempi:
##### Codifica ASCII (Irridondante):
American Standard Code for Information Interchange (ASCII), basata su un byte, superata da unicode per estendere la quantità di simboli rappresentati.
###### Tradizionale:
- 7 Bit
- 128 caratteri rappresentabili
- l'ottavo bit era utilizzato come codice di controllo di errore![[Pasted image 20240930151055.png]]
###### Esteso:
- 8 bit
- 256 caratteri rappresentabili (compresi i codici di controllo)
 
##### Codice Binary Coded Decimal (BCD), (Irridondante)
- è un codice irridondante per rappresentare le 10 cifre decimali usando quattro cifre binarie
- ciascuna cifra è codificata indipendentemente
- Tipicamente, due cifre sono memorizzate in un singolo bye (packed BCD)
- Di facile interpretazione per gli umani, comodo per consentire alle macchine una conversione per la stampa
- Molti bit sono sprecati (circa 1/6) rispetto alla rappresentazione binaria
![[Pasted image 20240930151346.png]]
##### Codice di Gray (Irridondante):
- La rappresentazione è tale per cui tra due numeri adiacenti cambia una sola cifra binaria.
- è un codice particolarmente utile per i casi di contatori elettronici, per evitare fenomeni transitori. Questo concetto è spiegabile attraverso un esempio, consideriamo la transizione: $(3_{10}\to (4_{10})) \equiv (011)_{2}\to(100)_2$ 
	- Possono verificarsi molte sequenze intermedie, ad esempio:$$(001)_{2}\to(010)_{2}\to(000)_{2}\to(100)_{2}$$Ed il sistema non può distinguere tra configurazioni transitorie e corrette.
	![[Pasted image 20240930151419.png]]
#### Distanza di Hamming (h)
Si dice distanza di Hamming il numero minimo di cifre diverse tra due parole del codice.
##### Esempio:

d(**10**0**10**, **01**0**01**) = 4

Esso è scrivibile come:
$$h =min(d(x,y))$$
- Nel caso di codice irridondante, la distanza è 1
- Un codice ridondante è capace di rivelare errori di peso $$\le~
h-1$$
#### Codici Ridondanti:
- Permetti di riconoscere o correggere gli errori
- Amplissimi spazi di applicazione:
	- aerospazio
	- super computer
	- Reti di calcolatori
![[Pasted image 20240930152540.png]]
Dove con la linea rossa indico la causa dell'errore
##### Come riveliamo l'errore?
Per capirlo, vediamo un esempio.
Ho questi due codici:
![[Pasted image 20240930152700.png]]

Il modo in cui utilizziamo lo spazio disponibile per rappresentare gli elementi può consentire di rivelare la presenza di errori:
![[Pasted image 20240930152759.png]]
##### Codice di parità o disparità (Ridondante):
Si tratta di un codice ridondante con h = 2 e si ottiene aggiungendo una cifra di parità ad un codice irridondante. Vi sono due tipologie: 
###### Parità:
vale 1 se il numero di 1 nella codifica irridondante è dispari, sennò 0
###### Disparità:
vale 1 se il numero di 1 nella codifica è pari, sennò 0
###### Tabella riassuntiva: 
![[Pasted image 20240930182922.png]]
###### Come funziona?
Supponiamo di usare un codice di _Parità_, si può determinare se c'è stato un **singolo** errore di trasmissione, vedremo perché è importante "singolo":
- se la parità varrà 0, allora non ci sono stati errori di trasmissione.
![[Pasted image 20241015000730.png]]
[Per capire meglio il funzionamento](https://www.edscuola.it/archivio/software/bit/bitfaq58.html) 

###### Esempio:
Voglio trasmettere 101.
Il generatore di parità aggiungerà 0 alla fine, trasmettendo 1010.
Vediamo diversi casi:
![[Pasted image 20241015001244.png]]
1) Se ricevo lo stesso bit, non avrò nessun segnale di errore perché la parità continua a valere 0, visto che la somma degli 1 è pari.
2) Nel secondo caso ricevo un valore con un valore diverso, riceverò un segnale di errore poiché  la parità è diversa da 0, visto che la somma degli 1 è dispari
3) Infine se gli elementi ad essere cambiati sono due (più in generale a coppie) la parità tornerà ad essere 0, quindi non riceverò alcun messaggio di errore,  questo è **totalmente sbagliato**. 
##### Codice di Hamming:
è un metodo per la costruzione di codici a distanza  $h \ge 3$. Data una parole di codice di $m = n+k~cifre, con~n \le 2^k - k-1$, avremo:
- i bit in posizione $2^i$ sono bit di parità
- ciascun bit di parità controlla la correttezza dei bit di informazione la cui posizione, espressa in binario, ha un 1 nella potenza di 2 corrispondente
![[Pasted image 20241015104730.png]]
###### Esempio 1:
![[Pasted image 20241015105120.png]]
###### Esempio 2:
![[Pasted image 20241015105157.png]]
###### Esempio 3:
![[Pasted image 20241015105332.png]]

## Capitolo 3 Algebra Booleana:
### Cos'è?
è un tipo di algebra definita dal matematico George Boole e fu inizialmente proposta nel tentativo di verificare la verità o la falsità di affermazioni in linguaggio naturale, partendo da alcune verità di base.
Nel 1936 venne utilizzata da Shannon per studiare i circuiti basati su relé. Questo poiché l'algebra di Boole si basa sui concetti di vero/falso, quella di relé su aperto/chiuso
Possiamo dunque dire che gli elementi fondamentali dei circuiti elettronici, al giusto livello di astrazione, rispettano ancora le regole dell'algebra booleana.

### Proprietà, assiomi ed elementi introduttivi: 
#### Variabili ed elementi di commutazione:
- Una variabile booleana (o di commutazione) è una quantità algebrica x definita su un insieme S= {0, 1}, ossia che può assumere solo due valori.

- Una funzione di commutazione di una variabile booleana è definita come la proiezione di {0,1} su {0,1}
	- $f:[{0,1}]\to [{0,1}]$
	- $y = f(x)$
- Una funzione di commutazione di n variabili booleane è una funzione il cui dominio è dato da tutte le n-uple $(x_{1}, x_{2},...,x_{n})~in~[0,1]^{n}$ ed il codominio è $[0,1]$:
	- $f:[0,1]^{n}\to [0,1]$
	- $y=f(x_{1},x_{2},...,x_{n})$
#### Operatori ed Assiomi fondamentali:
- Somma logica: indicata con il segno +
- Prodotto logico: indicato con il segno $*$ 
- Negazione: dato un valore x, il suo valore negato è $\bar{x}$
Questi permettono di definire gli **assiomi** fondamentali sul dominio S:
- $\forall a, b \in S; a + b \in S, a * b \in S~(chiusura)$
- $\exists0 \in S|\forall a \in s, a+0 =a; \exists 1 \in S |\forall a\in S, a*1=a~(elemento~idendità)$     
- $a+b=b+a~(proprità~commutativa)$
- $(a+b)+c = a+(b+c);(a*b)*c=a*(b*c)~(proprietà~associativa)$
- $a*(b+c)=a*b+a*c;a+b*c=(a+b)*(a+c)~(proprietà~distributiva)$
- $\forall a \in S \exists \bar{a} \in S|a+\bar{a}=1;a*\bar{a}=0~(elemento~inverso)$
- $|S|=2^{n}; n=1,2,3,...,(cardinalità)$
#### Legge di dualità:
##### Teorema:
Ogni identità booleana rimane invariata scambiando $+~con~*,e~0~con~1$
##### Esempi:
$Se~0+1 = 1,ponendo~1\to\alpha~e~0\to\beta~otteniamo~\alpha+\beta=\alpha$
$Se~0+1 = 1,ponendo~1\to0~e~0\to1~otteniamo~0+1=0$
$Se~0*1 = 0,ponendo~+\to*~e~*\to+~otteniamo~1*0=0$
#### Proprietà di idempotenza:
Nell'algebra booleana binaria vale $a+a=a~e~a*a=a$
##### Dimostrazione:
- $a= a+ 0$
-  $a= a+ a*\bar{a}$
- $a=(a+a)*(a+\bar{a})$
- $a=a+a$
- Di conseguenza, per la legge di dualità vale anche: $a=a*a$
#### Annichilatori funzionali:
Nell'algebra booleana binaria vale $a+1=1~e~a*0=0$
##### Dimostrazione:
La dimostrazione si basa sulla [[#Proprietà di idempotenza]]:
- $a+1=a+a+\bar{a}$
- $a+1=a+\bar{a}$
- $a+1=1$
- Di conseguenza, per la legge di dualità vale anche: $a*0=0$
#### Legge dell'assorbimento:
Nell'algebra booleana binaria vale $a+a*b=a~e~a*(a+b)=a$
##### Dimostrazione:
- $a+a*b=a*1+a*b$
- $a+a*b=a*(1+b)$
- $a+a*b=a*1$
- $a+a*b=a$
- Di conseguenza, per la legge di dualità vale anche: $a+a*b=a$
#### Teorema di De Morgan:
Il teorema di De Morgan è un teorema importante perché permette di esprimere gli operatori + e * in funzione degli altri due operatori fondamentali$$\overline {a+b}= \bar a* \bar b~~~~~~~~~~\overline{a*b}=\bar a+\bar b$$
##### Dimostrazione:
Per dimostrare il teorema è sufficiente verificare che $\bar a*\bar b$ è il complemento di $a+b$
- $(a+b)+(\bar a*\bar b)=(a+b+\bar a)*(a+b+\bar b)$
- $(a+b)*(\bar a+\bar b)=(1+b)*(1+a)$
- $(a+b)*(\bar a+\bar b)=1*1=1$
- La seconda si ottiene per la legge di dualità

#### Funzioni di commutazione:
Riprendiamo il discorso iniziato in [[#Variabili ed elementi di commutazione]] e vediamo come rappresentare le funzioni di commutazione attraverso gli operatori appena citati:
- Una funzione di commutazione di n variabili $y=f(x_{1},x_{2},...,x_{n})$ e il codominio è l'insieme $[0,1]$
- $f:[0,1]^{n}\to [0,1]$
Ci sono diversi modi per esprimere una funzione di commutazione:
- forma tabellare (tabelle di verità)
- forme canoniche 
- forme decimali
##### Tabelle di verità:
Crea una relazione fra le variabili di input ed il valore di output della funzione. In queste tabelle si utilizza speso in maniera interscambiabile il vettore **x**=$[x_{1},x_{2},..,x_n]$ e le variabili che lo compongono. 
Una tabella di verità di una funzione di n variabili è costituita da $2^{n}$ righe:![[Pasted image 20241015175418.png]]
###### Esempi:
Si possono vedere come funzioni di commutazione anche gli operatori fondamentali, attraverso 1 o 2 variabili di commutazione:![[Pasted image 20241015175353.png]]
