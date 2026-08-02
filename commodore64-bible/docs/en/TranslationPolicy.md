# READY.

# Commodore 64 Bible

## The Complete Reverse Engineering Project

---

# Translation Policy

| Property    | Value              |
| ----------- | ------------------ |
| Document    | Translation Policy |
| Language    | English            |
| Status      | Draft              |
| Version     | 0.1.0              |
| Last Update | 2026-08-02         |

---

# Purpose

The Commodore 64 Bible is an international project.

The goal of this policy is to define how documentation translations are created, maintained and verified.

The purpose is to make knowledge accessible to the largest possible community while preserving technical accuracy and consistency.

---

# Canonical Language

English is the official reference language of the project.

The English documentation represents the canonical source.

All translations must be based on the English version.

---

# Supported Languages

The project starts with:

* English (canonical);
* Italian (first translation).

Additional languages may be added in the future.

Examples:

* French;
* German;
* Spanish;
* Russian;
* Chinese;
* Japanese.

Each language must have its own dedicated directory.

Example:

```
docs/

    en/

    it/

    fr/

    de/
```

---

# Translation Principles

## 1. Preserve Meaning, Not Just Words

Translations should communicate the original meaning.

A literal word-by-word translation is not always required.

Technical accuracy and clarity are the priorities.

---

## 2. Keep Structure Identical

Translated documents should preserve:

* title hierarchy;
* sections;
* tables;
* examples;
* references;
* document metadata.

The structure should remain synchronized with the original document.

---

## 3. English Is the Source of Truth

When differences exist between translations, the English version is considered authoritative.

Changes should always be applied first to the English document.

Translations should then be updated accordingly.

---

# Technical Content Rules

## Source Code

Source code is always written in English.

This includes:

* labels;
* variable names;
* macro names;
* routine names;
* comments inside source examples.

Example:

Correct:

```asm
PrintString:
    ; Print a zero terminated string
```

Incorrect:

```asm
StampaStringa:
    ; Stampa una stringa terminata da zero
```

---

## Technical Terminology

Hardware terminology should remain consistent.

Examples:

Preferred:

* VIC-II;
* SID;
* CIA;
* raster interrupt;
* sprite multiplexing;
* zero page;
* cycle counting.

Avoid unnecessary translation of established technical terms.

---

# Translation Metadata

Every translated document must indicate:

* original document;
* original version;
* translation version;
* translation date.

Example:

```
Language:
Italian

Translated From:
docs/en/ProjectPhilosophy.md

Original Version:
0.1.0

Translation Version:
0.1.0
```

---

# Encoding Standard

All documentation files must use:

```
UTF-8
```

This guarantees compatibility with international languages and tools.

---

# Translation Status

Translations may have different maturity levels.

## Draft

Initial translation.

Requires review.

---

## Review

Translation completed and being checked.

---

## Stable

Translation reviewed and synchronized with the original document.

---

# Community Contributions

Everyone is welcome to contribute translations.

Contributors should:

* respect the original meaning;
* maintain technical terminology;
* avoid unnecessary modifications;
* update translation metadata.

---

# Final Principle

The purpose of translation is not only to convert words.

It is to allow more people to understand, learn and contribute.

Knowledge preserved in one language is valuable.

Knowledge shared across languages becomes universal.

READY.
