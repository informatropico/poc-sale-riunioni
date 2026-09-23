# Risorse

Le fonti su cui si regge il processo descritto in questo sito. Tutte verificate
direttamente: link, autore e contenuto controllati, non raccolti di seconda mano.

## Il playbook AI-native

- [The AI-native SDLC playbook](https://claude.com/blog/the-ai-native-sdlc-playbook) — Louis
  Claxton, Anthropic, 21 agosto 2026. Il post che definisce il ciclo a sei fasi e il
  principio dell'artefatto committato.
- [Il corso omonimo](https://academy.claude.com/courses/ai-native-sdlc-playbook) — stesso
  contenuto in quattordici lezioni, una per play. Più comodo se si vuole approfondire una
  fase alla volta.

!!! warning "Un limite da conoscere"
    Il playbook **non tratta l'avvio di un progetto nuovo**: niente scelta dello stack,
    niente struttura iniziale del repository. Presuppone un repo che esiste già, con la sua
    documentazione e le sue convenzioni. È uno dei vuoti che questo progetto documenta.

## Le skill di engineering

- [mattpocock/skills](https://github.com/mattpocock/skills) — il repository.
- [Documentazione per singola skill](https://github.com/mattpocock/skills/tree/main/docs/engineering)
  — diciotto pagine. Nell'ordine utile a chi segue questo processo: `wayfinder`, `to-spec`,
  `to-tickets`, `implement`, `triage`, `code-review`.
- [La skill di setup](https://www.aihero.dev/skills-setup-matt-pocock-skills) — cosa
  configura e perché va eseguita una volta per repository.
- [L'ordine del flusso, chiarito dall'autore](https://x.com/mattpocockuk/status/2075856898142740821?lang=en)
  — `/wayfinder → /to-spec → /to-tickets → /implement`. Utile perché è l'errore più comune:
  usare la mappa come se fosse l'intero flusso.

## Il tracker e i suoi agenti

- [Linear for Agents](https://linear.app/agents) — cosa significa delegare un'issue a un
  agente, e quali agenti sono integrati.
- [Documentazione tecnica per sviluppatori di agenti](https://linear.app/developers/agents) —
  Agent Sessions, webhook, installazione OAuth. Serve a chi volesse costruire l'agente che
  oggi manca.

## Sviluppo guidato dalle specifiche

Tre riferimenti per collocare questo processo in un panorama più ampio.

- [GitHub Spec Kit](https://github.com/github/spec-kit) — principi di progetto scritti una
  volta, poi una specifica per funzionalità. Lo stack si sceglie nella fase di piano.
- [Documentazione di Kiro](https://kiro.dev/docs/steering/) — separa i documenti di
  fondazione del progetto (prodotto, tecnologia, struttura) dalle specifiche per
  funzionalità.
- [Understanding Spec-Driven Development](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
  — Birgitta Böckeler, 15 ottobre 2025. La lettura critica: l'eccesso di documentazione da
  revisionare, un solo flusso per problemi di ogni taglia, il falso senso di controllo.
  Da leggere **dopo** gli altri due, come contrappeso.
