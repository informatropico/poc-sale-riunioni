---
name: capture-intent
description: Cattura un'idea, un bisogno o un problema come intento versionato in intent/, prima che qualcuno cominci a progettare la soluzione. Usala quando arriva un'idea nuova, quando va deciso se vale la pena fare qualcosa, o quando un incidente o una metrica fanno nascere una richiesta di cambiamento.
---

# Capture Intent (`intent/`)

Primo passo del ciclo, a monte di tutto. Qui si cattura **il problema**; la soluzione arriva
dopo, altrove.

L'intento è scritto **con le parole di chi ha l'idea**, corretto da lui, e committato. Non è
un documento di specifica in miniatura: è la registrazione fedele di un bisogno, comprese le
parti che non sono ancora chiare.

## La regola che viene prima di tutte

Se questa skill e un artefatto approvato divergono, **vince l'artefatto** — e questa skill va
corretta. Le skill descrivono il metodo; le decisioni vivono negli artefatti (`intent/`,
`spec/`, `docs/adr/`).

Questa skill non contiene, e non deve mai contenere, decisioni sul merito del progetto.

## Le tre regole d'ingaggio

### 1. Non progettare

Niente framework, architettura, struttura dei dati, nomi di librerie, disegno delle pagine.
Se durante la conversazione emerge una soluzione, va annotata come **ipotesi**, marcata come
tale, non promossa a requisito. Progettare qui significa rispondere a una domanda che nessuno
ha ancora finito di porre.

### 2. Non riempire i buchi

Quando qualcosa non è chiaro, **si chiede**. Se resta senza risposta, **resta aperto**: va
nella sezione delle domande aperte, non colmato con l'interpretazione più probabile.

Un intento con molte domande aperte non è un lavoro fatto male. È il contrario: significa che
i vuoti sono stati riconosciuti invece che tappati. Serviranno subito dopo — è da lì che
parte il lavoro di diradare la nebbia.

### 3. Domande aperte, mai suggerite

Chiedi *"chi lo userà?"*, non *"immagino lo useranno i team interni, giusto?"*. La seconda
forma ottiene una conferma, non un'informazione: l'interlocutore accetta la tua ipotesi per
comodità e tu registri una risposta che non è sua.

È il rischio classico delle interviste ai committenti, e non sparisce perché a condurle è un
agente.

## Come si conduce

Conversazione, non questionario. Si parte da come la persona racconta la cosa, e si scava
dove serve:

- **Il problema**: cosa non funziona oggi, o cosa manca. Con parole sue.
- **Chi è coinvolto**: chi ha il problema, chi userà la cosa, chi decide. Se non c'è un
  destinatario, va detto che non c'è — è un'informazione, non una lacuna.
- **Come si vede che ha funzionato**: il criterio di successo, possibilmente osservabile.
- **Vincoli**: tempo, tecnologia obbligata, budget, cose che devono restare come sono.
- **Fuori scope**: cosa **non** si vuole. Spesso è la parte più informativa, e va chiesta
  esplicitamente perché nessuno la offre spontaneamente.
- **Domande aperte**: tutto ciò che resta incerto.

Fermati quando le risposte smettono di aggiungere informazione, non quando le sezioni
sembrano piene.

## L'artefatto

Un file in `intent/`, nome breve e descrittivo (`intent/<argomento>.md`), con le sezioni
sopra. Nessun template rigido: se il caso chiede una struttura diversa, proponila e spiega
perché.

Prima del commit:

1. **La persona rilegge e corregge.** È il checkpoint: le parole devono essere sue, e i
   fraintendimenti si correggono ora, non a valle.
2. Si committa con un messaggio che dice di cosa parla l'intento.
3. **Ci si ferma.** Il passaggio alla fase successiva è una decisione umana: un intento
   committato non autorizza nessuno a cominciare a progettare.

## Cosa succede dopo (e non è compito tuo)

L'intento approvato diventa l'ingresso della fase di progettazione, che comincia proprio
dalle **domande aperte** lasciate qui: quelle che si sanno formulare con precisione diventano
decisioni da prendere, le altre restano in attesa di diventare formulabili.

Per questo le domande aperte non sono uno scarto dell'intento: sono il suo prodotto più
utile.
