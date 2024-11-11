## Conversione:
Convertire il numero (-53,1) base 10 in base 2

Punto 1) Divisioni per 2
$$ 53/2 = 26 R=1 $$$$ 26/2 = 13 R=0$$$$ 13/2 = 6 R=1, $$$$
6/2 = 3 R=0$$ $$ 3/2= 1 R=1$$$$
1/2 = 0 R=1$$quindi il numero intero sarà = 110101 in base due,
Svolgo il procedimento per trovare il numero decimale in base 2 e arriverò a:
$$ (110101,00011), con~le ~ultime~quattro~cifre~periodiche$$.
Ora lo scrivo con la virgola mobile:
$$(1,1010100011) * 2^5 $$
A questo punto trovo l'esponente andando a sommare il 5 al 127 e mi trovo la  rappresentazione binaria della somma: $$5+127 = 132$$
Cioè, in forma binaria:
$$10000100$$
Quindi l'esponente avrà 9 cifre, il segno 1 e la mantissa 23, quindi dovrò svolgere il periodico delle ultime 4 cifre fino ad ottenere 23 cifre:
$$ s = 1,~e =10000100, m = valori~dopo~la~virgola~in~ (1,1010100011),$$$$ ~aggiungendo~i~valori~periodici~per~arrivare~a~23~elementi~nella~mantissa $$
quindi verrà  $$ s = 1,~e =10000100,~m = 10101000110011001100110 $$
Questo numero può essere "tradotto" anche in base 16, come?
Raccolgo a quattro a quattro: 
$$ 11000010010101000110011001100110=1100~0010~0101~0100~0110~0110~0110~0110 $$
E trovo il corrispettivo nell'alfabeto esadecimale 
[[Calcolatori#Esistono delle scorciatoie per la conversione]]:
che corrisponde a $$ C~2~5~4~6~6~6~6 $$
l'uguaglianza fra questo termine in base 16 e il termine -53,1 in base 10 non è una uguaglianza matematica, ma una corrispondenza nei rispettivi sistemi di riferimento, cioè il numero (-53,1) in base 10 corrisponde a (C 2 5 4 6 6 6 6) in base 16, ma i due numeri non sono obbligatoriamente uguali.
## Scambio ferroviario:
### Testo:
![[Pasted image 20241022145529 1.png]]
alla stazione arriva un treno per volta, ma i treni possono sostare sui marciapiedi per un tempo arbitrario. Normalmente il treno viene indirizzato al marciapiede A, se questo è occupato a B, e cosi via fino a D. Un marciapiede libero viene rappresentato dal valore 0, mentre un marciapiede occupato viene rappresentato dal valore 1.
Vi è poi un semaforo che viene tenuto a 1 (verde) se vi sono marciapiedi liberi e portato a 0(rosso) se sono tutti occupati, al fine di far arrestare un eventuale altro convoglio in arrivo.
L'indirizzamento avviene mediante tre scambi: 
- Y1 Viene portato a 1 se il treno può continuare a transitare sul binario 1, mentre viene portato a 0 per indicare che il treno deve essere trasferito al binario 4
- Y2 viene portato a 1 se il treno può continuare a transitare sul binario 1, mentre viene portato a 0 se il treno deve essere trasferito al binario 3.
- Y3 viene portato a 1 se il treno può continuare a transitare sul binario 1, mentre viene portato a 0 se il treno deve essere trasferito al binario 3
### Svolgimento:
La prima cosa da fare è quella di scrivere le funzioni Y1, Y2, Y3, S:
$S:=\overline{A}+\overline{B}+\overline{C}+\overline{D}$
$Y1:=\overline{A}+\overline{B}+\overline{C}$
$Y2:=\overline{A}+\overline{B}$
$Y3:=\overline{A}$
Una volta costruite le funzioni, creiamo la tabella che avrà $2^{n}$ righe, con n=numero incognite, quindi in questo caso 4, di conseguenza anche i risultati una volta inseriti nella funzione:

| A   | B   | C   | D   | S   | Y1  | Y2  | Y3  |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 1   | 1   | 1   | 1   |
| 0   | 0   | 0   | 1   | 1   | 1   | 1   | 1   |
| 0   | 0   | 1   | 0   | 1   | 1   | 1   | 1   |
| 0   | 0   | 1   | 1   | 1   | 1   | 1   | 1   |
| 0   | 1   | 0   | 0   | 1   | 1   | 1   | 1   |
| 0   | 1   | 0   | 1   | 1   | 1   | 1   | 1   |
| 0   | 1   | 1   | 0   | 1   | 1   | 1   | 1   |
| 0   | 1   | 1   | 1   | 1   | 1   | 1   | 1   |
| 1   | 0   | 0   | 0   | 1   | 1   | 1   | 0   |
| 1   | 0   | 0   | 1   | 1   | 1   | 1   | 0   |
| 1   | 0   | 1   | 0   | 1   | 1   | 1   | 0   |
| 1   | 0   | 1   | 1   | 1   | 1   | 1   | 0   |
| 1   | 1   | 0   | 0   | 1   | 1   | 0   | 0   |
| 1   | 1   | 0   | 1   | 1   | 1   | 0   | 0   |
| 1   | 1   | 1   | 0   | 1   | 0   | 0   | 0   |
| 1   | 1   | 1   | 1   | 0   | 0   | 0   | 0   |
