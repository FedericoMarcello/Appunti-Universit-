## Lezioni:
### Lezione 1: (introduzione)
#### Libreria e Sintassi di base:
Includiamo la libreria stdio.h al fine di importarla e utilizzarla. Questo poiché contiene delle funzioni di base utili alla creazione dello script. 
Una di queste è printf(). Inoltre utilizziamo return al fine di far finire il programma, cosi che esca dalla funzione e ritorna 0 se non c'è problema.
##### Codice:

```c title:"Primo Script"
#include <stdio.h>

int main()

{
	
	printf("Hello Word");
	
	
	return 0;
	
}

```




### Lezione 2: (variabili)
#### Cos'è una variabile?
Una variabile è un dato che viene corrisposto ad un valore. 
#### Inizializzazione
L'inizializzazione di una variabile consiste nel dichiarare che tipo di dato esso è e il suo valore.
##### Codice:
```c title:"Variabili 1"
#include <stdio.h>

int main()
{
int eta = 20; 
printf("%d ", eta);
eta = 21;

printf("ciao ho %d anni", eta);
return 0;
}
```
#### Dichiarazione ed Assegnazione:
Potevo scrivere il precedente codice anche come il seguente, con la differenza che nel prossimo invece che inizializzare una variabile, prima la dichiaro e poi l'assegno. 
- La dichiarazione equivale ad informare il programma che esiste una determinata variabile
 - L'assegnazione equivale a dare un valore alla variabile
##### Codice:
```c title:"Variabili 2"
#include <stdio.h>

int main()
{
int eta; // dichiarazione
eta = 20; // assegnazione

printf("%d ", eta);

  

}
```

#### Liste di Variabili:

Posso dichiarare una lista di variabili dove sono tutte lo stesso tipo, andando ad assegnargli un valore dopo.
##### Codice:
```c title:"Variabili 3"
#include <stdio.h>

int main_3()
{
int etaMamma, etaZia, etaMia;
printf("%d ", etaMamma);
}
```

### Lezione 3: (costanti)
#### Cos'è?
Una costante è un valore che, una volta inizializzato, non può essere modificata, solo letta.
Si dichiara attraverso l'uso del termine "const" e, di solito, utilizzando il maiuscolo per ogni lettera.
##### Codice:
```c title:"Costanti"
#include <stdio.h>
int main()
{
const int GIORNI_SETTIMANA = 7;
printf("i giorni della settimana sono");
return 0;
}
```

### Lezione 4: (tipi di dati)
#### Perché esistono più dati?
Il linguaggio c presenta diversi tipi di dato essendo un linguaggio che lavora a stretto contatto con la memoria, quindi necessita di importanti specifiche. Inoltre ho necessità di utilizzare correttamente la memoria poiché se il numero è troppo grande rispetto alla memoria assegnata si va in overflow, se è troppo piccolo vi è una perdita di memoria rispetto a quella assegnata. 
Ad esempio, se sfrutto "long long" per un numero a due cifre avrò perso importanti quantità di memoria, questo potrà creare problemi al mio script.
#### Numeri interi:
Esistono 4 tipi di dato per i numeri interi: int, short, long, long long:
1) <span style="color:rgb(0, 112, 192)">int</span> considera i dati da -2 miliardi a 2 miliardi

2) <span style="color:rgb(0, 112, 192)">short</span> considera i dati da -32 mila fino a 32,767

3) <span style="color:rgb(0, 112, 192)">long</span> considera i dati oltre i due miliardi

4) <span style="color:rgb(0, 112, 192)">long long</span> ancora più che long
#### Numeri con la virgola:
per numeri che presentano la virgola, bisogna utilizzare float, double e long double, in ordine da chi contiene meno numeri con la virgola a chi ne contiene di più
1) <span style="color:rgb(0, 112, 192)">float</span> presenta sette cifre dopo la virgola

2) <span style="color:rgb(0, 112, 192)">double</span> presenta 15 cifre dopo la virgola

3) <span style="color:rgb(0, 112, 192)">long</span> <span style="color:rgb(0, 112, 192)">double</span> più di 15
#### Lettere:
Si utilizza char che significa character = carattere. Si tratta di un singolo elemento e si utilizza ' ' per indicarlo.
#### Stringhe:
Una stringa è l'unione di diversi char, si indica con " ".
#### Algebra Booleana:
Si usa bool che serve per indicare un valore "vero" o "falso", poiché nell'alfabeto booleano esistono 2 dati:{0, 1}
- <span style="color:rgb(0, 112, 192)">bool</span> <span style="color:rgb(0, 176, 240)">seiOnline</span> =  true/false
#### Puntatori (pointer):
Sono delle variabili che contengono indirizzi alle celle di memoria, si indicano con & e poi il nome della variabile di cui vogliamo sapere l'indirizzo. 

#### Come usare printf():
Ad ogni % 'lettera' corrisponde un tipo particolare di dato:
- <span style="color:rgb(255, 255, 112)">printf</span><span style="color:rgb(255, 255, 0)">(</span><span style="color:rgb(185, 88, 24)">"</span><span style="color:rgb(0, 176, 240)">%d</span><span style="color:rgb(185, 88, 24)">"</span>-> numeri<span style="color:rgb(255, 255, 0)">)</span>

- <span style="color:rgb(255, 255, 112)">printf</span><span style="color:rgb(255, 255, 0)">(</span><span style="color:rgb(185, 88, 24)">"</span><span style="color:rgb(0, 176, 240)">%f</span><span style="color:rgb(185, 88, 24)">"</span>-> double<span style="color:rgb(255, 255, 0)">)</span>

- <span style="color:rgb(255, 255, 112)">printf</span><span style="color:rgb(255, 255, 0)">(</span><span style="color:rgb(185, 88, 24)">"</span><span style="color:rgb(0, 176, 240)">%c</span><span style="color:rgb(185, 88, 24)">"</span>-> carattere<span style="color:rgb(255, 255, 0)">)</span> 

- <span style="color:rgb(255, 255, 112)">printf</span><span style="color:rgb(255, 255, 0)">(</span><span style="color:rgb(185, 88, 24)">"</span><span style="color:rgb(0, 176, 240)">%s</span><span style="color:rgb(185, 88, 24)">"</span>-> stringhe<span style="color:rgb(255, 255, 0)">)</span> 
### Lezione 5: (conversioni)
#### Conversione implicita
Questo tipo di conversione si chiama implicita poiché quando inizializziamo y, è il computer a trovarne il valore corretto. 
##### Codice:
Nell'esempio, il computer trova automaticamente il valore float di x corrispondente all'intero in precedenza inizializzato.
```c title:"Conversioni 1"
#include <stdio.h>
#include <stdbool.h>
int main()
{
	int x = 10;
	float y = x;
	printf("%f", y);
	return 0;
}
```
#### Conversione Esplicita:
Questo tipo di conversione si chiama esplicita poiché quando inizializziamo y, attribuiamo ad y il valore corretto;
##### Codice:
Nell'esempio, ad y abbiamo chiesto esplicitamente il valore intero di x

```c title:"Conversioni 2"
#include <stdio.h>
#include <stdbool.h>

int main()
{
	double x = 10.293851;
	int y = (int)x;
	printf("%d", y);
	return 0;
}
```
### Lezione 6: (numeri)
#### Operatori di Assegnazione 
Essi sono degli operatori che assegnano ad una variabile dichiarata precedentemente un valore aumentato o diminuito.
##### Codice:
```c title:"Operatori di assegnazione"
#include <stdio.h>
#include <stdbool.h>

int main()
{
	int x = 19;
	x += 5;
	printf("%d", x);
}
```
#### Operazioni:
Nel linguaggio c è possibile svolgere sia le operazioni di base, sia quelle più complicate.
Posso inoltre porre ++ o -- sia <span style="color:rgb(255, 0, 0)">prima</span> sia <span style="color:rgb(255, 102, 0)">dopo</span> per aumentare o diminuire il valore:
Le due modalità presentano delle differenze:
1) Se scrivo l'operazione <span style="color:rgb(255, 0, 0)">prima</span> della variabile, allora i <span style="color:rgb(255, 0, 0)">cambiamenti</span> riguardano <span style="color:rgb(255, 0, 0)">sia</span> la <span style="color:rgb(255, 0, 0)">variabile</span> che sto aumentando, <span style="color:rgb(255, 0, 0)">sia</span> <span style="color:rgb(255, 0, 0)">quella</span> dichiarata <span style="color:rgb(255, 0, 0)">in funzione della prima</span>.
2) Se scrivo l'operazione <span style="color:rgb(255, 64, 0)">dopo</span> la variabile, allora i <span style="color:rgb(255, 64, 0)">cambiamenti</span> riguardano <span style="color:rgb(255, 64, 0)">solo</span> la <span style="color:rgb(255, 64, 0)">variabile</span> che sto aumentando.
##### Codice:
1) <span style="color:rgb(255, 0, 0)">Caso</span>:
```c title:"Operazioni"
#include <stdio.h>
#include <stdbool.h>

int main()
{
	int x = 19;
	int y = ++x;
	printf("%d", x);
	printf("%d", y);
	return 0;
}
```
restituirà $x = 20, y = 20$

2) <span style="color:rgb(255, 102, 0)">Caso</span>:
```c title:"Operazioni"
#include <stdio.h>
#include <stdbool.h>

int main()
{
	int x = 19;
	int y = x++;
	printf("%d", x);
	printf("%d", y);
	return 0;
}
```
restituirà $x = 20, y = 19$
#### Operazioni più complicate:
Le operazioni più complicate in un script c sono possibili solo se includiamo l'header math.h.
- Un esempio può essere la potenza di un numero.
Per la libreria completa guardare: [Liberia Math.h](https://www.tutorialspoint.com/c_standard_library/math_h.htm)
##### Codice:
```c title:"Operatori di assegnazione"
#include <stdio.h>
#include <stdbool.h>

int main()
{
	int x;
	x = pow(5, 2);
	printf("%d", x);
}
```
restituirà $25=(5^2)$ 

### Lezione 7: (comparazione):
#### Operatori di comparazione:
Esistono degli operatori di comparazione che ci permettono di comparare due elementi.
Degli esempi possono essere:
- >
- <
- ==
- != (diverso)
##### Codice:
```c title:"Operatori di comparazione"
#include <stdio.h>
#include <stdbool.h>
#include <math.h>

int main()
{
	int x = 5;
	bool condition = x < 10;
	printf("%d", condition);
	return 0;
}
```
ritornerà 1 poiché in termini booleani "vero" corrisponde ad 1.
#### Operatori Logici:
Esistono degli operatori logici che permettono di esprimere delle condizioni come "e", "o", "non"

1) Utilizziamo && per intendere "e" (cioè che le condizioni siano verificate contemporaneamente).
2) Utilizziamo || per intendere "o" (cioè è necessario che sia verificata almeno una condizione)
3) !(argomento) per intendere "NOT" (inverte il risultato dell'argomento):
##### Codice:
1) caso
```c title:"Operatori logici AND"
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
	int x = 21;
	bool condition = x > 5 && x < 23;
	printf("%d", condition);
	return 0;
}
```
tornerà 1 poiché sono rispettate entrambe le condizioni, quindi tornerà true.

2) caso 
```c title:"Operatori logici or"
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
	int x = 21;
	bool condition = x > 5 || x < 7;
	printf("%d", condition);
	return 0;
}
```
tornerà 1 poichè è rispettata almeno una delle condizioni, quindi tornerà true

3) caso 
```c title:"Operatori logici NOT"
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
	int x = 21;
	bool condition = !(x > 5 || x < 7);
	printf("%d", condition);
	return 0;
}
```
tornerà 0 poiché essendo rispettata almeno una delle condizioni, normalmente risponderebbe 1, quindi tornerà false
### Lezione 8: (condizioni)
#### If, Else, Else if:
Per imporre una condizione al nostro programma possiamo utilizzare questi 3 elementi:
- <span style="color:rgb(185, 88, 24)">if</span>: impone una <span style="color:rgb(185, 88, 24)">condizione</span> che, se avverata, viene attivato il codice nel blocco
- <span style="color:rgb(0, 176, 80)">else</span>: segue if, potremmo tradurlo con "<span style="color:rgb(0, 176, 80)">altriment</span><span style="color:rgb(0, 176, 80)">i</span>"
- <span style="color:rgb(255, 0, 0)">else if</span>: traducibile con "<span style="color:rgb(255, 0, 0)">altrimenti se</span>", quindi si usa quando non si verifica l'if precedente e si vuole dare un'altra condizione
##### Codice:
```c title:"Condizioni"
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
	int x;
	scanf("%d", &x);
	if (x < 0) 
	{
		printf("negative");
	}
	else if (x > 9)
	{
		printf("ad una cifra");
	}
	else { 
		printf("grande");
	}
	return 0;
}
```
### Lezione 9: (operatore ternario)
#### Cos'è?
L'operatore ternario è un operatore che permette di scrivere con una diversa sintassi le condizioni "if, and" e la sua sintassi è del tipo:
("condizione") ? "cosa succede se è vero" :  "cosa succede se falso"
##### Codice:
un codice molto semplice per capirne la sintassi ed il funzionamento.

```c title:"Operatore ternario 1"
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
	(12>1) ? printf("vero") : printf("falso");
	return 0;
}
```
ed il programma tornerà vero.

Un codice più complicato che, in base al voto ottenuto, risponde classificandolo. Il codice contiene l'operatore if ed else if:
```c title:"Operatore ternario 2" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
	int voto = 95;
    char *valutazione = (voto >= 90) ? "Ottimo" : (voto >= 80) ? "Buono" : (voto >= 70) ? "Sufficiente" : "Insufficiente";
    printf("Valutazione: %s\n", valutazione);
}
```
### Lezione 10: (switch)
#### Cos'è?
Utilizziamo "switch" per scegliere in un elenco, in funzione della variabile che definiamo. La sintassi è data dalla definizione della funzione, il comando switch che la richiama, i vari casi e l'ultimo, ovvero "default" che equivale al messaggio se si selezionano elementi diversi da quelli scelti.
##### Codice:
```c title:"Switch 1" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
int giornoSettimana = 8;
switch (giornoSettimana)
	{
    
    case 1:
        printf("Lunedì");
        break;
    
    case 2:
        printf("Martedì");
        break;
    
    case 3:
        printf("Mercoledì");
        break;
    
    case 4:
        printf("Giovedì");
        break;

    case 5:
        printf("Venerdì");
        break;

    case 6:
        printf("Sabato");
        break;

    case 7:
        printf("Domenica");
        break;
        
    default:
        printf("non ci sono più di 7 giorni");
        break;
    }
    return 0;
}
```

Se diversi elementi dello switch hanno in comune la stessa caratteristica, per evitare di scrivere la stessa cosa sotto ogni "case", posso scrivere:
```c title:"Switch 1" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
	switch (giornoSettimana)
	{
	case 1:
	case 2:
	case 3:
	case 4:
	case 5:
		printf("Giorno feriale");
		break;
	case 6:
	case 7:
		printf("Giorno festivo");
		break;
	default:
	printf("non ci sono più di 7 giorni");
	break;
	}
return 0;
}
```
### Lezione 11: ( cicli while)

#### While:
Il ciclo while indica "mentre una condizione è vera" allora svolgi il contenuto. 
##### Codice:
Nell'esempio, il programma stamperà i numeri dall'uno al 5
```c title:"Switch 1" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
 int i = 1;
    while (i < 6) 
    {
        printf("%d\n", i); 
        i ++; 
    }
    return 0;
}
```
#### While do:
un altro modo di scrivere un ciclo while.
##### Codice:
```c title:"Switch 2" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
 do {
	
    printf("%d\n", i); 
    
    i ++;
    
    } while (i < 6);
    
    return 0;
}
```
### Lezione 12 (cicli for):
#### Cosa sono?
Esiste anche un altro tipo di ciclo, ovvero il ciclo for, utilizzato per studiare un caso in cui la condizione è verificata "per" qualcosa. La sintassi è diversa da quella degli altri linguaggi:
##### Codice:
```c title:"Ciclo for" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
    for (int i = 4; i <= 8; i++)
    { 
        if (i % 2 == 0)
        {
            printf("%d è pari\n", i);
        }
        else 
        {
            printf("%d è dispari\n", i);
        }
    }
    return 0;
}
```
### Lezione 13 (break e continue)
#### Break:
utilizzando il comando break il ciclo si ferma e fa stampare il comando successivo.
```c title:" Break" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
    for (int i = 4; i <= 8; i++)
    { 
        if (i % 2 == 0)
        {
            printf("%d è pari\n", i);
            break;
        }
    }
    return 0;
}
```
Il programma risponderà solamente "4 è pari" perché il break fa si che appena si avvera la condizione dell'if, si esce dal ciclo
#### Continue:
Il ciclo si ferma e fa stampare il comando successivo.
##### Codici:
il programma risponderà "4, 5, 7, 8" perchè il continue fa si che appena si avvera la condizione dell'if
```c title:" continue" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
    for (int i = 4; i <= 8; i++)
    { 
        if (i == 6)
        {
            continue;
        }
        
     printf("%d\n", i);
    
    }
    return 0;
}
```
### Lezione 14 (Variabili globali):
#### Cosa sono?
Il discorso delle variabili locali va inteso come una sorta di "matriosca" delle variabili.
Quelle che si trovano fuori rispetto ad un blocco di codice posso utilizzare il valore assegnato in quel momento.
Se sono presenti dei blocchi di codice interni alla funzione principale, essi hanno accesso sia al valore precedente.
Sia a quello che volendo si può assegnare.
Un esempio più concreto può essere quello di
immaginare di avere una via chiamata "via Roma", essa può essere via Roma di Milano, di Napoli, di Genova, di Roma..
Quindi la variabile globale sarà via Roma e nelle singole città (funzioni) esse prendono il valore voluto.
##### Codice:
```c title:" continue" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
    int x = 3;

    if (x == 3)
    {
        int x = 9; 
        printf("%d\n", x);

    }// 
    printf("%d\n", x);

    return 0;
}
```
Bisogna ricordarsi che la variabile interna deve essere inizializzata con il tipo di dato corrispondente. 
### Lezione 15: (array)
#### Cos'è?
L'array è definito come una collezione di dati. 
I dati che sono inseriti nell'array sono posizionati in ordine nella memoria. 
Per capire meglio possiamo immaginare cellette di memoria conseguenziali.
- Se vogliamo ottenere il numero di bit occupati dal nostro array, utilizziamo la seguente scrittura:
  "printf("%zu", sizeof(nome_array))"
- Per capire invece il numero di dati:
  "printf("%zu", sizeof(nome_array)/sizeof(nome_array[0]))"
##### Codice:
```c title:" array 1" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
  int votiUni[]={22,20,25};
    votiUni[0] = 22;
    votiUni[1] = 20;
    votiUni[2] = 25;
    printf("%zu", sizeof(votiUni)/sizeof(votiUni[0]));
    return 0;
}
```

Se volessi inserire un array in un ciclo:
```c title:" array 2" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
	int votiUni[]={22,20,25};
    votiUni[0] = 22;
    votiUni[1] = 20;
    votiUni[2] = 25;
    for (int i = 0; i < sizeof(votiUni) / sizeof(votiUni[0]); i++){
        printf("%d\n", votiUni[i]);
    }
    return 0;
```
### Lezione 16: (stringhe)
#### Cos'è?
Una stringa non è altro che un array di caratteri. Infatti nell'analisi e nella sintassi possiamo considerarla come un array:
- la sintassi è char _nome_stringa_[]= " "
La costruzione dei cicli è uguale. 
Inoltre esiste un file header chiamato string.h che può essere importato che contiene e permette di utilizzare diverse funzioni legate alle stringhe.
##### Codice:
```c title:"stringhe" 
#include <stdio.h>
#include <stdbool.h>
#include <math.h>
int main()
{
    char nome[]="Federico";
    for (int i = 0; i < sizeof(nome)/ sizeof(nome[0]); i++)
    {
        printf("%c\n", nome[i]);
    }
    return 0;
```
### Lezione 17: (funzioni)
#### Cosa sono?
Una funzione in C è una porzione del programma che esegue un compito specifico. Le funzioni consentono di suddividere un programma complesso in blocchi più piccoli e gestibili, promuovendo la modularità e la riusabilità del codice. Ogni funzione ha un nome unico e può avere parametri (input) e un valore di ritorno (output).

#### Vantaggi dell’Utilizzo delle Funzioni:

Le funzioni offrono diversi vantaggi:
1. **Riusabilità del Codice**: Una volta definita una funzione, può essere richiamata in tutto il programma senza la necessità di riscrivere lo stesso codice.
    
2. **Modularità**: Divide il codice in blocchi più piccoli e gestibili, semplificando la comprensione e la manutenzione del programma.
    
3. **Ridondanza Ridotta**: Elimina la necessità di scrivere lo stesso codice più volte, riducendo così il rischio di errori.
    
4. **Facilità di Debugging**: Le funzioni consentono di concentrarsi su parti specifiche del codice durante il debug.
#### Dichiarazione e Definizione di Funzioni

Per utilizzare una funzione in C, è necessario dichiararla prima di utilizzarla. La dichiarazione di una funzione include il suo nome, il tipo di ritorno e i parametri (se presenti).

#### Chiamata di Funzioni

Per chiamare una funzione in C, è sufficiente utilizzare il suo nome seguito da parentesi tonde () che contengono gli argomenti della funzione (se presenti)
#### Parametri e Argomenti delle Funzioni

I parametri di una funzione sono le variabili dichiarate all’interno delle parentesi tonde nella dichiarazione o definizione della funzione stessa. Gli argomenti sono i valori specifici passati alla funzione quando viene chiamata.

#### Valori di ritorno:
Le funzioni possono restituire un valore usando l’istruzione `return`. Il tipo di valore di ritorno è specificato nella dichiarazione della funzione
#### Funzioni Ricorsive

Le funzioni ricorsive sono funzioni che si chiamano da sole in modo ricorrente. Sono utilizzate per risolvere problemi che possono essere suddivisi in sottoproblemi simili. Un esempio classico di funzione ricorsiva è il calcolo del fattoriale:
#### Codici
### Lezione 18 (puntatori)
#### Cosa sono?
In C, un **puntatore** è una variabile che contiene l’indirizzo di memoria di un’altra variabile. 
Gli indirizzi di memoria sono numeri interi che rappresentano la posizione di una variabile in memoria. I puntatori consentono di accedere e manipolare direttamente i dati in memoria.
#### Perché Usare i Puntatori

I puntatori sono utili per diverse ragioni:

1. **Gestione della Memoria**: Consentono di gestire la memoria in modo più efficiente, consentendo l’allocazione dinamica di memoria quando necessario.    
2. **Passaggio per Riferimento**: Consentono di passare grandi quantità di dati alle funzioni senza copiare effettivamente i dati, migliorando le prestazioni.
3. **Manipolazione Diretta della Memoria**: Consentono di accedere direttamente ai dati in memoria, utile per la manipolazione di array e strutture di dati complesse.
#### Creare e Utilizzare un Puntatore

Per dichiarare un puntatore in C, è necessario specificare il tipo di dati a cui il puntatore farà riferimento.
##### Codice:
il puntatore deve essere dello stesso tipo del puntatore
Ricordarsi inoltre deve essere utilizzato il termine & per indicare che non si intende la variabile, ma il suo indirizzo

#### Dereferenziare un Puntatore

Per accedere al valore a cui un puntatore fa riferimento, utilizziamo l’operatore di dereferenziazione `*`. 

#### Array e Puntatori:
Posso notare come l'indirizzo di x coincide con l'indirizzo del primo elemento (quindi indice 0) di x 
stesso.
##### Codice:
#### Puntatore doppio:
I **puntatori doppi** (o puntatori a puntatori) in C sono una delle caratteristiche avanzate del linguaggio, utilizzati per manipolare strutture dati complesse come array multidimensionali, liste collegate e alberi.
Un **puntatore doppio** è un puntatore che punta a un altro puntatore. In altre parole, è una variabile che contiene l’indirizzo di un’altra variabile che, a sua volta, contiene un indirizzo.
##### Codici:
### Lezione 19: (strutture)
Le **struct** in C sono una delle caratteristiche più potenti e versatili del linguaggio, consentendo di combinare diversi tipi di dati in un’unica entità.
Una **struct** è una collezione di variabili di diversi tipi, raggruppate sotto un unico nome. Queste variabili sono chiamate membri della struct.
![[Pasted image 20241114194222.png]]
Questa struct `Persona` ha tre membri: `nome`, `età`, e `altezza`.
![[Pasted image 20241114194304.png]]
#### Struct Annidate:
Le **struct annidate** consentono di definire una struct all’interno di un’altra struct, permettendo di creare strutture dati gerarchiche.
![[Pasted image 20241114195349.png]]
In questo esempio, la struct `Studente` contiene una struct `Data` per memorizzare la data di nascita.
##### Accesso ai Membri di una Struct Annidata
![[Pasted image 20241114195438.png]]
#### Array di Struct

Un **array di struct** permette di creare una collezione di elementi di tipo struct, consentendo di gestire più 
entità simili in modo ordinato.
##### Codice:
![[Pasted image 20241114195515.png]]
la cui uscita sarà
![[Pasted image 20241114195714.png]]
#### Puntatori a Struct:
I **puntatori a struct** permettono di accedere ai membri di una struct tramite un puntatore. Questo è utile per passare le struct a funzioni senza copiare l’intera struttura, migliorando l’efficienza.
![[Pasted image 20241114195804.png]]
`r->larghezza` è equivalente a `(*r).larghezza`, ed è utilizzato per accedere ai membri di una struct tramite un puntatore.
### Lezione 20: (gli enumeratori):
#### Cosa sono?
Gli **enumeratori** in C sono un tipo speciale di variabile che ci consente di assegnare nomi significativi a interi. Questi nomi rendono più leggibile il codice sorgente, poiché forniscono un contesto significativo per i valori numerici. 
Chiamati anche “enum” in breve, sono una collezione di costanti intere denominate **valori enumerati**. Ogni valore enumerato è associato a un nome simbolico che rende più chiaro il suo significato. Gli enumeratori vengono utilizzati per creare un set limitato di valori che rappresentano uno stato, una scelta o una condizione.
##### Codice:
#### Come si dichiara?
![[Pasted image 20241114201821.png]]
In questo esempio, `enum GiorniDellaSettimana` è il nome dell’enumeratore, e i nomi simbolici elencati sono i valori enumerati. Di default, gli enumeratori iniziano con il valore 0 e successivamente incrementano di uno per ciascun elemento. Quindi, `Lunedì` ha il valore 0, `Martedì` ha il valore 1 e così via.
#### Come si usa?
Gli enumeratori vengono utilizzati per dichiarare variabili e costanti con i valori enumerati:
##### Esempio:
![[Pasted image 20241114202029.png]]In questo caso, stiamo dichiarando una variabile `oggi` di tipo `enum GiorniDellaSettimana` e assegnando il valore enumerato `Martedì` ad essa.
#### Personalizzare Valori Enumerati
È possibile personalizzare i valori enumerati 
assegnando valori specifici ai nomi simbolici:
![[Pasted image 20241114202231.png]]In questo esempio, stiamo assegnando valori specifici a ciascun nome simbolico. `Spento` avrà il valore 0, `Acceso` avrà il valore 1, `InAttesa` avrà il valore 5 e `Errore` avrà il valore -1.

#### Vantaggi degli Enumeratori
Gli enumeratori migliorano la leggibilità del codice, in quanto i nomi simbolici forniscono un contesto significativo per i valori. Questo rende più facile comprendere il significato di variabili e costanti all’interno del codice. Gli enumeratori sono spesso utilizzati per rappresentare stati, opzioni o scelte in modo più intuitivo.
### Lezione 21: (input e output)