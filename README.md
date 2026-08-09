# Guardrails Health (`grh`)

Presidio del dominio clinico sullo sviluppo di software sanitario — modello dati clinico e codifiche, interoperabilità, sicurezza del paziente, workflow reale di reparto — più il percorso guidato di qualificazione del software come dispositivo medico.

Modulo BMad. È una porzione del bundle [Guardrails](https://github.com/mlarese/bmad-module-guardrails):
stesse figure, stesso comportamento, solo l'area health.

> **Generato.** Questo repository è prodotto da `tools/build_modules.py` nel
> repository [bmad-module-guardrails](https://github.com/mlarese/bmad-module-guardrails).
> Le modifiche si fanno lì e poi si rigenera: qui vengono sovrascritte.

## Figure

| Figura | Ruolo | Skill | Cosa presidia |
| ------ | ----- | ----- | ------------- |
| 🩺 Livia | Clinical Informatics | `grl-agent-health` | Medico che ha passato vent'anni dentro i sistemi informativi sanitari: sa che un farmaco non è una stringa, che una dose senza unità di misura è un errore in attesa, e che il… |

## Skill e workflow

| Skill | Comando | Cosa fa |
| ----- | ------- | ------- |
| `grh-profile` | Profila il progetto | Raccoglie in pochi minuti gli otto campi che danno contesto a tutte le figure, criticità inclusa. |
| `grh-profile` | Aggiorna il profilo | Riallinea il profilo quando il progetto cambia, e dice se il cambiamento invalida rischi già accettati. |
| `grh-board` | Convoca il collegio | Fa leggere lo stesso artefatto alle sole figure pertinenti e restituisce un riepilogo unico, conflitti compresi. |
| `grh-board` | Rischi già accettati | Mostra, raggruppato per figura, quello che il progetto ha consapevolmente scelto di accettare. |
| `grh-board` | Gate di rilascio | Verifica una release identificata e restituisce GO, GO_CON_CONDIZIONI, NO_GO o EVIDENZA_INSUFFICIENTE. |
| `grl-mdsw` | È un dispositivo medico? | Verifica se una funzione software ha una finalità medica su un singolo paziente, distingue archiviazione e visualizzazione da interpretazione clinica e indica se rientra nel MDR e in quale classe (I, IIa, IIb, III), con l'impatto sul piano. Non produce certificazione. |
| `grl-automation` | Instrada un'automazione | Classifica lo scenario, sceglie agenti e workflow BMad e dichiara capability mancanti, scope e approvazioni, includendo social/content e creative video. |
| `grl-automation` | Prepara un piano eseguibile | Costruisce passi idempotenti con input, output, precondizioni, rischio, approvazione e rollback. |
| `grl-automation` | Esegui controlli read-only | Raccoglie evidenze e confronti riproducibili senza modificare sistemi esterni. |
| `grl-automation` | Prepara un dry-run | Genera e valida diff o payload senza spendere, pubblicare o applicare side effect. |
| `grl-automation` | Esegui dopo approvazione | Applica solo lo scope approvato, registra prima/dopo e osserva il risultato; in caso di errore attiva il rollback. |
| `grl-automation` | Riprendi un'automazione | Riprende un run esistente dal primo passo non concluso senza duplicare scritture o side effect. |

## Installazione

```
bmad install grh
```

Poi, come primo passo, `grh-profile`: raccoglie il profilo di progetto — settore,
dati trattati, mercato, stack, criticità — e da lì ogni figura deriva quanto essere
severa. Senza profilo il default resta `normal` e le figure partono senza contesto.

## Memoria condivisa

Il profilo vive in `{project-root}/_bmad/memory/grl-shared/project-profile.md`, insieme
a `decisions.md` e `accepted-risks.md`. Il percorso è lo stesso per tutti i moduli
Guardrails: installandone due, il profilo resta uno solo e si compila una volta.

## Convivenza con il bundle

Questo modulo installa skill con **lo stesso nome** del bundle `grl` — `grl-agent-health`
sta identica in entrambi. Bundle e moduli tematici non vanno installati insieme nello
stesso progetto: si sceglie il bundle completo, oppure i moduli delle aree che servono.

## Licenza

MIT.
