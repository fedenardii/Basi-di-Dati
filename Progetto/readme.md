# Progetto
## Traccia: FilmSphere

### Obiettivo
Progettare e realizzare un database relazionale (MySQL) per **FilmSphere**, un servizio di memorizzazione e **streaming** di contenuti video online, includendo alcune funzionalità di **data analytics**.

### Deliverable (output attesi)
- Documentazione di progetto (PDF, con indice e scelte motivate fase per fase)
- Diagramma **E-R non ristrutturato** + **E-R ristrutturato** (PDF)
- Schema logico relazionale e vincoli di integrità (anche tramite CHECK/TRIGGER)
- Script **MySQL** completo:
  - creazione schema
  - popolamento (dati sufficienti per demo)
  - implementazione operazioni e funzionalità richieste (query/procedure/event/trigger)
- Funzionalità di analytics lato DB

### Fasi di lavoro (workflow consigliato)
1. Analisi delle specifiche
2. Progettazione concettuale (diagramma E-R)
3. Ristrutturazione E-R (eliminazione generalizzazioni, attributi composti/multivalore, ecc.)
4. Individuazione di **almeno 8 operazioni** significative sui dati (letture/scritture)
5. Analisi prestazioni delle operazioni (volumi, frequenze, tavola accessi)
6. Miglioramento prestazioni tramite introduzione di **ridondanze**
7. Progettazione logica (traduzione a schema relazionale + vincoli referenziali)
8. Analisi dipendenze funzionali e normalizzazione (obiettivo: **BCNF**)
9. Implementazione su MySQL (DDL + DML + vincoli + trigger)
10. Implementazione funzionalità di analisi dati (analytics)

### Requisiti minimi (checklist)
- ≥ **8 operazioni** implementate in MySQL (query/insert/update/delete)
- ≥ **2 ridondanze** + relativa analisi costo/beneficio e gestione aggiornamenti
- ≥ **2 vincoli di integrità generici** (es. CHECK/trigger)
- Schema in **Boyce–Codd (BCNF)**, salvo parti volutamente non normalizzate per ridondanza
- Dataset di test adeguato per mostrare output sensati
- Discussione orale del progetto (tutti i membri devono saper spiegare tutto)

---

## Dominio applicativo: aree funzionali richieste (sintesi)

### 1) Area contenuti
- Film: id univoco, titolo, descrizione, genere, regista, cast principale, durata, anno, paese
- Lingue disponibili (audio) e lingue sottotitoli
- Rating globale e (opzionale) rating personalizzati per utente

### 2) Area formati
- Formati audio/video con caratteristiche tecniche (risoluzione, bitrate, aspect ratio, dimensione file, ecc.)
- Associazione Film–Formato (possibile tabella ponte) + versioning/rilascio
- Restrizioni geografiche su formati

### 3) Area clienti
- Utenti (id, dati personali, credenziali)
- Tracking connessioni: inizio/fine, device, indirizzo IP e geolocalizzazione
- Piani di abbonamento (Basic/Premium/Pro/Deluxe/Ultimate) + pacchetti/limitazioni
- Fatturazione: pagamenti, carte, fatture, scadenze, stato pagato
- (Eventuale) raccomandazione contenuti basata su history

### 4) Area streaming (CDN)
- Modellazione server CDN (posizione, banda, capacità, stato di carico)
- Funzionalità di scelta server “migliore” (vicinanza + bilanciamento carico)
- Caching e previsione contenuti da mettere in cache per utente

### 5) Area analytics
- Classifiche contenuti/formati più visti per area geografica e piano
- Bilanciamento carico: stima sovraccarichi e proposta spostamenti contenuti
- Custom analytics (a scelta) motivata e documentata

