# UTRtek — Guida utente

Documentazione in italiano per il pannello gestionale UTRtek (CMS Laravel/Filament).

Costruita con [Mintlify](https://mintlify.com).

## Contenuto

- Introduzione e primi passi (login OTP, profilo)
- Concetti base (PIK Card, corsi, utenti, documenti)
- Navigazione del menu Filament
- Guide operative passo passo
- Ruoli, permessi ed email automatiche
- Glossario

## Sviluppo locale

```bash
npm i -g mint
mint dev
```

Apri `http://localhost:3000`.

## Validazione

```bash
mint validate
mint broken-links
```

## Deploy

Vedi [DEPLOY.md](./DEPLOY.md) per la guida completa al deploy su Mintlify.

In sintesi:

1. Push su `main` del repository `jiin/docs`
2. Collega il repo nel [dashboard Mintlify](https://dashboard.mintlify.com)
3. Installa la GitHub App per deploy automatici
4. (Opzionale) Configura `docs.utrtek.com` come dominio personalizzato

## Workspace

Il file `../utr.code-workspace` apre insieme:

- **cms** — `utrtek-brevetti`
- **docs** — questo repository
