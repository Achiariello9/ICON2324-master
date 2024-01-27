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

## Sistema esperto/Sommario

Un sistema esperto è un'applicazione di intelligenza artificiale che si impegna nella risoluzione di problemi, cercando di emulare i comportamenti di esperti in un determinato campo di attività. La sua struttura fondamentale include una knowledge base che rappresenta e conserva informazioni e regole riguardanti il dominio in questione. L'inference engine è responsabile dell'applicazione pratica delle nozioni acquisite dalla base di conoscenza, mentre l'interfaccia utente facilita l'interazione tra il sistema e l'utente.

## Implementazione del sistema esperto

Abbiamo sviluppato un sistema esperto in Python utilizzando la libreria Experta. Questo sistema si basa su regole che associano fatti accaduti a condizioni (LHS) e azioni (RHS). Ad esempio, per ogni sintomo, abbiamo definito una regola che chiede all'utente se riscontra quel sintomo e aggiorna il fatto corrispondente di conseguenza.

Il sistema analizza i sintomi dell'utente e, in base alle risposte, attiva altre regole correlate ai sintomi. A seconda dei sintomi attivati, vengono considerate regole aggiuntive relative a condizioni più complesse come ulcere, cisti e vomito. Alla fine, il sistema applica una regola finale che comunica la diagnosi basata sui sintomi dell'utente.

Inizialmente, il sistema chiede all'utente dei sintomi di base. Se l'utente presenta almeno uno dei sintomi basilari, come perdita di peso o diarrea, il sistema procede nell'analisi per determinare la forma della malattia. Se l'utente mostra sintomi della forma lieve del virus, come nausea e eventualmente vomito, il sistema cerca di confermare la presenza di cisti.

Se l'utente mostra tutti i sintomi della forma lieve, riceverà una diagnosi positiva. Se manca un sintomo tra cisti e vomito, il sistema esamina la possibilità che l'utente sia affetto dal secondo stadio della malattia. In questo caso, il sistema cerca di determinare la presenza di ulcere, considerando sintomi come dolore addominale, acidità di stomaco e nausea. Se l'utente presenta tutti e tre questi sintomi, il sistema conclude che l'utente ha contratto la forma grave del virus.

**Esempi tratti dal codice**

// Immagine

Questa regola è responsabile di comunicare la diagnosi all'utente quando il sistema ha determinato che l'utente ha contratto la forma lieve della malattia. Nella parte sinistra della regola (LHS), le condizioni necessarie per l'applicazione della regola sono che i fatti relativi ai sintomi di base, al vomito e alle cisti siano tutti impostati a True. Nella parte destra della regola (RHS), il sistema si occupa di comunicare la diagnosi all'utente attraverso stampe o messaggi appropriati.

// Immagine

Questa regola viene attivata quando i fatti nella parte sinistra (LHS) sono valutati come True. Una volta attivata, il sistema porrà una domanda all'utente e, in base alla risposta, imposterà il fatto relativo al sintomo come True o False.

// Immagine

Se il sintomo "nausea" è stato identificato come True nella regola precedente, questa regola successiva viene attivata per determinare se l'utente sta vivendo attacchi di vomito.

