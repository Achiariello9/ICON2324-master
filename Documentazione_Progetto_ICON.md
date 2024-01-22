# SISTEMA DI DIAGNOSTICA DI UNA MALATTIA

## Gruppo di lavoro
| **Nome Cognome** | **Matricola** | **Email** |
| ---- | ---- | ---- |
| Leonardo Colucci | 758298 | l.colucci23@studenti.uniba.it |
| Gianfranco De Vincenzo | 758318 | g.devincenzo14@studenti.uniba.it |
| Andrea Chiariello | 717771 | a.chiariello9@studenti.uniba.it |

[Link GitHub](https://github.com/Achiariello9/ICON2324.git "https://github.com/Achiariello9/ICON2324.git")

## Sistema di diagnostica

Il sistema del progetto mira a diagnosticare la presunta malattia del "**virus di fantasia**" basandosi sui dati forniti dall'utente. L'utente è coinvolto nel processo rispondendo a una serie di domande mirate, finalizzate a identificare i sintomi che l'utente potrebbe manifestare e le possibili correlazioni con il presunto virus. Questo processo serve a stabilire la probabilità che l'utente sia affetto dal patogeno.

La procedura diagnostica adottata dal sistema segue una logica di backward chaining. In un linguaggio logico come Prolog, ciò significherebbe interrogare lo stato di malattia e, notando atomi con valori sconosciuti, porre automaticamente domande relative a tali atomi definiti come 'askable'. Tuttavia, a causa delle limitazioni della libreria utilizzata, il sistema è costretto a operare con una modalità di forward chaining. In questa modalità, vengono poste domande iniziali, e ciascuna domanda controlla le sue condizioni per essere formulata, per poi determinare se è presente o meno una forma di malattia nell'individuo.

L'approccio generale si basa su una regola di derivazione, che è una forma generalizzata della regola di inferenza nota come modus ponens:

Se “$ℎ ← 𝑎1 ∧ … ∧ 𝑎𝑚$” è una clausola definita nella base di conoscenza e 
ogni 𝑎𝑖 è stato derivato, allora $h$ può essere derivato.

Dove:
```
• ℎ è la testa dell’atomo,
• 𝑎1 ∧ … ∧ 𝑎𝑚 è il corpo della clausola, formato da 𝑎𝑖 atomi
```

Se 𝑚 > 0, la clausola è detta regola, se 𝑚 = 0, il corpo è vuoto e la clausola è detta  clausola atomica o fatto, e tutte le clausole atomiche nella base di conoscenza sono sempre derivate in maniera diretta. Nel caso del sistema di diagnostica del virus la base di conoscenza è stata organizzata dalle seguenti clausole:

```
𝑠𝑖𝑛𝑡𝑜𝑚𝑖_𝑏𝑎𝑠𝑒 ⇐ 𝑝𝑒𝑟𝑑𝑖𝑡𝑎_𝑑𝑖_𝑝𝑒𝑠𝑜
𝑠𝑖𝑛𝑡𝑜𝑚𝑖_𝑏𝑎𝑠𝑒 ⇐ 𝑑𝑖𝑎𝑟𝑟𝑒𝑎
𝑣𝑜𝑚𝑖𝑡𝑜 ⇐ 𝑛𝑎𝑢𝑠𝑒𝑎
𝑐𝑖𝑠𝑡𝑖 ⇐ 𝑒𝑠𝑎𝑚𝑒_𝑝𝑜𝑠𝑖𝑡𝑖𝑣𝑜
𝑐𝑖𝑠𝑡𝑖 ⇐ 𝑛𝑜_𝑒𝑠𝑎𝑚𝑒 ∧ 𝑑𝑜𝑙𝑜𝑟𝑒_𝑎𝑑𝑑𝑜𝑚𝑖𝑛𝑎𝑙𝑒 ∧ 𝑟𝑖𝑔𝑜𝑛𝑓𝑖𝑎𝑚𝑒𝑛𝑡𝑜
𝑢𝑙𝑐𝑒𝑟𝑎 ⇐ 𝑑𝑜𝑙𝑜𝑟𝑒_𝑎𝑑𝑑𝑜𝑚𝑖𝑛𝑎𝑙𝑒 ∧ 𝑎𝑐𝑖𝑑𝑖𝑡à_𝑑𝑖_𝑠𝑡𝑜𝑚𝑎𝑐𝑜 ∧ 𝑛𝑎𝑢𝑠𝑒𝑎
𝑚𝑎𝑙𝑎𝑡𝑡𝑖𝑎 𝑙𝑖𝑒𝑣𝑒 ⇐ s𝑖𝑛𝑡𝑜𝑚𝑖_𝑏𝑎𝑠𝑒 ∧ 𝑐𝑖𝑠𝑡𝑖 ∧ 𝑣𝑜𝑚𝑖𝑡𝑜
𝑚𝑎𝑙𝑎𝑡𝑡𝑖𝑎 𝑔𝑟𝑎𝑣𝑒 ⇐ 𝑠𝑖𝑛𝑡𝑜𝑚𝑖_𝑏𝑎𝑠𝑒 ∧ 𝑢𝑙𝑐𝑒𝑟𝑎
```

La malattia presenta due forme distintive: una forma lieve e una forma grave. Entrambe condividono sintomi di base, tra cui perdita di peso improvvisa e episodi di diarrea. La forma lieve è caratterizzata da sintomi aggiuntivi come la presenza di cisti e episodi di vomito, mentre la forma grave è contrassegnata dalla presenza di ulcere.

La presenza di cisti può essere confermata in modo certo se l'utente ha sostenuto un esame medico con risultato positivo. In caso contrario, il sistema prende in considerazione sintomi correlati, come rigonfiamento e dolore addominale, per valutare la probabilità della presenza di cisti.

Analogamente, la presenza di ulcere viene identificata in base alle risposte dell'utente riguardo a sintomi come acidità di stomaco, nausea e dolore addominale.

