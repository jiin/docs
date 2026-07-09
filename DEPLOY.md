# Deploy documentazione UTRtek (Mintlify)

Guida passo passo per pubblicare la guida utente su Mintlify.

## Prerequisiti

- Account [Mintlify](https://mintlify.com/start)
- Accesso admin al repository GitHub `jiin/docs`
- (Opzionale) Accesso DNS per `docs.utrtek.com`

## 1. Pubblicare il codice su GitHub

Prima del deploy, assicurati che tutte le pagine siano sul branch `main`:

```bash
cd /Users/neri/Development/UTR/docs
git add .
git commit -m "feat(docs): aggiungi guida utente UTRtek"
git push origin main
```

## 2. Creare il progetto Mintlify

1. Vai su [mintlify.com/start](https://mintlify.com/start)
2. Completa l'onboarding con il tuo account
3. Scegli **GitHub** come provider
4. Seleziona il repository **`jiin/docs`**
5. Branch di deploy: **`main`**
6. Directory radice: **`/`** (il file `docs.json` è nella root)

Al termine riceverai un URL provvisorio:

```
https://<nome-progetto>.mintlify.site
```

## 3. Installare la GitHub App

1. Nel [dashboard Mintlify](https://dashboard.mintlify.com) vai in **Git Settings**
2. Clicca **Install GitHub App**
3. Autorizza l'organizzazione `jiin` e il repository `docs`
4. Conferma i permessi

Da questo momento, ogni push su `main` aggiorna automaticamente il sito.

## 4. Verificare il deploy

Dopo il push:

1. Apri il dashboard Mintlify → **Deployments**
2. Controlla che l'ultimo deploy sia **Successful**
3. Apri l'URL `.mintlify.site` e verifica le pagine principali:
   - `/` (home)
   - `/primi-passi/accedere`
   - `/guide/emettere-pik`
   - `/glossario`

## 5. Dominio personalizzato (consigliato)

Per usare `https://docs.utrtek.com`:

### 5.1 Aggiungi il dominio nel dashboard

1. Vai in [Custom domain setup](https://dashboard.mintlify.com/settings/deployment/custom-domain)
2. Inserisci `docs.utrtek.com`
3. Clicca **Add domain**

### 5.2 Configura il DNS

Il dashboard mostra **due record TXT** da aggiungere prima del CNAME.

**Importante:** non aggiungere il CNAME finché entrambi i TXT non risultano verificati (spunta verde).

Quando i TXT sono verificati, aggiungi:

| Tipo  | Nome | Valore                  |
|-------|------|-------------------------|
| CNAME | docs | `cname.mintlify.builders` |

La propagazione DNS può richiedere fino a 24–48 ore.

### 5.3 Canonical URL

Il file `docs.json` è già configurato con:

```json
"seo": {
  "metatags": {
    "canonical": "https://docs.utrtek.com"
  }
}
```

Se usi un dominio diverso, aggiorna questo valore prima del push.

## 6. CI su GitHub Actions

Il workflow `.github/workflows/docs.yml` esegue automaticamente:

- `mint validate` — verifica che la build sia valida
- `mint broken-links` — controlla i link interni

Si attiva su push e pull request verso `main`.

## 7. Sviluppo locale

```bash
npm i -g mint
cd docs
mint dev
```

Apri `http://localhost:3000`.

Comandi utili:

```bash
mint validate      # verifica build
mint broken-links  # controlla link
mint update        # aggiorna CLI
```

## 8. Checklist finale

- [ ] Codice pushato su `main`
- [ ] Progetto Mintlify collegato a `jiin/docs`
- [ ] GitHub App installata
- [ ] Deploy riuscito su `.mintlify.site`
- [ ] Dominio `docs.utrtek.com` configurato (opzionale)
- [ ] Link "Apri pannello" funzionante (`https://www.utrtek.com/admin`)
- [ ] Logo UTRtek sostituito in `/logo/` (attualmente placeholder Mintlify)

## Personalizzazioni future

| Elemento | File | Note |
|----------|------|------|
| Logo | `logo/light.svg`, `logo/dark.svg` | Sostituire con logo UTRtek |
| Favicon | `favicon.svg` | Icona UTRtek |
| Colori | `docs.json` → `colors` | Già allineati al pannello (ambra) |
| Navbar | `docs.json` → `navbar` | Link al CMS e sito |

## Supporto

- [Documentazione Mintlify](https://mintlify.com/docs)
- [Deploy con GitHub](https://mintlify.com/docs/deploy/github)
- [Dominio personalizzato](https://mintlify.com/docs/customize/custom-domain)
