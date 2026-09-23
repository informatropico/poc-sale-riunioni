# Issue tracker: Linear

Ticket e specifiche vivono su **Linear**, workspace `mattia-personal`, team **`MAT`**,
progetto **"POC - Prenotazione Sale"** (`P-MAT-1`). Tutte le operazioni passano dal server
MCP `linear-server`. Codice, CI e pull request restano su **GitHub**.

## Specifiche: Documents, non ticket

Una specifica non è un'unità di lavoro: non ha stato, non si chiude, resta il riferimento
mentre i ticket nascono e muoiono.

- **Creare**: `save_document` con `title`, `content` (markdown) e `project: "P-MAT-1"`.
- **Aggiornare**: `save_document` con `id` e `patch` (o `content` per riscriverla).
- **Leggere / elencare**: `get_document` / `list_documents` filtrati sul progetto.
- I ticket la citano **per link** (`links: [{url, title}]` su `save_issue`), mai copiandola.

## Ticket

- **Creare**: `save_issue` con `team: "MAT"`, `project: "P-MAT-1"`, `title`, `description`.
  Stato iniziale: **`Todo`** se il ticket è prendibile subito, **`Backlog`** se ha un
  blocco non ancora chiuso.
- **Leggere**: `get_issue` con `id: "MAT-<n>"` e `includeRelations: true`; commenti con
  `list_comments`.
- **Elencare**: `list_issues` con `project: "P-MAT-1"` e i filtri `label`, `state`,
  `assignee` che servono.
- **Commentare**: `save_comment` con `issueId` e `body`.
- **Label**: `save_issue` con `addLabels` / `removeLabels`. Mai `labels`, che sostituisce
  l'intero insieme e cancellerebbe le label di tipo (`Bug`, `Feature`, `Improvement`).
- **Dipendenze**: relazioni di blocco **native**, `blockedBy` / `blocks` su `save_issue`.
  Mai come testo nella descrizione. Un ticket è sbloccato quando tutti i bloccanti sono in
  `Done`.
- **Prendere in carico**: `save_issue` con `assignee: "me"` e `state: "In Progress"`.
- **Chiudere**: commento con l'esito, poi `save_issue` con `state: "Done"`. Se non si fa:
  label `wontfix` e `state: "Canceled"`.

## Pull request

Le PR stanno su GitHub (`gh pr ...`) e **non entrano nel triage**. Per collegarle al
ticket, citare `MAT-<n>` nel titolo o nel ramo della PR.

## When a skill says "publish to the issue tracker"

- Una **specifica** (es. `/to-spec`) → Document di Linear sul progetto.
- Un **ticket** (es. `/to-tickets`) → issue su team `MAT`, progetto `P-MAT-1`, con link al
  Document della spec e dipendenze come `blockedBy`.

## When a skill says "fetch the relevant ticket"

`get_issue` con `includeRelations: true`, più `list_comments`. Se il ticket linka una
spec, leggerla con `get_document`.

## Wayfinding operations

Usate da `/wayfinder`. La **mappa** è lavoro, non specifica: è un ticket padre con i
ticket come sotto-issue.

- **Mappa**: issue con label `wayfinder:map`, corpo Notes / Decisions-so-far / Fog.
- **Ticket figlio**: `save_issue` con `parentId: "<mappa>"` e label `wayfinder:<tipo>`
  (`research` / `prototype` / `grilling` / `task`). Le label `wayfinder:*` si creano con
  `save_issue_label` al primo uso.
- **Blocco**: `blockedBy` nativo, come sopra.
- **Frontiera**: `list_issues` con `parentId: "<mappa>"`; scartare quelli in `Done` /
  `Canceled`, quelli con un bloccante aperto, quelli già assegnati. Vince il primo in ordine.
- **Claim**: `assignee: "me"`, prima scrittura della sessione.
- **Resolve**: commento con la risposta, `state: "Done"`, poi un puntatore (sintesi + link)
  nelle Decisions-so-far della mappa.
