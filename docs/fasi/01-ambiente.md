# Fase 1 — L'ambiente

Prima di scrivere una riga di codice: rendere la macchina uno stato noto, e **verificare**
invece di assumere.

## Cosa è stato fatto

Aggiornati gli strumenti già presenti e installato ciò che mancava.

| Strumento | Prima | Dopo |
|---|---|---|
| Python | 3.14.4 | **3.14.7** |
| Poetry | 2.3.4 | **2.5.1** |
| pipx | 1.11.1 | **1.17.5** |
| pyenv | 2.6.27 | **2.8.6** |
| MkDocs | 1.6.1 | invariato (già l'ultima) |
| GitHub CLI | assente | **2.101.0** |

Assenti e lasciati tali, come scelta: `uv`, `node`, `docker`. Nessuno serve al processo che
questo progetto mette alla prova, e ognuno avrebbe aggiunto superficie da mantenere.

## Con quale strumento, e perché

- **pyenv** per Python, **pipx** per gli strumenti a riga di comando, **Homebrew** per il
  resto. Ogni strumento installato dal gestore che gli compete: nessuna installazione
  globale con `pip`.
- **GitHub CLI** perché il repo va creato e pubblicato dal terminale. Il tracker dei ticket
  è Linear, ma il codice, la CI e le pull request vivono su GitHub: sono due ruoli diversi.

## Una verifica che valeva la pena fare

Python 3.14 è recente, e `mkdocs-material` non dichiarava di supportarlo. Invece di
scommettere, è stato creato un ambiente virtuale usa-e-getta e installato davvero lo stack
candidato.

Esito: funziona tutto, incluso `pydantic-core` — che essendo compilato era il vero rischio,
non FastAPI in sé. Nessun ripiego su Python 3.13.

!!! note "Il principio"
    Un dubbio su una versione si chiude con un'installazione vera, che costa due minuti, non
    con una deduzione dai metadati, che costa zero e può essere sbagliata.

## Un effetto collaterale da conoscere

Il file di versione globale di pyenv conteneva il prefisso `3.14`, non una versione esatta.
Installando la 3.14.7, **la versione attiva si è spostata da sola**. Non è un guasto, ma se
non lo sai te lo ritrovi addosso: da qui in avanti il progetto pinna la propria versione con
`.python-version`.

## Checkpoint umano

Gli aggiornamenti sono stati autorizzati esplicitamente prima di essere eseguiti. La scelta
di quale versione di Python pinnare nel progetto **non** è stata presa qui: è materia del
primo ADR, che si scrive dopo la specifica.

## Cosa rifaremmo diversamente

Controllare il file globale di pyenv **prima** di installare, non dopo: l'effetto collaterale
era prevedibile leggendo un file di una riga.
