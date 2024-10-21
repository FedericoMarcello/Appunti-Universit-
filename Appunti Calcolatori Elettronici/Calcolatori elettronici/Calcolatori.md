# Esempi:
## 1)  Sistema di monitoraggio
Progettare il sistema di monitoraggio di un'azienda manifatturiera. Il sistema monitora il funzionamento di due macchine di produzione (M1 e M2) e controlla un sistema di raffreddamento ed allarme, in base alle condizioni operative delle due macchine:
- M1 indica se la macchina M1 è in funzione (1 si, 0 no)
- M2 indica se la macchina M2 è in funzione (1 si,0 no)
- T indica se la temperatura della stanza è elevata
- A attiva l'allarme se le macchine sono in funzione a la temperatura è elevata, o se nessuna macchina è in funzione
- V attiva la ventola di raffreddamento se almeno una delle due macchine è attiva e se la temperatura è elevata
Svolgimento:
$A=M_{1}*M_{2}*T+\overline{M_1}*\overline{M_2}$
$V=(M_{1}+M_{2})T=M_{1}*T+M_{2}*T$

Costruisco la tabella collegata alle equazioni e ai singoli casi

| $M_1$ | $M_2$ | T   | A   | V   |
| ----- | ----- | --- | --- | --- |
| 0     | 0     | 0   | 1   | 0   |
| 0     | 0     | 1   | 1   | 0   |
| 0     | 1     | 0   | 0   | 0   |
| 0     | 1     | 1   | 0   | 1   |
| 1     | 0     | 0   | 0   | 0   |
| 1     | 0     | 1   | 0   | 1   |
| 1     | 1     | 0   | 0   | 0   |
| 1     | 1     | 1   | 1   | 1   |

# Teoria:
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
([[Calcolatori#Complemento a uno]])
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

#### Operatori derivati:
Sulla base degli [[#Operatori ed Assiomi fondamentali]] è possibile definire i seguenti operatori derivati:
1) OR esclusivo (XOR), indicato con il simbolo $\bigoplus$ 
 2) Not AND, indicato con |.
 3) NOR, indicato con $\downarrow$ 
 4) NOR esclusivo (XNOR), indicato con il simbolo $\bigodot$
 
##### OR esclusivo (XOR)
Esso è equivalente alla somma modulo 2 ed è definito così:$$a~\oplus~b = \bar a b+a\bar b $$
Viene utilizzato per verificare la disuguaglianza tra due variabili.
 ![[Pasted image 20241016115031.png]]
###### Proprietà Principali:
- $a\oplus b = b\oplus a~(proprietà~commutativa)$
- $a\oplus(b\oplus c)=(a\oplus b)\oplus c~(proprietà~associativa)$
- $a\oplus a=0$
- $a\oplus \bar a = 1$
- $a\oplus 1=\bar a$
- $\bar a \oplus b = a \oplus \bar b= \overline{a\oplus b}$


##### Not AND (NAND):
Definito così:$$a|b=\overline{a * b}=\bar a +\bar b$$
![[Pasted image 20241016115216.png]]
###### Proprietà:
- $a|b=b|a~(Proprietà~commutativa)$
- $a|1=\bar a$
- $a|0=1$
- $a|\bar a = 1$
- $a|(b|c)\neq (a|b)|c~(l'operatore~non~è~associativo)$    


##### NOR
Si tratta del duale dell'operatore NAND ed è definito cosi:$$a\downarrow b = \overline{a+b}=\bar a *\bar b$$ ![[Pasted image 20241016121655.png]]
###### Proprietà:
- $a\downarrow b = b\downarrow a~(proprietà~commutativa)$
- $a\downarrow 1 = 0$
- $a\downarrow 0 = \bar a$
- $a\downarrow \bar a = 0$
- $a\downarrow(b\downarrow c)\neq (a\downarrow b) \downarrow c~(l'operatore~non~è~associativo)$


##### Nor esclusivo (XNOR)
Definito come segue:$$a\odot b=(\bar a+b)*(a+\bar b)$$ ![[Pasted image 20241016121907.png]]
###### Proprietà:
- $a\odot b = b\odot a~(proprietà~commutativa)$
- $a\odot(b\odot c)=(a\odot b)\odot c~(proprietà~associativa)$
- $a\odot 1= a$
- $a \odot \bar a =0$
- $a \odot 0 =\bar a$

#### Teorema di Shannon:
Il teorema afferma che una qualsiasi funzione $y= f(x_{1}, x_{2},...,x_{n})$ può essere rappresentata in una delle due seguenti forme duali:
$f(x_{1}, x_{2},...,x_{n})=x_{1}*f(1,x_{2},...,x_n)+\overline{x_1}*f(0,x_2,...,x_n)$ 
$f(x_{1}, x_{2},...,x_{n})=(x_1+f(0,x_{2},..,x_{2}))*(\overline {x_1}+f(1,x_2,..,x_n))$  
I termini che moltiplicano o si sommano a $x_{1}$ sono chiamati i residui della funzione. Ciò è vero nel caso di variabili indipendenti.
Questo teorema può essere applicato iterativamente a tutte le variabili della funzione.
Se svolgo questo processo otterrò:$$f(x_{1},...,x_{n})=\overline{x_{1}}*\overline {x_{2}}*...*\overline {x_{n}}*f(0,0,...,0)+ {x_{1}}*\overline {x_{2}}*...*\overline {x_{n}}*f(1,0,...,0)+\\ $$$$+\overline {x_{1}}*{x_{2}}*...*\overline {x_{n}}*f(0,1,...,0)+...+{x_{1}}*{x_{2}}*...*\overline {x_{n}}*f(1,1,...,0)+{x_{1}}*{x_{2}}*...*{x_{n}}*f(1,1,...,1)$$ Che può essere riassunto, per ogni termine cosi:$$x_1^{\alpha_1}x_2^{\alpha_2}...x_n^{\alpha_n}*f(\alpha_1,\alpha_2,...,\alpha_2)$$
con $\alpha_i=[0,1]~e~x_{i}^{\alpha_{i}}=x_{i}~se~\alpha_i=1,x_{i}^{\alpha_{i}}=\overline{x_i}~se~\alpha_{i}=0$
#### Forme canoniche:
Sono rappresentazioni uniformi utilizzate per descrivere una funzione di commutazione. Qualsiasi funzione può essere trasformata in forma canonica:
- Tabelle di verità e utilizzare la tecnica dei mintermini o maxtermini
- Si possono effettuare trasformazioni analitiche: se una variabile $x_i$ non è presente, si può moltiplicare per $(x_{i}+\overline{x_i})$ 
##### Prima tecnica: Min e Max termini
###### Prima forma canonica: _somma di prodotti_
(o forma canonica disgiuntiva):$$f(x_{1},x_2,...,x_n)=\sum_{k=0}^{2^n-1}m_kf(k)$$
- il termine $m_k$ viene chiamato mintermine ed è nella forma $x_1^{\alpha_1}x_2^{\alpha_2}...x_n^{\alpha_n}$
- In ciascun mintermine, le variabili compaiono una ed una sola volta in forma diretta o negata.
###### Seconda  forma canonica: _prodotti di somme_
Utilizzando il teorema di De Morgan possiamo trasformare la forma canonica precedente in :$$\overline{f(x_{1},x_2,...,x_n)}=\sum_{k=0}^{2^{n}-1} m_{k}\overline{f(k)}$$Che possiamo scrivere come:$${f(x_{1},x_2,...,x_n)}=\overline{\sum_{k=0}^{2^{n}-1} m_{k}\overline{f(k)}}=\prod_{k=0}^{2^{n}-1} \overline{m_{k}\overline{f(x)}}=\prod_{k=0}^{2^{n}-1} (M_{k}+f(k))$$
Dove il termine $M_k$ viene chiamato maxtermine ed è nella forma:
$M_k=$ $\sum_{i=0}^{n-1}x_i^{a_{i}}$ con $\alpha_{i}=[0,1]$ e $~x_{i}^{\alpha_{i}}=x_{i}~se~\alpha_i=0,x_{i}^{\alpha_{i}}=\overline{x_i}~se~\alpha_{i}=1$
###### Esempio:
Consideriamo la seguente funzione di commutazione definita mediante tabella di verità:
![[Pasted image 20241016194746.png]]
- I **mintermini** corrispondono alle configurazioni k = 0,4,5,7
- I **maxtermini** corrispondono alle configurazioni k= 1,2,3,6
A questo punto, dai mintermini possiamo definire la seguente rappresentazione in somme di prodotto:$$f(x_1,x_2,x_3)=\overline{x_1}~\overline{x_2}~\overline{x_3}+x_1~\overline{x_2}~\overline{x_3}+x_1~\overline{x_2}~{x_3}+x_1~{x_2}~{x_3}$$
![[Pasted image 20241016195321.png]]


Invece dai maxtermini possiamo definire la seguente rappresentazione in somme di prodotti:$$f(x_{1}, x_{2},x_{3})=(x_{1}+x_{2}+\overline{x_3})(x_{1}+ \overline{x_2}+x_{3})(x_{1}+\overline{x_{2}}+\overline{x_3})(\overline{x_{1}}+\overline{x_{2}}+x_{3})$$ ![[Pasted image 20241017094726.png]]

###### Forma decimale:
Si indica l'interpretazione decimale delle variabili booleane associate a mintermini e maxtermini:$$f(k)=\sum\limits(0,4,5,7)=\prod(1,2,3,6)
$$![[Pasted image 20241017105808.png]]

##### Seconda tecnica: Trasformazioni Analitiche:
Per capire meglio, utilizziamo il seguente esempio:$$x_{1}x_{3}+\overline{x_{1}}(x_{2}+\overline{x_{3}})$$ questa funzione può essere trasformata come segue:$$x_{1}x_{3}+\overline{x_{1}}(x_{2}+\overline{x_{3}})=x_{1}x_{3}(x_{2}+\overline{x_{2}})+\overline{x_{1}}x_{2}(x_{3}+\overline{x_{3}})+\overline{x_{1}}\overline{x_{3}}(x_{2}+\overline{x_{2}})$$Risolvendo la moltiplicazione otterremo:$$x_{1}x_{2}x_{3}+x_{1}\overline{x_{2}}x_{3}+\overline{x_{1}}x_{2}x_{3}+2(\overline{x_{1}}x_{2}\overline{x_{3}})+\overline{x_{1}x_{2}x_{3}}$$

#### Forme semplificate:
Le forme canoniche non sono necessariamente le forme minime per rappresentare una funzione booleana.
Identificare una forma minima è importante poiché permetterà di realizzare circuiti più compatti ed il processo può essere svolto attraverso due metodi:
- analitici
- algoritmici
##### Metodi analitici:
I metodi analitici richiedono di applicare le proprietà dell'algebra e teoremi visti fin ora.
Non esiste un tipo di risoluzione corretto per ogni forma.
###### Esempio:
![[Pasted image 20241017110240.png]]![[Pasted image 20241017110409.png]]

#### Mappe di Karnaugh:
Le mappe di Karnaugh sono una rappresentazione differente delle tabelle di verità.
##### Caratteristiche:
- Le variabili vengono organizzate in tabelle quadrate o rettangolari, a seconda del loro numero
- I valori che possono assumere le variabili vengono ordinati secondo un Codice di Gray (distanza di Hamming=1)
- In questo modo, spostandosi da una cella all'altra, si causa il cambiamento del valore di _una sola variabile_
- Poiché $(a+\overline{a})=1$ è possibile eliminare (semplificare) una variabile se la funzione assume lo stesso valore in gruppi di celle adiacenti
- Esso è un metodo facile per gli umani (max 6 variabili), di difficile realizzazione automatizzata per un algoritmo
##### Mappe di Karnaugh (funzioni a 2,3,4 variabili):
![[Pasted image 20241017154632.png]]
E' importante notare che l'uso del codice di Gray garantisce che anche le celle agli estremi siano _adiacenti_.
###### Funzioni a 4 variabili:
Studiando la funzione a 4 variabili osserviamo che le adiacenze ai bordi e agli angoli sono valide poiché la mappa è lo sviluppo di un solido multidimensionale.
Ad esempio, per 4 variabili la mappa è lo sviluppo di un _toro_:
![[Pasted image 20241017160109.png]]
##### Mappe di Karnaugh (funzioni a 5 variabili):
![[Pasted image 20241017160244.png]]
L'adiacenza è anche tra le due tabelle, come se queste fossero sovrapposte.
##### Mappe di Karnaugh (funzioni a 6 variabili):
Come nel caso di cinque variabili, anche qui le adiacenze valgono per tabelle sovrapposte:
![[Pasted image 20241017160509.png]]

##### Mappe di Karnaugh e tabelle di verità:
Per trasforma una tabella di verità in una mappa di Karnaugh è sufficiente riempire le celle della mappa con il valore della funzione in corrispondenza delle variabili di ingresso:
![[Pasted image 20241017161537.png]]
[Approfondimento ChatGPT](https://chatgpt.com/share/67112f87-4d14-8008-be3c-1e64b19238ec)
##### Semplificazioni mediante mappe di Karnaugh:
Per sfruttare le adiacenze è possibile costruire insiemi di copertura di dimensione 1,2,4,8,16,... celle, raddoppiando via via la dimensione. Questi insiemi devono coprire tutti i termini 1. 
Così facendo, si identificano gli implicanti primi, ossia gli insiemi di termini che determinano la funzione equivalente minima. Tuttavia è possibile lavorare anche con i maxtermini, in tal caso si parla di implicanti minimi e le coperture avvengono sugli 0.
Non è detto che, data una funzione, esista un solo insieme di implicanti minimi.

###### Esempio:
Consideriamo la funzione:$$f(x,y,z,w)=\sum\limits(0,1,3,7.15)$$
Andiamo a scrivere la tabella di verità, sappiamo che:
- deve avere $x^{n}~righe$
- in questo caso, l'output(ovvero l'ultima colonna) sarà 0 se il numero corrispondente non è tra i mintermini, viceversa si otterrà 1, per esempio $f(0,0,0,1)=1$ poiché 1 è un mintermine. 

| $x_1$ | $x_{2}$ | $x_{3}$ | $x_4$ | $f(x,y,z,w)$ |
| ----- | ------- | ------- | ----- | ------------ |
| 0     | 0       | 0       | 0     | 1            |
| 0     | 0       | 0       | 1     | 1            |
| 0     | 0       | 1       | 0     | 0            |
| 0     | 0       | 1       | 1     | 1            |
| 0     | 1       | 0       | 0     | 0            |
| 0     | 1       | 0       | 1     | 0            |
| 0     | 1       | 1       | 0     | 0            |
| 0     | 1       | 1       | 1     | 1            |
| 1     | 0       | 0       | 0     | 0            |
| 1     | 0       | 0       | 1     | 0            |
| 1     | 0       | 1       | 0     | 0            |
| 1     | 0       | 1       | 1     | 0            |
| 1     | 1       | 0       | 0     | 0            |
| 1     | 1       | 0       | 1     | 0            |
| 1     | 1       | 1       | 0     | 0            |
| 1     | 1       | 1       | 1     | 1            |
Ora rappresentiamo la tabella di verità su una mappa di Karnaugh:
![[Pasted image 20241017164132.png]]
a questo punto, identifichiamo gli **implicanti primi** selezionando degli insiemi di dimensione 1,2,4,... fino a coprire tutti gli 1 almeno una volta(semplificazione con mintermini).
A questo punto, identifichiamo gli implicanti primi selezionando degli insiemi di dimensione 1,2,4,.. fino a coprire tutti gli 1 almeno una volta:
![[Pasted image 20241018092648.png]]
Le variabili che cambiano valore nelle celle adiacenti in ciascun insieme possono essere semplificate:
- $f(x,y,z,t)=\bar{x}\bar{y}\bar{z}+\bar{x}zw+yzw$ (insiemi di sinistra)
- $f(x,y,z,t)=\bar{x}\bar{y}\bar{z}+\bar{x}\bar{z}w+yzw$ (insiemi di sinistra)
###### Esempio mediante prodotto di somme:
è possibile effettuare la semplificazione creando insiemi che ricoprano gli zeri:
- le funzioni minime ottenute sono equivalenti
In questo caso dobbiamo esprimere la funzione come prodotto di somme:

Quale usare?
- Una regola non universale ma molto pratica e quella di utilizzare i max termini se gli 1 sono meno della metà e se invece sono gli zeri ad essere meno della metà, si usano i mintermini.
- In generale è opportuno identificare la strategia che porta al numero minore di termini o di termini con meno variabili.
![[Pasted image 20241018182259.png]]
![[Pasted image 20241018182314.png]]
###### Esempi di adiacenze: funzioni di 4 variabili
![[Pasted image 20241018182405.png]]
###### Esempi di adiacenze: funzioni di 5 variabili
![[Pasted image 20241018182445.png]]
###### Don't Care Condition:
A volte, una funzione è parzialmente specificata.
In questi casi il valore dell'uscita non è definito per tutte le configurazioni delle variabili di ingresso:
- variabili dipendenti
- Configurazioni non di interesse.
In questi casi, i mintermini/maxtermini vengono associati (nella notazione decimale) a un insieme $\sum\limits_\frac{0}{1}$ che rappresenta il fatto che non è noto (o di interesse) che il valore della funzione sia 0 o 1.
Nel caso delle mappe di Karnaugh, si indica tale condizione con un trattino (-) e si più comodo per la minimizzazione.
![[Pasted image 20241018183317.png]]
###### Esempio di funzioni con 6 variabili:
L'insieme azzurro costruisce un insieme di copertura che racchiude 4 termini, permettendo una riduzione di due variabili.
Se avessimo considerato il solo mintermine $\bar{a}bcd\bar{e}\bar{f}$ l'espressione sarebbe stata più complessa.
![[Pasted image 20241018183609.png]]
##### Operatori Universali:
Essi sono utili nell'implementazione dei circuiti perché la loro implementazione in hardware può richiedere un numero minore di componenti elettroniche
###### Operatore NAND
L'operatore NAND permette, da solo, di esprimere tutta l'algebra booleana (_operatore universale_). Infatti è possibile esprimere tutte le costanti e gli operatori fondamentali dell'algebra sfruttando solo ed esclusivamente l'operatore NAND
$a|a=\bar a$
$(a|a)|(b|b)=\overline{\bar{a}~\bar{b}}= a+b$ 
$(a|b)|(a|b)=\overline{\overline{(ab)}~\overline{(ab)}}=(ab)+(ab)=ab$ 
$a|(a|a)=\overline{a\bar{a}}=a+\bar a=1$
$(a|(a|a))|(a|(a|a))=1|1=0$
###### Operatore NOR:
L'operatore NOR è stato definito come duale dell'operatore NAND, quindi anch'esso deve essere universale.
$a\downarrow a=\bar a$
$(a\downarrow a)\downarrow(b\downarrow b)=\overline{\bar{a}~\bar{b}}= a*b$ 
$(a\downarrow b)\downarrow(a\downarrow b)=\overline{\overline{(a+b)}}=a+b$ 
$a\downarrow(a\downarrow a)=0$
$(a\downarrow (a\downarrow a))\downarrow(a\downarrow(a\downarrow a))=1$ 
## Capitolo 4: circuiti combinatori:
### Circuiti logici (o di commutazione):
Sono reti di componenti che accettano variabili booleane in input e le restituiscono in output. Per capirle meglio è utile affidarsi all'algebra booleana. Gli operatori booleani sono implementati in hardware da circuiti chiamate porte logiche che vengono astratte con i seguenti simboli:
![[Pasted image 20241019134140.png]]
#### Negazioni e porte a più ingressi:
Circuitalmente è più efficiente inserire il calcolo della negazione degli input direttamente nelle porte logiche:
![[Pasted image 20241019224740.png]]
Inoltre è possibile costruire porte a più ingrassi, dipendentemente dalla tecnologia costruttiva:
![[Pasted image 20241019224829.png]]
La maggior parte degli operatori è associativo e commutativo
##### NAND a più ingressi:
Abbiamo visto che l'operatore NAND non è associativo,([[#Not AND (NAND)]]), quindi 
$$x_{1}|(x_{2}|x_{3})=\overline{x_{1}}+x_{2}x_{3}\ne x_{1}x_2+\overline {x_3}=(x_{1}|x_{2})|x_{3}$$
ciò significa che i seguenti cicli non sono equivalenti:
![[Pasted image 20241020120231.png]]
E' però possibile costruire la seguente porta logica:
![[Pasted image 20241020120308.png]]
ed il suo significato è dato da $x_{1}|x_{2}|x_{3}=\overline{x_{1}x_{2}x_{3}}$ costruendo quindi un operatore NAND associativo. 
Questo operatore calcolare una funzione differente dal NAND booleano.
##### NOR a più ingressi:
vale lo stesso ragionamento per l'operatore NOR, infatti:![[Pasted image 20241020125034.png]]
##### Porte logiche a diodi:
###### Tipo di porta AND:
E' possibile costruire un selettore di velocità secondo il circuito in figura e poichè 
operiamo con circuiti di commutazione, assumiamo che siano possibili solo due livelli di tensione:$V_{L}~e~V_{H}$.
Il circuito rappresentato funziona attraverso le caratteristiche dei singoli componenti:![[Pasted image 20241020190238.png]]
- diodi: sono degli interruttori che funzionano come dei conduttori solo se il lato che è collegato a $V_{1}~o~a~V_{2}$ 
- resistenza: collega l'uscita $V_{out}$ alla tensione di alimentazione $V_{CC}$ 
 Sapendo che i diodi funzionano in un modo specifico, possiamo analizzare le condizioni di tensione:
- Se $V_{1}$ è positivo, ci sarà un blocco di tensione in posizione del diodo corrispondente, condurrà la corrente a $V_{2}$.
	- Se $V_{2}$ è positivo, allora ci sarà un blocco anche in corrispondenza del secondo diodo, dunque la tensione in $V_{out}$ sarà alta.
	- Se $V_{2}$ è negativo, non ci sarà blocco e la corrente passerà fino ad arrivare in $V_{2}$, quindi la tensione in $V_{out}$ sarà bassa.
- se entrambi gli ingressi sono bassi, nessun diodo condurrà e $V_{out}$ sarà mantenuto alto grazie a $V_{CC}$ attraverso la resistenza R, quindi la corrente sarà alta.
Questo circuito si comporta come una porta AND, poiché il caso di tensione alta si può verificare in $V_{2}$ SE E SOLO SE le altre due sono alte.
Se anche una delle due è bassa, allora il risultato sarà basso. In termini booleani, $V_{out}$ sarà 1 se sia $V_{1}$, sia $V_{2}$ sono 1.
###### Tipo di porta OR:
Immaginiamo un circuito ideale di questo tipo, per implementare una porta logica di tipo OR:
![[Pasted image 20241021122123.png]]
Implementa la porta OR poiché la tensione in $V_{out}$ sia alta, basta che si verifichi che o $V_{1}$ sia alta o $V_{2}$ lo sia, come anche spiegato dalla tabella. In termini booleani $V_{out}$ è 1 se o$V_{1}$ è 1 o $V_{2}$  lo è

###### Problemi:
Le porte basate su diodi provocano un'attenuazione del segnale. Collegando in cascata più porte, il segnale subirà un'attenuazione progressiva che può distruggere la differenza tra $V_{L}$ e $V_{H}$. Questo fenomeno ha portato al progressivo abbandono di queste porte negli anni '60 a favore delle porte a transistor.
##### Logica TTL:
La Transistor/Transistor Logic si basa sull'uso di alcuni transistor per la realizzazione  della funzione di commutazione e di alcuni transistor per l'amplificazione del segnale, per eliminare il fenomeno dell'attenuazione.
Si basano sul concetto di resistenze _pull up_.
###### Esempio (Inverter TTL):
Implementa una porta NOT:
![[Pasted image 20241021123942.png]]
##### Logica CMOS:
si basa sull'uso di transistor pMOS e nMOS nella stessa rete, rispettivamente la prima si comporta da _pull up_, mentre la seconda implementa la parte di _pull down_ il vantaggio è che l'area utilizzata è estremamente piccola.
###### Esempio: (inverter CMOS):
![[Pasted image 20241021131220.png]]
##### Porta NAND:
![[Pasted image 20241021133808.png]]

##### Porta NOR:
![[Pasted image 20241021133839.png]]

##### Riduzione del costo nelle operazioni AND/OR:
Immaginiamo di avere una funzione composta del tipo:
$$y=\sum\limits_{i=1}^{n}f_{i}~oppure~y=\prod_{i=1}^{n}f_{i}$$
Il circuito logico risultante è del tipo:
![[Pasted image 20241021134252.png]]
Vi sono però dei problemi, in particolare nei "puntini", infatti visto che il numero di ingressi cresce, aumenterà anche il numero di transistor, ma non è detto che si conoscono a priori il numero di input da considerare. Nel caso in cui gli input fossero in grande numero, il relativo accumulo di corrente potrebbe danneggiare i dispositivi elettronici.
#### Tecnologia in Open Collector:
Le porte Open collector utilizzano un transistor aggiuntivo in cui il collettore è connesso all'uscita della porta che funziona come un circuito aperto o come come circuito connesso a massa. Visto che si lavora in logica negata,viene utilizzata una resistenza di pull up che fa salire la tensione quando il circuito è chiuso:
![[Pasted image 20241021172205.png]]
Per indicare un operatore logico in open collector, viene utilizzato il simbolo della porta logica negata, marcato con "OC". Esempio: NAND in Open Collector, dove la resistenza di pull up diventa esterna alla porta:![[Pasted image 20241021175210.png]]
Le porte in open collector vengono usate quando c'è la necessit di collegare insieme più porte che possono fornire corrente in uscita contemporaneamente. L'accumulo di corrente in uscita, nel caso di un numero elevato di componenti, può produrre un danno fisico al circuito. Con l'uso dell'open collector la quantità di corrente che fluisce nel circolo non è più in funzione del numero di porte con l'uscita attiva:
![[Pasted image 20241021175530.png]]
##### Buffer Three-State :
è un circuito che viene utilizzato per collegare tra loro parti di un circuito complesso. E' un circuito a tre canali:
- un segnale di ingresso
- un segnale di uscita
- un segnale di controllo
Il segnale di uscita è uguale al segnale di ingresso se questo è attivo, altrimenti l'uscita è ad alta impedenza. Si comporta quindi da interruttore:![[Pasted image 20241021180854.png]]
#### Dalle funzioni booleane ai circuiti e viceversa:
Grazie alle parti logiche introdotte si può partire da una funzione e arrivare ad un circuito e viceversa, vediamo i due casi:
##### Da una funzione booleana a un circuito:
1. Si considerano i termini più interni (per precedenza) e si realizza quella parte della funzione come circuito
2. Le uscite delle porte così definitite vengono usate come input delle funzione esterne
###### Esempio:
![[Pasted image 20241021181258.png]]![[Pasted image 20241021181539.png]]![[Pasted image 20241021181603.png]]
##### Dalla funzione al circuito:
- Si assegna un nume all'uscita di ogni porta
- Queste variabili ausiliare vengono progressivamente eliminate fino a quando non si ha un'espressione che usa solo le variabili di input.
###### Esempio:
![[Pasted image 20241021181341.png]]
##### Efficienza del circuito realizzato:
Una volta costruito il circuito, dobbiamo chiederci quanto esso sia efficiente. Possiamo rispondere attraverso due definizioni:
- Costo: quante componenti elettroniche utilizziamo per realizzare il circuito?
- Tempo: quanto è veloce il circuito a calcolare l'uscita dati gli ingressi?
La differenza tra una funzione booleana e un circuito, è che la funzione è impulsiva mentre un circuito di commutazione ha un ritardo di calcolo.
###### Ritardo di commutazione:
![[Pasted image 20241021183902.png]]
I circuiti sono componenti fisiche, pertanto se applichiamo un gradino in ingresso, l'uscita si stabilizzerà dopo un po' di tempo:
- $\tau_{d}:$ ritardo di commutazione (tempo per arrivare al 10% del valore finale)
- $\tau_{r}$ : tempo di salita (tempo per arrivare al 90% del valore finale)
Per semplicità si considera di solito un unico tempo di propagazione $\tau_{p}$ 
###### Ritardo su un circuito complesso:
Il tempo di propagazione si accumula quando ci sono più porte in cascata che implementano una funzione.
Per stimare le prestazione, si può ricorrere al crital path:
- il percorso più lungo che un segnale di input attraversa in un circuito.
![[Pasted image 20241021184053.png]]
Possiamo stimarer un ritardo pari a $4\tau_{p}$ : è un circuito a quattro livelli.
##### Costo:
possiamo sfruttare le tecniche di minimizzazione delle funzioni booleane per cercare di minimizzare il costo e massimizzare le prestazioni:
![[Pasted image 20241021184252.png]]
Queste tecniche ci permettono di identificare l'equivalenza tra i due circuiti seguenti:
![[Pasted image 20241021184603.png]]
##### Forme canoniche come reti:
Ogni funzione booleana può essere espressa in forma canonica. Queste possono essere realizzate usando 2 soli livelli di porte logiche (AND/OR).
Non è detto che una rappresentazione in forma canonica sia in forma minima.
##### Esempio:
![[Pasted image 20241021184924.png]]
#### Componenti:
##### Codificatore:
Il codificatore è un circuito che realizza la funzione di codifica binaria. Associa ad ogni elemento di un certo insieme di codifica composto da m simboli una sequenza distinta di n bit.
Per ogni simbolo, generale il codice corrispondente (con $2^{n}>=m$)
Il circuito ha quindi m linee di ingresso $x_{0},...,x_{m-1}$ ed n linee di uscita $y_0,...,y_{n-1}$
![[Pasted image 20241021185626.png]]
###### Esempio:
![[Pasted image 20241021185654.png]]
##### Decodificatore:
Realizza la funzione inversa del codificatore: a partire da una parola di un codice binario, genera una uscita che identifica uno dei simboli dell'insieme di interesse. Per ciascuna configurazione di ingresso, una sola uscita vale 1, le altre 0.
###### Esempio:
![[Pasted image 20241021185841.png]]
![[Pasted image 20241021185853.png]]![[Pasted image 20241021185913.png]]
##### Multiplexer:
In alcuni casi è necessario scegliere tra più segnali in input/output, per esempio quando forniamo input diversi ad una stessa funzione booleana implementata in hardware:
Il _multiplexer_ è un circuito che permette di selezionare tra un insieme di input, un solo output.
Esso si basa su n segnali di controllo (**x**),$2^n$ segnali dati(**d**) e una sola uscita (y)
![[Pasted image 20241018114739.png]]

L'uscita assume il valore $d_i$ quando x=i
possiamo quindi scrivere la funzione di uscita come somma logica tra il prodotto di tutti i mintermini di x e i dati d:$$y=\sum\limits_{i=o}^{2^{n}-1}d_{i}m_{i}$$![[Pasted image 20241018114914.png]]![[Pasted image 20241018114958.png]]

Un multiplexer può essere utilizzato per implementare qualsiasi funzione booleana di n variabili. Questa rappresentazione in forma tabellare di una funzione determina per ogni configurazione dell'input il valore dell'output.
un multiplexer può implementare tale tabella.
![[Pasted image 20241018115308.png]] 
##### Demultiplexer:
il circuito duale del multiplexer è il demultiplexer. l'uscita i esima assume i valore y quando la variabile di controllo x=i. Possiamo trovare una somiglianza con il decoder.
![[Pasted image 20241018115503.png]]
##### Read Only Memory:
è una memoria in sola lettura. Le locazioni di memoria possono essere lette specificandone l'indirizzo:
![[Pasted image 20241018115643.png]]
è un'implementazione alternativa di un circuito combinatorio, dato un'ingresso, c'è una sola uscita.
###### Schema logico di una ROM:
Le funzioni di commutazione sono realizzate come OR di mintermini:![[Pasted image 20241018115834.png]]
e questa è la rispettiva implementazione.
![[Pasted image 20241018115902.png]]
###### ROM Paginata:
Per motivi di ottimizzazione di superficie, si cerca di realizzare le ROM in forma quadrata. 
Viene quindi organizzata in "pagine", con una parte dei bit dell'indirizzo viene usata per selezionare la pagina. 
La restante parte seleziona la parola all'interno della pagina.![[Pasted image 20241018120202.png]]
##### PLA
Una ROM è una matrice di AND (con cui sostituisco il decoder) che implementa tutti i mintermini, accoppiata ad una matrice di OR che implementa le varie funzioni. Si potrebbe rendere programmabile sia la rete AND che OR:
La Programmable Logic Array (PLA) realizza questa struttura:
![[Pasted image 20241018120605.png]]
Come nel caso della ROM, la programmazione avviene a tempo di sintesi. 
Dei fusibili possono essere utilizzati per collegare i fila sia nella rete AND che nella rete OR. 
###### Esempio:
![[Pasted image 20241018121830.png]]
Studio il grafico attraverso le equazioni delle singole y:
$$y_{1}=\bar{x_{1}}x_{2}\bar{x_4}+\bar{x_{1}}x_{3}{x_4}+x_{1}$$
Questo perché presi $x_{1},x_{2},x_{4}$ notiamo che dobbiamo studiare il loro comportamento e quello dei rispettivi negati. $y_{1}$ presenta 3 fusibili e studiandoli singolarmente noto che le "linee" tracciate di $\bar{x_{1}}x_{2}\bar{x_4}$ mi restituiscono 1 se sono  sulla stessa linea. Nella precedente formula, la moltiplicazione fra le varie x dell'input, corrisponde all'operatore "AND", questo significa che il fusibile che si trova nella prima riga della colonna di $y_1$ si illumina se tutti e tre i fusibili corrispondenti sulla stessa riga sono accesi. Lo stesso vale per le righe successive. Da questo ne deduciamo che la somma fra le i tre elementi corrisponde all'operatore "OR". Nel complesso cosa significa questo? 
Il fusibile che si trova in corrispondenza della prima riga e sulla colonna di $y_1$ si illumina SE E SOLO SE tutti e tre i fusibili sulla stessa riga si illuminano, restituendo quindi come valore 1. Affinché $y_{1}$ ritorni 1, è necessario che SOLO 1 dei 3 fusibili della colonna y si illumini. In termini numerici questo significa y torna 1 SE E SOLO SE uno tra $\bar{x_{1}}x_{2}\bar{x_4},~~\bar{x_{1}}x_{3}{x_4},~~x_{1}$ ritorni 1.
 Queste sono le due equazioni di $y_{2},y_{3}$
 $$y_{2}=\overline{x_{2}}x_{3}{x_4}+\overline{x_{3}}~\overline{x_{4}}+{x_1}{x_3}+x_{2}\overline{x_{4}}$$
 $$y_{3}={x_{1}}x_{2}+\overline{x_{1}}~\overline{x_{2}}+{x_1}{x_3}+x_{2}{x_{4}}$$
 
 
## Capitolo 5: Reti iterative:
### Reti combinatorie iterative:
I metodi di sintesi che abbiamo analizzato fino a questo punto permettono la sintesi di circuiti in cui sono poche le variabili in inout.
Per progettare una CPU, dobbiamo essere in grado di gestire dati a 16, 32, 64 bit. Un circuito di questo tipo può essere difficile da sintetizzare. Per ovviare a questo problema possiamo organizzare i circuiti in maniera iterativa. Ciò significa che uno stesso circuito elementare tratta un sottoinsieme dei bit dei dati, riducendo il numero di variabili. Più circuiti elementari sono interconnessi fra loro per calcolare la funzione finale.
![[Pasted image 20241021152258.png]]
- Vettore **y** rappresenta le informazioni di stato trasferite da un modulo al successivo. L'ultimo modulo può esporre parte di questa informazione all'esterno, ad esempio per notificare dettagli circa il risultato finale dell'operazione.
- Vettore **x** rappresenta il dato in input, decomposto tra i vari moduli.
- Vettore **z** rappresenta l'output, calcolato iteramente dai moduli 
#### Comparatori:
I comparatori sono dei circuiti che confrontano il valore di due numeri, A e B, rappresentati in formato binario.
Il risultato di un comparatore determina se A=B, il confronto può essere effettuato su ciascuna coppia di bit in moduli separati, tuttavia è necessario propagare il risultato della comparazione dai moduli precedenti:
![[Pasted image 20241021161118.png]]
##### Esempio:
Considero due numeri 10110 e 10010, il comparatore agirà calcolando a due a due le cifre partendo da destra:
				!	 $\longleftarrow$	     $\longleftarrow$ 

| Bit 5 | Bit 4 | Bit 3 | Bit 2 | Bit 1 |
| ----- | ----- | ----- | ----- | ----- |
| 1     | 0     | 1     | 1     | 0     |
| 1     | 0     | 0     | 1     | 0     |
Il controllo inizia e appena trova un bit diverso, propaga il segnale ai moduli successivi, indipendentemente dall'uguaglianza dei singoli termini.
##### Esempio con le tabelle di verità:
![[Pasted image 20241021163449.png]]
Ed i mintermini della funzione sono soltanto due:$$z_{i}=z_{i-1}\bar{a}~\bar{ b}+z_{i-1}*a*b=z_{i-1}(a\odot b)$$
e la sua rappresentazione circuitale è:![[Pasted image 20241021163840.png]]
##### Problema delle reti iterative:
Analizzando la struttura del comparatore realizzato è evidente quale sia il limite di queste reti:![[Pasted image 20241021164044.png]]
Il tempo di calcolo della funzione può diventare inaccettabile se il numero di bit da processare è troppo elevato.
##### Comparatore veloce:
I bit dei numeri da confrontare vengono divisi in h blocchi di k bit. Ciascun blocco viene confrontato da un comparatore iterativo dedicato.
Le uscite dei vari comparatori vengono processate da un comparatore aggiuntivo.
![[Pasted image 20241021164246.png]]
###### Comparatore veloce ad albero:
Poiché il numero di bit è tipicamente una potenza di due, si possono organizzare i comparatori in una struttura ad albero a più livelli.
Per esempio, per interi a 16 bit:
![[Pasted image 20241021165712.png]]
##### Half adder:
Il circuito più semplice per effettuare una somma di operandi ad un solo bit deve calcolare il valore della somma e il valore del riporto:$$s=a⊕b,~~~c=a*b$$
![[Pasted image 20241021165901.png]]
##### Full adder:
Per calcolare la somma di un inter a n bit, possiamo realizzare una rete iterativa composta da n sommatori, dove il circuito del modulo va modificato per considerare anche il riporto proveniente dai moduli precedenti.
![[Pasted image 20241021170130.png]]
![[Pasted image 20241021170145.png]]
![[Pasted image 20241021170219.png]]
