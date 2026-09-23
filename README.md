# POC — Prenotazione sale riunioni

Progetto piccolo, dominio **inventato**, costruito per mettere alla prova un processo di
sviluppo, non per essere un prodotto.

## A cosa serve

Integrare in un solo flusso tre cose che oggi vivono separate:

1. il ciclo di un playbook SDLC AI-native (cattura dell'intento a monte, poi test, rilascio
   e manutenzione a valle);
2. un insieme di skill di engineering centrate su un issue tracker
   (spec → ticket → implementazione → review);
3. **Linear** come tracker reale.

Il risultato che conta non è l'applicazione: è la **documentazione del processo**, scritta
mentre le fasi accadono e pubblicata da questo repo, in modo che sia replicabile e
migliorabile da altri.

## Stato

Appena seminato. Nessuna decisione tecnica presa: `pyproject.toml` non dichiara ancora
dipendenze applicative di proposito — **la scelta dello stack è oggetto del primo ADR**, che
si scrive dopo la specifica, non prima.

## Come è organizzato il lavoro

| Artefatto | Dove |
|---|---|
| Intento del progetto | `intent/` |
| Specifiche | `spec/` |
| Decisioni architetturali | `docs/adr/` |
| Sito del processo | `docs/`, pubblicato con MkDocs |
| Ticket | Linear, progetto "POC - Prenotazione Sale" |
| Codice | `src/`, test in `tests/` |

Il referto dell'esperimento — ipotesi, metrica, esito — non vive qui ma in un vault di
studio separato: questo repo può cambiare o sparire, quel referto resta.
