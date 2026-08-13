# READY.

# Trail 001 -- La Macchina Commodore 64

## Stage 003 -- Incontriamo il 6510

---

# Informazioni sul Documento

| Proprietà | Valore |
|---|---|
| Documento | Stage 003 -- Incontriamo il 6510 |
| Lingua | Italiano |
| Tipo | Stage del Knowledge Trail |
| Trail | Trail 001 -- La Macchina Commodore 64 |
| Stage | 003 |
| Stato | Bozza |
| Versione | 0.1.0 |
| Difficoltà | ????? |
| Tempo di studio stimato | 60-90 minuti |
| Prerequisiti | Stage 001 -- Conosciamo la Macchina; Stage 002 -- Dentro il C64 |

---

# ? Destinazione del Sentiero

Abbiamo visto il Commodore 64 dall'esterno.

Abbiamo aperto la macchina.

Abbiamo conosciuto i suoi principali specialisti hardware.

Ora incontreremo il componente che **esegue effettivamente le istruzioni che fanno fare qualcosa al computer**.

La CPU.

Più precisamente:

**il MOS 6510.**

Alla fine di questo Stage dovresti aver compreso:

- che cosa fa realmente una CPU;
- perché la CPU è diversa dalla RAM, dalla ROM e dai dispositivi di I/O;
- che cos'è un'istruzione;
- che cosa sono i registri;
- che cosa fa il Program Counter;
- che cosa fa lo Stack Pointer;
- che cosa rappresenta il Processor Status Register;
- perché il 6510 appartiene alla famiglia del 6502;
- che cosa rende speciale il 6510 all'interno del C64;
- perché comprendere la CPU è fondamentale per comprendere il linguaggio Assembly.

Non è necessario conoscere l'Assembly prima di iniziare questo Stage.

Anzi, questo Stage è stato progettato proprio per prepararti ad affrontarlo.

---

# ? Cartello del Sentiero -- Qualcuno Deve Eseguire il Programma

Quando digitavi:

```text
PRINT "HELLO"
