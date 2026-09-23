# Fase 3 — Il tracker

I ticket di questo progetto non vivono su GitHub ma su **Linear**. Il codice, la CI e le
pull request restano su GitHub: sono due ruoli distinti, tenuti distinti apposta.

## Perché è una fase e non una configurazione

Le skill di engineering che questo progetto mette alla prova sono costruite **attorno a un
issue tracker**: producono una specifica, la spezzano in ticket, li smistano, li
implementano, ne rivedono il risultato. Il tracker non è un accessorio del flusso, ne è il
supporto.

E qui c'è il punto: quelle skill supportano GitHub, GitLab e file markdown locali. Per
qualunque altro tracker — Linear compreso — chiedono all'umano di **descrivere il flusso in
prosa**, e lo registrano così com'è.

Quindi l'integrazione non esiste già: va scritta. È il primo pezzo originale di questo
progetto.

## Cosa è stato fatto

Esplorato ciò che il server MCP di Linear espone davvero, dato che la documentazione
ufficiale non lo elenca ("strumenti per trovare, creare e aggiornare oggetti… altre
funzionalità in arrivo").

Risultato: **oltre settanta strumenti**, ben oltre le issue — progetti, team, stati, label,
commenti, documenti, milestone, cicli, release, notifiche, allegati, e perfino diff e review.

Due scoperte hanno cambiato il disegno dell'integrazione:

1. **Le relazioni di blocco sono native.** Creando un ticket si possono dichiarare
   direttamente i ticket che lo bloccano. Le dipendenze non vanno quindi scritte come testo
   nella descrizione: diventano collegamenti veri, navigabili.
2. **Le label possono essere gruppi a selezione singola.** Serve per il punto qui sotto.

## L'attrito vero: le label di triage

Il flusso prevede cinque stati di smistamento — *da smistare*, *servono informazioni*,
*pronto per un agente*, *pronto per una persona*, *non si fa*. Nel workspace esistono solo
`Bug`, `Feature` e `Improvement`.

Mapparli sugli esistenti sarebbe un errore di categoria: `Bug`/`Feature`/`Improvement` dicono
**cosa è** un ticket, gli stati di smistamento dicono **a che punto è** e **chi lo può
prendere**. Sono due assi indipendenti — un bug può essere pronto per un agente oggi e in
attesa di informazioni domani.

**Proposta**: creare i cinque valori come **gruppo a selezione singola**, così che un ticket
non possa portarne due insieme. È l'invariante dello smistamento, imposta dalla struttura
invece che dalla disciplina.

!!! question "Una domanda lasciata aperta di proposito"
    Gli stati che Linear ha già — *Backlog*, *Todo*, *In Review* — rappresentano in parte le
    stesse informazioni: "pronto per una persona" somiglia a *In Review*, "servono
    informazioni" somiglia a un ticket fermo in *Backlog*.

    C'è quindi una sovrapposizione fra ciò che le skill chiedono e ciò che il tracker già
    offre. Si parte come chiedono le skill e si osserva sul campo se gli stati rendono le
    label ridondanti: è una misura da fare, non una previsione da indovinare.

## Checkpoint umano

La descrizione del flusso e la proposta sulle label sono state preparate come **proposta**.
La configurazione effettiva avviene in una sessione aperta dentro questo repository — la
skill di setup esamina la cartella in cui gira, quindi eseguirla altrove configurerebbe il
progetto sbagliato.

## Esito della configurazione

La skill di setup è stata eseguita dentro il repository. Ha prodotto tre file in
`docs/agents/`, che le skill di engineering leggono, e una sezione `## Agent skills` in
`CLAUDE.md`.

- **`issue-tracker.md`**: scritto da zero, perché per Linear non esiste un modello. È la
  descrizione del flusso in prosa che la skill chiede, tradotta in operazioni MCP concrete.
- **`triage-labels.md`**: le cinque label predefinite, con i nomi che le skill si
  aspettano, dentro il gruppo `Triage` a selezione singola, come proposto sopra.
- **`domain.md`**: contesto unico, un solo `CONTEXT.md` e `docs/adr/` alla radice. Il
  repo non ha la forma di un monorepo, quindi non c'era scelta da fare.

Due decisioni sono emerse al checkpoint umano. Non erano nella proposta:

1. **Le specifiche sono Documents di Linear, non ticket.** Una specifica non è un'unità di
   lavoro: non ha stato, non si chiude, e resta il riferimento mentre i ticket nascono e
   muoiono citandola per link. Il ticket padre con sotto-ticket resta invece lo strumento
   per la mappa di `/wayfinder`, che è lavoro.
2. **Lo stato iniziale dei ticket dice se si possono prendere.** Un ticket parte in `Todo`
   se è prendibile subito, in `Backlog` se dipende da qualcosa non ancora fatto.

La domanda sulla sovrapposizione fra label di triage e stati di Linear resta aperta: si
misura sul campo.
