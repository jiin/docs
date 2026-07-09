# Documentazione UTRtek

Sito di documentazione utente per il CMS UTRtek, costruito con [Mintlify](https://mintlify.com).

## Contenuto

Manuale in italiano per utenti non tecnici (segreteria, istruttori, allievi, amministratori). Copre:

- Introduzione e primi passi
- Concetti base (PIK, corsi, utenti, documenti)
- Navigazione del pannello Filament
- Guide operative passo passo
- Ruoli, permessi ed email

## Sviluppo locale

```bash
cd docs
mint dev
```

Apri `http://localhost:3000` per l'anteprima.

## Workspace

Il file `../utr.code-workspace` apre insieme il CMS (`cms`) e questa documentazione (`docs`).

## Terminologia

- **UTRtek** — nome del prodotto e del pannello
- **PIK Card** — carta didattica digitale
- **CMS** — il repository `utrtek-brevetti` (applicazione Laravel/Filament)
- **Pannello** — interfaccia admin su `/admin`

## Stile

- Italiano, tono semplice e diretto
- Guide con componenti `<Steps>` di Mintlify
- Seconda persona ("tu", "clicca", "vai")
- Titoli in sentence case
