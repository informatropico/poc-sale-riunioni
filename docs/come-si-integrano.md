# Come si integrano i tre strumenti

Questo progetto fa convivere tre cose nate separate. Questa pagina spiega **dove si
incastrano**, perché nessuna delle tre da sola basta, e quale principio decide i casi in cui
si contraddicono.

## I tre pezzi, e il buco che ciascuno lascia

| | Cosa copre | Cosa gli manca |
|---|---|---|
| **Il playbook AI-native** | la catena completa: cattura dell'intento a monte, poi test, rilascio, manutenzione. E il principio dell'**artefatto committato** | dà per scontato che tu sappia già *cosa* specificare. Non dice come si arriva a saperlo |
| **Le skill di engineering** | il centro, in modo denso: mappa delle decisioni, specifica, ticket, implementazione, revisione | parte dalla specifica. Nessuna cattura a monte, niente test/rilascio/manutenzione |
| **Il tracker** | lo stato condiviso del lavoro | non ha opinioni sul processo. È un contenitore, non un metodo |

Si **compongono**, non si scelgono: ognuno riempie un buco degli altri.

## La catena, dall'idea al codice

| Fase | Artefatto | Strumento | Dove vive |
|---|---|---|---|
| Cattura dell'intento | `intent.md` | skill dedicata | repo |
| Diradare la nebbia | decisioni | `/wayfinder` | mappa + ticket sul tracker |
| Specifica | `spec.md` | `/to-spec` | repo |
| Scomposizione | ticket | `/to-tickets` | tracker |
| Costruzione | codice + test | `/implement`, `/tdd` | repo |
| Revisione | pull request | `/code-review` | GitHub |
| Manutenzione | metriche → nuovo intento | — | CI |

## Intento e nebbia: due domande diverse

È il punto che si fraintende più facilmente, perché sembrano sovrapporsi. Non è così.

- **L'intento raccoglie le domande di bisogno**: cosa serve, a chi, cosa conterebbe come
  successo, cosa è fuori scope. Di queste **l'originatore è la fonte**: la risposta esiste
  già, va solo estratta e messa per iscritto.
- **La mappa raccoglie le domande di rotta**: cosa va deciso prima di poter costruire. Di
  queste **nessuno ha la risposta in tasca**: vanno scoperte indagando, prototipando o
  discutendo.

!!! tip "Il criterio, quando non sai dove mettere una domanda"
    Se la risposta la sai e basta dirla, è **intento**. Se va scoperta, è **nebbia**.

Il collegamento fra i due è letterale: **le domande che l'intento lascia deliberatamente
aperte sono la prima nebbia**. Un intento onesto ne lascia parecchie — è un pregio, non un
difetto: significa che non ha riempito i vuoti con ipotesi.

La mappa poi le tratta in due modi. Quelle che si sanno formulare con precisione diventano
ticket subito; quelle che si intuiscono ma non si sanno ancora formulare restano in una
sezione a parte e diventano ticket più tardi, man mano che la frontiera avanza. Il criterio
non è *"so rispondere?"* ma **"so formulare la domanda?"**.

## Dove i due possono pestarsi i piedi

Il primo atto della mappa è dare un nome alla **destinazione**, e per farlo la skill
interroga l'umano. Lasciata a briglia sciolta, rifà le domande di scope a cui l'intento ha
già risposto.

La regola che lo evita:

> La destinazione si **deriva** dall'intento, non si rinegozia. La mappa può chiedere di
> precisarla, non di ridecidere cosa si vuole costruire.

È lo stesso principio che regge tutto il resto: **quando una skill e un artefatto approvato
divergono, vince l'artefatto**.

## Dove vivono gli artefatti, e perché

Gli artefatti del processo — intento, specifiche, decisioni architetturali — vivono **nel
repository, committati**. I ticket vivono sul tracker.

La ragione non è estetica. Il principio portante del playbook è che ogni fase finisce
scrivendo un file in version control e la successiva comincia leggendolo: è questo che rende
il processo verificabile a posteriori. Un documento che vive solo nel tracker non ha diff,
non passa da una revisione, non lascia storia. Perderebbe esattamente la proprietà per cui
lo si scrive.

La distinzione che resta valida è un'altra: **una specifica non è un'unità di lavoro**. Non
ha stato, non si chiude, e resta il riferimento mentre i ticket nascono e muoiono citandola.
Per questo non è un ticket — ma è un file versionato, non una pagina nel tracker.

## Una nota su cosa il tracker non fa

Il tracker permette di delegare un'issue a un agente: la persona resta responsabile, l'agente
diventa esecutore, e il lavoro torna indietro come commenti e cambi di stato. Alcuni agenti
commerciali sono già integrati così.

**L'agente che usiamo qui non è fra quelli.** La conseguenza pratica, da sapere prima di
costruirci sopra un'aspettativa: puoi lavorare dentro il tracker e la sessione successiva
leggerà quello stato, ma **nulla nel tracker fa partire una sessione**. Il tracker è lo stato
condiviso, non il motore. Il motore è sempre una sessione aperta da una persona.

## Quando la mappa non serve

La skill della mappa ha una condizione di arresto esplicita: se cartando non emerge nebbia —
la strada è già chiara, il lavoro sta in una sessione sola — dice di fermarsi e non fare la
mappa.

Su un progetto piccolo può succedere, ed è un esito legittimo. Forzare una mappa per far
tornare il piano significherebbe misurare la propria fedeltà al piano invece che l'utilità
dello strumento.
