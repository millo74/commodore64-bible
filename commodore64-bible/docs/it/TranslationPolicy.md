# READY.

# Commodore 64 Bible

## The Complete Reverse Engineering Project

---

# Politica delle Traduzioni

| Proprietà            | Valore                       |
| -------------------- | ---------------------------- |
| Documento            | Politica delle Traduzioni    |
| Lingua               | Italiano                     |
| Stato                | Draft                        |
| Versione             | 0.1.0                        |
| Ultimo Aggiornamento | 2026-08-02                   |
| Traduzione di        | docs/en/TranslationPolicy.md |
| Versione originale   | 0.1.0                        |

---

# Scopo

La Commodore 64 Bible è un progetto internazionale.

Questa politica definisce come le traduzioni della documentazione vengono create, mantenute e verificate.

L'obiettivo è rendere la conoscenza accessibile alla comunità più ampia possibile mantenendo accuratezza tecnica e coerenza.

---

# Lingua Canonica

L'inglese è la lingua ufficiale di riferimento del progetto.

La documentazione inglese rappresenta la sorgente canonica.

Tutte le traduzioni devono essere basate sulla versione inglese.

---

# Lingue Supportate

Il progetto nasce con:

* inglese (lingua canonica);
* italiano (prima traduzione).

In futuro potranno essere aggiunte altre lingue.

Ad esempio:

* francese;
* tedesco;
* spagnolo;
* russo;
* cinese;
* giapponese.

Ogni lingua deve avere una propria directory dedicata.

Esempio:

```
docs/

    en/

    it/

    fr/

    de/
```

---

# Principi di Traduzione

## 1. Preservare il Significato, Non Solo le Parole

Le traduzioni devono comunicare il significato originale.

Una traduzione letterale parola per parola non è sempre necessaria.

La priorità è mantenere chiarezza e accuratezza tecnica.

---

## 2. Mantenere la Struttura Identica

I documenti tradotti devono preservare:

* gerarchia dei titoli;
* sezioni;
* tabelle;
* esempi;
* riferimenti;
* metadati del documento.

La struttura deve rimanere sincronizzata con il documento originale.

---

## 3. L'Inglese È la Fonte Ufficiale

Quando esistono differenze tra traduzioni diverse, la versione inglese è considerata quella autorevole.

Le modifiche devono essere applicate prima al documento inglese.

Successivamente devono essere aggiornate le traduzioni.

---

# Regole per il Contenuto Tecnico

## Codice Sorgente

Il codice sorgente è sempre scritto in inglese.

Questo include:

* label;
* nomi delle variabili;
* nomi delle macro;
* nomi delle routine;
* commenti negli esempi di codice.

Esempio:

Corretto:

```asm
PrintString:
    ; Print a zero terminated string
```

Non corretto:

```asm
StampaStringa:
    ; Stampa una stringa terminata da zero
```

---

## Terminologia Tecnica

La terminologia hardware deve rimanere coerente.

Esempi:

Preferire:

* VIC-II;
* SID;
* CIA;
* raster interrupt;
* sprite multiplexing;
* zero page;
* cycle counting.

Evitare traduzioni non necessarie di termini tecnici consolidati.

---

# Metadati delle Traduzioni

Ogni documento tradotto deve indicare:

* documento originale;
* versione originale;
* versione della traduzione;
* data della traduzione.

Esempio:

```
Lingua:
Italiano

Tradotto da:
docs/en/ProjectPhilosophy.md

Versione originale:
0.1.0

Versione traduzione:
0.1.0
```

---

# Standard di Codifica

Tutti i documenti devono utilizzare:

```
UTF-8
```

Questo garantisce compatibilità con lingue internazionali e strumenti moderni.

---

# Stato delle Traduzioni

Le traduzioni possono avere differenti livelli di maturità.

## Draft

Prima versione della traduzione.

Richiede revisione.

---

## Review

Traduzione completata in fase di controllo.

---

## Stable

Traduzione revisionata e sincronizzata con l'originale.

---

# Contributi della Comunità

Tutti sono invitati a contribuire alle traduzioni.

I contributori devono:

* rispettare il significato originale;
* mantenere la terminologia tecnica;
* evitare modifiche non necessarie;
* aggiornare i metadati della traduzione.

---

# Principio Finale

Lo scopo della traduzione non è soltanto convertire parole.

È permettere a più persone di comprendere, imparare e contribuire.

La conoscenza preservata in una sola lingua è preziosa.

La conoscenza condivisa tra più lingue diventa universale.

READY.
