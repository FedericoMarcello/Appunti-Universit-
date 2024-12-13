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
