# CLAUDE.md

Repo di un POC: un'applicazione piccola su dominio inventato, usata per **mettere alla prova
un processo**. Il valore sta nel processo e nella sua documentazione, non nel prodotto.

> Questo file è **deliberatamente scarno**. Non dice cosa deve essere il prodotto: quello lo
> cattura `intent/`, e scriverlo qui significherebbe deciderlo prima di averlo chiesto.
> Cresce per *working rule*: quando lo stesso errore capita due volte, la correzione entra
> qui.

## Regole di ingaggio

- **Proponi, non decidere.** Ogni scelta di merito — scope, stack, struttura, quale lavoro
  fare prima — è di Mattia. L'agente porta opzioni e una raccomandazione.
- **Un artefatto per fase, committato.** Una fase finisce quando produce un file in version
  control, non quando la conversazione sembra conclusa.
- **Niente decisioni di progetto dentro le skill.** Le skill descrivono il metodo; le
  decisioni vivono negli artefatti (intent, spec, ADR). Se una skill e un artefatto
  divergono, **vince l'artefatto**.
- **Dichiara le assunzioni.** Se serve assumere qualcosa per procedere, va detto, non
  nascosto in mezzo al lavoro.

## Convenzioni

- Messaggi di commit in **italiano**, brevi e descrittivi.
- Push su `main` solo tramite pull request quando la CI sarà attiva.
- Documentazione del processo in `docs/`, generata con MkDocs.

## Agent skills

### Issue tracker

Ticket su Linear (team `MAT`, progetto "POC - Prenotazione Sale") tramite il server MCP `linear-server`; specifiche come Documents di Linear. Codice e PR su GitHub. Vedi `docs/agents/issue-tracker.md`.

### Triage labels

Le cinque label predefinite, in un gruppo Linear `Triage` a selezione singola. Vedi `docs/agents/triage-labels.md`.

### Domain docs

Single-context: `CONTEXT.md` e `docs/adr/` alla radice. Vedi `docs/agents/domain.md`.
