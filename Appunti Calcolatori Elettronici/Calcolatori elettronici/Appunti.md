
# Capitolo 2 Rappresentazioni:
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
![[Pasted image 20240927161949 1.png]]

- Se parto da una base 2 ed arrivo ad una base 16, varranno le seguente corrispondenze, o viceversa:
![[Pasted image 20240927163327 1.png]] 
### Intervalli rappresentabili con la notazione posizionale
Dato un numero k di cifre di un alfabeto associato al sistema numerico in base b, è possibile rappresentare tutti i valori nell'intervallo: 
$${[0, b^k-1]}$$
 allo stesso modo per rappresentare n elementi, sono necessarie un numero di cifre pari a:
$$k=log_{b}(n)$$
è importante quindi conoscere gli intervalli rappresentabili perché le codifiche funzionano su insiemi finiti, questo perché un computer è in grado di interpretare informazioni a dimensione prefissata.

### Operazioni aritmetiche in altre basi:
Sono simili a quelle in base 10, ma introduciamo i concetti di riporto e prestiti:
![[Pasted image 20240927171217 1.png]]
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
![[Pasted image 20240927174102 1.png]]
Attraverso questa operazione però otterrò due zeri:
![[Pasted image 20240927174149 1.png]]
E' una rappresentazione inefficiente però, quindi non sarà quella utilizzata.
#### Complemento a uno:
Questo metodo consiste nell'invertire tutti i bit.
![[Pasted image 20240927175528 1.png]]
Il nome deriva dal fatto che sommando ogni valore otterremo una sequenza di tutti 1. Rimangono però due zeri.
Con n cifre, si rappresentano i numeri nell'intervallo:
$$[-(2^{n-1}-1), 2^{n-1}-1]$$
Ciò significa che il complemento a 1 di x è quel valore x' tale che se sommato a x mi restituisce una sequenza n di 1, ovvero:
$$x+x'=2^n-1$$
Questo tipo di rappresentazione, però, crea problemi quando svolgo operazioni di somma fra numeri negativi:
![[Pasted image 20240927180033 1.png]]
- Il risultato è sbagliato
- Il fenomeno si chiama end-around carry (riporto di fine giro)
- Per ottenere il risultato corretto, è necessario sommare al risultato ottenuto anche il bit di riporto.

#### Complemento a due:
La rappresentazione più efficiente è data dal complemento a 2, una rappresentazione ad n cifre, il complemento a due di un numero x è definita come il complemento a 2^n
$$2^n-x$$
Per calcolare il complemento a due di x possiamo ragionare sulla proprietà fondamentale del complemento a 1. 
([[Appunti#Complemento a uno]])
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
![[Pasted image 20240927183515 1.png]] 
Notiamo che vi è un solo zero, ma si può codificare -8 e non 8 (chiamato per questo numero strano)

Con n cifre, si rappresentano i numeri nell'intervallo:
$$[-2^{n-1}, 2^{n-1}-1]$$
##### Somma e Differenza in complemento a 2:
Può essere svolta ignorando il segno:
![[Pasted image 20240927184618 1.png]]
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
![[Pasted image 20241012170320 1.png]]

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
- lunghezza
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
![[Pasted image 20241014113848 1.png]]
Un numero reale (float) ha dimensione 32 bit così utilizzati:
- segno s: 1 bit
- esponente e: 8 bit
- mantissa m: 23 bit
#### Caratteristiche:
L'esponente decimale E è rappresentato in eccesso a 127:
$$e= E +127$$
La mantissa rappresenta il valore binario $$(1.m)_2$$
- dove la parte intera viene omessa nella rappresentazione
Il valore decimale può essere calcolato come $$(-1)^{s}*2^{è-127}*(1.m)$$ questa viene chiamata rappresentazione _normalizzata_
##### Tipologie di numero:
- numeri normalizzati: sono la maggior parte dei numeri rappresentabili dallo standard
- numeri denormalizzati: valori molto prossimi allo zero. Generano alcuni problemi nella gestione degli errori di arrotondamento.
	- la parte intera omessa non è 1, bensì 0
- zeri: è possibile rappresentare ±0
	- la maggior parte delle operazioni ignora il segno, ma dividere per ±0 può dare come risultato $\pm\infty$ 
- infiniti: $\pm\infty$. Sono il risultato di una divisione per zero, o di un'operazione che genera un _overflow_
- NaNs(not a number): sono il risultato di un'operazione che non ha significato: $(\infty - \infty, \frac{0}{0},\sqrt{-1},...)$ 

Attraverso questa tabella possiamo individuare il  tipo di valore corrispondente grazie al valore della mantissa e dell'esponente:
![[Pasted image 20241014132810 1.png]]
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
![[Pasted image 20241014155605 1.png]]
La presenza di numeri massimi e minimi rappresentabili, crea dei buchi nella linea dei numeri rappresentabili.
Altri buchi piccoli si creano tra la rappresentazione normalizzata quella denormalizzata.
Se un numero non è rappresentabile in alcun modo:
- **Overflow**:numero troppo grande o troppo piccolo (negativo)
- **Underflow**: arrotondamento allo zero
![[Pasted image 20241014163515 1.png]]
La divisione in mantissa/esponente fa nascere un ulteriore peculiarità del formato
quando siamo vicini allo zero, l'esponente è piccolo, quindi un incremento nella mantissa di 1 provoca un "salto" piccolo.
Viceversa, per numeri grandi, questo numero sarà migliore.
La densità dei numeri in virgola mobile non è quindi costante.
- con 32 bit, circa la metà dei numeri rappresentabili sono compresi tra -1 e 1
- vi è la stessa quantità di numeri rappresentabili tra 65536 e 131072
![[Pasted image 20241014173928 1.png]]
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
![[Pasted image 20241014174950 1.png]]
### Altri tipi di codifica:
Volendo se definiamo un alfabeto e un tipo di codifica, possiamo far corrispondere questo linguaggio a quello che vogliamo.
#### Esempio:
![[Pasted image 20241014192459 1.png]]
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
- l'ottavo bit era utilizzato come codice di controllo di errore![[Pasted image 20240930151055 1.png]]
###### Esteso:
- 8 bit
- 256 caratteri rappresentabili (compresi i codici di controllo)
 
##### Codice Binary Coded Decimal (BCD), (Irridondante)
- è un codice irridondante per rappresentare le 10 cifre decimali usando quattro cifre binarie
- ciascuna cifra è codificata indipendentemente
- Tipicamente, due cifre sono memorizzate in un singolo bye (packed BCD)
- Di facile interpretazione per gli umani, comodo per consentire alle macchine una conversione per la stampa
- Molti bit sono sprecati (circa 1/6) rispetto alla rappresentazione binaria
![[Pasted image 20240930151346 1.png]]
##### Codice di Gray (Irridondante):
- La rappresentazione è tale per cui tra due numeri adiacenti cambia una sola cifra binaria.
- è un codice particolarmente utile per i casi di contatori elettronici, per evitare fenomeni transitori. Questo concetto è spiegabile attraverso un esempio, consideriamo la transizione: $(3_{10}\to (4_{10})) \equiv (011)_{2}\to(100)_2$ 
	- Possono verificarsi molte sequenze intermedie, ad esempio:$$(001)_{2}\to(010)_{2}\to(000)_{2}\to(100)_{2}$$Ed il sistema non può distinguere tra configurazioni transitorie e corrette.
	![[Pasted image 20240930151419 1.png]]
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
![[Pasted image 20240930152540 1.png]]
Dove con la linea rossa indico la causa dell'errore
##### Come riveliamo l'errore?
Per capirlo, vediamo un esempio.
Ho questi due codici:
![[Pasted image 20240930152700 1.png]]

Il modo in cui utilizziamo lo spazio disponibile per rappresentare gli elementi può consentire di rivelare la presenza di errori:
![[Pasted image 20240930152759 1.png]]
##### Codice di parità o disparità (Ridondante):
Si tratta di un codice ridondante con h = 2 e si ottiene aggiungendo una cifra di parità ad un codice irridondante. Vi sono due tipologie: 
###### Parità:
vale 1 se il numero di 1 nella codifica irridondante è dispari, sennò 0
###### Disparità:
vale 1 se il numero di 1 nella codifica è pari, sennò 0
###### Tabella riassuntiva: 
![[Pasted image 20240930182922 1.png]]
###### Come funziona?
Supponiamo di usare un codice di _Parità_, si può determinare se c'è stato un **singolo** errore di trasmissione, vedremo perché è importante "singolo":
- se la parità varrà 0, allora non ci sono stati errori di trasmissione.
![[Pasted image 20241015000730 1.png]]
[Per capire meglio il funzionamento](https://www.edscuola.it/archivio/software/bit/bitfaq58.html) 

###### Esempio:
Voglio trasmettere 101.
Il generatore di parità aggiungerà 0 alla fine, trasmettendo 1010.
Vediamo diversi casi:
![[Pasted image 20241015001244 1.png]]
1) Se ricevo lo stesso bit, non avrò nessun segnale di errore perché la parità continua a valere 0, visto che la somma degli 1 è pari.
2) Nel secondo caso ricevo un valore con un valore diverso, riceverò un segnale di errore poiché  la parità è diversa da 0, visto che la somma degli 1 è dispari
3) Infine se gli elementi ad essere cambiati sono due (più in generale a coppie) la parità tornerà ad essere 0, quindi non riceverò alcun messaggio di errore,  questo è **totalmente sbagliato**. 
##### Codice di Hamming:
è un metodo per la costruzione di codici a distanza  $h \ge 3$. Data una parole di codice di $m = n+k~cifre, con~n \le 2^k - k-1$, avremo:
- i bit in posizione $2^i$ sono bit di parità
- ciascun bit di parità controlla la correttezza dei bit di informazione la cui posizione, espressa in binario, ha un 1 nella potenza di 2 corrispondente
![[Pasted image 20241015104730 1.png]]
##### Esempio:
![[Pasted image 20241015105120 1.png]]
###### 1 caso:
![[Pasted image 20241015105157 1.png]]
###### 2 Caso:
![[Pasted image 20241015105332 1.png]]

# Capitolo 3 Algebra Booleana:
## Cos'è?
è un tipo di algebra definita dal matematico George Boole e fu inizialmente proposta nel tentativo di verificare la verità o la falsità di affermazioni in linguaggio naturale, partendo da alcune verità di base.
Nel 1936 venne utilizzata da Shannon per studiare i circuiti basati su relé. Questo poiché l'algebra di Boole si basa sui concetti di vero/falso, quella di relé su aperto/chiuso
Possiamo dunque dire che gli elementi fondamentali dei circuiti elettronici, al giusto livello di astrazione, rispettano ancora le regole dell'algebra booleana.

## Proprietà, assiomi ed elementi introduttivi: 
### Variabili:
- Una variabile booleana (o di commutazione) è una quantità algebrica x definita su un insieme S= {0, 1}, ossia che può assumere solo due valori.
### Funzioni di commutazione:
- Una funzione di commutazione di una variabile booleana è definita come la proiezione di {0,1} su {0,1}
	- $f:[{0,1}]\to [{0,1}]$
	- $y = f(x)$
- Una funzione di commutazione di n variabili booleane è una funzione il cui dominio è dato da tutte le n-uple $(x_{1}, x_{2},...,x_{n})~in~[0,1]^{n}$ ed il codominio è $[0,1]$:
	- $f:[0,1]^{n}\to [0,1]$
	- $y=f(x_{1},x_{2},...,x_{n})$
### Operatori ed Assiomi fondamentali:
#### Quali sono?
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
---
### Leggi e proprietà:
#### Legge di dualità:
##### Teorema:
Ogni identità booleana rimane invariata scambiando $+~con~*,e~0~con~1$
##### Esempi:
$Se~0+1 = 1,ponendo~1\to\alpha~e~0\to\beta~otteniamo~\alpha+\beta=\alpha$
$Se~0+1 = 1,ponendo~1\to0~e~0\to1~otteniamo~0+1=0$
$Se~0*1 = 0,ponendo~+\to*~e~*\to+~otteniamo~1*0=0$

---
#### Proprietà di idempotenza:
Nell'algebra booleana binaria vale $a+a=a~e~a*a=a$
##### Dimostrazione:
- $a= a+ 0$
-  $a= a+ a*\bar{a}$
- $a=(a+a)*(a+\bar{a})$
- $a=a+a$
- Di conseguenza, per la legge di dualità vale anche: $a=a*a$

---
#### Annichilatori funzionali:
Nell'algebra booleana binaria vale $a+1=1~e~a*0=0$
##### Dimostrazione:
La dimostrazione si basa sulla [[#Proprietà di idempotenza]]:
- $a+1=a+a+\bar{a}$
- $a+1=a+\bar{a}$
- $a+1=1$
- Di conseguenza, per la legge di dualità vale anche: $a*0=0$
---
#### Legge dell'assorbimento:
Nell'algebra booleana binaria vale $a+a*b=a~e~a*(a+b)=a$
##### Dimostrazione:
- $a+a*b=a*1+a*b$
- $a+a*b=a*(1+b)$
- $a+a*b=a*1$
- $a+a*b=a$
- Di conseguenza, per la legge di dualità vale anche: $a+a*b=a$
---
#### Teorema di De Morgan:
Il teorema di De Morgan è un teorema importante perché permette di esprimere gli operatori + e * in funzione degli altri due operatori fondamentali$$\overline {a+b}= \bar a* \bar b~~~~~~~~~~\overline{a*b}=\bar a+\bar b$$
##### Dimostrazione:
Per dimostrare il teorema è sufficiente verificare che $\bar a*\bar b$ è il complemento di $a+b$
- $(a+b)+(\bar a*\bar b)=(a+b+\bar a)*(a+b+\bar b)$
- $(a+b)*(\bar a+\bar b)=(1+b)*(1+a)$
- $(a+b)*(\bar a+\bar b)=1*1=1$
- La seconda si ottiene per la legge di dualità
---
### Funzioni di commutazione:
#### Cosa sono?
Riprendiamo il discorso iniziato in [[#Variabili ed elementi di commutazione]] e vediamo come rappresentare le funzioni di commutazione attraverso gli operatori appena citati:
- Una funzione di commutazione di n variabili $y=f(x_{1},x_{2},...,x_{n})$ e il codominio è l'insieme $[0,1]$
- $f:[0,1]^{n}\to [0,1]$
Ci sono diversi modi per esprimere una funzione di commutazione:
- forma tabellare (tabelle di verità)
- forme canoniche 
- forme decimali
#### Tabelle di verità:
##### Cosa sono?
Crea una relazione fra le variabili di input ed il valore di output della funzione. In queste tabelle si utilizza speso in maniera interscambiabile il vettore **x**=$[x_{1},x_{2},..,x_n]$ e le variabili che lo compongono. 
Una tabella di verità di una funzione di n variabili è costituita da $2^{n}$ righe:![[Pasted image 20241015175418 1.png]]
##### Esempi:
Si possono vedere come funzioni di commutazione anche gli operatori fondamentali, attraverso 1 o 2 variabili di commutazione:![[Pasted image 20241015175353 1.png]]

---
#### Operatori derivati:
##### Introduzione:
Sulla base degli [[#Operatori ed Assiomi fondamentali]] è possibile definire i seguenti operatori derivati:
1) OR esclusivo (XOR), indicato con il simbolo $\bigoplus$ 
 2) Not AND, indicato con |.
 3) NOR, indicato con $\downarrow$ 
 4) NOR esclusivo (XNOR), indicato con il simbolo $\bigodot$
 ---
##### OR esclusivo (XOR)
Esso è equivalente alla somma modulo 2 ed è definito così:$$a~\oplus~b = \bar a b+a\bar b $$
Viene utilizzato per verificare la disuguaglianza tra due variabili.
 ![[Pasted image 20241016115031 1.png]]
###### Proprietà Principali:
- $a\oplus b = b\oplus a~(proprietà~commutativa)$
- $a\oplus(b\oplus c)=(a\oplus b)\oplus c~(proprietà~associativa)$
- $a\oplus a=0$
- $a\oplus \bar a = 1$
- $a\oplus 1=\bar a$
- $\bar a \oplus b = a \oplus \bar b= \overline{a\oplus b}$
---
##### Not AND (NAND):
Definito così:$$a|b=\overline{a * b}=\bar a +\bar b$$
![[Pasted image 20241016115216 1.png]]
###### Proprietà:
- $a|b=b|a~(Proprietà~commutativa)$
- $a|1=\bar a$
- $a|0=1$
- $a|\bar a = 1$
- $a|(b|c)\neq (a|b)|c~(l'operatore~non~è~associativo)$    
---
##### NOR
Si tratta del duale dell'operatore NAND ed è definito cosi:$$a\downarrow b = \overline{a+b}=\bar a *\bar b$$ ![[Pasted image 20241016121655 1.png]]
###### Proprietà:
- $a\downarrow b = b\downarrow a~(proprietà~commutativa)$
- $a\downarrow 1 = 0$
- $a\downarrow 0 = \bar a$
- $a\downarrow \bar a = 0$
- $a\downarrow(b\downarrow c)\neq (a\downarrow b) \downarrow c~(l'operatore~non~è~associativo)$
---
##### Nor esclusivo (XNOR)
Definito come segue:$$a\odot b=(\bar a+b)*(a+\bar b)$$ ![[Pasted image 20241016121907 1.png]]
###### Proprietà:
- $a\odot b = b\odot a~(proprietà~commutativa)$
- $a\odot(b\odot c)=(a\odot b)\odot c~(proprietà~associativa)$
- $a\odot 1= a$
- $a \odot \bar a =0$
- $a \odot 0 =\bar a$
---
#### Teorema di Shannon:
##### Enunciato
Il teorema afferma che una qualsiasi funzione $y= f(x_{1}, x_{2},...,x_{n})$ può essere rappresentata in una delle due seguenti forme duali:
$f(x_{1}, x_{2},...,x_{n})=x_{1}*f(1,x_{2},...,x_n)+\overline{x_1}*f(0,x_2,...,x_n)$ 
$f(x_{1}, x_{2},...,x_{n})=(x_1+f(0,x_{2},..,x_{2}))*(\overline {x_1}+f(1,x_2,..,x_n))$  
I termini che moltiplicano o si sommano a $x_{1}$ sono chiamati i residui della funzione. Ciò è vero nel caso di variabili indipendenti.

---
##### Esempio di applicazioni:
Questo teorema può essere applicato iterativamente a tutte le variabili della funzione.
Se svolgo questo processo otterrò:$$f(x_{1},...,x_{n})=\overline{x_{1}}*\overline {x_{2}}*...*\overline {x_{n}}*f(0,0,...,0)+ {x_{1}}*\overline {x_{2}}*...*\overline {x_{n}}*f(1,0,...,0)+\\ $$$$+\overline {x_{1}}*{x_{2}}*...*\overline {x_{n}}*f(0,1,...,0)+...+{x_{1}}*{x_{2}}*...*\overline {x_{n}}*f(1,1,...,0)+{x_{1}}*{x_{2}}*...*{x_{n}}*f(1,1,...,1)$$ Che può essere riassunto, per ogni termine cosi:$$x_1^{\alpha_1}x_2^{\alpha_2}...x_n^{\alpha_n}*f(\alpha_1,\alpha_2,...,\alpha_2)$$
con $\alpha_i=[0,1]~e~x_{i}^{\alpha_{i}}=x_{i}~se~\alpha_i=1,x_{i}^{\alpha_{i}}=\overline{x_i}~se~\alpha_{i}=0$

---
#### Forme canoniche:
##### Cosa sono?
Sono rappresentazioni uniformi utilizzate per descrivere una funzione di commutazione. Qualsiasi funzione può essere trasformata in forma canonica:
- Tabelle di verità e utilizzare la tecnica dei mintermini o maxtermini
- Si possono effettuare trasformazioni analitiche: se una variabile $x_i$ non è presente, si può moltiplicare per $(x_{i}+\overline{x_i})$ 
##### Prima tecnica: Min e Max termini
###### Prima forma canonica: _somma di prodotti_
(o forma canonica disgiuntiva):$$f(x_{1},x_2,...,x_n)=\sum_{k=0}^{2^n-1}m_kf(k)$$
- il termine $m_k$ viene chiamato mintermine ed è nella forma $x_1^{\alpha_1}x_2^{\alpha_2}...x_n^{\alpha_n}$
- In ciascun mintermine, le variabili compaiono una ed una sola volta in forma diretta o negata.
###### Seconda forma canonica: _prodotti di somme_
Utilizzando il teorema di De Morgan possiamo trasformare la forma canonica precedente in :$$\overline{f(x_{1},x_2,...,x_n)}=\sum_{k=0}^{2^{n}-1} m_{k}\overline{f(k)}$$Che possiamo scrivere come:$${f(x_{1},x_2,...,x_n)}=\overline{\sum_{k=0}^{2^{n}-1} m_{k}\overline{f(k)}}=\prod_{k=0}^{2^{n}-1} \overline{m_{k}\overline{f(x)}}=\prod_{k=0}^{2^{n}-1} (M_{k}+f(k))$$
Dove il termine $M_k$ viene chiamato maxtermine ed è nella forma:
$M_k=$ $\sum_{i=0}^{n-1}x_i^{a_{i}}$ con $\alpha_{i}=[0,1]$ e $~x_{i}^{\alpha_{i}}=x_{i}~se~\alpha_i=0,x_{i}^{\alpha_{i}}=\overline{x_i}~se~\alpha_{i}=1$
###### Esempio:
Consideriamo la seguente funzione di commutazione definita mediante tabella di verità:
![[Pasted image 20241016194746 1.png]]
- I **mintermini** corrispondono alle configurazioni k = 0,4,5,7
- I **maxtermini** corrispondono alle configurazioni k= 1,2,3,6
A questo punto, dai mintermini possiamo definire la seguente rappresentazione in somme di prodotto:$$f(x_1,x_2,x_3)=\overline{x_1}~\overline{x_2}~\overline{x_3}+x_1~\overline{x_2}~\overline{x_3}+x_1~\overline{x_2}~{x_3}+x_1~{x_2}~{x_3}$$
![[Pasted image 20241016195321 1.png]]


Invece dai maxtermini possiamo definire la seguente rappresentazione in somme di prodotti:$$f(x_{1}, x_{2},x_{3})=(x_{1}+x_{2}+\overline{x_3})(x_{1}+ \overline{x_2}+x_{3})(x_{1}+\overline{x_{2}}+\overline{x_3})(\overline{x_{1}}+\overline{x_{2}}+x_{3})$$ ![[Pasted image 20241017094726 1.png]]

---
###### Forma decimale:
Si indica l'interpretazione decimale delle variabili booleane associate a mintermini e maxtermini:$$f(k)=\sum\limits(0,4,5,7)=\prod(1,2,3,6)$$![[Pasted image 20241017105808 1.png]]

---
##### Seconda tecnica: Trasformazioni Analitiche:
###### In cosa consiste?
Per capire meglio, utilizziamo il seguente esempio:$$x_{1}x_{3}+\overline{x_{1}}(x_{2}+\overline{x_{3}})$$ questa funzione può essere trasformata come segue:$$x_{1}x_{3}+\overline{x_{1}}(x_{2}+\overline{x_{3}})=x_{1}x_{3}(x_{2}+\overline{x_{2}})+\overline{x_{1}}x_{2}(x_{3}+\overline{x_{3}})+\overline{x_{1}}\overline{x_{3}}(x_{2}+\overline{x_{2}})$$Risolvendo la moltiplicazione otterremo:$$x_{1}x_{2}x_{3}+x_{1}\overline{x_{2}}x_{3}+\overline{x_{1}}x_{2}x_{3}+2(\overline{x_{1}}x_{2}\overline{x_{3}})+\overline{x_{1}x_{2}x_{3}}$$

---
#### Forme semplificate:
##### Cosa sono?
Le forme canoniche non sono necessariamente le forme minime per rappresentare una funzione booleana.
Identificare una forma minima è importante poiché permetterà di realizzare circuiti più compatti ed il processo può essere svolto attraverso due metodi:
- analitici
- algoritmici
##### Metodi analitici:
I metodi analitici richiedono di applicare le proprietà dell'algebra e teoremi visti fin ora.
Non esiste un tipo di risoluzione corretto per ogni forma.
###### Esempio:
![[Pasted image 20241017110240 1.png]]![[Pasted image 20241017110409 1.png]]

---
#### Mappe di Karnaugh:
##### Cosa sono?
Le mappe di Karnaugh sono una rappresentazione differente delle tabelle di verità.
##### Caratteristiche:
- Le variabili vengono organizzate in tabelle quadrate o rettangolari, a seconda del loro numero
- I valori che possono assumere le variabili vengono ordinati secondo un Codice di Gray (distanza di Hamming=1)
- In questo modo, spostandosi da una cella all'altra, si causa il cambiamento del valore di _una sola variabile_
- Poiché $(a+\overline{a})=1$ è possibile eliminare (semplificare) una variabile se la funzione assume lo stesso valore in gruppi di celle adiacenti
- Esso è un metodo facile per gli umani (max 6 variabili), di difficile realizzazione automatizzata per un algoritmo
##### Mappe di Karnaugh (funzioni a 2,3,4 variabili):
![[Pasted image 20241017154632 1.png]]
E' importante notare che l'uso del codice di Gray garantisce che anche le celle agli estremi siano _adiacenti_.
###### Funzioni a 4 variabili:
Studiando la funzione a 4 variabili osserviamo che le adiacenze ai bordi e agli angoli sono valide poiché la mappa è lo sviluppo di un solido multidimensionale.
Ad esempio, per 4 variabili la mappa è lo sviluppo di un _toro_:
![[Pasted image 20241017160109 1.png]]
##### Mappe di Karnaugh (funzioni a 5 variabili):
![[Pasted image 20241017160244 1.png]]
L'adiacenza è anche tra le due tabelle, come se queste fossero sovrapposte.
##### Mappe di Karnaugh (funzioni a 6 variabili):
Come nel caso di cinque variabili, anche qui le adiacenze valgono per tabelle sovrapposte:
![[Pasted image 20241017160509 1.png]]

##### Mappe di Karnaugh e tabelle di verità:
Per trasforma una tabella di verità in una mappa di Karnaugh è sufficiente riempire le celle della mappa con il valore della funzione in corrispondenza delle variabili di ingresso:
![[Pasted image 20241017161537 1.png]]
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
![[Pasted image 20241017164132 1.png]]
a questo punto, identifichiamo gli **implicanti primi** selezionando degli insiemi di dimensione 1,2,4,... fino a coprire tutti gli 1 almeno una volta(semplificazione con mintermini).
A questo punto, identifichiamo gli implicanti primi selezionando degli insiemi di dimensione 1,2,4,.. fino a coprire tutti gli 1 almeno una volta:
![[Pasted image 20241018092648 1.png]]
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
![[Pasted image 20241018182259 1.png]]
![[Pasted image 20241018182314 1.png]]
###### Esempi di adiacenze: funzioni di 4 variabili
![[Pasted image 20241018182405 1.png]]
###### Esempi di adiacenze: funzioni di 5 variabili
![[Pasted image 20241018182445 1.png]]
###### Don't Care Condition:
A volte, una funzione è parzialmente specificata.
In questi casi il valore dell'uscita non è definito per tutte le configurazioni delle variabili di ingresso:
- variabili dipendenti
- Configurazioni non di interesse.
In questi casi, i mintermini/maxtermini vengono associati (nella notazione decimale) a un insieme $\sum\limits_\frac{0}{1}$ che rappresenta il fatto che non è noto (o di interesse) che il valore della funzione sia 0 o 1.
Nel caso delle mappe di Karnaugh, si indica tale condizione con un trattino (-) e si più comodo per la minimizzazione.
![[Pasted image 20241018183317 1.png]]
###### Esempio di funzioni con 6 variabili:
L'insieme azzurro costruisce un insieme di copertura che racchiude 4 termini, permettendo una riduzione di due variabili.
Se avessimo considerato il solo mintermine $\bar{a}bcd\bar{e}\bar{f}$ l'espressione sarebbe stata più complessa.
![[Pasted image 20241018183609 1.png]]
##### Operatori Universali:
###### Perché sono importanti?
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
# Capitolo 4: Circuiti combinatori:
## Circuiti logici (o di commutazione):
### Visita generale:
#### Cosa sono?
Sono reti di componenti che accettano variabili booleane in input e le restituiscono in output. Per capirle meglio è utile affidarsi all'algebra booleana. Gli operatori booleani sono implementati in hardware da circuiti chiamate porte logiche che vengono astratte con i seguenti simboli:
![[Pasted image 20241019134140 1.png]]
#### Negazioni e porte a più ingressi:
Circuitalmente è più efficiente inserire il calcolo della negazione degli input direttamente nelle porte logiche:
![[Pasted image 20241019224740 1.png]]
Inoltre è possibile costruire porte a più ingrassi, dipendentemente dalla tecnologia costruttiva:
![[Pasted image 20241019224829 1.png]]
La maggior parte degli operatori è associativo e commutativo
##### NAND a più ingressi:
Abbiamo visto che l'operatore NAND non è associativo,([[#Not AND (NAND)]]), quindi 
$$x_{1}|(x_{2}|x_{3})=\overline{x_{1}}+x_{2}x_{3}\ne x_{1}x_2+\overline {x_3}=(x_{1}|x_{2})|x_{3}$$
ciò significa che i seguenti cicli non sono equivalenti:
![[Pasted image 20241020120231 1.png]]
E' però possibile costruire la seguente porta logica:
![[Pasted image 20241020120308 1.png]]
ed il suo significato è dato da $x_{1}|x_{2}|x_{3}=\overline{x_{1}x_{2}x_{3}}$ costruendo quindi un operatore NAND associativo. 
Questo operatore calcolare una funzione differente dal NAND booleano.
##### NOR a più ingressi:
vale lo stesso ragionamento per l'operatore NOR, infatti:![[Pasted image 20241020125034 1.png]]
#### Porte logiche a diodi:
##### Tipo di porta AND:
E' possibile costruire un selettore di velocità secondo il circuito in figura e poichè operiamo con circuiti di commutazione, assumiamo che siano possibili solo due livelli di tensione:$V_{L}~e~V_{H}$.

---
**Introduzione**
Il circuito rappresentato funziona attraverso le caratteristiche dei singoli componenti:![[Pasted image 20241020190238 1.png]]
- diodi: sono degli interruttori che funzionano come dei conduttori solo se il lato che è collegato a $V_{1}~o~a~V_{2}$ 
- resistenza: collega l'uscita $V_{out}$ alla tensione di alimentazione $V_{CC}$ 
---
**Funzionamento:**
Sapendo che i diodi funzionano in un modo specifico, possiamo analizzare le condizioni di tensione:
- Se $V_{1}$ è positivo, ci sarà un blocco di tensione in posizione del diodo corrispondente, condurrà la corrente a $V_{2}$.
	- Se $V_{2}$ è positivo, allora ci sarà un blocco anche in corrispondenza del secondo diodo, dunque la tensione in $V_{out}$ sarà alta.
	- Se $V_{2}$ è negativo, non ci sarà blocco e la corrente passerà fino ad arrivare in $V_{2}$, quindi la tensione in $V_{out}$ sarà bassa.
- se $V_{1}$ è negativo, il diodo non verrà attivato, quindi:
	- Se $V_{2}$ è positivo, ci sarà un blocco di tensione in posizione del diodo corrispondente, condurrà la corrente a $V_{1}$, tenendo $V_{out}$ a $V_L$  
	- Se $V_{2}$ è negativo, non ci sarà blocco e la corrente passerà fino ad arrivare in $V_{1}$, quindi la tensione in $V_{out}$ sarà bassa
---
**Conclusioni:**
Questo circuito si comporta come una porta AND, poiché il caso di tensione alta si può verificare in $V_{2}$ SE E SOLO SE le altre due sono alte.
Se anche una delle due è bassa, allora il risultato sarà basso. In termini booleani, $V_{out}$ sarà 1 se sia $V_{1}$, sia $V_{2}$ sono 1.

---
##### Tipo di porta OR:
Immaginiamo un circuito ideale di questo tipo, per implementare una porta logica di tipo OR:
![[Pasted image 20241021122123 1.png]]
Implementa la porta OR poiché la tensione in $V_{out}$ sia alta, basta che si verifichi che o $V_{1}$ sia alta o $V_{2}$ lo sia, come anche spiegato dalla tabella. In termini booleani $V_{out}$ è 1 se o$V_{1}$ è 1 o $V_{2}$  lo è

---
#### Problemi delle porte a diodi:
Le porte basate su diodi provocano un'attenuazione del segnale. Collegando in cascata più porte, il segnale subirà un'attenuazione progressiva che può distruggere la differenza tra $V_{L}$ e $V_{H}$. Questo fenomeno ha portato al progressivo abbandono di queste porte negli anni '60 a favore delle porte a transistor.

---
##### Logica TTL:
La Transistor/Transistor Logic si basa sull'uso di alcuni transistor per la realizzazione  della funzione di commutazione e di alcuni transistor per l'amplificazione del segnale, per eliminare il fenomeno dell'attenuazione.
Si basano sul concetto di resistenze _pull up_.
###### Esempio (Inverter TTL):
Implementa una porta NOT:
![[Pasted image 20241021123942 1.png]]

---
##### Logica CMOS:
La logica cMOS (Complementary Metal-Oxide-Semiconductor) si basa sull'uso di transistor pMOS e nMOS nella stessa rete, rispettivamente la prima si comporta da _pull up_, mentre la seconda implementa la parte di _pull down_ il vantaggio è che l'area utilizzata è estremamente piccola.
###### Esempio: (inverter CMOS):
![[Pasted image 20241021131220 1.png]]

**Struttura del circuito**
1. **Transistori utilizzati:**
    
    - Q1: È un **transistor PMOS** (complementare al NMOS).
    - Q2: È un **transistor NMOS**.
    - Entrambi i transistor hanno il gate connesso all'ingresso $V_{in}.$
2. **Connessioni:**
    - Il PMOS (Q1) è connesso tra VCC (alimentazione positiva) e $V_{out}$
    - L'NMOS (Q2) è connesso tra $V_{out}$ e GND (massa, tensione zero).
    - Il **gate di entrambi i transistor** è controllato dal segnale di ingresso VinV_{in}.
3. **Comportamento complementare:**    
    - PMOS e NMOS lavorano in modo **complementare**:
        - Quando il PMOS è acceso (conduce), l'NMOS è spento (non conduce), e viceversa.

---

**Funzionamento del circuito**
Il comportamento del circuito dipende dal valore del segnale $V_{in}:$

1) Caso 1: $V_{in} = 0$ (basso, $V_L$)
	1. Il PMOS (Q1):
    - Il gate del PMOS è a 00, quindi $Q_1$ è acceso e conduce.
    - Ciò significa che V_{out} viene collegato a VCC (tensione alta, $V_H$).
	1. L'NMOS (Q2):
    
    - Il gate del NMOS è a 00, quindi Q2 è spento e non conduce.
    - Non c'è connessione tra $V_{out}$ e GND.

**Risultato:** $V_{out}$ = VCC (alto, $V_H$).

---

**Caso 2: $Vin=VCC$ (alto, $V_H$)**

1. Il PMOS (Q11):
    
    - Il gate del PMOS è a VCC, quindi Q1 è spento e non conduce.
    - $V_{out}$ non è collegato a VCC.
2. L'NMOS (Q2):
    
    - Il gate del NMOS è a VCC, quindi Q2 è acceso e conduce.
    - Ciò significa che $V_{out}$ viene collegato a GND (tensione bassa, $V_L$).

**Risultato:** $V_{out} = 0$ (basso, $V_L$).

---

**Tabella della verità (comportamento dell'inverter)**

| $V_{in}$ | $V_{out}$ |
| -------- | --------- |
| $V_L$    | $V_H$     |
| $V_H$    | $V_L$     |

Il circuito **inverte** il segnale di ingresso: quando l'ingresso è alto, l'uscita è bassa, e viceversa.

---

**Vantaggi della logica CMOS**

1. **Basso consumo di potenza:**
    
    - Nella logica CMOS, la corrente scorre solo durante la **commutazione** tra stati (da basso ad alto o viceversa). In uno stato stabile (alto o basso), uno dei due transistor è spento, quindi il consumo è quasi nullo.
2. **Alta velocità:**
    
    - La logica CMOS può operare a frequenze molto elevate, rendendola ideale per circuiti digitali moderni come microprocessori e memorie.
3. **Alta densità di integrazione:**
    
    - I transistor CMOS possono essere miniaturizzati, consentendo l'integrazione di milioni (o miliardi) di transistor in un singolo chip.

---

**Logica CMOS in generale**

La **logica CMOS** sfrutta coppie di transistor PMOS e NMOS per implementare porte logiche:

- **PMOS**: Conduce quando il segnale al gate è basso (0).
- **NMOS**: Conduce quando il segnale al gate è alto (1).

Ogni porta logica CMOS (AND, OR, NAND, NOR, ecc.) è costruita combinando queste coppie in modo tale da ottenere il comportamento desiderato. Ad esempio:

- Una **NAND CMOS** utilizza una configurazione simile all'inverter, ma con più transistor PMOS e NMOS.

---

**Conclusione**

Questo circuito è un **inverter CMOS**, uno degli elementi più semplici della logica CMOS. Con un basso consumo energetico e un'elevata velocità, la logica CMOS è ampiamente utilizzata nella progettazione di circuiti integrati, dai microprocessori ai chip di memoria.

---
##### Porta NAND:
![[Pasted image 20241021133808 1.png]]

##### Porta NOR:
![[Pasted image 20241021133839 1.png]]

##### Riduzione del costo nelle operazioni AND/OR:
Immaginiamo di avere una funzione composta del tipo:
$$y=\sum\limits_{i=1}^{n}f_{i}~oppure~y=\prod_{i=1}^{n}f_{i}$$
Il circuito logico risultante è del tipo:
![[Pasted image 20241021134252 1.png]]
Vi sono però dei problemi, in particolare nei "puntini", infatti visto che il numero di ingressi cresce, aumenterà anche il numero di transistor, ma non è detto che si conoscono a priori il numero di input da considerare. Nel caso in cui gli input fossero in grande numero, il relativo accumulo di corrente potrebbe danneggiare i dispositivi elettronici.
#### Tecnologia in Open Collector:
##### Cosa sono?
Le porte Open collector utilizzano un transistor aggiuntivo in cui il collettore è connesso all'uscita della porta che funziona come un circuito aperto o come come circuito connesso a massa. 
Visto che si lavora in logica negata,viene utilizzata una resistenza di pull up che fa salire la tensione quando il circuito è chiuso:
![[Pasted image 20241021172205 1.png]]
Per indicare un operatore logico in open collector, viene utilizzato il simbolo della porta logica negata, marcato con "OC". 

---
##### Esempio: NAND

NAND in Open Collector, dove la resistenza di *pull up* diventa esterna alla porta:![[Pasted image 20241021175210 1.png]]
Le porte in open collector vengono usate quando c'è la necessità di collegare insieme più porte che possono fornire corrente in uscita contemporaneamente. 
L'accumulo di corrente in uscita, nel caso di un numero elevato di componenti, può produrre un danno fisico al circuito. Con l'uso dell'open collector la quantità di corrente che fluisce nel circolo non è più in funzione del numero di porte con l'uscita attiva:
![[Pasted image 20241021175530 1.png]]

---
##### Esempio pratico:
###### Introduzione:
Immaginiamo un **sistema di allarme** in una casa con più sensori (ad esempio, sensore di apertura porta, sensore di movimento, e sensore di fumo). 
Tutti questi sensori devono essere collegati a un'unica **centralina di controllo**. Se uno qualsiasi dei sensori rileva un problema, la centralina deve accendere una sirena.
###### Funzionamento del sistema
1. **Quando nessun sensore rileva problemi**:
    - Tutti i transistor dei sensori sono **spenti** (non conducono corrente).
    - La resistenza pull-up tira la linea comune a livello **alto** (5V).
    - La centralina interpreta il livello alto come "nessun problema".
2. **Quando un sensore rileva un problema**:
    
    - Il transistor del sensore interessato si **accende** (conduce corrente).
    - La linea comune viene abbassata a **0V** (livello basso).
    - La centralina interpreta il livello basso come "allarme" e attiva la sirena.
3. **Cosa succede se più sensori rilevano un problema contemporaneamente?**
    
    - Anche se più sensori accendono i loro transistor, la linea comune sarà comunque a livello **basso** (0V).
    - Non ci sono conflitti, perché tutti i transistor stanno semplicemente collegando la linea a terra.
---
###### Vantaggi:
- **Nessun conflitto tra sensori**: La linea comune è abbassata solo quando necessario, senza interferenze tra sensori.
- **Risparmio di cavi**: Una singola linea comune può essere condivisa da tutti i sensori, riducendo la complessità del cablaggio.
- **Semplicità di progettazione**: La resistenza pull-up garantisce un comportamento stabile e prevedibile.
- **Compatibilità con dispositivi diversi**: Sensori alimentati a tensioni diverse possono essere collegati allo stesso sistema usando pull-up adeguati.
---

#### Buffer Three-State :
##### Cos'è?
è un circuito che viene utilizzato per collegare tra loro parti di un circuito complesso. E' un circuito a tre canali:
- un segnale di ingresso
- un segnale di uscita
- un segnale di controllo

---
##### Comportamento:
Il segnale di uscita è uguale al segnale di ingresso se il segnale di controllo è attivo, altrimenti l'uscita è ad alta impedenza. Una porta ad alta impedenza, offre un'elevata resistenza al passaggio della corrente e quindi dei segnali elettrici.
Si comporta quindi da **interruttore**:![[Pasted image 20241021180854 1.png]]

---
##### La tabella di verità:
La tabella di verità corrispondente sarà:
![[Pasted image 20241208114019.png]]
Con Z equivalente ad "Alta Impedenza"

---
#### Dalle funzioni booleane ai circuiti e viceversa:
Grazie alle parti logiche introdotte si può partire da una funzione e arrivare ad un circuito e viceversa, vediamo i due casi:
##### Da una funzione booleana a un circuito:
###### Come fare?
1. Si considerano i termini più interni (per precedenza) e si realizza quella parte della funzione come circuito
2. Le uscite delle porte così definite vengono usate come input delle funzione esterne
###### Esempio:
![[Pasted image 20241021181258 1.png]]![[Pasted image 20241021181539 1.png]]![[Pasted image 20241021181603 1.png]]
##### Dalla funzione al circuito:
###### Come fare?
- Si assegna un nume all'uscita di ogni porta
- Queste variabili ausiliare vengono progressivamente eliminate fino a quando non si ha un'espressione che usa solo le variabili di input.
###### Esempio:
![[Pasted image 20241021181341 1.png]]
##### Efficienza del circuito realizzato:
###### Cosa si intende?
Una volta costruito il circuito, dobbiamo chiederci quanto esso sia efficiente. Possiamo rispondere attraverso due definizioni:
- Costo: quante componenti elettroniche utilizziamo per realizzare il circuito?
- Tempo: quanto è veloce il circuito a calcolare l'uscita dati gli ingressi?
La differenza tra una funzione booleana e un circuito, è che la funzione è impulsiva mentre un circuito di commutazione ha un ritardo di calcolo.
###### Ritardo di commutazione:
![[Pasted image 20241021183902 1.png]]
I circuiti sono componenti fisiche, pertanto se applichiamo un gradino in ingresso, l'uscita si stabilizzerà dopo un po' di tempo:
- $\tau_{d}:$ ritardo di commutazione (tempo per arrivare al 10% del valore finale)
- $\tau_{r}$ : tempo di salita (tempo per arrivare al 90% del valore finale)
Per semplicità si considera di solito un unico tempo di propagazione $\tau_{p}$ 
###### Ritardo su un circuito complesso:
Il tempo di propagazione si accumula quando ci sono più porte in cascata che implementano una funzione.
Per stimare le prestazione, si può ricorrere al crital path:
- il percorso più lungo che un segnale di input attraversa in un circuito.
![[Pasted image 20241021184053 1.png]]
Possiamo stimarer un ritardo pari a $4\tau_{p}$ : è un circuito a quattro livelli.
###### Costo:
possiamo sfruttare le tecniche di minimizzazione delle funzioni booleane per cercare di minimizzare il costo e massimizzare le prestazioni:
![[Pasted image 20241021184252 1.png]]
Queste tecniche ci permettono di identificare l'equivalenza tra i due circuiti seguenti:
![[Pasted image 20241021184603 1.png]]
##### Forme canoniche come reti:
Ogni funzione booleana può essere espressa in forma canonica. Queste possono essere realizzate usando 2 soli livelli di porte logiche (AND/OR).
Non è detto che una rappresentazione in forma canonica sia in forma minima.
###### Esempio:
![[Pasted image 20241021184924 1.png]]
### Componenti:
#### Codificatore:
##### Cos'è?
Il codificatore è un circuito che realizza la funzione di codifica binaria. Associa ad ogni elemento di un certo insieme di codifica composto da m simboli una sequenza distinta di n bit.
Per ogni simbolo, generale il codice corrispondente (con $2^{n}\ge m$).
Il circuito ha quindi m linee di ingresso $x_{0},...,x_{m-1}$ ed n linee di uscita $y_0,...,y_{n-1}$
![[Pasted image 20241021185626 1.png]]
Ipotizziamo che sia acceso solo l'input $X_{9}$, il decoder avrà come uscita 1001 (numero 9 in binario).
##### Esempio Cifre decimali:
![[Pasted image 20241021185654 1.png]]

---
##### Applicazioni pratiche nella realtà:
1. **Tastiere dei computer**:
    
    - Quando premi un tasto su una tastiera, il codificatore digitale converte il segnale del tasto in un codice binario corrispondente al carattere.
2. **Sistemi di controllo**:
    
    - Nei sistemi di interrupt nei microprocessori, un codificatore di priorità determina quale periferica deve essere servita per prima.
3. **Robotica e automazione**:
    
    - I codificatori rotativi vengono usati per misurare la posizione e il movimento degli assi in macchine e robot.
4. **Display digitali**:
    
    - I codificatori BCD sono usati per rappresentare i numeri decimali in binario, come nei display a 7 segmenti delle calcolatrici
##### Codificatore prioritario:
###### Cos'è?
Se ci sono più ingressi attivati è necessario, onde evitare problemi con l'input, utilizzare i codificatori prioritari. Questi hanno la caratteristica di dare una diversa priorità per ogni livello di ciascun input. Ad esempio:
![[Pasted image 20241208180107.png]]


#### Decodificatore:
##### Cos'è?
Realizza la funzione inversa del codificatore: a partire da una parola di un codice binario, genera una uscita che identifica uno dei simboli dell'insieme di interesse. Per ciascuna configurazione di ingresso, una sola uscita vale 1, le altre 0. Ipotizziamo di aver inserito il come input ABC $\rightarrow$ 101 avremo come output $U_{5}$, poichè il valore decimale corrispondente è proprio 5. 
![[Pasted image 20241208180314.png]]

---
##### Costruzione con AND e NAND:
![[Pasted image 20241021185841 1.png]]
![[Pasted image 20241021185853 1.png]]![[Pasted image 20241021185913 1.png]]

---
#### Multiplexer:
##### Cos'è?
In alcuni casi è necessario scegliere tra più segnali in input/output, per esempio quando forniamo input diversi ad una stessa funzione booleana implementata in hardware:
Il _multiplexer_ è un circuito che permette di selezionare tra un insieme di input, un solo output.
Esso si basa su n segnali di controllo (**x**),$2^n$ segnali dati(**d**) e una sola uscita (**y**):
![[Pasted image 20241018114739 1.png]]
Il segnale di controllo ($x_{n}$) sono scritti in notazione decimale, quindi questo significa che se x vale 3 e ci sono 3 segnali di controllo avremo come input 100.

---
##### Funzionamento:
L'uscita assume il valore $d_i$ quando x=i, quindi, basandosi sulla seguente tabella, se il segnale di controllo vale 2, l'uscita sarà proprio $d_{2}$ e così via
![[Pasted image 20241018114914 1.png]]

---
Possiamo quindi scrivere la funzione di uscita come somma logica tra il prodotto di tutti i mintermini di x e i dati d:$$y=\sum\limits_{i=o}^{2^{n}-1}d_{i}m_{i}$$![[Pasted image 20241018114958 1.png]]

---
##### Utilizzo con funzioni booleane:
Un multiplexer può essere utilizzato per implementare qualsiasi funzione booleana di n variabili. Questa rappresentazione in forma tabellare di una funzione determina per ogni configurazione dell'input il valore dell'output.
Un multiplexer può implementare tale tabella.
![[Pasted image 20241018115308 1.png]] 
Infatti y (che è l'uscita) avrà un valore $Y_{3}$ quando x, il segnale di controllo varrà 3, quindi se e solo se (essendo 2 segnali di controllo) entrambi saranno accesi (questo poiché 11 in binario equivale a 3 in decimale).

---
#### Demultiplexer:
##### Cos'è?
È Il circuito duale del multiplexer. L'uscita i-esima assume il valore y quando la variabile di controllo x=i. Possiamo trovare una somiglianza con il decoder.
![[Pasted image 20241018115503 1.png]]

---
#### Read Only Memory (ROM):
##### Cos'è?
è una memoria in sola lettura. Le locazioni di memoria possono essere lette specificandone l'indirizzo:
![[Pasted image 20241018115643 1.png]]
è un'implementazione alternativa di un circuito combinatorio, dato un'ingresso, c'è una sola uscita.
##### Schema logico di una ROM:
Le funzioni di commutazione sono realizzate come OR di mintermini:![[Pasted image 20241018115834 1.png]]
e questa è la rispettiva implementazione.
![[Pasted image 20241018115902 1.png]]
###### ROM Paginata:
Per motivi di ottimizzazione di superficie, si cerca di realizzare le ROM in forma quadrata. 
Viene quindi organizzata in "pagine", con una parte dei bit dell'indirizzo viene usata per selezionare la pagina. 
La restante parte seleziona la parola all'interno della pagina.![[Pasted image 20241018120202 1.png]]
##### PLA
Una ROM è una matrice di AND (con cui sostituisco il decoder) che implementa tutti i mintermini, accoppiata ad una matrice di OR che implementa le varie funzioni. Si potrebbe rendere programmabile sia la rete AND che OR:
La Programmable Logic Array (PLA) realizza questa struttura:
![[Pasted image 20241018120605 1.png]]
Come nel caso della ROM, la programmazione avviene a tempo di sintesi. 
Dei fusibili possono essere utilizzati per collegare i fila sia nella rete AND che nella rete OR. 
###### Esempio:
![[Pasted image 20241018121830 1.png]]
Studio il grafico attraverso le equazioni delle singole y:
$$y_{1}=\bar{x_{1}}x_{2}\bar{x_4}+\bar{x_{1}}x_{3}{x_4}+x_{1}$$
Questo perché presi $x_{1},x_{2},x_{4}$ notiamo che dobbiamo studiare il loro comportamento e quello dei rispettivi negati. $y_{1}$ presenta 3 fusibili e studiandoli singolarmente noto che le "linee" tracciate di $\bar{x_{1}}x_{2}\bar{x_4}$ mi restituiscono 1 se sono  sulla stessa linea. Nella precedente formula, la moltiplicazione fra le varie x dell'input, corrisponde all'operatore "AND", questo significa che il fusibile che si trova nella prima riga della colonna di $y_1$ si illumina se tutti e tre i fusibili corrispondenti sulla stessa riga sono accesi. Lo stesso vale per le righe successive. Da questo ne deduciamo che la somma fra le i tre elementi corrisponde all'operatore "OR". Nel complesso cosa significa questo? 
Il fusibile che si trova in corrispondenza della prima riga e sulla colonna di $y_1$ si illumina SE E SOLO SE tutti e tre i fusibili sulla stessa riga si illuminano, restituendo quindi come valore 1. Affinché $y_{1}$ ritorni 1, è necessario che SOLO 1 dei 3 fusibili della colonna y si illumini. In termini numerici questo significa y torna 1 SE E SOLO SE uno tra $\bar{x_{1}}x_{2}\bar{x_4},~~\bar{x_{1}}x_{3}{x_4},~~x_{1}$ ritorni 1.
 Queste sono le due equazioni di $y_{2},y_{3}$
 $$y_{2}=\overline{x_{2}}x_{3}{x_4}+\overline{x_{3}}~\overline{x_{4}}+{x_1}{x_3}+x_{2}\overline{x_{4}}$$
 $$y_{3}={x_{1}}x_{2}+\overline{x_{1}}~\overline{x_{2}}+{x_1}{x_3}+x_{2}{x_{4}}$$
 
 
# Capitolo 5: Reti iterative:
### Reti combinatorie iterative:
I metodi di sintesi che abbiamo analizzato fino a questo punto permettono la sintesi di circuiti in cui sono poche le variabili in inout.
Per progettare una CPU, dobbiamo essere in grado di gestire dati a 16, 32, 64 bit. Un circuito di questo tipo può essere difficile da sintetizzare. Per ovviare a questo problema possiamo organizzare i circuiti in maniera iterativa. Ciò significa che uno stesso circuito elementare tratta un sottoinsieme dei bit dei dati, riducendo il numero di variabili. Più circuiti elementari sono interconnessi fra loro per calcolare la funzione finale.
![[Pasted image 20241021152258 1.png]]
- Vettore **y** rappresenta le informazioni di stato trasferite da un modulo al successivo. L'ultimo modulo può esporre parte di questa informazione all'esterno, ad esempio per notificare dettagli circa il risultato finale dell'operazione.
- Vettore **x** rappresenta il dato in input, decomposto tra i vari moduli.
- Vettore **z** rappresenta l'output, calcolato iteramente dai moduli 
#### Comparatori:
I comparatori sono dei circuiti che confrontano il valore di due numeri, A e B, rappresentati in formato binario.
Il risultato di un comparatore determina se A=B, il confronto può essere effettuato su ciascuna coppia di bit in moduli separati, tuttavia è necessario propagare il risultato della comparazione dai moduli precedenti:
![[Pasted image 20241021161118 1.png]]
##### Esempio:
Considero due numeri 10110 e 10010, il comparatore agirà calcolando a due a due le cifre partendo da destra:
				!	 $\longleftarrow$	     $\longleftarrow$ 

| Bit 5 | Bit 4 | Bit 3 | Bit 2 | Bit 1 |
| ----- | ----- | ----- | ----- | ----- |
| 1     | 0     | 1     | 1     | 0     |
| 1     | 0     | 0     | 1     | 0     |
Il controllo inizia e appena trova un bit diverso, propaga il segnale ai moduli successivi, indipendentemente dall'uguaglianza dei singoli termini.
##### Esempio con le tabelle di verità:
![[Pasted image 20241021163449 1.png]]
Ed i mintermini della funzione sono soltanto due:$$z_{i}=z_{i-1}\bar{a}~\bar{ b}+z_{i-1}*a*b=z_{i-1}(a\odot b)$$
e la sua rappresentazione circuitale è:![[Pasted image 20241021163840 1.png]]
##### Problema delle reti iterative:
Analizzando la struttura del comparatore realizzato è evidente quale sia il limite di queste reti:![[Pasted image 20241021164044 1.png]]
Il tempo di calcolo della funzione può diventare inaccettabile se il numero di bit da processare è troppo elevato.
##### Comparatore veloce:
I bit dei numeri da confrontare vengono divisi in h blocchi di k bit. Ciascun blocco viene confrontato da un comparatore iterativo dedicato.
Le uscite dei vari comparatori vengono processate da un comparatore aggiuntivo.
![[Pasted image 20241021164246 1.png]]
###### Comparatore veloce ad albero:
Poiché il numero di bit è tipicamente una potenza di due, si possono organizzare i comparatori in una struttura ad albero a più livelli.
Per esempio, per interi a 16 bit:
![[Pasted image 20241021165712 1.png]]
##### Half adder:
Il circuito più semplice per effettuare una somma di operandi ad un solo bit deve calcolare il valore della somma e il valore del riporto:$$s=a⊕b,~~~c=a*b$$
![[Pasted image 20241021165901 1.png]]
##### Full adder:
Per calcolare la somma di un inter a n bit, possiamo realizzare una rete iterativa composta da n sommatori, dove il circuito del modulo va modificato per considerare anche il riporto proveniente dai moduli precedenti.
![[Pasted image 20241021170130 1.png]]
![[Pasted image 20241021170145 1.png]]
![[Pasted image 20241021170219 1.png]]
##### Carry Lookahead Adder:
l **carry lookahead adder (CLA)** è un tipo di sommatore binario progettato per migliorare la velocità delle operazioni di somma rispetto a un sommatore binario tradizionale (come il **ripple-carry adder**). L'idea principale del CLA è di **calcolare il bit di carry in modo parallelo** piuttosto che in modo sequenziale, rendendo l'addizione molto più veloce, specialmente per numeri binari lunghi. Per comprenderne il funzionamento, devo 
##### Shifter:
L'operazione di shift consiste nel muovere a destra o a sinistra i bit di una parola binaria:
- alcune cifre possono venire scartate
- quelle libere possono essere riempite con degli zeri
Considerando la possibilità di spostare un bit di una sola posizione,
dobbiamo prevedere i seguenti “comandi” per un circuito:
- SH=0 non effettuare alcun cambiamento, SH=1 effettua la traslazione
- D=0 trasla a sinistra, D=1 trasla a destra
Possiamo descrivere il circuito che calcola il valore del bit in uscita con il seguente sistema:

quindi l'equazione che calcola il valore del bit diventa:$$z_{i}=\overline{SH}a_{i}+SH*(a_{i-1}*\overline D)+a_{i+1}*d$$![[Pasted image 20241022124822 1.png]]
Per supportare una traslazione di più posizioni possiamo costruire una rete iterativa di shifter
Utilizzando un vettore di controllo SH possiamo controllare i vari livelli:
![[Pasted image 20241022124948 1.png]]
Può infatti essere implementato al fine di essere utilizzato per la criptazione di dati, infatti con un numero a 4 bit potremmo utilizzare lo shift classico a sinistra per 3 cifre e la quarta la porto come prima cifra: $0111\longleftarrow1011$
###### Esempio:
$1101\longrightarrow0110$ 
$1010\longleftarrow1101$ 
In entrambi i casi, però, se lavoriamo esclusivamente a 4 bit ci troveremo nella condizione di overflow. Diversamente, la funzione di shift funziona come una divisione per 2 se eseguita verso destra, mentre come una moltiplicazione, sempre per 2, se eseguita verso sinistra.
##### Barrel Shifter:
Il costo della rete può essere elevato. Si può utilizzare una rete basata su interruttori posti in posizione predefinite. Ed attivando gli interruttori corretti, è possibile implementare in tempo costante, tutte le traslazione a destra e a sinistra

##### Operazioni di shift tipiche:
![[Pasted image 20241022125820 1.png]]
Esistono altre operazioni tipiche, ovvero rotazioni e shif aritmetico. In alcuni casi viene preso in considerazione anche un bit di carry (il quadrato C in figura).
##### Alu:
![[Pasted image 20241025115114 1.png]]
![[Pasted image 20241025115212 1.png]]

# Capitolo 6: Reti sequenziali:
I circuiti visti fin ad ora possono essere definiti combinatori, infatti dato un certo input, essi calcolano un certo output, secondo la relazione:$$y=f(x)$$
Tali circuiti quindi hanno un’uscita che dipende esclusivamente dall’input. Se avessimo a disposizione solo questo tipo di circuito, non potremmo implementare elementi di memoria.
#### Circuito latch: 
Circuito che cattura il valore di input utilizzando degli anelli a retroazione.
È un circuito analogico che consente di immagazzinare un’informazione digitale.
Non funzione se uno utilizza come output 1,1 poiché non riesce a memorizzare un valore, restituirà infatti 0,0.
In una configurazione io devo dare un valore di reset R ed un valore di set S, otterrò Q e $\overline{Q}$.
($Q’$ è $\neq\overline Q$)
Attraverso le tre combinazioni:$$(0,0),(0,1),(1,0)$$ possono chiedere di ottenere un valore o di salvarlo.
![[Pasted image 20241025121034 1.png]]
##### Problemi del latch:
Una configurazione di ingresso in cui S= 1 e R = 1 manda il circuito
in uno stato oscillante
• I valori di S ed R possono essere calcolati da altre reti combinatorie
• Non è possibile garantire che, a causa dei ritardi di propagazione, nosi
osservi mai una configurazione transiente pari a S = 1 e R = 1
• Soluzione: campionare il valore di S ed R quando siamo certi che gli
input si sono stabilizzati
• In questo caso il circuito assume il nome di flip flop

###### Flip Flop SR:
Si basa sull’aggiunta di un segnale di clock al latch:
Funziona come un orologio, serve a tenere il tempo e vedere se il circuito funziona regolarmente. Si usano dei quarzi che creano circuito elettromagnetico e lo invertono.
![[Pasted image 20241025121344 1.png]]
Rimane il problema dell’input con S ed R = 1.
Possiamo costruire un circuito che prevenga l’insorgere di configurazioni oscillanti.
###### Flip Flop JK:
Aggiunge una rete di controllo ai segnali di ingresso. Questa rete rende impossibile che is verifichi la condizione che avevamo enunciato prima in input:
![[Pasted image 20241025121742 1.png]]
###### Flip Flop D:
I due precedenti Flip Flop hanno la necessità di due segnali di controllo opposti, spesso infatti si vuole utilizzare un flip flop per immagazzinare un bit generato da una funzione di commutazione. Per non dover negare esplicitamente il bit, si può usare un flip flop D. Tale circuito si comporta da **ritardo**(delay):
- l’input viene propagato in output dopo un periodo di clock. ![[Pasted image 20241025200118 1.png]]

###### Flip Flop T:
Può essere anche utile avere a disposizione un flip flop che si comporta come switch:
- Al primo segnale, commuta da 0 a 1
- Al secondo segnale, commuta da 1 a 0
Il flip flop T (**toggle**) implementa questo comportamento:
![[Pasted image 20241025200553 1.png]]


##### Fronti di commutazione.
Per funzionare correttamente, questi flip flop devono avere i segnali di controllo stabili per tutta la durata del periodo di clock. È utile prevedere circuiti che effettuino la commutazione in finestre temporali precise e di durata più breve. _Edge-triggeredd_ flip flop: commutano su fronte di salita o di discesa:
![[Pasted image 20241025122354 1.png]]

Andiamo a studiare i diversi comportamenti eseguiti dallo stesso flip flop: 
![[Pasted image 20241025122321 1.png]]
Se studiamo i fronti di salita, di costanza del valore o di discesa, posso notare come nella figura, in corrispondenza di una discesa o salita sono corrisposte diverse uscite dipendentemente dal grafico. 
Per capire se i calcolatori sono corretti si valuta il tempo di salita o il tempo di discesa, se i risultati in questo intervallo sono gli stessi allora si continua nello studio, sennò si resetta il funzionamento e si inverte il bit. Se un segnale nello istante risponde in due modi differenti, uno dei due viene resettato ed invertito il bit di uscita.

#### Reti combinatorie:
##### Cosa sono?
Con tutto questo studio si è capito che l’algebra booleana non è in grado di descrivere completamente i circuiti, visto che, come scritto nella tabella, il risultato finale Q’ non dipende più solo dall’input,  ma anche dallo stato Q (che dipende dall’input); abbiamo dunque bisogno delle funzioni (che rimangono booleane), quindi per analizzarlo abbiamo bisogno di altro:
##### Tipi di reti sequenziali:
Esistono due classi principali di reti sequenziali:
- Sincrone: se la transizione di stato avviene in instanti temporali controllabili dall’esterno
- Asincrone: non controllabili dall’esterno.
Studieremo le prime:
![[Pasted image 20241025123622 1.png]]
##### Macchine a stati finiti:
Si tratta di un modello matematico per la descrizione della computazione. È una macchina astratta:
- in un dato istante si trova in uno stato (tra un insieme finito di stati)
- Eventi esterni provocano una transizione da uno stato all’altro
- La macchina può generare output verso l’esterno.
Esistono due principali varianti:
- macchina di Moore: l’output dipende unicamente dallo stato:
- macchina di Mealy: l’output dipende dallo stato e dalla transizione innescata:
###### Macchina di Moore:
![[Pasted image 20241025124159 1.png]]
###### Macchina di Mealy:
![[Pasted image 20241025124240 1.png]]

##### Rappresentazioni:
È possibile utilizzare due formalismi:
###### Diagramma degli stati: 
Mostra graficamente le relazioni tra gli stati e le transizioni, identificando anche i caratteri di output:
![[Pasted image 20241025124448 1.png]]
###### Tabella degli stati:
![[Pasted image 20241025124608 1.png]]

##### Equivalenza fra modelli:
Esiste sempre una trasformazione tra una macchina di Mealy e una macchina di Moore, poichè essi sono equivalenti.
###### Trasformazione da Moore a Mealy:
- Gli alfabeti di input ed output sono gli stessi
- Gli stati sono gli stessi
- Se in uno stato $S_{i}$ raggiunto da una transizione causata da un carattere $i_{j}$, viene generato un output $o_{k}$ quello stesso output viene generato durante la transizione $i_{j}$ verso lo stato $s_{i}$.
###### Trasformazione da Mealy a Moore:
![[Pasted image 20241025125158 1.png]]
##### Sintesi delle macchine:
Per realizzare circuitalmente una macchina è necessario:
- Realizzare il blocco M: questo può essere fatto utilizzando un numero sufficiente di flip flop D
- Realizzare la rete $\delta$: è necessario realizzare un circuito di commutazione per aggiornare lo stato di ciascun flip flop D (cioè l’equazione di eccitazione di un flip flop)
- Realizzare la rete $\omega$: è necessario realizzare un circuito di commutazione per generare ciascun bit dei caratteri di output.
Trattandosi di reti combinatorie, è possibile utilizzare le tecniche di sintesi e minimizzazione che abbiamo studiato per le funzioni booleane.
La sintesi può essere svolta a partire dalla tabella degli stati e transizioni.
###### Esempio:
![[Pasted image 20241025194318 1.png]]

# Capitolo 7: z64 (Processing Unit)
### Componenti interne:
Abbiamo suddiviso logicamente l’architettura di von Neumann in due
blocchi logici:
• Unità di calcolo: tutto ciò che esegue il lavoro
• Unità di controllo: la componente in grado di interpretare le istruzioni
Graficamente potremmo rappresentarla così:
![[Pasted image 20241111201205.png]]

In realtà possiamo esprimerlo in modo più specifico così:
![[Pasted image 20241111204951.png]]


### Registri:
Sono delle unità di memoria interne al processore:
- compongono la parte di memoria di lavoro interna alla CPU. 
- Permettono  di memorizzare parole binarie
- La quantità di memoria disponibile è estremamente limitate.
- Sono realizzate attraverso un insieme di flip flop:
![[Pasted image 20241029114605.png]]
Vengono utilizzate tante componenti hardware per memorizzare gli elementi, questo è utile perché i registri lavorano alla stessa velocità del processore e l'abilità si trova nel metterci proprio le informazioni giuste.
#### Suddivisione:
Possono essere suddivisi in più classi.
- Registri fondamentali: sono i registri senza i quali non è possibile realizzare un 'architettura di von Neumann
- Registri visibili al programmatore: sono registri che il programmatore può utilizzare esplicitamente nel suo programma
- Registri invisibili al programmatore: sono registri che il programmatore può modificare solo indirettamente e non programmaticamente.
##### Registri Visibili:
Ci sono 16 registri _general purpose_ a 64 bit che il programmatore può utilizzare esplicitamente come _operandi_ delle istruzioni:
![[Pasted image 20241029120051.png]]
Alcuni di questi registri hanno un significato particolare e sono utilizzabili implicitamente utilizzando specifiche istruzioni assembly

##### Come si interconnettono i registri?
###### Necessità di interconnessione tra registri:
###### Prima modalità, interconnessione diretta:
Possiamo prevedere la seguente interconnessione se vogliamo supportare l'esecuzione dei segnali: _mov, %rax, %rbx_:
![[Pasted image 20241029120514.png]]
quindi ci saranno 64 x 15 fili che collegano:
Possiede il vantaggio della semplicità di progettazione, ma lo svantaggio di interconnettere più registri fra loro.
###### Seconda modalità, Interconnessione tramitre multiplexer:
![[Pasted image 20241029120711.png]]
Presenta i seguenti vantaggi:
- semplici da implementare
- possibilità di trasferire più dati contemporaneamente
###### Terza modalità:
costruzione di un Bus interno, cioè un gruppo di 64 fili che corrono all'interno del processore:
- collega tra loro tutti i registri interni.
Occorre smistare i dati sul bus:
- recupero di dati: i bit presenti sul BUS sono memorizzati in un registro
- immissioni di dati: il contenuto di un registro è posto sul BUS
Utilizzo di più segnali di controllo opportunamente generati dalla CU:
- Wirte enable per abilitare la scrittura
- Buffer Three-State per abilitarne la lettura.

Ricordandosi che si può avere una sola immissione per volta sul BUS, il modo per interconnettere i registri tramite BUS solamente andando ad utilizzare il buffer three state per evitare che un output di un circuito arrivi ad un altro e questi messaggi viaggiano attraverso i bus. ![[Pasted image 20241029121943.png]]
Quindi per leggere quello che è scritto nel RAX (registro) mi basta un Buffer-Three-State, il tipo di registro iniziale attraverso 4 bit, visto che questi compongono i registri. Quindi per leggerne uno in entrata ed in uscita, necessitò in totale di 6 bit, 4 di "costruzione" e 2 per o scriverlo o leggerlo.
###### Ottimizzazione del banco dei registri:
Ottimizzazione: banco dei registri (o file dei registri o memoria dei registri). I registri sono codificati con un codice numerico identificativo $\in[0,15]$ totali. (per questo motivo per calcolare i registri bastano 4 bit (4!=16)).
![[Pasted image 20241029122232.png]]
###### Processamento di dati a dimensione differente:
Un processore può operare su dati di dimensione differente:
- Esempi tipici: 8, 16, 32, 64 bit
- Non è vantaggioso e pratico avere più banchi di registri:
- E' utile poter accedere a sottoporzioni dei dati nei registri
 ![[Pasted image 20241029123311.png]]
 i rispettivi registri a 8,16,32,64 si rappresentano:
 AL|H|AX|EAX|$\overline\epsilon \le |f(x_{2})|f(z_{k})$ ?

###### Registri virtuali:
Le istruzioni assembly usano un suffisso per indicare la dimensione:$$MOVx <sorgente>, <destinazione>$$
B: byte (8 bit), W:word(16 bit), L: longword (32 bit), Q: quadword (64 bit)
Il suffisso fornisce parte del contesto alla CU per poter trattare i dati correttamente.
![[Pasted image 20241029124214.png]]
![[Pasted image 20241029124443.png]]
###### Instruction Registrer:
Sapendo che accedere alla memoria è un'operazione costosa, i registri dei processori sono realizzati con tecnologia molto più veloce, ma più costosa. La memoria, avendo dimensione più grande, è realizzata con tecnologia più economiche ma meno veloci.
I circuiti combinatori e sequenziali interni alla CPU devono avere gli input stabili fino alla loro stabilizzazione. Non è ragionevole mantenere stabili gli input direttamente dalla RAM, dunque si introduce un registro tampone, ovvero l'Instruction Registrer: esso mantiene una _copia_ della codifica di un'istruzione assembly  prelevata dalla memoria. 
In questa codifica, sono mantenuti i codici del registro e della taglia dei dati:
![[Pasted image 20241029130144.png]]

###### Componenti per il processamento dei dati :
I circuiti elementari costruiti fin'ora sono la ALU e lo shifter.
![[Pasted image 20241104142712.png]] 
I dati da fornire in input a questi due circuiti sono contenuti nel banco dei registri.
C'è un problema, la ALU ha bisogno di due operandi (da mantenere stabili) ed è possibile eseguire una sola immissione di dati sul BUS interno. La soluzione è quella di utilizzare dei registri tampone:
![[Pasted image 20241104142940.png]]
##### Registro FLAGS:
ALU e Shifter sono reti iterative che emettono dei bit di stato. E' utile esporre lo stato al programmatore: occorre memorizzarli. Si utilizza il registro fondamentale in FLAGS. 
I bit al suo interno si dividono in status e control:
![[Pasted image 20241104143326.png]]i bit di stato sono aggiornati dalla ALU e dallo Shifter per memorizzare informazioni sull'ultima operazione eseguita. I bit di controllo sono modificabili dal programmatore per alterare alcune funzionalità del processore.
###### Utilizzo del registro Flags:
![[Pasted image 20241104143833.png]]
#### Interazioni con la memoria:
La restante parte della memoria di lavoro è esterna alla CPU. E' necessario prevedere un interfacciamento con essa ed un protocollo di scambio dati.
![[Pasted image 20241104144017.png]]
##### Modello astratto di memoria di lavoro:
![[Pasted image 20241104144111.png]]
##### Trasferimento di dati con memoria esterna:
Il bus di sistema è un insieme di fili che "corrono" alla memoria dal sistema. Poiché esistono tre componenti, vengono organizzati su viaggi differenti:
![[Pasted image 20241104144242.png]]
Il numero minimo di fili che ci deve essere è 8, poiché nel  modello astratto di memoria ci sono almeno 8 bit. Ad oggi il numero massimo è di 48 bit, quindi posso indirizzare fino a $2^{48}$cavi.
Sappiamo che la memoria è più lenta del processore e si comporta come un circuito combinatorio, e le altre componenti sul BUS di controllo devono rimanere stabili. Visto che il data BUS è unico, sarà sempre la CPU a scegliere in quale modo utilizzarlo, se per leggere o scrivere. Questo poiché è il processore che "svolge" i programmi.
Visto che occorre utilizzare un tampone tra i dispositivi, allora dovrò posizionare gli elementi in questo modo:
![[Pasted image 20241104145115.png]]
 >MAR sta per memory address bus quindi l'indirizzo di riferimento del BUS
 
 Sul memory data bus si scrivono i dati raccolti:
 possiamo disaccoppiare, quindi scinderlo in modo tale da non collegare memory data BUS e memory address BUS.
###### Zoom della logistica della memoria: 
![[Pasted image 20241104145723.png]]
#### Anatomia dei programmi in memoria:
ogni dato è identificabile solo attraverso gli indirizzi:
![[Pasted image 20241104150644.png]]
Questo tipo di architettura è "a stack". Utilizza una pila per immagazzinare valori, nel nostro caso cresce verso il basso. Per esempio, ipotizziamo di utilizzare una variabile, essa deve essere dichiarata nella parte dello stack, non può occupare spazio in "data", perchè andrebbe a creare problemi di memoria con  i dati che sono presenti nel livello.

#### Come capire il punto in cui si è arrivati
Se .text è una sequenza lineare di istruzioni la CPU deve tenere traccia del punto in cui è arrivata ad eseguire le istruzioni.
Viene utilizzato un altro registro fondamentale: _**l'instruction pointer.**_
Questo registro si aggiorna in continuazione e trascrive la prossima istruzione da eseguire. 
RIP mantiene (quasi) sempre l'indirizzo della prossima istruzione (è un puntatore a memoria che punterà al bit successivo appena letto):
![[Pasted image 20241104151545.png]]

##### Come incrementarlo?
Se utilizzassi la ALU, il programma sarebbe molto lento. Poiché il processo di somma andrebbe ripetuto ad ogni istruzione e non si potrebbe svolgere in contemporanea l'istruzione. Si pone come registro a incremento, il quale è accoppiato ad un sommatore veloce dedicato. E' un circuito più complesso ma il processo può svolgersi in parallelo all'esecuzione dell'istruzione corrente.

#### Lo stack di programma:
Il processore ha un numero estremamente limitato di registri, un programma potrebbe avere bisogno di gestire tante variabili o alcune molto grandi.
E' possibile utilizzare un'area di memoria come "area di appoggio": lo stack di programma.
##### Cos'è?
Essa è una struttura dati di tipo LIFO (Last-In-First-Out):: il primo elemento che può essere prelevato è l'ultimo ad essere memorizzato.
Si possono effettuare due operazioni su questa struttura dati:
	• push: viene inserito un elemento sulla sommità (top) della pila
	• pop: viene prelevato l’elemento affiorante (top element) dalla pila
Data l’importanza di questa struttura dati, molte ISA forniscono
istruzioni dedicate per la sua manipolazione.
##### Gestione dello stack nello z64:
Lo stack è composto da quadword (non si può eseguire una push di un singolo byte)
La cima dello stack è individuata dall'indirizzo memorizzato in un registro specifico chiamato stack pointer
Lo stack “cresce” se il valore contenuto in SP diminuisce, “decresce” se il valore contenuto in SP cresce
Le istruzioni che implementano le operazioni di push e pop utilizzano il registro RSP in modo implicito
Modificare esplicitamente il valore di RSP significa perdere il riferimento alla cima dello stack, e quindi a tutto il suo contenuto
È però accessibile al programmatore: si può decidere di utilizzare più stack
È quello che fanno i sistemi operativi per eseguire più processi contemporaneamente 

##### Utilizzo stack 
Posso utilizzare più stack per far funzionare meglio un computer, per esempio qualsiasi pc utilizza un singolo stack per ogni singolo programma												
![[Pasted image 20241105121704.png]]

##### Undefined behaviour:
è un comportamento del programma per il quale ogni messaggio inviato risponde corretto, poiché potrebbe essere che ci sia stato un overflow dello stack, cioè ha sovrascritto "logicamente" il livello dei dati. Se infatti si vanno a sommare più elementi alla pila dello stack esso può essere che vada ad occupare uno spazio maggiore ed interferire proprio con i dati.										

### Modalità di indirizzamento:
#### Strutture dati e modello di memoria lineare:
Il modello astratto di memoria è lineare, quindi indirizzato al byte.
I linguaggi di programmazione offrono astrazioni diverse:
	• Vettori: x = A[i];
	• Strutture dati: x = str.member;
Il programmatore (o il compilatore) può scrivere un programma assembly per tradurre un accesso ad un elemento di struttura dati in un indirizzo effettivo di memoria:
![[Pasted image 20241105122721.png]]
Ad esempio, un accesso all’elemento i-esimo di un vettore può essere “tradotto” in un indirizzo effettivo applicando l’operatore **spiazzamento**
Se la variabile a è associata all'indirizzo di base del vettore e tutti gli elementi hanno la stessa dimensione, allora vale:
![[Pasted image 20241105123021.png]]
Strutture dati più complesse posso utilizzare celle di memoria
contigue per memorizzare dati di tipo differente. 
La memoria è lineare: occorre dare un contesto a ciascun membro della struttura.
![[Pasted image 20241105123156.png]]

Se una variabile di tipo struttura libro è associata all’indirizzo di
base in memoria in cui si trova la struttura, accedere a un membro
equivale a calcolare:
libro.year ⟺ libro + spiazzamento(titolo) + spiazzamento(autore).

E dal punto di vista della programmazione si presenta:

Poiché stiamo realizzando un’architettura CISC, è sensato offrire un
supporto migliore al calcolo degli indirizzi effettivi a livello di CPU.
Nei casi (molto comuni) di vettori e strutture, gli elementi ricorrenti
per il calcolo di un indirizzo effettivo sono stati:

• indirizzo di base

• indice

• spiazzamento

Per quanto riguarda l’indice dei vettori, è utile anche conoscere la
taglia dei singoli elementi del vettore:
					a[i] ⟺ a + size ∗ i
					
• Poiché i tipi primitivi della CPU sono a 8, 16, 32 e 64 bit, è utile
prevedere una scala pari a questi valori

##### Operando in memoria:
Serve a definire delle "definizioni" ricorrenti.
Le istruzioni assembly possono accettare anche operandi in memoria
• Per motivi di codifica, al più uno solo
• MOVx $<sorgente>,~<destinazione>$ 
• Uno tra $<sorgente>~e~<destinazione>$può essere un operando in memoria
Per supportare le operazioni comuni, gli operandi in memoria hanno la forma:
			spiazzamento(base, indice, scala)
Base e indice sono registri general purpose
• base: si può riusare lo stesso codice per accedere, ad esempio, a vettori differenti
• indice: si può utilizzare la stessa istruzione all’interno di un ciclo per scandire un vettore
Sappiamo che scala e spiazzamento sono delle costanti codificate nell'istruzione.
###### Esempi:


#### Implementazione della modalità di indirizzamento:
La determinazione di un indirizzo di memoria è un'operazione più complessa. E' necessario fare affidamento sulla PU per calcolare questo indirizzo.
Ho due possibilità:
- introduzione di hardware dedicato
- utilizzo dell'hardware già presente 
La seconda opzione è la più conveniente, per evitare di appesantire ulteriormente:
![[Pasted image 20241105125002.png]]![[Pasted image 20241105125021.png]]
### Istruzioni dello z64: 
#### Cosa sono?
Definire una codifica della istruzioni è fondamentale per progettare un'ISA: 
- Determina in che modo la CU interpreta le istruzioni
- Determina quali sequenze di parole binarie il compilatore inserisce in .text
Sono organizzate in otto classi:
- Classe 0: Controllo dell’hardware
- Classe 1: Spostamento dati
- Classe 2: Aritmetiche (su interi) e logiche
- Classe 3: Rotazione e shift
- Classe 4: Operazioni sui bit di FLAGS
- Classe 5: Controllo del flusso d’esecuzione del programma
- Classe 6M: Controllo condizionale del flusso d’esecuzione del programma
- Classe 7: Ingresso/uscita di dati
Le istruzioni hanno un formato a lunghezza variabile:
![[Pasted image 20241111142825.png]]
La lunghezza variabile permette la generazione di programmi più compatti (meno consumo di memoria e spazio su disco).
##### Il campo Opcode:
la prima parte delle istruzioni è il campo Ocode:
![[Pasted image 20241111142953.png]]
- Class è un codice di 4 bit che identifica la famiglia di istruzioni cui
appartiene quella corrente
- Type è un codice di quattro bit che identifica la precisa istruzione
nella famiglia
- Questa differenziazione ci consentirà di realizzare una CU più ottimizzata
##### Il campo Mode:
Il campo Mode è strutturato in questo modo:
![[Pasted image 20241111152741.png]]
- SS e DS contengono rispettivamente la codifica della dimensione
dell’operando sorgente e destinazione
- DI è un campo di 2 bit che indica o meno la presenza di un displacement e di un dato immediato
- Mem indica quali degli operandi (sorgente o destinazione) sono da considerarsi operandi in memoria.
Inoltre in base ai valori assegnati ai singoli elementi avremo un significato diverso:
![[Pasted image 20241111162314.png]]
##### Campo SIB
è organizzato in questo modo:
![[Pasted image 20241111162633.png]]

Bp e Ip indicano se si deve utilizzare una base e/o un indice per
calcolare l’indirizzo effettivo
• Se Ip 1, il campo Index mantiene la codifica binaria del registro indice
• Scale mantiene il valore della scala, i cui valori leciti sono 1 (codificato come 00), 2 (codificato come 01), 4 (codificato come 10) e 8 (codificato come 11).
###### Codifica dei registri:
![[Pasted image 20241111163310.png]]
##### Il campo R/M:
![[Pasted image 20241111171019.png]]
- Questo campo ha spazio per mantenere esattamente due codifiche di registri
- L’interpretazione di questi campi dipende dai valori dei sottocampi di Mem e del bit Bp di SIB
- I registri possono quindi essere interpretati come registri semplici oppure come registri base
#### Classi:
##### Classe 0: Controllo hardware
Le istruzioni di controllo hardware consentono di modificare lo stato della CPU, oppure eseguono istruzioni particolari.
![[Pasted image 20241111143327.png]]
Hit può essere utilizzata per esempio se la CPU si surriscalda.
Nop indica nessuna operazione.
##### Classe 1: Istruzioni di movimento dati:
![[Pasted image 20241111144914.png]]
L'istruzione movzX supporta le stesse combinazioni di suffissi.
I nomi dei registri virtuali devono essere coerenti con i suffissi.
L'istruzione lea valuta la modalità di indirizzamento, salva il risultato in G.
###### Comandi per il movimento di dati:
![[Pasted image 20241111145016.png]]
##### Classe 2: Istruzioni logico aritmetiche (1):
![[Pasted image 20241111145926.png]]
Con lo z64 è possibile effettuare operazioni aritmetiche (somme e
sottrazioni) usando dati a 64 bit
-  Può essere necessario effettuare operazioni con dati più grandi
- Le istruzioni adc e sbb permettono di realizzare programmi a precisione arbitraria![[Pasted image 20241111152009.png]]

##### Classe 2: Istruzioni logico aritmetiche (2)
![[Pasted image 20241111151931.png]]
##### Classe 3: Istruzioni di rotazioni e shift
![[Pasted image 20241111152145.png]]
##### Classe 4:  Manipolazione dei bit di FLAGS
![[Pasted image 20241111152210.png]]
##### Classe 5: Controllo del flusso di programma
![[Pasted image 20241111152313.png]]
Call serve ad attivare una funzione

##### Classe 6:  Controllo condizionale del flusso
![[Pasted image 20241111152511.png]]![[Pasted image 20241112114748.png]]


#### Alcune istruzioni assembly:

- `movb %al, %bl`: _copia_ il _contenuto_ del _byte **meno** significativo_ di _RAX in RBX_

- `movw %ax, (%rdi)`: _copia_ il _contenuto_ dei _2 byte meno significativi_ di _RAX_ _nei due byte_ di _memoria_ il cui _indirizzo_ __iniziale__ è _memorizzato in RDI_

- `movl (%rsi), %eax`: _copia nei 4 byte **meno** significativi di RAX_ il _contenuto_ dei _4 byte_ di memoria _il cui indirizzo è specificato in RSI_.

- `movq (%rsi, %rcx, 8)`, %rax: copia nel registro RAX il
  contenuto degli 8 byte di memoria il cui indirizzo iniziale è calcolato come RSI + RCX ∙ 8
  
- `subl %eax, %edx`: sottrai il contenuto dei 4 byte meno significativi di RAX dai 4 byte meno significativi di RDX e aggiorna il contenuto dei 4 byte meno significativi di RDX

- `addb $d, %al`: somma al byte meno significativo di RAX la quantità costante d.

- `addb d, %al`: somma al byte meno significativo di RAX il byte contenuto all'indirizzo di memoria d.
#### Traduzione istruzioni assembly in linguaggio macchina:
##### Esempi:

###### $movw~\%ax,~\%bx$

- Copia il contenuto dei 2 byte meno significativi di RAX nei due byte di memoria il cui indirizzo iniziale è memorizzato in RDI

- Non si ha alcun accesso in memoria

- Sorgente e destinazione sono entrambi di 2 byte

- Non è coinvolta alcuna costante

![[Pasted image 20241111172148.png]]


###### $addb~\$0xa, ~ \%d1$

- Somma al byte meno significativo di RAX la quantità costante d.

- Si utilizza una costante numerica come operando

- Non è presente uno spiazzamento
![[Pasted image 20241111172601.png]]



###### $subb~\$0x2,~0xAAAA$

- Si utilizza una costante numerica come operando

- E' presente uno spiazzamento
![[Pasted image 20241111172753.png]]

###### $movq~0xabcd(\%rsi,~\%rcx,~4),~ \%rax$

- copia nel registro RAX il contenuto degli 4 byte di memoria il cui indirizzo iniziale è calcolato come RSI + RCX ∙ 4
- La sorgente è un operando in memoria

- Per accedere in memoria vengono usati scala, indice, base e spiazzamento
  
![[Pasted image 20241111173446.png]]


#### Memory Endianness: Ordine dei byte
L’ordine dei byte descrive la modalità utilizzata dai calcolatori per immagazzinare in memoria dati di dimensione superiore al byte. La differenza dei sistemi è data dall'ordine con il quale i byte
costituenti il dato da immagazzinare vengono memorizzati:
1) litte-endian: memorizzazione che inizia dal byte meno significativo per finire col più significativo (usato dai processori Intel)
2) big-endian: memorizzazione che inizia dal byte più significativo per finire col meno significativo (Network-byte order)
3) middle-endian: ordine dei byte né crescente né decrescente (es: 3412,2143)
La differenza si rispecchia nel network-byte order vs host order
##### 1) Effetti della little Endianness
Il processore z64 accede in memoria secondo lo schema little-endian. I valori multibyte sono memorizzati con il loro byte meno significativo all'indirizzo più basso. Il valore 0xAABBCCDD è poso nel layout di memoria in questo modo:
![[Pasted image 20241111190348.png]]
Cosa succede se memorizziamo due interi di 4 byte in modo consecutivo in memoria?
Prendiamo ad esempio 0x00cf9200 e 0x0000ffff:
![[Pasted image 20241111190459.png]]
I byte di ogni singolo intero sono scambiati, ma non l’ordine degli interi. infatti la little endianness non è una complicazione per l'ordinamento dei bit perché si occupa esclusivamente dell'ordine dei **byte** e non dei singoli **bit** all'interno di ciascun byte. L'ordinamento dei bit in memoria è sempre lo stesso, indipendentemente dall'endianness.

# Capitolo 8: z64 (Control Unit)
### Cos'è?
Un programma è mantenuto in memoria come una sequenza di istruzioni codificate in codice macchina
• Il registro RIP punta alla prossima istruzione da eseguire
• Se non viene eseguita alcuna istruzione di controllo (condizionale) del flusso di programma, il processore esegue un’istruzione dopo l’altra
in memoria
• Lo stato del programma viene mantenuto in:
• Registri della CPU
• Memoria (variabili globali e stack)
• La corretta esecuzione di un programma richiede l’orchestrazione di
tutte queste risorse da parte della CPU
### Esecuzione di un programma in C:
Dove per PC si intende Program Counter, che contiene l'indirizzo della prossima istruzione da seguire e IC sta per Instruction Register, che memorizza l’istruzione attualmente in esecuzione.
Sappiamo che ogni immagine nella sequenza rappresenta lo stato dei registri e del programma in un dato momento.
#### Slide 1-2: (Introduzione)
##### Slide 1 : (Setup Iniziale):
![[Pasted image 20241112120909.png]]
**Introduzione al codice e struttura delle funzioni**:
- **Funzione `foo`**: Accetta un intero `x` come parametro, calcola il quadrato di `x` (cioè `y = x * x`), e restituisce il valore di `y`. Questo rappresenta una funzione semplice con un solo scopo di calcolo.
- **Funzione `bar`**: Funzione senza parametri che richiama `foo` passando `2` come argomento. `bar` memorizza il risultato restituito da `foo` in una variabile locale `x`.
- **Funzione `baz`**: Analoga a `bar`, ma chiama `foo` con l’argomento `4` e memorizza il risultato di `foo` in `x`.
- **Funzione `main`**: La funzione principale del programma. È il punto di ingresso dell'esecuzione e chiama prima `bar`, poi `baz`.
- **Struttura dello stack**: Nello stack di esecuzione, `main` risiede alla base, poiché è il punto di partenza del programma. Ogni funzione chiamata (`bar`, `baz`, e `foo`) viene aggiunta in cima allo stack quando è invocata e viene rimossa al completamento.
##### Slide 2: (Diagramma della Chiamata delle Funzioni)
![[Pasted image 20241112120956.png]]
**Inizio dell’esecuzione e prima chiamata a `bar`**:
- **Chiamata `call bar()`**: `main` invoca `bar`, con `bar` che diventa il contesto attivo sullo stack.
- **Preparazione di `foo(2)` all'interno di `bar`**:
    - `bar` chiama `foo` con `x=2`, avviando il processo di calcolo del quadrato di `2`.
- **Dettagli di stack e registri**:
    - Lo stack mostra `main` come chiamante principale, con `bar` e `foo(2)` come sottoprocessi in esecuzione.
    - **PC e IR**: Vengono aggiornati per riflettere le istruzioni attualmente in esecuzione.
#### Slide 3-7: (Chiamate di Funzione e Struttura dello Stack)
##### Slide 3: (Chiamata alla funzione `bar`)
![[Pasted image 20241112121009.png]]
Sappiamo che la chiamata alla funzione `bar()` rappresenta un passaggio critico, poiché la CPU deve interrompere il flusso sequenziale di `main` per passare all’inizio di `bar`, e deve ricordarsi come tornare a `main` dopo.
Quindi ha necessità di prepararsi alla chiamata.
**Preparazione alla Chiamata di `bar`**:
- **Salvataggio dell’Indirizzo di Ritorno nello Stack**: La CPU salva nello stack l’indirizzo dell’istruzione successiva in `main` (dove riprenderà l’esecuzione una volta terminata `bar`). Questo indirizzo di ritorno è importante per consentire alla CPU di ricordare dove deve tornare dopo `bar`(cioè foo(4)).
- Lo **stack** è una struttura dati LIFO (Last In, First Out) che permette di accedere velocemente all’ultimo elemento aggiunto, quindi è ideale per le chiamate annidate.
Nella funzione `bar`, viene chiamata `foo(2)`, portando a questi passaggi:
- **Chiamata a `foo`**: `bar` invoca `foo` con l'argomento `2`, che viene passato tramite un registro (potrebbe essere RDI per convenzione in alcuni ABI).
**Chiamata di `foo` da `bar` con `x=2`**:
- **CPU**: La CPU esegue la chiamata `foo(2)`. Viene passato il valore `2` come argomento e il PC è aggiornato per puntare a `foo`.
- **Stack**: Viene creato un nuovo frame per `foo`, con `x=2` memorizzato nel contesto di `foo` nello stack.
- **Registri**: `IR` è aggiornato per mostrare l'istruzione `y = x * x`. `RAX` è inattivo, in attesa del risultato del calcolo di `y`.
##### Slide 4: (Chiamata alla funzione `foo(2)` all'interno di `bar`)
![[Pasted image 20241112121022.png]]
- **Codice**:
    - All'interno di `bar`, viene chiamata `foo` con l'argomento `2`, assegnato al parametro `x` di `foo`.
- **CPU**:
    - La CPU esegue l’istruzione `call foo(2)` all’interno di `bar`.
    - Il Program Counter (PC) viene aggiornato per puntare all'inizio della funzione `foo`.
    - L'Instruction Register (IR) riflette la chiamata di `foo`.
- **Stack**:
    - Un nuovo frame viene allocato per `foo` sopra `bar`, con `x=2` come variabile locale. Lo stack ora contiene i frame di `main`, `bar`, e `foo(2)` in quest’ordine.
##### Slide 5: (Esecuzione di `y = x * x` in `foo`):
![[Pasted image 20241112121121.png]]
**Esecuzione della funzione `foo(2)` con il calcolo `y = x * x`**:
- **Codice**:
    - `foo` calcola `y = x * x` con `x=2`, ottenendo `y=4`.
- **CPU**:
    - La CPU esegue il calcolo in `foo`. Il valore `4` viene generato e preparato per essere restituito.
    - Il registro `RAX` (spesso usato per i valori di ritorno) viene impostato su `4`, il valore di `y`.
    - Il Program Counter (PC) si aggiorna per puntare all’istruzione di ritorno (`return y`) di `foo`.
- **Stack**:
    - Nessun cambiamento nello stack in questa fase; `foo(2)` rimane attivo in cima mentre completa il calcolo.
##### Slide 6: (Preparazione al Ritorno di `foo` verso `bar`)
![[Pasted image 20241113175353.png]]
**Conclusione di `foo(2)` e ritorno a `bar`**

- **Codice**:
    - `foo` ha completato il calcolo e si appresta a restituire il valore `4` a `bar`.
- **CPU**:
    - La CPU esegue l’istruzione di ritorno (`RET`) in `foo`.
    - Il registro `RAX` contiene `4`, il risultato di `foo`, pronto per essere utilizzato da `bar`.
    - Il Program Counter (PC) viene aggiornato per tornare all’istruzione successiva in `bar`.
- **Stack**:
    - Il frame di `foo` viene rimosso, lasciando `bar` in cima allo stack con `main` alla base.
##### Slide 7: (Assegnazione del Risultato in `bar`)
![[Pasted image 20241113175414.png]]
**- **Codice**:
    - `bar` ha ottenuto il valore `4` da `foo` e conclude la sua esecuzione, pronta per ritornare a `main`.
- **CPU**:
    - La CPU prepara l'istruzione di ritorno (`RET`) per completare `bar`.
    - `RAX` mantiene `4`, il valore calcolato da `foo`.
    - Il Program Counter (PC) si allinea alla prossima istruzione in `main`, che verrà eseguita dopo il ritorno di `bar`.
- **Stack**:
    - Il frame di `bar` è in fase di rimozione, lasciando `main` come unico frame attivo nello stack.
#### Slide 8-16: (Dettaglio delle Operazioni in `foo` e Gestione dei Valori di Ritorno)
##### Slide 8: (Conclusione di `bar` e Ritorno a `main`)
![[Pasted image 20241113175430.png]]
##### Slide 9: (Ritorno da `bar` a `main`)
![[Pasted image 20241113175445.png]]
##### Slide 10 (Esecuzione di `main` dopo il ritorno da `bar`)
![[Pasted image 20241113175504.png]]
- **CPU**:
    
    - La CPU ha appena terminato di eseguire `foo(2)`, e il valore di ritorno, `y=4`, è stato trasferito a `bar`.
    - Ora la CPU si prepara a completare `bar` e a tornare a `main`. Il Program Counter (PC) è puntato verso l’istruzione di ritorno, pronta a completare la funzione `bar`.
- **Stack**:
    
    - Lo stack mostra che `foo` è stato rimosso dopo aver calcolato e restituito il valore `4`.
    - Il frame di `bar` è ancora attivo, ma in fase di chiusura, poiché ha ottenuto il risultato di `foo(2)` e deve solo restituire il controllo a `main`.
- **Registri**:
    
    - Il registro `RAX` contiene `4`, risultato calcolato da `foo(2)`.
    - `IR` (Instruction Register) mostra l'istruzione `return`, indicativa del trasferimento finale da `bar` a `main`.
    - `PC` è allineato alla prossima istruzione in `main`, pronto per riprendere l’esecuzione una volta che `bar` ha completato il ritorno.
##### Slide 11: (Chiamata a `baz` da `main`) 
![[Pasted image 20241113175526.png]]
il diagramma mostra il punto in cui `main` sta per completare l’esecuzione di `bar` e prepararsi a chiamare `baz`. In questo stadio:

1. **CPU**:
    
    - La CPU ha completato l’esecuzione della funzione `bar`, che ha chiamato `foo(2)` per calcolare `y=4`, e ora si prepara a continuare con `baz`.
    - Il Program Counter (PC) è impostato per passare alla chiamata `call baz()`, seguendo la logica di `main`.
2. **Stack**:
    
    - Il frame di `bar` è stato rimosso dallo stack, lasciando `main` come contesto attivo. `main` è in attesa di completare la chiamata a `baz`.
3. **Registri**:
    
    - Il registro `RAX` contiene il valore `4`, il risultato finale della chiamata a `foo(2)` tramite `bar`.
    - Il registro Instruction Register (IR) mostra l'istruzione `call baz()`, segnalando che la funzione successiva da eseguire sarà `baz`, con `PC` pronto per puntare alla nuova istruzione.
##### Slide 12: (Chiamata di `foo(4)` da `baz`)
![[Pasted image 20241113175541.png]]
- **CPU**:
    
    - La CPU ha appena terminato l’esecuzione di `bar` e si prepara ad attivare `baz` tramite `main`. Ora, il Program Counter (PC) è puntato verso la prossima chiamata di funzione, `call baz()`.
- **Stack**:
    
    - `main` è attivo nello stack e sta per invocare `baz`. Lo stack rappresenta `main` come contesto di chiamata e mostra la funzione `baz` in fase di attivazione.
- **Registri**:
    
    - `RAX` contiene il valore `4`, che è il risultato restituito da `foo(2)` tramite `bar`.
    - L'Instruction Register (IR) indica che l'istruzione `call baz()` sarà eseguita successivamente, e `PC` si aggiornerà per gestire la chiamata a `baz`

##### Slide 13: (Esecuzione di `y = x * x` in `foo` con `x = 4`):
![[Pasted image 20241113175556.png]]
il programma si trova nello stato in cui la funzione `baz` ha appena assegnato il valore di `RAX` (risultato di `foo(2)`) alla variabile locale `x`.

Ecco cosa avviene in questa fase:

1. **CPU**:
    
    - La CPU ha eseguito l'istruzione `x = RAX` all'interno di `baz`, che assegna il valore di `RAX` (in questo caso, `16`, risultato del calcolo `foo(4)`) alla variabile `x` in `baz`.
    - Il Program Counter (PC) ora punta alla prossima istruzione di `baz`, che sarà il ritorno a `main` poiché `baz` ha completato le sue operazioni.
2. **Stack**:
    
    - Lo stack mostra `main` come funzione di base, con `baz` come frame attivo. Dopo questa assegnazione, `baz` si prepara a chiudersi e a ritornare a `main`.
    - `foo` è già stato rimosso dallo stack dopo aver completato il calcolo di `y = 16`.
3. **Registri**:
    
    - `RAX` contiene `16`, il valore calcolato da `foo(4)`, ora assegnato alla variabile `x` in `baz`.
    - Il registro Instruction Register (IR) ha mostrato l'istruzione `x = RAX` appena eseguita.
##### Slide 14: (Ritorno da `foo(4)` a `baz`)
![[Pasted image 20241113175620.png]]
- **CPU**:
    
    - La CPU sta processando l'istruzione `RET` di `baz`, segnalando che `baz` sta per completare la sua esecuzione e tornare al chiamante, `main`.
    - La CPU sta preparando il Program Counter (PC) per tornare alla funzione `main`.
- **Stack**:
    
    - Lo stack mostra `main` alla base, e `baz` in fase di ritorno. `foo` è già stato rimosso dallo stack dopo il completamento della chiamata `foo(4)`.
    - `baz` si prepara quindi a rimuovere il proprio frame dallo stack al termine del `RET`.
- **Registri**:
    
    - `RAX` contiene il valore `4`, residuo della chiamata `foo(2)` che era stata effettuata da `bar`. Questo valore non è stato sovrascritto, poiché `baz` non ha utilizzato `RAX` in modo diretto dopo la chiamata a `foo(4)`.
    - Il registro `IR` mostra l'istruzione `RET`, e il PC è pronto a spostarsi al contesto di `main`.
##### Slide 15  (Assegnazione del risultato di `foo(4)` a `x` in `baz`)
![[Pasted image 20241113175648.png]]
Ora che `foo` ha restituito `16`:
- **Aggiornamento della variabile locale**: `baz` assegna il valore restituito da `foo(4)` (cioè `16`) alla variabile locale `x` di `baz`.
- **Preparazione per il ritorno**: Una volta che `x` è stato aggiornato, la funzione `baz` è pronta a restituire il controllo a `main`.
##### Slide 16: (Ritorno da `baz` a `main`)
![[Pasted image 20241113175703.png]]
Quando `baz` termina l'esecuzione:
- **Ripristino dello stack**: Il frame di `baz` viene rimosso dallo stack.
- **Aggiornamento del PC**: Il Program Counter è aggiornato per continuare l'esecuzione di `main` dopo la chiamata a `baz`.
#### Slide 17-23: (Conclusione di `main` e Stato Finale del Programma)
##### Slide 17: (Preparazione alla fine di `main`)
![[Pasted image 20241113175838.png]]
Questa slide mostra la fase in cui `main` sta per chiamare la funzione `baz`:
- **PC e IR**: Il Program Counter (PC) è aggiornato per puntare all'istruzione `call baz()`, mentre l'Instruction Register (IR) contiene questa istruzione, pronta per essere eseguita.
- **Stack**: È presente un frame che tiene traccia del punto di ritorno di `main` dopo la chiamata a `baz`.
##### Slide 18: (Fine dell'esecuzione del programma)
![[Pasted image 20241113180010.png]]
All’interno di `baz`, viene invocata la funzione `foo` con l'argomento `4`. L'immagine mostra:
- **IR aggiornato**: L’Instruction Register ora contiene l'istruzione `call foo(4)`, e PC punta alla prima istruzione di `foo`.
- **Stack**: Lo stack include ora il frame di `baz`, con il puntatore di ritorno aggiornato per riportare il controllo a `baz` al termine della chiamata a `foo`.
##### Slide 19 (po):
![[Pasted image 20241113180517.png]]
Qui viene visualizzata l’operazione `y = x * x` in `foo` con `x = 4`:
- **Calcolo del valore di `y`**: La CPU esegue `y = 4 * 4`, ottenendo `y = 16`, e il valore viene caricato nel registro **RAX**.
- **ALU in uso**: L’ALU esegue l'operazione di moltiplicazione, elaborando `x` e memorizzando `y = 16` in RAX.
##### Slide 20: (Effettivo Ritorno da `foo(4)` a `baz`)
![[Pasted image 20241113180820.png]]
In questa fase, `foo` ha completato il calcolo:
- **Valore di `y` in RAX**: `RAX` contiene il risultato `16`, che rappresenta il valore di ritorno della funzione.
- **PC e IR**: PC punta all'istruzione di ritorno (`return y`) e IR indica l'istruzione `return`, preparando il controllo a tornare a `baz`
##### Slide 21: (Uso del Valore di Ritorno in `baz`)
![[Pasted image 20241113180946.png]]
Questa slide visualizza il momento in cui `foo` termina e restituisce il controllo a `baz`:
- **Valore di ritorno in RAX**: `RAX` conserva il valore `16`, che `baz` utilizza per aggiornare la variabile locale `x`.
- **Rimozione del frame**: Lo stack viene aggiornato per rimuovere il frame di `foo`, e PC punta alla successiva istruzione in `baz`.
##### Slide 22: (Preparazione al Ritorno da `baz` a `main`)
![[Pasted image 20241113181146.png]]In questa fase, `baz` assegna il valore `16` a `x`, la variabile locale:
- **Aggiornamento di x**: Il valore di `16` (presente in **RAX**) viene assegnato alla variabile locale `x` in `baz`.
- **Preparazione per il ritorno**: Una volta assegnato `x`, `baz` è pronta a restituire il controllo a `main`.
##### Slide 23: (Ritorno di `foo(4)` a `baz` e Assegnazione del Risultato)
![[Pasted image 20241113181522.png]]
Dopo aver terminato le proprie operazioni, `baz` torna a `main`:

- **Pulizia dello stack**: Il frame di `baz` viene rimosso dallo stack, lasciando solo il frame di `main`.
- **PC aggiornato**: Il Program Counter (PC) è impostato per riprendere l'esecuzione di `main` subito dopo la chiamata a `baz`.
#### Slide 24-30 (Ciclo di Esecuzione Fetch-Decode-Execute)
##### Slide 24: (Pulizia Finale dello Stack)
![[Pasted image 20241113181537.png]]
Questa slide mostra che `main` è pronto a terminare dopo aver completato la chiamata a `baz`:
- **PC e Stack**: Il Program Counter (PC) è aggiornato per eseguire la parte finale di `main`, e il frame di `baz` è stato rimosso dallo stack, lasciando solo quello di `main`.
- **Valore finale in RAX**: **RAX** contiene `16`, il risultato dell’ultima chiamata a `foo` fatta tramite `baz`.
- **Conclusione di `main`**: L'esecuzione di `main` è quasi completa, e il Program Counter si prepara alla fine del programma.
##### Slide 25-26: (Ripristino dei Registri)
![[Pasted image 20241113181602.png]]
**Ripristino dei Registri della CPU**:
Questa slide rappresenta lo stato finale del programma:

- **Valore finale nel registro RAX**: **RAX** conserva il valore `16`, ottenuto dall'ultima esecuzione di `foo(4)` e rappresenta l'ultimo calcolo eseguito.
- **PC e stack**: Il Program Counter punta ora all'uscita del programma, mentre lo stack è vuoto, segnalando che tutte le chiamate di funzione sono state completate e i relativi frame sono stati rimossi.
- **Indicazione di completamento**: Con lo stack svuotato e RAX contenente il risultato, il programma ha concluso l’esecuzione.
##### Slide 26: Ulteriori dettagli sull’uscita dal programma

Questa slide enfatizza ulteriormente il completamento del programma:

- **Registro RAX invariato**: **RAX** continua a contenere `16`, confermando il valore calcolato come risultato finale.
- **Stack e contesto di esecuzione**: Lo stack è ancora vuoto, e il contesto di esecuzione di `main` è stato completamente liberato, segnalando che non ci sono altre istruzioni da eseguire.
- **PC pronto alla fine**: Il Program Counter punta alla fine, con l’Instruction Register (IR) pronto a uscire dal ciclo di esecuzione.


##### Immagine 27 - Stato Finale della Funzione `main` e Pulizia
![[Pasted image 20241113182233.png]]
A partire da questa slide, vengono illustrate le fasi di esecuzione di una singola istruzione, iniziando con la fase di **fetch**:
- **Fetch dell’istruzione**: La fase di fetch consiste nel prelevare l'istruzione dalla memoria. Per fare ciò, l'indirizzo dell'istruzione corrente, memorizzato nel **RIP** (Registro Instruction Pointer), viene caricato nel registro **MAR** (Memory Address Register).
- **Passaggio a MDR**: Il contenuto dell’indirizzo in **MAR** viene quindi trasferito in **MDR** (Memory Data Register).
- **Incremento di RIP**: Il **RIP** viene incrementato, aggiornandosi per puntare all'istruzione successiva. Questa operazione prepara il ciclo a processare una nuova istruzione dopo quella in corso.
#### Slide 28-30 - Stato di Riposo della CPU:
##### Slide 28: (Ripristino del Program Counter e del Registro delle Istruzioni)
![[Pasted image 20241113182249.png]]
Questa slide descrive la fase **decode**, che segue il fetch:
- **Caricamento in IR**: Una volta che l’istruzione è in **MDR**, questa viene trasferita nel registro **IR** (Instruction Register), dove è pronta per la decodifica.
- **Interpretazione della CU**: La **CU** (Control Unit) interpreta il contenuto di **IR** per determinare il tipo di istruzione (es. operazione aritmetica, movimento di dati, salto condizionale) e i parametri necessari per l’esecuzione.
- **Impostazione dei segnali di controllo**: In base all'istruzione decodificata, la CU attiva i segnali di controllo necessari per l'esecuzione dell'operazione, preparando i registri e l’ALU per l’elaborazione dei dati.
##### Slide 29: (Pulizia Finale dello Stack)
![[Pasted image 20241113182303.png]]
Questa slide rappresenta la fase **execute**, in cui viene effettuata l’operazione vera e propria dell’istruzione:
- **Processo di esecuzione**: La CPU esegue l’operazione definita nell’istruzione (ad esempio, un’operazione aritmetica nell’ALU, un trasferimento di dati tra registri, o un’operazione di accesso in memoria).
- **Utilizzo dei registri e dell'ALU**: Se l’istruzione richiede un calcolo, l’ALU utilizza i valori dei registri coinvolti (come RAX o RBX), eseguendo l’operazione specificata (ad esempio, addizione o moltiplicazione).
- **Aggiornamento dello stato**: Il risultato dell’operazione viene memorizzato nel registro di destinazione specificato nell’istruzione (ad esempio, il valore risultante di un'operazione di somma può essere salvato in RAX).
##### Slide 30: (Stato di Inattività della CPU)
![[Pasted image 20241113182339.png]]
**Stato di Riposo della CPU**:
- La CPU è ora in stato di inattività, o “idle”. Questo significa che non è più impegnata in alcuna esecuzione di istruzioni, e i registri principali come il **Program Counter (PC)** e l’**Instruction Register (IR)** sono azzerati.
- Il **Program Counter (PC)** non punta più ad alcuna istruzione in memoria, segnalando che l’esecuzione è completamente terminata.
 **Pronta per una Nuova Esecuzione**:
- In questo stato di inattività, la CPU è pronta a ricevere nuovi comandi. Il sistema operativo o il gestore del programma potranno caricare un nuovo set di istruzioni o un nuovo programma senza preoccuparsi di dati residui.
 **Sistema in Stato Stabile**:
   - Con i registri e lo stack svuotati e azzerati, la CPU si trova in uno stato stabile. Questo assicura che, qualora un nuovo programma venga avviato, non vi sia alcuna interferenza da dati o istruzioni precedenti.

### Processamento delle istruzioni
Le istruzioni che compongono un programma possono avere un
comportamento complesso
	es: accesso a memoria, utilizzo di più componenti hardware, ...
- L’unità di controllo governa il funzionamento di tutto il sistema, anche delle componenti esterne
Ad alto livello, il processamento delle istruzioni prevede tre fasi:
 1) fetch: prelievo della rappresentazione binaria dell’istruzione dalla memoria di lavoro
 2) decodifica: l’istruzione prelevata viene interpretata per capire come questa dovrà essere eseguita
 3) esecuzione: la semantica dell’istruzione viene effettivamente implementata
- L’unità di controllo deve essere progettata coerentemente con il datapath della CPU
-  Modello uniciclo o multiciclo
#### Modello uniciclo:
- Un’istruzione viene eseguita in un solo colpo di clock
- Il periodo di clock deve essere tarato per garantire che tutta la rete sistabilizzi
- È necessario prevedere componenti hardware dedicate perché non è possibile la condivisione delle componenti
- Ad esempio, se devo eseguire due somme differenti per eseguire un’istruzione, avrò bisogno di due ALU
##### Modello uniciclo: esempio di datapath
$$movw \%ax, \%bx$$
![[Pasted image 20241112122952.png]]

con la lettura sul fronte di salita ed il fronte di discesa avrò un calcolo più preciso dei sotto istanti di un ciclo periodico
##### Modello uniciclo 2:
![[Pasted image 20241112124606.png]]
#### Ciclo istruzione, ciclo macchina, stato macchina:
- Ciclo istruzione: intervallo temporale necessario ad eseguire una istruzione nella sua interezza 
- Ciclo macchina: intervallo temporale necessario ad eseguire una fase (fetch, decode, execute)
	- A seconda del tipo di istruzione, possono essere necessari un numero diverso di cicli macchina (es: più accessi in memoria)
	
- Stato macchina: periodo di tempo necessario per stabilizzare la rete delle unità di controllo e calcolo (corrispondente al clock)
![[Pasted image 20241112124833.png]]
#### Implementazione della CU: le Microoperazioni:
La CU implementa un’istruzione con un insieme di microoperazioni. Ogni microoperazione è definita dai segnali di controllo abilitati in uno specifico stato macchina.
![[Pasted image 20241112124833.png]]
Ogni stato macchina corrisponde all'aggiornamento di una macchina a stati che implementa i microprogrammi.  
### Realizzazione della CU
![[Pasted image 20241112125725.png]]
#### Organizzazione della CU
Per eseguire il microprogramma di un’istruzione, la CU userà come
input:
	• La classe e il tipo dell’istruzione — contenuta in IR
	• Le variabili di condizione che arrivano da fuori la CPU — interazione con
	dispositivi di I/O
	• Le variabili di condizione che arrivano da dentro la CPU — ad esempio i bit di FLAGS
	• La modalità di indirizzamento degli operandi dell’istruzione — dedotta
da IR
Il numero di segnali di output della CU dipende dall’implementazione
della PU e dei moduli esterni. 
==L’organizzazione della CU dipende dal costo implementativo, dalle prestazioni desiderate e dal tipo di macchina a stati finiti scelta (Maley o Moore)==
#### La CU come macchina di Mealy:
La CU è una rete sequenziale complessa, con molte variabili in input e output. Le funzioni $\delta$ e $\omega$ della macchina possono essere rappresentate tramite una ROM, essa però va "paginata" in funzione dei microprogrammi.
Ad ogni colpo di clock, vengono emessi i segnali di controllo per implementare una microoperazione
![[Pasted image 20241112153513.png]]
#### Paginazione dei microprogrammi:
Ogni pagina è associata ad un microprogramma di una classe di operazioni, per questo le operazioni "simili" sono raggruppate nella stessa classe.
La decodifica di un'istruzione può quindi essere svolta inizializzando il registro di base con il codice della classe. Bisogna ricordarsi che non tutti i microprogrammi hanno la stessa lunghezza, quindi il trade off (ciò che vado a perdere) necessaria una frammentazione interna
I codici che mi interessano:
Indirizzo pagine 0 = 000 000
Indirizzo pagina 1 = 001 000
Indirizzo pagina 2 = 010 000 
questo poiché bastano 3 bit per esprimere quello che può esserci utili.
Questo significa che se voglio saltare da un programma ad un altro, posso semplicemente inserire  il codice della classe che mi interessa.
![[Pasted image 20241112154106.png]]
In questo modo vado a diminuire il tempo di esecuzione della fase di decode

#### Riduzione delle variabili in input:
Visto che il numero di variabili in input può essere molto grande, andando a complicare la sintesi da parte della macchina, e che non tutti i segnali servono per eseguire tutti i passi dei microprogrammi, è possibile implementare una strategia di selezione:
1) Si identifica la microoperazione con il numero massimo di variabili in input
2) si ridirezionano le variabili in input su un numero minore di segnali.
### Fase di Fetch:
L'esecuzione di ogni istruzione incomincia ocn la fase di fetch, le cui microoperazioni associate sono :
- MAR  <- RIP Copio l'indirizzo in MAR
- MDR <- (MAR); ciò che ha la memoria lo scrivo nel Memory Data Register RIP <- RIP +8 in parallelo posso incrementare l'Instruction pointer di 8 (dimensione minima di codifica di un istruzione)
- IR <- MDR Quindi nel MDR ci sarà la prossima istruzione che va messa nell
In questo modo, l'istruzione successiva viene caricata nel registro IR, in modo tale da poter essere interpretata ed eseguita. Il valore di RIP viene così incrementato in modo tale da puntare alla prossima istruzione/dato. 

#### Illustrazione della fase di Fetch:
![[Pasted image 20241115111226.png]]
1) Istruzione: Abilito la scrittura su MAR
![[Pasted image 20241115111013.png]]
2) abilito il buffer three state, quindi mando il segnale alla memoria.
![[Pasted image 20241115111242.png]]
3) Nel mentre che aspetto la memoria invio un segnale di controllo, poiché la frequenza di clock della memoria è un multiplo della frequenza di clock del processore, nel mentre che arriva il segnale codificato si attivano i segnali di controllo
![[Pasted image 20241115111259.png]]


![[Pasted image 20241115111312.png]]
5) devo copiare il segnale nel IR dalla memoria
![[Pasted image 20241115111321.png]]
#### Istruzione movimento dati
Devo eseguire la fase di Fetch attraverso le microoperazioni
Ipotizziamo di voler spostare un registro in un altro:
$$movq~\%rax,~\%rqx$$

# Capitolo 9: (Assembly)
### Compilazione
Normalmente il processo di compilazione dei file funziona cosi. Si ha un binomio tra c e assembly.
![[Pasted image 20241118143126.png]]
#### Esempio:
Possiamo vedere un esempio di come un semplice codice in C funzioni in Assembly.
![[Pasted image 20241118150213.png]]
![[Pasted image 20241118150932.png]]
Ciò che succede nella prima parte, ovvero nella dichiarazione del main, è il setup dello stack, attraverso il registro che punta alla memoria stack (Register Stack Pointer), nel quale ci sono le variabili locali e gli indirizzi di ritorno ed un altro registro, chiamato "RBP", (Register Base Pointer) che punta alla base dello stack.
Poiché nella dichiarazione della funzione vado ad introdurre delle variabili, devo far scendere il puntatore dello stack verso il basso, in modo tale da inserire le variabili  in uno spazio preciso.
L'organizzazione di partenza è:
![[Pasted image 20241118152213.png]]
Successivamente, una volta eseguito il comando, anche il RBP punterà allo stesso di RSP, in modo tale da far capire al RSP di andare avanti con le istruzioni, e il processo è continuo.
Dopo essere entrati nella funzione main, il puntatore RSP sarà portato nuovamente in alto, così come il RBP.








### I Debugger:
I debugger ci consentono di controllare l’esecuzione di un programma, interrompendo l’esecuzione in maniera selettiva. Quando è interrotta l'esecuzione, possiamo osservare lo stato dei registri, lo stato della memoria, il codice sorgente originale.
Possiamo inoltre modificare lo stato del programma, come cambiare una variabile, prima di riprendere l'esecuzione.
#### Esempio con GDB Cheatsheey:
![[Pasted image 20241118150914.png]]
### Direttive assembly:
- `label`: mnemonico testuale definito dal programmatore ed associato all'indirizzo di ciò che la segue immediatamente dopo
- `Location Counter` identificato da ., viene valutato con il valore dell'indirizzo corrente.
	- può essere impostato esplicitamente per far "saltare" la generazione di indirizzi.
	- può essere usato per calcolare le dimensioni di strutture dati; **msg**:
		.ascii "Hello, world!\\n"
		len= .-**msg**
- `.org address, fill`: metodo alternativo di impostare il location counter, impostando i byte a fill
- `.equ` symbol, expression: definisce una costante (non occupa memoria al tempo della dichiarazione)
	- metodo alternativo `symbol = expression`
	- Lo stesso simbolo può essere utilizzato in più parti del codice
	- Non si può usare il simbolo prima della sua definizione (_one pass scan_)
-  `.byte` expressions: riserva memoria (di dimensione byte) per expressions: var: .byte 0 array: .byte 0, 1, 2, 3, 4, 5 
- `.word` expressions: riserva memoria (di dimensione word) per expressions
- .long expressions: riserva memoria (di dimensione longword) per expressions 
-  `.quad` expressions: riserva memoria (di dimensione quadword) per expressions 23 Direttive assembly 
- `.ascii “string”`: riserva memoria per un vettore di caratteri e imposta il valore a string 
- `.fill repeat, size, value`: riserva una regione di memoria composta da repeat celle di dimensione size impostate a value (size e value sono opzionali (default: size = 1, value = 0)). 
- `.text`: tutto ciò che compare da qui in poi va nella sezione testo 
- `.data`: tutto ciò che compare da qui in poi va nella sezione data 
- `.comm symbol, length`: dichiara un’area di memoria con nome (symbol) di dimensione length nella sezione .bss 
- `.driver ivn` : identifica l’inizio della routine di servizio associato al codice ivn
#### Altre istruzioni:
[[#Alcune istruzioni assembly]]
[[#Classi]]
### Strutture di controllo:
#### Esempio:
Andiamo a scrivere una comparazione fra un codice ipotetico scritto in C e uno in Assembly
![[Pasted image 20241119123316.png]]
##### Codice in C
Nel codice a sinistra scritto in **C**, abbiamo una struttura condizionale con tre blocchi di codice (`CODE BLOCK A`, `CODE BLOCK B`, `CODE BLOCK C`) che vengono eseguiti in base al valore della variabile `x`:

1. **`if (x == 1)`**:
   - Se la condizione è vera (`x` è uguale a 1), viene eseguito il `CODE BLOCK A`.
   
2. **`else if (x == 2)`**:
   - Se la prima condizione è falsa, ma la seconda condizione (`x == 2`) è vera, viene eseguito il `CODE BLOCK B`.

3. **`else`**:
   - Se entrambe le condizioni precedenti sono false, viene eseguito il `CODE BLOCK C`.

---
##### Traduzione in Assembly
A destra, vediamo come questo codice viene tradotto in **Assembly**, un linguaggio a basso livello. Ogni blocco del codice in C è rappresentato da istruzioni Assembly specifiche.

1. **Primo confronto: `if (x == 1)`**
   - **`cmpb $1, %al`**:
     Questa istruzione confronta il valore immagazzinato nel registro `%al` (assumendo che contenga `x`) con il valore `1`. 
     - Se `x` è diverso da `1`, si verifica una condizione di "non zero" e si passa all'etichetta `.elseif` tramite l'istruzione **`jnz .elseif`**.
     - Se `x` è uguale a `1`, viene eseguito il `CODE BLOCK A` (rappresentato da un commento).
     - Dopo il `CODE BLOCK A`, c'è un salto diretto a `.endif` tramite **`jmp .endif`**, per evitare l'esecuzione degli altri blocchi.

2. **Secondo confronto: `else if (x == 2)`**
   - **`.elseif:`**:
     Questo è un'etichetta (un punto nel codice a cui si può saltare).
   - **`cmpb $2, %al`**:
     Qui si confronta `x` con `2`. 
     - Se `x` è diverso da `2`, si passa al blocco successivo (`.else`) tramite l'istruzione **`jnz .else`**.
     - Se `x` è uguale a `2`, viene eseguito il `CODE BLOCK B`.
     - Dopo il `CODE BLOCK B`, un salto diretto a `.endif` con **`jmp .endif`** evita di eseguire il codice del blocco `else`.

3. **Ultimo caso: `else`**
   - **`.else:`**:
     Se nessuna delle condizioni precedenti è vera (`x != 1` e `x != 2`), si entra in questo blocco, dove viene eseguito il `CODE BLOCK C`.

4. **Fine del controllo: `.endif`**
   - **`.endif:`**:
     Questo rappresenta il punto in cui termina la struttura condizionale. Dopo l'esecuzione di uno dei blocchi, il programma continua qui.

---

##### Dettaglio delle istruzioni Assembly
- **`cmpb $X, %al`**: Confronta il valore `X` con il contenuto del registro `%al` (che presumibilmente contiene la variabile `x`). Non modifica `%al`, ma aggiorna i **flag** del processore (ad esempio il flag Zero, ZF, se i valori confrontati sono uguali).
- **`jnz` (Jump if Not Zero)**: Salta a una determinata etichetta se il risultato del confronto non è zero (cioè se i due valori sono diversi).
- **`jmp` (Jump)**: Esegue un salto incondizionato all'etichetta indicata.

---

##### Flusso logico del codice Assembly
Il codice Assembly segue il seguente flusso logico:
1. Confronta `x` con `1`.
   - Se `x == 1`, esegue il `CODE BLOCK A` e salta alla fine della struttura (`.endif`).
   - Altrimenti, passa al prossimo confronto.
2. Confronta `x` con `2`.
   - Se `x == 2`, esegue il `CODE BLOCK B` e salta alla fine della struttura (`.endif`).
   - Altrimenti, entra nel blocco `else`.
3. Se nessuna condizione è vera, esegue il `CODE BLOCK C`.

---
##### Differenze tra C e Assembly
- In **C**, le condizioni sono espresse in modo più leggibile e dichiarativo. Il compilatore si occupa di tradurle in istruzioni specifiche.
- In **Assembly**, il programmatore deve gestire manualmente ogni confronto, salto e percorso logico utilizzando istruzioni come `cmpb`, `jnz`, e `jmp`.

---
#### Aggiornamento del Carry Flag:
Ricordiamo che Il **Carry Flag** è un bit del registro di stato della CPU che segnala:

1. **Un prestito** nelle operazioni di sottrazione.
2. **Un riporto** nelle operazioni di addizione.

Analizziamo i casi specifici:
1) L'operazione a-b richiede un prestito quando b è maggiore di a. 
	- a = 3, b = 5
	
2) Nel caso di sottrazione, la CU rileva la necessità di prestito verificando se l'addizione in complemento a 2 corrispondente determina un riporto:
	
	- La CPU esegue la sottrazione convertendola in un'**addizione** utilizzando il **complemento a 2** del valore da sottrarre.
	- Il complemento a 2 di un numero `b` si calcola così:
	    1. Inverti i bit di `b`.
	    2. Somma 1 al risultato.
     quindi: _a + (complemento a 2 di b)
	
3)  Se nell'addizione non c'è un riporto, allora c'è un prestito nella sottrazione, in altre parole 
	- Se la somma dell'addizione (con complemento a 2) **non genera un riporto**, significa che è stato necessario fare un **prestito**. Di conseguenza, il **Carry Flag (CF)** viene impostato a **1**.
	- Esempio: 
```
a = 3 (binario: 0000 0011)
b = 5 (complemento a 2: 1111 1011)
a + complemento a 2 di b:
0000 0011 +
1111 1011
---------------
0000 0000 (riporto = 0, quindi CF = 1)
25
```
Viceversa:
- Se c'è un riporto nell'addizione, allora non c'è un prestito nella sottrazione e dunque **CF = 0**.
Infine possiamo dire che:
- Nel caso di esecuzione di `sub`, CF viene negato. Quando si utilizza l'istruzione **`sub`** per eseguire una sottrazione, il **Carry Flag (CF)** viene interpretato in modo **negativo**.

	- **CF = 1** → C'è stato un **prestito** (la sottrazione ha richiesto un prestito).
	- **CF = 0** → Non c'è stato un prestito.
#### Confronti in aritmetica non segnata:
##### Cosa significa?
**`cmp`** è un'istruzione di confronto che:
- **Sottrae** il valore della sorgente (source) dalla destinazione (dest).
- **Non salva il risultato della sottrazione** ma aggiorna i **bit del registro FLAGS**.
- I **flag aggiornati** (come CF e ZF) possono essere utilizzati per prendere decisioni logiche (ad esempio, nei salti condizionali).
Dopo l'esecuzione di `cmp`, i due bit più rilevanti sono:
- **CF (Carry Flag)**: Indica un **prestito** in sottrazione (vedi [[#Aggiornamento del Carry Flag]]). Esso è fondamentale in **aritmetica non segnata** per verificare la relazione tra gli operandi.
	- **CF = 1**: la sorgente è maggiore della destinazione.
	- **CF = 0**: la sorgente è minore o uguale alla destinazione.
- **ZF (Zero Flag)**: il quale indica se il risultato della sottrazione è **zero**.
    - **ZF = 1**: i due valori sono uguali.
    - **ZF = 0**: i due valori sono diversi.

La tabella mostra come determinare la relazione tra la destinazione (`dest`) e la sorgente (`source`) usando **CF** e **ZF**.
##### Tabella:
![[Pasted image 20241119124456.png]]
1. **`dest < source`**:
    - Quando la destinazione è **minore** della sorgente:
        - **CF = 1**: Si verifica un prestito nella sottrazione.
    - Il valore dello ZF non è rilevante in questo caso.
2. **`dest > source`**:
    - Quando la destinazione è **maggiore** della sorgente:
        - **CF = 0**: Non c'è prestito.
        - **ZF = 0**: La sottrazione non dà zero (valori diversi).
3. **`dest == source`**:
    - Quando la destinazione è **uguale** alla sorgente:
        - **ZF = 1**: Il risultato della sottrazione è zero.
    - Il valore di CF non è rilevante in questo caso.
4. **`$$dest != source$$**:
    - Quando la destinazione è **diversa** dalla sorgente:
        - **ZF = 0**: La sottrazione non dà zero.
##### Uso pratico:
Dopo l'istruzione **`cmp dest, source`**, puoi usare istruzioni condizionali basate su CF e ZF:
- **`jnc` (Jump if No Carry)**: Salta se **CF = 0** (dest ≥ source in aritmetica non segnata).
- **`jz` (Jump if Zero)**: Salta se **ZF = 1** (dest == source).
- **`jnz` (Jump if Not Zero)**: Salta se **ZF = 0** (dest != source).
- **`jc` (Jump if Carry)**: Salta se **CF = 1** (dest < source)
#### Confronti in aritmetica segnata:
##### Cosa significa?
- CF non ha alcun significato nel caso di operazioni in complemento a due: l’overflow si verifica confrontando gli ultimi due riporti 
	- - **CF è significativo solo per numeri senza segno** (unsigned).
	- Per numeri con segno, ciò che conta è:
	    - Il **flag di segno (SF)**, che indica se il risultato è negativo.
	    - Il **flag di overflow (OF)**, che segnala se c’è stato un errore nel segno dovuto a un overflow.
Per effettuare confronti, effettuiamo una sottrazione (cmp): ci chiediamo se è vero che `dest - src < 0`
Il risultato di questa disequazione è dato dal flag di segno SF, ma, se c’è stato un overflow, allora il segno è cambiato.
Il bit OF è calcolato come lo xor degli ultimi due riporti: determina se c’è stato un overflow 
 - Se non si è verificato overflow, la disuguaglianza è verificata se SF=1. 
 - Se si è verificato un overflow, la disuguaglianza è verificata se SF=0.
##### Esempio:
Se stai confrontando `dest = -127` con `src = 1`:
- La sottrazione `-127 - 1 = -128` è rappresentabile.
- **SF = 1** (risultato negativo), **OF = 0** → confronto affidabile.
Ora confrontiamo `dest = 127` con `src = -1`:
- La sottrazione `127 - (-1) = 128` provoca overflow (non rappresentabile come numero con segno a 8 bit).
- **OF = 1**, quindi il risultato di SF potrebbe essere errato.
#### Esempio Assembly 
![[Pasted image 20241119175928.png]]
##### 1. Scenario
L'obiettivo di questo codice è impostare il valore `1` all'indirizzo **0x1280**, ma **solo se il valore di `x` è maggiore di `y`**.  
In particolare:
- `x` e `y` sono dichiarati come variabili in `.data` e possono assumere valori **negativi**, quindi è necessario utilizzare i confronti **con segno**.

---
##### 2. Struttura del codice
Il codice Assembly lavora in modo sequenziale:
**Sezione `.data`**
```asm
x: .word 3
y: .word -2
```
- `x` contiene il valore `3`.
- `y` contiene il valore `-2`.

---
**Sezione `.text`**
Questa è la sezione del programma eseguibile.
###### Passo 2.1. Caricamento dei valori nei registri
```asm
movw x, %ax
movw y, %bx
cmpw %bx, %ax
```
- **`movw x, %ax`**: Carica il valore di `x` (3) nel registro **`%ax`**.
- **`movw y, %bx`**: Carica il valore di `y` (-2) nel registro **`%bx`**.
- **`cmpw %bx, %ax`**: Confronta `x` (`%ax`) con `y` (`%bx`) facendo una **sottrazione** logica:  
  $$Risultato~x−y=3−(−2)=5$$

I **flag** (**ZF, SF, OF**) vengono aggiornati in base al risultato del confronto.

---

###### Passo 2.2: Controllo dei flag
Il codice controlla i **Sign Flag (SF)** e **Overflow Flag (OF)** per determinare la relazione tra `x` e `y`.
- **Caso 1: `x == y`**
  ```asm
  jz .nonImpostare
  ```
  - **`jz`**: Salta a `.nonImpostare` se il **Zero Flag (ZF)** è attivo, ovvero se `x` è uguale a `y`.

---

- **Caso 2: `x < y`**
  ```asm
  js .SFset
  jo .nonImpostare
  ```
  - **`js`**: Salta a `.SFset` se il **Sign Flag (SF)** è attivo, cioè se il risultato della sottrazione `x - y` è negativo (`x < y`).
  - **`jo`**: Salta a `.nonImpostare` se il **Overflow Flag (OF)** è attivo. Questo verifica che l'overflow non invalidi il confronto.

---

- **Caso 3: `x > y`**
  ```asm
  jno .nonImpostare
  ```
  - **`jno`**: Salta a `.nonImpostare` se non c'è overflow (**OF = 0**). In questo caso, si conferma che `x > y`.

---

###### Passo 2.3: Azione finale
Se i controlli precedenti indicano che `x > y`:
```asm
movb $1, 0x1280
```
- Imposta il valore `1` all'indirizzo **0x1280**.

Se invece i controlli mostrano che `x ≤ y`:
```asm
jmp .nonImpostare
```
- Salta alla label `.nonImpostare`, dove il programma termina senza eseguire l’operazione.

---

##### 3. Collegamento con l'aritmetica con segno
Questo programma sfrutta **SF** e **OF** per gestire i confronti correttamente:
- **SF** verifica se il risultato è negativo.
- **OF** gestisce eventuali overflow nei calcoli con segno, che potrebbero alterare il significato del confronto.

---

##### 4. Esempio pratico
Con i valori forniti (`x = 3`, `y = -2`):
1. La sottrazione `3 - (-2)` dà `5`.
2. Il **Sign Flag (SF)** è `0` (risultato positivo).
3. Non c'è overflow (**OF = 0**).
4. Il valore `1` viene scritto all'indirizzo **0x1280**, poiché `x > y`.

---
#### Pseudo operazioni:
Alcuni costrutti assembly possono essere complessi o ripetitivi, quindi l’assemblatore può fornire pseudo-operazioni per semplificare il processo di sviluppo.
Queste sono operazioni non realmente implementate in hardware che l’assemblatore sostituisce con blocchi di codice equivalenti. 
Lo z64 implementa come pseudo-operazioni le istruzioni x86 per i confronti in aritmetica segnata e non segnata
![[Pasted image 20241119180303.png]]


### Switch:
#### Codice 1.0
Partiamo dal caso in cui il codice in assembly è eccessivamente lungo:
![[Pasted image 20241119125623.png]]
##### Codice in C (a sinistra)

La struttura **switch-case** viene utilizzata per eseguire uno specifico blocco di codice in base al valore della variabile `var`.

1. **`switch(var)`**:
    
    - Controlla il valore della variabile `var` e, in base ad esso, esegue uno dei blocchi `case`.
2. **Blocchi `case`**:
    
    - **`case 1:`**: Se `var` vale `1`, viene eseguito il primo blocco di codice. Il comando `break` assicura che il flusso non continui verso gli altri blocchi.
    - **`case 2:`**, **`case 3:`**, **`case 4:`**: Analogamente, se `var` vale rispettivamente `2`, `3` o `4`, viene eseguito il codice corrispondente.
    - **`default:`**: Se il valore di `var` non corrisponde a nessuno dei casi precedenti, viene eseguito il codice di default.
3. **`break`**:
    
    - Serve per uscire dal blocco `switch` una volta completato il codice del caso specifico, evitando che vengano eseguiti anche i casi successivi.

---

##### Codice in Assembly (a destra)

La traduzione in Assembly della struttura **switch-case** utilizza un insieme di confronti (`cmp`) e salti condizionali (`jz` e `jmp`) per replicare il comportamento del codice in **C**.

---

##### Dettaglio delle istruzioni

1. **Confronto del valore della variabile `var`**:
    
    - **`cmpl $5, var`**:
        - Confronta il valore di `var` con `5`.
        - Se `var` è maggiore di `5` (o il confronto non è valido), si salta al blocco `default` tramite **`jnc .default`**.
    - **`cmpl $4, var`**:
        - Se `var` è uguale a `4`, il programma salta direttamente al blocco `case4` con **`jz .case4`**.
    - **`cmpl $3, var`**:
        - Se `var` è uguale a `3`, il programma salta al blocco `case3` con **`jz .case3`**.
    - **`cmpl $2, var`**:
        - Se `var` è uguale a `2`, il programma salta al blocco `case2` con **`jz .case2`**.
    - **`cmpl $1, var`**:
        - Se `var` è uguale a `1`, il programma salta al blocco `case1`.
2. **Blocchi di codice**:
    
    - **`.case1:`**:
        - Qui viene eseguito il codice del `case 1` (commentato come `# CODE`).
        - Dopo l'esecuzione, c'è un salto diretto alla fine della struttura con **`jmp .end`** per evitare di eseguire i casi successivi.
    - **`.case2:`**, **`.case3:`**, **`.case4:`**:
        - Seguono lo stesso schema: eseguono il codice del caso corrispondente e poi saltano alla fine con `jmp .end`.
    - **`.default:`**:
        - Se nessuno dei casi corrisponde, viene eseguito il codice del blocco `default`.
3. **Fine della struttura `switch`**:
    
    - **`.end:`**:
        - Rappresenta il punto in cui termina la struttura `switch`. Dopo questo punto, il programma continua con le istruzioni successive.

---

##### Flusso Logico del Codice Assembly

1. Il valore di `var` viene confrontato con ciascun caso, partendo dal valore più alto (`5`) verso il valore più basso (`1`).
2. Quando una condizione è soddisfatta (`jz` - Jump if Zero), il flusso del programma salta direttamente al blocco corrispondente (`.case1`, `.case2`, ecc.).
3. Dopo aver eseguito il codice del caso specifico, viene eseguito un salto incondizionato (`jmp .end`) per evitare l'esecuzione dei casi successivi.
4. Se nessuna condizione è vera, viene eseguito il blocco `default`.

---

##### Differenze tra C e Assembly
- In **C**, la struttura `switch-case` è leggibile e astratta. È il compilatore che si occupa di ottimizzarla e tradurla in salti condizionali.
- In **Assembly**, il programmatore deve implementare manualmente ogni confronto e salto, rendendo esplicito il flusso logico e aumentando il controllo (ma anche la complessità).
##### Problemi:
- La lunghezza del codice è elevata  
- È necessario fare un confronto per tutti i valori di ciascun case
##### Soluzione:
Si possono utilizzare delle tabelle di salto:
sono vettori in memoria che associano un case ad un indirizzo. E' necessario considerare "buchi" nei valori associati ai case:
![[Pasted image 20241119134536.png]]
#### Codice 1.1: 
Avendo risolto i problemi precedenti (vedi [[#Codice 1.0#Problemi]]), possiamo scrivere il codice finale completo:
![[Pasted image 20241119135104.png]]
##### Cosa cambia rispetto a prima?
1. **Approccio basato su confronti sequenziali (1.0)**:
   - Ogni caso veniva gestito con un confronto (`cmp`) e un salto condizionale (`jz` o `jnc`).
   - Il numero di confronti cresce con il numero di casi: più casi ci sono, più confronti e salti devono essere eseguiti, il che può rallentare l'esecuzione.
2. **Approccio basato su una tabella di salti (1.1)**:
   - Assembly usa una **jump table**, una struttura dati che contiene gli indirizzi dei blocchi di codice associati ai diversi casi.
   - Invece di confrontare `var` con ogni caso, il valore di `var` viene usato come **indice** per accedere alla jump table, e l'esecuzione salta direttamente al blocco di codice corrispondente.

---

##### Codice Assembly in 1.1
Vediamo passo per passo cosa succede nel nuovo approccio.
1. **Confronto iniziale:**
   - **`cmpl $5, var`**:
     - Si controlla se `var` è maggiore di `5`.
     - Se `var > 5`, si salta direttamente al blocco `.default` con **`jnc .default`** (jump if not carry).
     - Questo serve per gestire valori di `var` che non rientrano nell'intervallo dei casi definiti.

2. **Caricamento del valore di `var` nel registro:**
   - **`movzq var, %rax`**:
     - Copia il valore di `var` nel registro `%rax`, con zero-extension (movimento da 32 bit a 64 bit per supportare indirizzi a 64 bit).
     - `%rax` diventerà l'indice per accedere alla jump table.

3. **Calcolo dell'indirizzo nella jump table:**
   - **`shl $3, %rax`**:
     - Esegue uno *shift sinistro* del valore in `%rax` di 3 bit (moltiplicazione per 8). Questo serve a convertire l'indice in un offset in byte, dato che ogni voce nella jump table occupa 8 byte (indirizzi a 64 bit).
     - Ad esempio:
       - Se `var == 1`, `%rax` diventa `8`.
       - Se `var == 2`, `%rax` diventa `16`, e così via.

4. **Accesso alla jump table:**
   - **`movq branchTable(%rax), %rax`**:
     - Usa il valore di `%rax` come offset per accedere alla **jump table** (`branchTable`), caricando l'indirizzo del blocco di codice corrispondente al caso in `%rax`.

5. **Salto al caso specifico:**
   - **`jmp *%rax`**:
     - Salta all'indirizzo memorizzato in `%rax`, cioè al blocco di codice corrispondente al caso selezionato.

6. **Blocco `.default`:**
   - Se nessun caso corrisponde, viene eseguito il codice del blocco `default`.

---

##### Vantaggi della jump table
1. **Efficienza**:
   - Con una jump table, il numero di istruzioni eseguite è costante, indipendentemente dal numero di casi. Invece di confrontare `var` con ogni valore (`case 1`, `case 2`, ecc.), si effettua un unico accesso alla tabella e un salto diretto.

2. **Riduzione dei salti condizionali**:
   - Questo approccio elimina la necessità di una lunga sequenza di confronti e salti condizionali. Ciò migliora le prestazioni, soprattutto quando ci sono molti casi.

3. **Predicibilità**:
   - Le jump table sfruttano meglio la **predizione dei salti** del processore (branch prediction), rendendo l'esecuzione più veloce rispetto a una lunga catena di salti condizionali.

---

##### Quando si usa una jump table?
- **Jump tables** sono usate dal compilatore quando i valori dei casi (`case`) sono **contigui** o **quasi contigui**, come in questo esempio (`1, 2, 3, 4, ...`).
- Se i valori fossero sparsi (es. `case 1, case 100, case 1000`), il compilatore potrebbe preferire una serie di confronti condizionali, perché una jump table sarebbe inefficiente (troppi "buchi" nella tabella).
### Salti e chiamate a funzioni:
#### Codice "goto":
![[Pasted image 20241122113410.png]]
La funzione `goto` è una funzione di salto, che equivale ad un'istruzione del tipo `jmp` o `jX`.
### Cicli:
#### While:
![[Pasted image 20241122113549.png]]
Esso dice che devo iterare lo stesso blocco di codice finché while la condizione non è più verificata. In assembly il codice potrebbe non essere 
eseguito perchè la condizione è verificata all'inizio.

---
#### Do While:
![[Pasted image 20241122113702.png]]
Qui invece il numero minimo di iterazioni è 1 perchè il codice viene verificato dopo l'esecuzione del primo codice.

---
#### For:
![[Pasted image 20241122113946.png]]
il codice in assembly corrisponde a $$for(int~i = 0,~i < 3,~i++)$$
#### Break e Continue:
Essendo entrambi utilizzati per saltare o fuori dal ciclo, o rieseguirlo, possiamo implementarli con istruzioni di tipo  `jump`
##### Break:
Serve a fermare il ciclo e uscirne, quindi utilizzeremo `jmp .end`
##### Continue:
Serve a fermare il ciclo e ricominciare escludendo un valore preciso, quindi utilizzeremo `jmp .test` per "farlo ricominciare"
### Tipi di dato:
Ogni variabile, in C, ha un tipo, differentemente dagli altri linguaggi. Esse possono essere raggruppate in tre tipologie:
- Tipi primitivi (interi, virgola mobile,.. )
- Tipi aggregati (strutture, unioni), sono insiemi di tipi primitivi
- Puntatori
#### Variabili:
Ogni variabile dichiarata nel programma ha un certo ambito (scope), che determina la visibilità della variabile a determinate porzioni del programma: 
- variabili globali: occupano memoria all’interno delle sezioni .data e .bss: visibili da tutte le funzioni
- variabili locali (o automatiche): occupano memoria all’interno dello stack: visibili alla funzione stessa (o a funzioni chiamate, se passate tramite puntatori)
Dal punto di vista del processore, ogni accesso a variabile viene rappresentato da un accesso all’indirizzo di memoria associato alla variabile. Le variabili locali sono “valide” fino a che l’area di stack in cui sono memorizzate è valida

### Stack
#### Introduzione:
Le variabili automatiche di una funzione occupano memoria all’interno dello stack. Da questo è possibile distinguere il "contesto" di esecuzione di una funzione poiché all'ingresso viene automaticamente creato una _finestra di stack_ (o record di attivazione).
Durante la creazione, viene riservato spazio per le variabili automatiche, ed il contesto contiene anche l'indirizzo di ritorno all'istruzione successiva al salto a funzione. Al termine della funzione, il record di attivazione viene _invalidato logicamente_, il suo contenuto permane in memoria fino a successiva sovrascrittura.
#### Finestra di stack:
![[Pasted image 20241122122031.png]]
##### Spiegazione:
###### 1. Il contesto: lo stack frame
Quando si entra in una funzione in assembly (o attraverso il compilatore), viene creata una struttura temporanea nello stack per gestire variabili locali, parametri, e salvare il contesto (come il valore del registro base `%rbp`).

- **Registro `%rbp`**: è il "base pointer", che punta all'inizio dello stack frame della funzione corrente.
- **Registro `%rsp`**: è il "stack pointer", che punta alla cima dello stack (cioè all'ultima variabile allocata o all'area disponibile).

---
###### 2. L'istruzione `leave`
La funzione di `leave` è "smontare" lo stack frame della funzione corrente, cioè:
1. Ripristinare il registro `%rsp` al valore che aveva all'inizio della funzione (il valore originale di `%rbp`).
2. Ripristinare il valore di `%rbp` che apparteneva alla funzione chiamante (il valore salvato nello stack).
 ---

###### 3. Analisi dettagliata delle due istruzioni
 **a. `mov %rbp, %rsp`**
- Questa istruzione copia il valore di `%rbp` nel registro `%rsp`.
- Cosa significa:
    - `%rbp` punta all'inizio dello stack frame (dove il vecchio `%rbp` è stato salvato all'inizio della funzione).
    - Copiando `%rbp` in `%rsp`, si fa sì che il puntatore dello stack (`%rsp`) torni esattamente a questo punto.
- Effetto: si dealloca l'area dello stack occupata dalle variabili locali.
 **b. `pop %rbp`**
- Questa istruzione rimuove (e ripristina) il valore di `%rbp` precedentemente salvato nello stack.
- Cosa significa:
    - Lo stack pointer (`%rsp`) punta al valore vecchio di `%rbp` salvato nello stack.
    - `pop` preleva quel valore e lo mette in `%rbp`, avanzando `%rsp` di 8 byte (su sistemi a 64 bit).
- Effetto: `%rbp` viene ripristinato al valore che aveva nella funzione chiamante, cioè al "base pointer" originale.

---
###### 4. Concetto di "invalidare la finestra di stack corrente"

La frase _"invalida la finestra di stack corrente"_ significa che l'istruzione `leave` smantella lo stack frame della funzione corrente:

- Il puntatore dello stack `%rsp` viene riportato indietro all'inizio del frame (deallocando l'area locale della funzione).
- Il valore del base pointer `%rbp` viene ripristinato per il chiamante.

Dopo queste operazioni, lo stack frame della funzione corrente non esiste più; lo stack è pronto per essere usato dalla funzione chiamante.

---
### Passaggio di parametri: Convenzioni di chiamata
Affinché una subroutine chiamante possa correttamente dialogare con la subroutine chiamata, occorre mettersi d’accordo su come passare i parametri ed il valore di ritorno. Le convenzioni di chiamata dipendono dal singolo sistema e dalla singola architettura
Le convenzioni principali permettono di passare i parametri tramite:
- lo stack
- i registri
- un misto delle due tecniche (utilizzata dall'architettura x86)
Le calling conventions definiscono anche quali registri possono essere utilizzati per memorizzare dati.
#### Calling convention z64/x86
I primi 6 parametri (interi e indirizzi) di una subroutine vengono passati tramite registri:
- RDI, RSI, RDX, RCX, R8, R9.
Se una subroutine accetta più di 6 parametri, si utilizza lo stack per quelli aggiuntivi
SI utilizzano dei registri per il valore di ritorno:
RAX e RDX
I registri sono divisi in 
- callee-save: RBP, RBX, R12-R15. Questi registri devono essere salvati dal chiamante, prima e dopo una funzione andranno utilizzati pop e push
- caller-save: tutti gli altri. Il registro si salva in automatico.

#### Anatomia dello stack:
Immaginiamo di avere la seguente funzione:
![[Pasted image 20241122125121.png]]
I primi 6 elementi si andranno a salvare sugli stack RDI, RSI, RDX, RCX, R8, R9; il salvataggio sarà in ordine crescente:

| RDI       | RSI        | RDX       | RCX        | R8        | R9        |
| --------- | ---------- | --------- | ---------- | --------- | --------- |
| int first | int second | int third | int fourth | int fifth | int sixth |

---

Gli altri due verranno pushati al contrario sulla cima dello stack, cioè prima "eighth" e poi "seventh", in modo tale poi da avere sullo stack questa configurazione:
![[Pasted image 20241122125529.png]]
### Movs e Stos:
Sono istruzioni per operare su stringhe (buffer di dati)
Utilizzano dei registri impliciti:
- RCx: contatore del numero di operazioni elementari da eseguire
- RSI: indirizzo sorgente (per il movimento)
- RDI: indirizzo di destinazione
- RAX: valore cui impostare la memoria
Il direction flag (DF) identifica la direzione dell'operazione:
Se:
- DF =0: l'operazione di copia si svolge in avanti
- DF = 1: si svolge indietro 
Il seguente codice mostra l'implementazione di `movs` e di `stos`
![[Pasted image 20241126114721.png]]
- **Sinistra (Copia da una sorgente a una destinazione)**
1. `movq $source, %rsi`
    - Carica l'indirizzo di partenza (sorgente) nella **register `%rsi`**.  
        `%rsi` è usato come puntatore alla memoria sorgente per operazioni di copia.
2. `movq $destination, %rdi`
    
    - Carica l'indirizzo di destinazione nella **register `%rdi`**.  
        `%rdi` è usato come puntatore alla memoria di destinazione.
3. `movq $size/8, %rcx`
    
    - Carica nel registro `%rcx` il numero di **parole di 8 byte** (64 bit) da copiare. La divisione `/8` indica che la dimensione è calcolata in multipli di 8 byte.
4. `cld`
    
    - Resetta il flag `DF` (Direction Flag) del registro `EFLAGS`, assicurandosi che l'operazione di copia proceda **in avanti** (dall'indirizzo basso a quello alto).
5. `movsq`
    - Copia un dato **a 8 byte (64 bit)** dalla posizione indicata da `%rsi` (sorgente) a quella indicata da `%rdi` (destinazione). Dopo ogni copia:
        - `%rsi` è incrementato di 8 (si sposta alla prossima parola nella sorgente).
        - `%rdi` è incrementato di 8 (si sposta alla prossima parola nella destinazione).
    - Questa istruzione è ripetuta automaticamente **`%rcx` volte**, cioè per il numero di parole specificato.

- Scopo:

Questa sequenza copia **blocchi di memoria** da una posizione a un'altra.

---
- Destra (Inizializzazione di memoria con un valore zero)
1. `movq $0x0, %rax`
 
    - Carica il valore `0x0` (zero) nel registro `%rax`.  
        `%rax` sarà usato come valore da scrivere nella memoria.
2. `movq $destination, %rdi`
    
    - Carica l'indirizzo della memoria di destinazione nella register `%rdi`.
3. `movq $size/8, %rcx`
    
    - Carica nel registro `%rcx` il numero di **parole di 8 byte (64 bit)** da inizializzare.
4. `cld`
    
    - Resetta il flag `DF` (Direction Flag), garantendo che le operazioni procedano **in avanti**.
5. `stosq`    
    - Scrive il valore presente in `%rax` (zero, in questo caso) nella posizione di memoria indicata da `%rdi`. Dopo ogni scrittura:
        - `%rdi` è incrementato di 8 (si sposta alla prossima parola).
    - Questa istruzione viene ripetuta automaticamente **`%rcx` volte**, cioè per il numero di parole specificato.
#### Scopo:
Questa sequenza **inizializza un blocco di memoria a zero**.

---

**Confronto delle operazioni**

| **Codice Sinistra (movsq)**                                        | **Codice Destra (stosq)**                             |
| ------------------------------------------------------------------ | ----------------------------------------------------- |
| Copia dati da una sorgente a una destinazione.                     | Inizializza la destinazione con il valore zero.       |
| Richiede due indirizzi: sorgente (`%rsi`) e destinazione (`%rdi`). | Richiede un solo indirizzo: la destinazione (`%rdi`). |
| Usa il valore della memoria sorgente.                              | Scrive costantemente il valore in `%rax`.             |

Queste due sequenze sono comunemente usate per operazioni di manipolazione di memoria a basso livello, come implementazioni di funzioni di libreria simili a `memcpy` e `memset`.
Il microcodice dello z64 incrementa/decrementa i valori di RDI e RSI in funzione di DF
RCX viene sempre decrementato. Se RCX è diverso da zero, RIP viene decrementato di 8.
### Sorgente e destinazione sovrapposte:
Se la sorgente e la destinazione sono sovrapposte, una copia in avanti può portare ad un risultato errato.
![[Pasted image 20241126115236.png]]
#### Soluzione:
![[Pasted image 20241126115413.png]]
### Unione:
Un'unione è un valore che può assumere una qualsiasi tra diverse rappresentazioni o formati all'interno della stessa posizione in memoria.
Si tratta di un blocco di memoria che viene utilizzata per conservare, una per volta, variabili di tipo differente.
![[Pasted image 20241126115620.png]]
![[Pasted image 20241126115907.png]]
#### Union Cast:
![[Pasted image 20241126120232.png]]
### Campi di bit
In alcuni casi può essere utile modificare alcuni singoli flag all'interno di un tipo primitivo:
- registri di controllo
- bitmap, per raggruppare insieme più variabili booleane
Come faccio a modificar erun singolo bit se l'istruzione che prende un valore minore possibile utilizza 1 byte (8 bit)
In alcuni linguaggi di programmazione (ad alto livello) si fa cosi:
![[Pasted image 20241126120626.png]]
ed avremo questa rappresentazione
![[Pasted image 20241126121314.png]]
#### Maschere di bit: Forzatura:
 • Per forzare dei bit ad un valore specifico, si usano maschere di bit. 
 1. Per forzare un bit a 1, si utilizza l’istruzione or:  
	 Forzatura a 1 del bit più significativo: orl $0x80000000, %eax 
2. Per forzare un bit a 0, si utilizza l’istruzione and: 
	 Forzatura a 0 del bit più significativo: andl $0x7FFFFFFF, %eax
Per invertire un bit, si utilizza l’istruzione xor: 
	Inversione dell’ultimo bit: xorl $0x80000000, %eax 
	Per azzerare un registro, si possono usare due istruzioni equivalenti: 
		movq $0, %rax 
		xorq %rax, %rax 
		La seconda è preferibile perché più efficiente 
Si possono comporre maschere di bit per forzare più bit contemporaneamente
##### Esempio:
• Supponiamo di avere un numero a 32 bit e di voler estrarre il valore dei 3 bit meno significativi 
Si costruisce una maschera di bit del tipo 000....00111, equivalente a 7 
Estrazione dei bit: `andl` $7, %eax 
Per verificare se i bit sono a zero: `testl` $7, %eax 

Che cosa fa l’istruzione `testq` $2, %rax? 
L'istruzione **`testq`** in assembly **x86-64** effettua un'operazione di **AND bit a bit** tra due operandi senza salvare il risultato, ma aggiornando i **flag del registro EFLAGS** in base all'esito dell'operazione. Vediamo il significato specifico di `testq $2, %rax`:

Che cosa fa l’istruzione `testq` %rax, %rax?
Modo "short" per dire che sia il valore di partenza sia quello finale devono essere uguali.
### Puntatori a funzione:
#### In C
In C è possibile utilizzare dei puntatori a funzione 
Si tratta di variabili a cui possono essere assegnati indirizzi di memoria all’interno della sezione .text 
Tramite questi puntatori è possibile invocare le funzioni puntate 
Sono uno degli strumenti fondamentali per il supporto della programmazione a oggetti in cui è possibile utilizzare l’overloading delle funzioni 
In generale, permettono di selezionare dinamicamente una funzione da chiamare 
- per rispondere ad eventi di un determinato tipo
- per realizzare strutture dati generiche
##### Esempio:
![[Pasted image 20241126122406.png]]
#### In Assembly:
• L’uso dei puntatori a funzione è particolarmente semplice in assembly 
• Le calling convention catturano il passaggio di parametri indipendentemente dalla funzione chiamata.Tuttavia se si passano i parametri nel modo sbagliato ci può essere undefined behaviour
Per chiamare una funzione memorizzata in un puntatore, si utilizza una chiamata assoluta:
![[Pasted image 20241126122958.png]]
# Capitolo 10 (Binary):
## Introduzione:
Immaginiamo di avere un programma in python:
![[Pasted image 20241126124241.png]]
esteticamente non sembra essere impegnativo, ma dal punto di vista del compilatore è:
![[Pasted image 20241126124342.png]]
Se riusciamo a sovrascrivere RET, al ritorno dalla funzione il flusso di controllo verrà ripristinato all’indirizzo che abbiamo scritto sullo stack.
Per esempio con questo input: • aaaaaaaaaaaaaaa...aaaaaaaaa + addr_to_return • si può restituire il controllo dove si vuole.
![[Pasted image 20241126124624.png]]
Riuscire a mescolare i contesti dei dati e del codice eseguibile è una delle vulnerabilità “storiche” più devastanti.
I passi di questo attacco sono semplici: 
1. Scrivi lo shellcode in memoria, sfruttando il contesto dati 
	-  ad esempio: scanf(“%s”, buffer); 
2. Redireziona il flusso di esecuzione allo shellcode, sfruttando il contesto codice 
	- ad esempio: sovrascrivendo l'indirizzo di ritorno 
3. Profit!
![[Pasted image 20241126124751.png]]![[Pasted image 20241126124805.png]]
## Return Oriented Programming 101
Possiamo usare sempre lo shellcode?
I processori più moderni impediscono l'esecuzione di un codice sullo stack. Possiamo però sempre sovrascrivere l'indirizzo di ritorno.
![[Pasted image 20241126124915.png]]
Dove possiamo saltare però? 
Alterare l'indirizzo di ritorno serve a fornire controllo a del codice scelto dall'attaccante. Se l'attaccante non può iniettare codice arbitrario nell'eseguibile, può comporre e riciclare quello che è già presente nel programma:
![[Pasted image 20241126125009.png]]
Cerchiamo le istruzioni all'interno del programma:
![[Pasted image 20241126125210.png]]
![[Pasted image 20241126125250.png]]
Ora va eseguita la catena:
![[Pasted image 20241126125401.png]]
![[Pasted image 20241126125429.png]]
#### Contromisure:
Address Space Layout Randomization (ASLR):
- Il sistema operativo rende casuali gli indirizzi in memoria dello stack, dell’heap e delle librerie ad ogni esecuzione
Canary Stack protection
- Un valore casuale viene aggiunto prima dell’indirizzo di ritorno sullo stack (il canarino)
- Prima di eseguire un’istruzione di return, si verifica che il valore del canarino non sia cambiato
Not Executable (NX) Bit 
- Porzioni di memoria sono indicate come non eseguibili  
- Se si tenta di eseguire codice sullo stack, il programma viene schiantato
Position-Independent Executables (PIE)
- La base dell’intero programma viene scelta casualmente all'avvio
# Capitolo 11 (Gerarchie di memoria):
## Memoria Primaria:
### Organizzazione logica:
#### Cos'è?
Modello di memoria flat: la memoria è un lungo vettore di celle di memoria (byte). Ogni cella è identificata da un indirizzo.
#### Esempio: 
Organizzazione logica a vettore di 32 celle.
	Indirizzo composto da 5 bit
![[Pasted image 20241202141523.png]]
### Organizzazione in moduli:
#### Cos'è?
Utilizzando l'organizzazione precedente, c'è il problema di leggere i singoli byte uno alla volta. Per poterlo fare utilizziamo l'organizzazione in moduli, dove i tre bit meno significativi identificano il modulo, quelli più significativi la riga.
#### Esempio:
Lettura della riga 01:
![[Pasted image 20241202141908.png]]
#### Problemi e Soluzioni:
##### Problema Minor Numero di Bit:
- **Problema:**
	Address bus e data bus sono a 64 bit. Il processore potrebbe voler leggere/scrivere meno di 8 byte.

---
- **Soluzione** 
	Si introduce il segnale Chip Select (CS):
	![[Pasted image 20241202142132.png]]
##### Allineamento e disallineamento:
- **Problema**
	La memoria è indirizzabile al byte il dato potrebbe essere disposto su più righe

---
- **Soluzione**
	- Soluzione hardware: effettuare più letture, ricostruire il dato
	- Soluzione software: padding
	![[Pasted image 20241202142626.png]]
### Organizzazione a Matrice:
#### Cos'è?
Viene organizzato in questo modo:
![[Pasted image 20241202143225.png]]
1. **m x m matrix of bits**:
    
    - Questa è la matrice principale dove i dati sono immagazzinati.
    - Ogni cella nella matrice può rappresentare un singolo bit (0 o 1). La matrice ha dimensioni m×mm \times m, quindi può immagazzinare m2m^2 bit.
2. **Row Decoder**:
    
    - Il decodificatore di riga seleziona una specifica riga della matrice.
    - Riceve un segnale in ingresso dall’**Address Bus (AB)** e lo converte in un segnale che attiva solo una delle righe della matrice.
3. **Column Decoder**:
    
    - Il decodificatore di colonna seleziona una specifica colonna della matrice.
    - Lavora in modo simile al decodificatore di riga, ma seleziona colonne invece di righe.
4. **Output Amplifier**:
    
    - Quando si legge un dato dalla memoria (operazione di **read**), l’amplificatore di uscita prende il segnale dalla matrice (che potrebbe essere debole) e lo amplifica, inviandolo al **Data Bus (DB)**.
5. **Write Amplifier**:
    
    - Durante un'operazione di **write**, il segnale in arrivo dal **Data Bus (DB)** viene amplificato per scrivere nella cella selezionata nella matrice.
6. **Segnali di controllo (CS, MRD, MWR)**:
    
    - **CS (Chip Select)**: Attiva o disattiva la memoria per consentire l'accesso ai dati.
    - **MRD (Memory Read)**: Indica un'operazione di lettura.
    - **MWR (Memory Write)**: Indica un'operazione di scrittura.
#### Funzionamento
![[Pasted image 20241202143403.png]]

### Flusso operativo:

- **Per la lettura:**
    
    1. L'indirizzo fornito dall'**Address Bus (AB)** viene inviato ai decodificatori di riga e colonna per selezionare una specifica cella della matrice.
    2. Il valore della cella viene letto, amplificato dall’**Output Amplifier**, e inviato al **Data Bus (DB)**.
- **Per la scrittura:**
    1. L'indirizzo selezionato dall'**AB** individua una cella tramite i decodificatori.
    2. Il dato da scrivere, proveniente dal **Data Bus (DB)**, viene amplificato dal **Write Amplifier** e immesso nella cella selezionata.
### Memorie RAM Statiche:
La cella elementare è costituita da 6 transistor MOS che formano un flip-flop.
L’informazione permane stabile in presenza della tensione di alimentazione. Ci sono due caratteristiche:
- Tempi di accesso rapidi
- Costi elevati
![[Pasted image 20241202145958.png]]
#### Organizzazione Logica di una SRAM:
![[Pasted image 20241202150113.png]]
La matrice di bit è realizzata da un insieme di flip flop che sono circondanti da un circuito combinatorio per la lettura o scrittura dei dati.
### Memoria RAM Dinamiche:
#### Cos'è?
La cella elementare è costituita da un condensatore che viene caricato (1) o scaricato (0). Ciò presenta tempi di accesso alti e la semplicità della cella consente capacità molto elevate in spazi (e costi) contenuti.
![[Pasted image 20241202150346.png]]
#### Come è fatta fisicamente:
![[Pasted image 20241202150415.png]]
#### Cella di memoria:
![[Pasted image 20241202150428.png]]
#### Operazione di lettura e scrittura:
#### DRAM "Refresh":
##### Introduzione:
C'è un problema:
i condensatori si scaricano naturalmente 
• Costante temporale: il tempo necessario a far scaricare il condensatore del 63%, dopo questo tempo, l’informazione è persa. Non è più possibile distinguere tra 0 e 1:
![[Pasted image 20241202150649.png]]
Il controllore della memoria deve “rinfrescare” periodicamente tutte le righe per ripristinare la carica 
##### Problematiche del refresh: 
- Consumo energetico: ogni refresh consuma energia 
- Degradazione delle prestazioni: durante il refresh, una riga non è disponibile 
- Lunghe pause nella possibilità di accesso alla memoria durante il refresh 
- Le dimensioni e le velocità delle memorie sono direttamente limitate dalla necessità di refresh
##### Overhead del Refresh:
![[Pasted image 20241202151205.png]]
Refresh a burst: ogni 64ms si effettua il refresh di tutte le righe. 
Refresh distribuito: le righe sono soggette a refresh in istanti temporali differenti:
![[Pasted image 20241202151247.png]]
Il refresh distribuito elimina, statisticamente, le lunghe pause.
##### Interazione sincrona con la memoria:
![[Pasted image 20241202151430.png]]
Parametri costruttivi delle memorie determinano la latenza di accesso. Questi parametri sono alcuni dei fattori di compatibilità tra memoria e CPU. Vanno visti sull'etichetta:
![[Pasted image 20241202152014.png]]
##### Parametri della temporizzazione della memoria:
L’esecuzione di un comando (lettura/scrittura) è soggetto a dei tempi definiti da alcuni parametri:
1. Column Address Strobe (CAS) latency: il ritardo tra il comando READ e il momento in cui i dati sono disponibili.
	- Espresso in cicli di clock per le DRAM sincrone 
	- Espresso in nanosecondi per le DRAM asincrone 
2. Ritardo tra indirizzo di riga e indirizzo di colonna: Il numero minimo di cicli di clock necessari tra l'apertura di una riga di memoria e l'accesso alle colonne al suo interno. Sommato alla CAS latency dà il tempo necessario a leggere il primo bit dal data bus.
3. Tempo di precaricamento di riga: tempo necessario in caso di conflitto per caricare una riga 
4. Tempo di attivazione di riga: cattura il tempo di refresh
#### Differenze di velocità tra CPU e DRAM:
##### Introduzione:
Nell'architettura di von Neumann il canale di comunicazione tra CPU e memoria è il punto critico (collo di bottiglia) del sistema.
![[Pasted image 20241202152309.png]]
La tecnologia consente di realizzare CPU sempre più veloci e memorie sempre più grandi. Tuttavia, la velocità di accesso alle memorie non cresce così rapidamente come la velocità della CPU.
##### Gap prestazionale tra CPU e memoria:
Il gap prestazionale tra memoria e CPU è cresciuto nel tempo. Come si può risolvere questa differenza?
![[Pasted image 20241202152425.png]]

---
La soluzione ottimale per un sistema di memoria è: 
• costo minimo 
• capacità massima 
• tempo di accesso minimo
e la soluzione approssimata è quella di implementare una gerarchia di memoria, ovvero:
- tecnologie diverse per soddisfare al meglio ciascuno dei requisiti
- La gerarchia cerca di ottimizzare globalmente i parametri.
#### Gerarchia di memoria:
##### Caratteristiche:
- Più livelli di memoria.
- Al crescere della distanza dalla CPU decresce il costo e cresce la capacità di memorizzazione.
- In ogni istante di tempo i dati sono copiati solamente tra ciascuna coppia di livelli adiacenti (Ci si può concentrare su due soli livelli).
##### Rappresentazione:
![[Pasted image 20241202153032.png]]
##### Esempio di latenza di accesso?
![[Pasted image 20241202152933.png]]
### Cache
Una cache (un deposito) è più piccola dell’intera memoria principale di lavoro (RAM). Le cache mantengono sottoinsiemi dei dati (copie).
Come possiamo aumentare le probabilità di trovare i dati che ci servono “vicini” alla CPU?
![[Pasted image 20241202153132.png]]





....



# Capitolo 12: Input ed Output (I/O)
## Protocollo di handshaking:
### Cos'è?
Si chiama **protocollo di handshaking** perché il meccanismo di scambio dei segnali tra il trasmettitore (**UTx**) e il ricevitore (**URx**) ricorda simbolicamente una **stretta di mano** tra due persone: entrambe le parti devono sincronizzarsi e confermare il loro stato per procedere. Analogamente, nel contesto digitale, il trasmettitore e il ricevitore si scambiano segnali per assicurarsi che ogni fase della comunicazione sia completata in modo coordinato.

Ecco perché si utilizza il termine **handshaking** (stretta di mano):

1. **Cooperazione bidirezionale**:
    
    - Entrambe le parti (trasmettitore e ricevitore) partecipano attivamente al protocollo. Nessuno procede finché non riceve la conferma dall'altra parte.
2. **Sincronizzazione**:
    
    - L'handshaking garantisce che i dati vengano inviati solo quando entrambe le parti sono pronte. Il trasmettitore segnala che ha un dato pronto (con `RDY1`), e il ricevitore segnala che ha ricevuto il dato (con `ACK2`).
3. **Conferma esplicita**:
    
    - Ogni azione viene seguita da una conferma. Ad esempio:
        - UTx invia un segnale `RDY1=1` per indicare che il dato è pronto.
        - URx risponde con `ACK2=1` per confermare la ricezione del dato.
        - Entrambe le parti attendono che l'altra completi la fase prima di passare alla successiva.
4. **Prevenzione di conflitti**:
    
    - L'handshaking evita che il trasmettitore invii un nuovo dato prima che il ricevitore sia pronto. Questo garantisce una comunicazione sicura e priva di sovrapposizioni.

---

**Parallelo con una stretta di mano:**

- **Persona A** (trasmettitore): tende la mano (invia `RDY1=1`) per segnalare l'intenzione di avviare la comunicazione.
- **Persona B** (ricevitore): accetta la stretta (risponde con `ACK2=1`), confermando la ricezione del messaggio.
- Una volta completata la comunicazione, entrambe le persone rilasciano la stretta (impostano `RDY1=0` e `ACK2=0`), preparando il sistema per un nuovo scambio.

In sintesi, il termine **handshaking** sottolinea l'idea di un coordinamento reciproco, sicuro e sincronizzato, fondamentale in molti protocolli di comunicazione elettronica.

---
### Rappresentazione:
![[Pasted image 20241206115649.png]]

---
L'immagine rappresenta un sistema di comunicazione sincrona tra due unità, denominate **UTx** (trasmettitore) e **URx** (ricevitore), che utilizzano segnali di handshake per garantire un trasferimento sicuro dei dati. Questo schema viene tipicamente utilizzato in contesti digitali per lo scambio dati tra due sistemi.

---
#### Elementi dello schema
1. **Blocchi principali**:
    - **UTx** (Unità Trasmettitrice): si occupa di inviare dati.
    - **URx** (Unità Ricevente): si occupa di ricevere i dati.
2. **Registri di stato**:
    
    - `RDY1`: segnale di disponibilità da parte di **UTx** (Ready). Indica che UTx ha un dato pronto per essere inviato.
    - `ACK2`: segnale di conferma da parte di **URx** (Acknowledge). Indica che URx ha ricevuto il dato.
3. **Flip-Flop**:
    
    - FF1 e FF2 memorizzano rispettivamente i segnali `RDY1` e `RDY2` sincronizzati con i rispettivi clock (`CK1` e `CK2`).
    - FF3 e FF4 gestiscono i segnali `ACK2`.
4. **Dati**:
    
    - I dati vengono trasferiti da un registro di trasmissione (**RTx**) a un registro di ricezione (**RRx**).
5. **Segnali di handshake**:
    
    - `RDY1` e `ACK2` sono usati per coordinare il trasferimento dei dati.

---

#### Procedura di funzionamento

##### **Fasi di trasmissione (UTx)**:

1. **WRITE e RDY1=1**:
    
    - Quando UTx ha un dato pronto, lo scrive in RTx e imposta il segnale `RDY1` a 1 per notificare a URx che il dato è disponibile.
2. **Attesa di ACK2=1**:
    
    - UTx aspetta che URx riconosca il dato impostando il segnale `ACK2` a 1.
3. **RDY1=0**:
    
    - Una volta ricevuta la conferma (`ACK2=1`), UTx imposta `RDY1` a 0 per segnalare che ha completato la trasmissione.
4. **Attesa di ACK2=0**:
    
    - UTx aspetta che URx reimposti `ACK2` a 0 per completare il ciclo di handshake.

---

##### **Fasi di ricezione (URx)**:

1. **ACK2=0**:
    
    - All'inizio, URx tiene `ACK2` a 0 per segnalare che è pronto per un nuovo dato.
2. **Attesa di RDY1=1**:
    
    - URx aspetta che UTx imposti `RDY1=1`, segnalando che un dato è disponibile.
3. **READ e ACK2=1**:
    
    - URx legge il dato dal registro RRx e imposta `ACK2=1` per confermare la ricezione del dato.
4. **Attesa di RDY1=0**:
    
    - URx aspetta che UTx reimposti `RDY1` a 0, indicando che la trasmissione è completata.
5. **ACK2=0**:
    
    - Una volta che RDY1=0, URx reimposta `ACK2` a 0 per segnalare che è pronto per ricevere un nuovo dato.

---

#### Stato iniziale

- **RDY1=0, ACK2=0**:
    - All'inizio del sistema, entrambi i segnali sono a 0. Questo stato indica che:
        - **UTx** non ha ancora dato pronto.
        - **URx** è pronto per ricevere.

---

#### Riassunto

L'immagine illustra un protocollo di handshake basato su segnali di disponibilità (`RDY1`) e conferma (`ACK2`) per trasferire dati tra un trasmettitore e un ricevitore. Questo schema è comunemente uParallelo con una stretta di mano:sato per evitare conflitti e garantire che i dati vengano trasferiti in modo affidabile e sincronizzato.

---
## I/O microprogrammato per un solo dispositivo:
### Input:
#### Rappresentazione:
![[Pasted image 20241206115920.png]]

#### Spiegazione:
##### Introduzione

Questa immagine descrive un sistema di comunicazione **sincrono e controllato** tra:

- Un'unità centrale (**z64**, il microprocessore) e
- Un dispositivo periferico (**Device**, come una memoria o un sensore).

La comunicazione è implementata nel **firmware**, ossia una logica software programmata direttamente nel microprocessore, che segue un **protocollo** ben definito per scambiare dati senza errori.

---

##### Elementi principali:

1. **z64 (Unità Centrale)**:
    
    - Si tratta di un microprocessore che controlla la periferica. Esso comanda la comunicazione con due segnali:
        - **I/ORD**: un segnale di richiesta di Input/Output che avvia la comunicazione (esempio: leggere o scrivere dati).
        - **WAIT**: un segnale che indica che l'unità centrale sta aspettando il dispositivo.
2. **Device (Periferica)**:
    
    - È il dispositivo che deve comunicare con lo z64. Questo può essere una memoria, un convertitore analogico-digitale, un sensore, ecc.
    - Contiene:
        - **REG (Registro)**: un'area di memoria temporanea dove viene immagazzinato il dato da trasferire.
        - **PU (Processing Unit)**: un'unità di elaborazione che prepara i dati o esegue operazioni richieste.
        - **STATUS (Registro di Stato)**: registra informazioni sullo stato della periferica:
            - **R (Ready)**: indica se la periferica è pronta a comunicare.
            - **S (Status)**: indica se l'operazione è completata.
3. **Segnali di comunicazione**:
    
    - **I/ORD**: avvio della comunicazione da parte del microprocessore.
    - **WAIT**: segnala l'attesa durante il tempo in cui il dispositivo non è pronto.
    - **Data**: il dato vero e proprio che viene trasferito.
    - **LD (Load)**: indica che il trasferimento del dato è terminato con successo.
4. **Lunghezza del dato**:
    
    - I dati scambiati possono avere diverse dimensioni: 8, 16, 32 o 64 bit, a seconda del tipo di periferica e della configurazione.

---

##### Funzionamento del protocollo

Il protocollo di comunicazione segue uno schema ben definito, basato su una sequenza temporale di **stati** e segnali. Analizziamolo nel dettaglio, fase per fase:

---

###### Fase T1: Avvio della comunicazione

- **z64**:
    - Il microprocessore invia il segnale **I/ORD** alla periferica, indicando che vuole leggere o scrivere un dato.
    - Questo segnale può corrispondere a un comando di lettura (read) o scrittura (write).
- **Device**:
    - La periferica riceve il segnale **I/ORD** e inizia a prepararsi per l'operazione (esempio: caricando il dato richiesto nel registro **REG**).

---

###### 2. Fase T2: Attesa della periferica (WAIT)

- **z64**:
    - Dopo aver inviato il segnale di richiesta (**I/ORD**), il microprocessore entra in uno stato di attesa.
    - Il segnale **WAIT** si attiva, indicando che z64 è in pausa e aspetta una risposta dalla periferica.
- **Device**:
    - La periferica controlla il suo stato interno e usa il registro **STATUS** per comunicare al microprocessore:
        - **STATUS.R = 1**: la periferica è pronta per il trasferimento.
        - **STATUS.R = 0**: la periferica non è ancora pronta, e il microprocessore deve continuare ad aspettare.

---

###### 3. Fase TW: Tempo di attesa aggiuntivo

- Questa fase può verificarsi se la periferica ha bisogno di più tempo per elaborare il dato.
- **z64**:
    - Rimane in attesa finché il segnale **STATUS.R** non diventa 1.
- **Device**:
    - La periferica completa la preparazione del dato o della sua operazione interna.

---

###### 4. Fase T3: Trasferimento del dato

- **z64**:
    - Una volta che il dispositivo è pronto (**STATUS.R = 1**), il microprocessore:
        - Legge il dato dal registro **REG** se si tratta di una lettura.
        - Scrive il dato nel registro **REG** se si tratta di una scrittura.
    - Attiva il segnale **LD** (Load) per indicare che il trasferimento è avvenuto con successo.
- **Device**:
    - Il dispositivo esegue il trasferimento del dato o lo memorizza.

---

###### 5. Fine della comunicazione

- Dopo il completamento del trasferimento, il microprocessore e la periferica si preparano per una nuova comunicazione:
    - I segnali **I/ORD**, **WAIT**, e **LD** tornano a **0**.
    - Il ciclo può ricominciare.

---

##### Rappresentazione temporale

Il diagramma temporale in basso a destra mostra come evolvono i segnali durante le fasi del protocollo:

1. **I/ORD**:
    - Viene attivato all'inizio (T1) per avviare la comunicazione.
2. **WAIT**:
    - Resta attivo durante T2 e TW, indicando che il microprocessore è in attesa della periferica.
3. **Data**:
    - Il dato viene trasferito durante T3, quando il dispositivo è pronto.
4. **LD**:
    - Si attiva alla fine del trasferimento, segnalando che il dato è stato caricato o memorizzato correttamente.

---

##### Perché è implementato a firmware?

Questo protocollo è programmato nel firmware del microprocessore per garantire:

1. **Sincronizzazione tra z64 e periferica**: il sistema centrale aspetta che il dispositivo sia pronto prima di procedere, evitando errori.
2. **Efficienza e flessibilità**: la sequenza è configurabile e si adatta a periferiche diverse (con tempi di risposta differenti).
3. **Prevenzione di errori**: l'uso dei segnali di stato evita conflitti o perdite di dati.

---
##### Conclusione

Il sistema rappresentato nell'immagine descrive un'interazione ordinata e controllata tra un processore e una periferica, utilizzando segnali di stato (**STATUS**) e temporizzazioni. La chiave è l'uso di un protocollo firmware che permette a z64 di attendere il dispositivo senza inviare o ricevere dati in modo non coordinato. Questo schema è molto comune nei sistemi embedded o industriali.

---
### Output:
#### Rappresentazione:
![[Pasted image 20241206122753.png]]

---
#### Spiegazione:
##### Introduzione
Questa immagine descrive un sistema di comunicazione **sincrono e controllato** tra:
- Un'unità centrale (**z64**, il microprocessore) e
- Un dispositivo periferico (**Device**, come una memoria o un sensore).

La comunicazione è implementata nel **firmware**, ossia una logica software programmata direttamente nel microprocessore, che segue un **protocollo** ben definito per scambiare dati senza errori.

---

##### Elementi principali

1. **z64 (Unità Centrale)**:
   - Si tratta di un microprocessore che controlla la periferica. Esso comanda la comunicazione con due segnali:
     - **I/ORD**: un segnale di richiesta di Input/Output che avvia la comunicazione (esempio: leggere o scrivere dati).
     - **WAIT**: un segnale che indica che l'unità centrale sta aspettando il dispositivo.

2. **Device (Periferica)**:
   - È il dispositivo che deve comunicare con lo z64. Questo può essere una memoria, un convertitore analogico-digitale, un sensore, ecc.
   - Contiene:
     - **REG (Registro)**: un'area di memoria temporanea dove viene immagazzinato il dato da trasferire.
     - **PU (Processing Unit)**: un'unità di elaborazione che prepara i dati o esegue operazioni richieste.
     - **STATUS (Registro di Stato)**: registra informazioni sullo stato della periferica:
       - **R (Ready)**: indica se la periferica è pronta a comunicare.
       - **S (Status)**: indica se l'operazione è completata.

3. **Segnali di comunicazione**:
   - **I/ORD**: avvio della comunicazione da parte del microprocessore.
   - **WAIT**: segnala l'attesa durante il tempo in cui il dispositivo non è pronto.
   - **Data**: il dato vero e proprio che viene trasferito.
   - **LD (Load)**: indica che il trasferimento del dato è terminato con successo.

4. **Lunghezza del dato**:
   - I dati scambiati possono avere diverse dimensioni: 8, 16, 32 o 64 bit, a seconda del tipo di periferica e della configurazione.

---

##### Funzionamento del protocollo

Il protocollo di comunicazione segue uno schema ben definito, basato su una sequenza temporale di **stati** e segnali. Analizziamolo nel dettaglio, fase per fase:

---

###### 1. Fase T1: Avvio della comunicazione
- **z64**:
  - Il microprocessore invia il segnale **I/ORD** alla periferica, indicando che vuole leggere o scrivere un dato.
  - Questo segnale può corrispondere a un comando di lettura (read) o scrittura (write).
- **Device**:
  - La periferica riceve il segnale **I/ORD** e inizia a prepararsi per l'operazione (esempio: caricando il dato richiesto nel registro **REG**).

---

###### 2. Fase T2: Attesa della periferica (WAIT)
- **z64**:
  - Dopo aver inviato il segnale di richiesta (**I/ORD**), il microprocessore entra in uno stato di attesa.
  - Il segnale **WAIT** si attiva, indicando che z64 è in pausa e aspetta una risposta dalla periferica.
- **Device**:
  - La periferica controlla il suo stato interno e usa il registro **STATUS** per comunicare al microprocessore:
    - **STATUS.R = 1**: la periferica è pronta per il trasferimento.
    - **STATUS.R = 0**: la periferica non è ancora pronta, e il microprocessore deve continuare ad aspettare.

---

###### 3. Fase TW: Tempo di attesa aggiuntivo
- Questa fase può verificarsi se la periferica ha bisogno di più tempo per elaborare il dato.
- **z64**:
  - Rimane in attesa finché il segnale **STATUS.R** non diventa 1.
- **Device**:
  - La periferica completa la preparazione del dato o della sua operazione interna.

---

###### 4. Fase T3: Trasferimento del dato
- **z64**:
  - Una volta che il dispositivo è pronto (**STATUS.R = 1**), il microprocessore:
    - Legge il dato dal registro **REG** se si tratta di una lettura.
    - Scrive il dato nel registro **REG** se si tratta di una scrittura.
  - Attiva il segnale **LD** (Load) per indicare che il trasferimento è avvenuto con successo.
- **Device**:
  - Il dispositivo esegue il trasferimento del dato o lo memorizza.

---

###### 5. Fine della comunicazione
- Dopo il completamento del trasferimento, il microprocessore e la periferica si preparano per una nuova comunicazione:
  - I segnali **I/ORD**, **WAIT**, e **LD** tornano a **0**.
  - Il ciclo può ricominciare.

---

##### Rappresentazione temporale
Il diagramma temporale in basso a destra mostra come evolvono i segnali durante le fasi del protocollo:

1. **I/ORD**:
   - Viene attivato all'inizio (T1) per avviare la comunicazione.
2. **WAIT**:
   - Resta attivo durante T2 e TW, indicando che il microprocessore è in attesa della periferica.
3. **Data**:
   - Il dato viene trasferito durante T3, quando il dispositivo è pronto.
4. **LD**:
   - Si attiva alla fine del trasferimento, segnalando che il dato è stato caricato o memorizzato correttamente.

---

##### Perché è implementato a firmware?
Questo protocollo è programmato nel firmware del microprocessore per garantire:
1. **Sincronizzazione tra z64 e periferica**: il sistema centrale aspetta che il dispositivo sia pronto prima di procedere, evitando errori.
2. **Efficienza e flessibilità**: la sequenza è configurabile e si adatta a periferiche diverse (con tempi di risposta differenti).
3. **Prevenzione di errori**: l'uso dei segnali di stato evita conflitti o perdite di dati.

---

##### Conclusione

Il sistema rappresentato nell'immagine descrive un'interazione ordinata e controllata tra un processore e una periferica, utilizzando segnali di stato (**STATUS**) e temporizzazioni. La chiave è l'uso di un protocollo firmware che permette a z64 di attendere il dispositivo senza inviare o ricevere dati in modo non coordinato. Questo schema è molto comune nei sistemi embedded o industriali!



---
## Possibili connessioni CPU-dispositivi:
### In che modo?
Per implementare le due rappresentazioni viste in precedenza, possiamo utilizzare dei BUS per connettere direttamente la CPU con i dispositivi:
![[Pasted image 20241206121626.png]]
Ancora meglio è l'utilizzo di due bus separati, sarà però necessaria la creazione di altri microprogrammi e di istruzioni assembly dedicate per scegliere quale bus utilizzare:
![[Pasted image 20241206121909.png]]
In particolare quindi devo avere un registro bidimensionale per i dati di i/o e per gli indirizzi.
![[Pasted image 20241206122006.png]]
Dunque dovrò creare una struttura più ampia dove sono presenti delle strutture di controllo:
![[Pasted image 20241206122153.png]]
il segnale è controllato e indirizzato dal decoder, ma visto che estremamente costoso a livello di porte, verrà utilizzato un insieme di registri già configurati.
### I/O gestito a software:

#### Introduzione:
L’I/O microprogrammato manda in stallo il processore sul segnale di WAIT per un tempo possibilmente inaccettabile. Si può decidere di spostare il controllo delle operazioni di I/O al livello software, utilizzando tre principali strategie differenti. 

---
I/O programmato: è il programma software che inizializza e governa le interazioni con i dispositivi per effettuare il trasferimento di dati. 
Su richiesta esterna: il dispositivo richiede l’attenzione della CPU che esegue un driver per gestire il trasferimento dati. 
Gestite da processori dedicati (canali o adattatori di bus): il processore demanda ad un coprocessore l’operazione di trasferimento dati.

---
#### I/O microprogrammato:
![[Pasted image 20241206124538.png]]
### Busy Waiting:
#### Procedimento:
1. Il processore avvisa il dispositivo che vuole effettuare un trasferimento
2. Il processore verifica se il flip flop STATUS è a 1.
3. Se è a 0, continuerà a chiederglielo.
4. Il programma finisce quando lo STATUS è a 1.
#### Caratteristiche:
- Non vi è la possibilità che più dispositivi utilizzino il bus se non interrogati esplicitamente dalla CPU 
- Non è più necessario il segnale WAIT: collegato a massa
- La modalità busy waiting (attesa attiva) soffre della stessa problematica dell’I/O microprogrammato 
- Il processore non esegue nessun’altra attività fino al completamento del trasferimento
#### Interfaccia:
![[Pasted image 20241206125432.png]]
#### Assembly:
##### Codice
![[Pasted image 20241206125836.png]]
Il codice, scritto in assembly, e interagisce con un dispositivo hardware utilizzando istruzioni di input/output. 

---
##### Spiegazione
###### 1. `outb %al, $device`

- Questa istruzione invia il contenuto del registro `%al` (il registro a 8 bit inferiore dell'accumulatore `%ax`) al dispositivo hardware specificato da `$device`.
- **Funzione**: Serve per scrivere un valore (dati o comandi) su una porta hardware associata al dispositivo `$device`.

###### 2. `.bw:`

- Questo è un'etichetta usata come riferimento per il ciclo. Può essere vista come un "punto di ritorno" per i salti condizionali successivi.

###### 3. `inb $device, %al`
- Questa istruzione legge un byte di dati dal dispositivo `$device` e lo memorizza nel registro `%al`.
- **Funzione**: Recupera un valore (ad esempio uno stato o una risposta) dalla porta del dispositivo.

###### 4. `btb $0, %al`

- Questa è un'istruzione di bit-test (`btb` potrebbe essere un errore e dovrebbe forse essere `test` o `bt`), che testa uno specifico bit (in questo caso il bit 0) del registro `%al`.
- **Risultato**: Aggiorna i flag della CPU basandosi sul valore del bit testato:
    - Se il bit è 0 → il flag di _carry_ (CF) non viene impostato.
    - Se il bit è 1 → CF viene impostato.

###### 5. `jnc .bw`

- **`jnc`** significa _"Jump if No Carry"_, ovvero salta all'etichetta `.bw` se il flag di _carry_ (CF) **non** è impostato.
- **Funzione**: Se il bit 0 di `%al` è 0 (quindi il carry non è impostato), il controllo ritorna all'etichetta `.bw`, ripetendo il ciclo.

---
##### Comportamento Complessivo

1. Viene scritto un comando o un dato sul dispositivo tramite la porta `$device`.
2. Il programma entra in un ciclo `.bw`, dove legge dallo stesso dispositivo.
3. Viene testato il bit 0 del valore letto:
    - Se è 0, il ciclo continua (il programma rimane in attesa di un certo evento o stato).
    - Se è 1, il programma esce dal ciclo.
---
##### Significato Pratico
Il busy waiting è una tecnica in cui il processore rimane attivo in un ciclo continuo, interrogando ripetutamente un dispositivo o una risorsa, in attesa che una certa condizione venga soddisfatta. Durante questo tempo, la CPU non fa altro che eseguire inutilmente istruzioni per verificare lo stato, sprecando cicli di elaborazione.

---
### Polling:
#### Cos'è?
È una verifica circolare (simile al busy waiting) per trovare la prima periferica pronta ad interagire.


#### Assembly
##### Codice:
![[Pasted image 20241210102401.png]]

##### Analisi del codice:

1. **Etichetta `.poll:`**
    - È il punto di inizio del ciclo di polling. Il programma ritorna a questo punto per controllare continuamente lo stato dei dispositivi.

---

2. **Primo dispositivo:**
    - **`inb $STATUS_DEV1, %al`**: Legge lo stato del primo dispositivo (`STATUS_DEV1`) e lo memorizza nel registro `%al`.
    - **`btb $0, %al`**: Esegue un test sul bit 0 del valore letto:
        - Se il bit 0 è impostato (1), significa che il dispositivo è pronto o ha generato un evento.
    - **`jc .dev1`**: Se il bit 0 è 1 (carry impostato), salta all'etichetta `.dev1`, dove viene gestito l'evento per il primo dispositivo.

---

3. **Secondo dispositivo:**
    - **`inb $STATUS_DEV2, %al`**: Legge lo stato del secondo dispositivo (`STATUS_DEV2`) e lo memorizza in `%al`.
    - **`btb $0, %al`**: Testa il bit 0 del valore letto.
    - **`jc .dev2`**: Se il bit 0 è 1 (carry impostato), salta all'etichetta `.dev2`, dove viene gestito l'evento per il secondo dispositivo.

---

4. **Ripetizione del ciclo:**
    - **`jmp .poll`**: Se nessuno dei dispositivi richiede attenzione (bit 0 = 0 per entrambi), ritorna all'inizio del ciclo per continuare il polling.

---

5. **Gestione di un dispositivo (es. `.devX`):**
    - **`# ...`**: Qui ci sarebbe il codice per gestire l'evento associato al dispositivo.
    - **`jmp .poll`**: Dopo la gestione, torna al ciclo di polling per controllare di nuovo gli stati.

---

##### Comportamento Complessivo
1. **Polling ciclico**:
    - Il programma controlla ciclicamente lo stato di più dispositivi (nel caso specifico, `STATUS_DEV1` e `STATUS_DEV2`).
    - Se uno dei dispositivi segnala un evento (bit 0 = 1), l'esecuzione salta al relativo handler (`.dev1` o `.dev2`).
2. **Gestione degli eventi**:
    
    - Quando un dispositivo richiede attenzione, il programma salta all'etichetta associata, esegue il codice di gestione, e poi ritorna al polling.

---

##### Caratteristiche e Limitazioni

1. **Busy Waiting**:
    
    - Come nel primo esempio, la CPU rimane occupata continuamente nel ciclo, verificando lo stato dei dispositivi, il che non è efficiente.
2. **Scalabilità**:
    
    - Il codice può essere esteso ad altri dispositivi aggiungendo ulteriori blocchi simili (`inb`, `btb`, `jc`) per ogni dispositivo.
3. **Uso tipico**:
    
    - Questo schema potrebbe essere utilizzato in ambienti semplici o sistemi a basso livello (ad esempio, firmware), dove la gestione tramite interrupt non è disponibile o necessaria.

---

##### Miglioramento
Un sistema più efficiente potrebbe sostituire questo ciclo di polling con un **meccanismo di interrupt**, in cui i dispositivi notificano direttamente la CPU quando richiedono attenzione, evitando il bisogno di controlli ripetitivi.

---
### Interruzioni (o interrupt):
#### Scopo:
Forzare il processore a sospendere le attività correnti per attivare l'esecuzione di un altro frammento di codice (_gestore_ o _driver_)
La necessità dell'uso di driver nasce dall'eterogeneità di dispositivi che possono essere interconnessi alla CPU.
Il progetto delle interfacce è libero, a patto che si utilizzino correttamente i segnali di controllo da/Verso la CPU.
I dispositivi, quando sono pronti ad interagire, sollevano una richiesta di interruzione.
al termine dell'esecuzione del gestore, il processore riprende la normale esecuzione del programma.
#### Gestione della richieste di interruzione:
##### Problemi
Ci sono vari problemi nella gestione delle richieste di interruzione 
1. La generazione di richieste di interruzione è un’attività asincrona
2. Più dispositivi possono richiedere contemporaneamente l’attenzione della CPU 
3. Il processore può eseguire un solo driver per volta 
4. Il processore deve poter identificare quali dispositivi hanno sollevato la richiesta di interruzione (per identificare il driver) 
5. Il programma interrotto deve essere correttamente ripristinato al termine dell’esecuzione del gestore della richiesta di interruzione 
---
##### Soluzioni 
Soluzione al punto 1:  
- Il processore verifica periodicamente la presenza di un segnale di richiesta di interruzione (interrupt request, IRQ) proveniente dai dispositivi.
Soluzione ai punti 2, 3 e 4: 
- Dare una priorità alle richieste di interruzione (daisy chain) 
- Realizzare un protocollo (basato su firmware) per l’identificazione dei dispositivi che hanno sollevato richieste di interruzione
Soluzione al punto 5: 
per attivare l’esecuzione di un gestore, il processore segue i seguenti passi: 
1. Salvataggio dello stato del programma in esecuzione 
2. Identificazione del programma di servizio relativo alla periferica che ha generato la richiesta di interruzione (driver) 
3. Esecuzione del programma di servizio 
4. Ripresa delle attività lasciate in sospeso
L’attivazione di un gestore determina un cambio di contesto (di esecuzione)



---
#### Interfaccia a daisy chain:
##### Introduzione:
1. **Tutti i dispositivi possono alzare il segnale IRQ (Interrupt Request):**
    
    - Ogni dispositivo è in grado di richiedere un interrupt al processore alzando il segnale **IRQ**.
    - **Open collector**: La logica di interrupt è implementata in modalità "open collector", cioè più dispositivi possono condividere lo stesso segnale senza conflitti, usando una resistenza di pull-up per rilevare lo stato "basso" (attivazione).
    - **Logica negata**: Un livello basso (0 logico) indica la richiesta di interrupt.
2. **Segnale di acknowledgment (IACK):**
    
    - Il processore risponde alle richieste di interrupt con un segnale di **acknowledgment (IACK)** per informare il dispositivo interessato che la richiesta è stata riconosciuta.
    - L'IACK viene propagato lungo la catena (daisy chain) per identificare quale dispositivo deve essere servito.
3. **Priorità dei dispositivi:**
    
    - I dispositivi più vicini al processore hanno una **priorità maggiore**, poiché ricevono il segnale IACK prima degli altri.
    - Se un dispositivo con priorità più alta gestisce l'interrupt, blocca il passaggio del segnale IACK ai dispositivi successivi nella catena.
4. **Identificazione tramite Interrupt Vector Number (IVN):**
    
    - Ogni dispositivo è associato a un codice numerico chiamato **Interrupt Vector Number**.
    - Questo codice viene utilizzato dal processore per identificare il dispositivo che ha generato l'interrupt e determinare la routine di gestione da eseguire.
---
##### Circuito:
1. **Richiesta di interrupt:**
    
    - Uno o più dispositivi alzano il segnale IRQ per notificare un evento al processore.
2. **Acknowledge del processore:**
    
    - Il processore invia il segnale IACK sulla catena.
    - Il primo dispositivo che rileva l'IACK e ha una richiesta IRQ attiva lo accetta e blocca il passaggio agli altri dispositivi.
3. **Gestione e identificazione:**
    
    - Il dispositivo che accetta l'IACK invia il proprio IVN al processore, permettendo l'esecuzione della routine appropriata.
4. **Fine dell'interrupt:**
    
    - Una volta completata la gestione dell'interrupt, il dispositivo ripristina lo stato e consente il passaggio del segnale IACK agli altri dispositivi, se necessario.

---
##### Vantaggi della Daisy Chain
- **Semplicità hardware**: La connessione dei dispositivi è lineare e semplice.
- **Priorità naturale**: I dispositivi vicini al processore hanno automaticamente una priorità più alta.

---
##### Svantaggi

- **Priorità rigida**: I dispositivi con priorità più bassa potrebbero subire ritardi, soprattutto se quelli con priorità più alta monopolizzano il segnale.
- **Scalabilità limitata**: Aggiungere molti dispositivi può aumentare i tempi di propagazione e complicare la gestione.

---
#### Interferenze con il programma interrotto:
##### Introduzione:
Consideriamo il seguente frammento di codice eseguito su un processore multiciclo:
![[Pasted image 20241210111134.png]]
Una richiesta di interruzione potrebbe essere ricevuta durante:
- l’esecuzione del microprogramma dell’istruzione movq 
- tra l’istruzione movq e testq 
Il gestore dell’interruzione può contenere qualsiasi istruzione assembly, ad esempio `movq $1, %rax` 
##### Problemi: 
- I registri invisibili potrebbero essere sporcati 
- Il registro FLAGS potrebbe essere alterato
- Il contenuto del registro RAX potrebbe essere stato modificato
-

##### Microcodice per la gestione delle interruzioni:
![[Pasted image 20241210113653.png]]
Certamente! Il codice che hai fornito rappresenta una sequenza di istruzioni in un contesto che sembra riguardare la gestione di interruzioni a basso livello, probabilmente in un sistema operativo o firmware. Di seguito spiegherò passo passo il significato di ogni istruzione e i concetti associati:
###### Spiegazione:
---

1. **FLAGS[I] ← 0; TEMP1 ← RSP**
   - **FLAGS[I] ← 0**: Un bit specifico del registro FLAGS viene resettato (impostato a 0). Questo potrebbe essere utilizzato per disattivare l'interrupt corrente o segnalare che il sistema è in stato "safe".
   - **TEMP1 ← RSP**: Il valore dello stack pointer (RSP) viene copiato in un registro temporaneo (TEMP1). Serve probabilmente per salvare lo stato dello stack corrente.

---

2. **TEMP2 ← 8**
   - Viene caricato il valore `8` nel registro TEMP2. Questo potrebbe rappresentare la dimensione di un elemento (es., 8 byte per un'architettura a 64-bit).

---

3. **RSP ← ALU_OUT[SUB]**
   - Lo stack pointer (**RSP**) viene aggiornato con un valore calcolato dalla ALU (Arithmetic Logic Unit), effettuando una **sottrazione** (SUB). Questa operazione sposta lo stack per creare spazio per salvare i dati.

---

4. **MDR ← RSP**
   - Il valore di **RSP** viene caricato nel registro **MDR** (Memory Data Register). Questo è preparatorio per scrivere su memoria.

---

5. **(MAR) ← MDR**
   - Il contenuto del registro **MDR** viene caricato in **MAR** (Memory Address Register). **MAR** punta alla posizione di memoria dove sarà eseguita una scrittura.

---

6. **MDR ← RIP**
   - Il registro del **RIP** (Instruction Pointer), che contiene l'indirizzo della prossima istruzione da eseguire, viene salvato in **MDR**. Questo è utile per salvare il contesto attuale del programma.

---

7. **(MAR) ← MDR**
   - L'indirizzo salvato in **MDR** viene scritto in memoria all'indirizzo specificato in **MAR**. Questo salva l'instruction pointer (RIP) nello stack.

---
8. **TEMP1 ← RSP**
   - RSP viene di nuovo copiato in TEMP1, probabilmente per aggiornamenti successivi.

---

9. **RSP ← ALU_OUT[SUB]**
   - Ancora una sottrazione su RSP per creare spazio nello stack. Questa operazione sembra far parte del salvataggio del contesto.

---

10. **MAR ← RSP**
   - RSP viene copiato in MAR per prepararsi a un'altra operazione di scrittura.

---

 11. **MDR ← FLAGS**
   - Il contenuto del registro **FLAGS** (che tiene traccia di stati o flag del processore) viene copiato in MDR. Questo è utile per preservare lo stato attuale dei flag.

---

12. **(MAR) ← MDR**
   - Il contenuto di MDR (FLAGS) viene salvato in memoria allo spazio puntato da MAR.

---

13. **IACK; MDR ← IVN**
   - **IACK** (Interrupt Acknowledge): Questo è un segnale che conferma l'accettazione di un'interruzione da parte del processore.
   - **MDR ← IVN**: Il valore dell'Interrupt Vector Number (**IVN**) viene caricato in MDR. Questo numero identifica quale interrupt è stato ricevuto.

---

14. **TEMP2 ← MDR**
   - Il valore dell'IVN viene copiato in TEMP2 per elaborazioni successive.

---

15. **MAR ← SHIFTER_OUT[SX, 3]**
   - Qui si usa un'unità di shift per calcolare un indirizzo specifico. Il valore potrebbe essere correlato al driver associato all'interruzione. La nota accanto indica che ci sono **256 driver** differenti, probabilmente perché si usano 8 bit per identificare i driver.

---

16. **MDR ← (MAR)**
   - Viene letto un valore dalla memoria all'indirizzo contenuto in MAR e salvato in MDR.

---

17. **RIP ← MDR**
   - Infine, il valore caricato in MDR (che rappresenta probabilmente l'indirizzo della routine dell'interrupt handler) viene trasferito a RIP, facendo partire l'esecuzione del codice del driver.

---

###### Note aggiuntive:
- **Salvataggio parziale del contesto**: L'**interrupt frame** salva solo parte del contesto, come **RIP** e **FLAGS**. I registri di uso generale devono essere salvati manualmente dal driver.
- **Compito del driver**: Tocca al driver stesso gestire il salvataggio completo dei registri che utilizza.

---

Questo codice rappresenta un processo tipico di gestione di interruzioni (interrupt handling) in un sistema a basso livello. Hai domande su un passaggio specifico?
##### Uscita dal contesto di interruzione: `iret`
![[Pasted image 20241210114022.png]]

### Driver di periferica:
L’esecuzione di un driver avviene con le interruzioni disabilitate, è necessario rendere il codice del driver il più veloce possibile 
Tipica divisione in due parti 
- top half: la parte di lavoro non rinviabile, eseguita con IF=0 
	- recupero dei dati dal dispositivo (per evitare sovrascritture) se necessario 
	- riprogrammazione della periferica (se necessario)
	- cancellazione della causa di interruzione (obbligatorio) 
- bottom half: la parte di lavoro a priorità inferiore
	- es, processamento dei dati 
	- può essere eseguita riabilitando le interruzione (esecuzione di `sti` esplicita).
#### Assembly:
![[Pasted image 20241210114754.png]]
![[Pasted image 20241210114811.png]]
### Modalità mista e supporto di più operazioni:
#### Cos'è?
Un singolo dispositivo può operare sia in modalità asincrona sia in busy waiting.
È sempre il processore a determinare la modalità operativa del dispositivo che viene regolato attraverso un codice:
è possibile programmare il dispositivo utilizzando un registro/flip-flop di opcode
#### Esempio:
![[Pasted image 20241210115758.png]]
Per capire quale funzionalità utilizzare, come si può fare? 
Ad esempio, attraverso flip flop binari al quale vado ad impostare attraverso il seguente codice:
```
movb $0, %al
outb %al, $mode 
```
ed in al ci sarà o 0 o 1, nell'esempio 0.
Con il prossimo codice avvio la modalità:
```
outb %al, $status
```

#### Problemi nella gestione delle priorità:
##### Quali sono?
Ci sono due problemi nella gestione delle priorità vista:
1. Rischio di _priority inversion_
	 Se un driver non decide esplicitamente di essere interrompibile (usando l’istruzione `sti`), nessun dispositivo può interromperlo 
2. Rischio di _starvation_ 
	 La richiesta di interruzione di un dispositivo a priorità minore potrebbe non essere mai servita a causa dell’organizzazione in daisy chain
---
##### Gestione effettiva:
![[Pasted image 20241210121850.png]]

##### Gestione a software
osso mascherare temporaneamente che un dispositivo si manifesti in modo tale che elementi con priorità inferiore possano essere letti:
![[Pasted image 20241210122031.png]]
###### Problemi:
Problematiche simili al polling: 
- priority inversion
- starvation
#### Controllore degli interrupt a livelli di priorità:
##### Come?
Si possono utilizzare più daisy chain, ciascuna associata a un livello di priorità. I flip-flop di maschera permettono di gestire i livelli di priorità
![[Pasted image 20241210122204.png]]
Con un gestore di questo tipo possiamo utilizzare gruppi di dispositivi differenti, quindi andiamo a disabilitare una certa classe di priorità per approfondire in un tempo ristretto quelli a minor priorità.
##### Interrupt non mascherabili:
###### Problemi:
l mascheramento degli interrupt con il flag IF può causare il processamento ritardato di attività critiche.
Alcuni dispositivi a priorità elevatissima potrebbero non poter attendere che il processore termini le sue attività correnti per essere serviti.
###### esempi:
errori hardware non recuperabili, profilamento del sistema, reset del sistema, watchdog (ovvero dei controlli che si occupano esclusivamente di qualcosa e notano se c'è una variazione di elementi.), batterie scariche. 
###### Soluzione: 
Aggiunta di una linea di interrupt request non mascherabili (Non-maskable Interrutp, NMI).
I gestori dell’NMI devono essere velocissimi (tipicamente, non viene installato nemmeno l’interrupt frame).
## Operazioni gestite da canale:
### Cos'è?
Voglio passare da un accesso di memoria indiretto ad uno diretto, infatti fino ad ora abbiamo visto i casi in cui il trasferimento passa attraverso il processore:![[Pasted image 20241210123403.png]]
Questo perché si vuole evitare il sovraccarico del processore in caso di trasferimento di file molto pesanti.
### DMAC:
#### Cos'è?
Per svolgere il processo descritto in precedenza bisogna necessariamente utilizzare il DMAC, ovvero un controllore di BUS (o anche coprocessore) che effettua trasferimenti tra dispositivi e memoria al posto della CPU.
Ci sono possibili organizzazioni differenti:
![[Pasted image 20241210123743.png]]
#### Arbitraggio del BUS:
##### Problema:
C'è la possibilità che la CPU e il DMAC possano scrivere sullo stesso BUS due output differenti
##### Soluzione:
C'è bisogno di un modo per arbitrare il BUS che viene fatto attraverso un protocollo di hanshaking dedicato:
- Richiesta: 
	Memory Bus Request ($\overline {MBR}$): allerta la CPU della volontà di effettuare un trasferimento dati da dispositivo a memoria. viene utilizzato negato come nella [[#Tecnologia in Open Collector]], perché potremmo avere più input (come nella tecnologia potremmo avere più dispositivi).
	Se $\overline {MBR}$ è asserito, la CPU è in stallo.
- Condivisione:
	Memory Bus Grant (MBG): il processore rilascia il bus (alta impedenza) per permettere il trasferimento da parte del DMAC
---
#### Protocolli di condivisione del BUS:
Cosa succede se il processore vuole effettuare un trasferimento dati mentre il DMAC sta trasferendo dati?
![[Pasted image 20241210125144.png]]
##### Burnst mode:
Quando il processore asserisce MBG, il DMAC mantiene MBR fino al termine del batch di trasferimento
- Sottoutilizzo del bus di sistema 
- Il DMAC passa la maggior parte del tempo ad interagire con le periferiche
- Utile per dispositivi (come i dischi) che lavorano alla grana del blocco 
--- 
##### Bus stealing: 
il DMAC richiede il bus solo quando ha un dato pronto da trasferire.

---
#### Interfaccia DMAC-processore:
![[Pasted image 20241210125233.png]]