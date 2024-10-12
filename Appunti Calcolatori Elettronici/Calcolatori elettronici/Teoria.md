### Conversione da base decimale a una base di destinazione qualsiasi:
#### Se ho parte intera:
1) Divisioni intere per la base di destinazione
2) Fermarsi quando si è arrivati al valore 0
3) Si ordinano i resti dall'ultimo al primo
#### Esempio
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

#### Esempio
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

### Esistono delle scorciatoie per la conversione:
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

### Altri tipi di codifica:
#### Codifica ASCII:
##### Tradizionale:
- 7 Bit
- 128 caratteri rappresentabili
- l'ottavo bit era utilizzato come codice di controllo di errore![[Pasted image 20240930151055.png]]
##### Esteso:
- 8 bit
- 256 caratteri rappresentabili (compresi i codici di controllo)
 
#### Codice Binary Coded Decimal (BCD)
![[Pasted image 20240930151346.png]]


#### Codice di Gray:
![[Pasted image 20240930151419.png]]


### Distanza di Hamming (h)
Si dice distanza di Hamming il numero minimo di cifre diverse tra due parole del codice.
##### Esempio:

d(**10**0**10**, **01**0**01**) = 4

Esso è scrivibile come:
$$h =min(d(x,y))$$
- Nel caso di codice irridondante, la distanza è 1
- Un codice ridontante è capace di rivelare errori di peso $$\le~
h-1$$
#### Codici Ridondanti:
- Permetti di riconoscere o correggere gli errori
- Amplissimi spazi di applicazione:
	- aerospazio
	- supercomputer
	- Reti di calcolatori
![[Pasted image 20240930152540.png]]
Dove con la linea rossa indico la causa dell'errore
Come riveliamo l'errore?
Esempio
Ho questi due codici:![[Pasted image 20240930152700.png]]
Il modo in cui utilizziamo lo spazio disponibile per rappresentare gli elementi può consentire di rivelare la presenza di errori:
![[Pasted image 20240930152759.png]]
#### Codice di parità:
Si tratta di un codice ridondante con h = 2 e si ottiene aggiungendo una cifra di parità ad un codice irridondante. Vi sono due tipologie: 
##### Parità:
vale 1 se il numero di 1 nella codifica irridondante è dispari.
##### Disparità:
vale 1 se il numero di 1 nella codifica è pari.
![[Pasted image 20240930182922.png]]
