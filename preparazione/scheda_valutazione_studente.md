# Scheda di Valutazione Individuale: Compito di Realtà IoT

**Studente:** _____________________________  
**Progetto/Gruppo:** ___________________________  
**Ruolo principale svolto:** [ ] Hardware/Embedded  |  [ ] Software/Python  |  [ ] Architetto/Rete

---

## 1. FASE 1: Analisi e Documento di Proposta (Punti: __ / 2)
Valutazione del contributo dello studente nella redazione del documento iniziale (indipendentemente dal ruolo tecnico successivo).
- [ ] **Comprensione del problema (0.5 pti):** Ha inquadrato la logistica e le necessita' della sfida aziendale?
- [ ] **Architettura proposta (1 pto):** Ha contribuito a proporre una logica di comunicazione ragionata (es. scegliere correttamente tra Raspberry/Arduino o Cavo/Radio)?
- [ ] **Giustificazione tecnico-economica (0.5 pti):** Sa difendere il perche' non e' stata usata una soluzione piu' semplice ma errata?

---

## 2. FASE 2: Hard Skills Tecniche (Valutare l'area di competenza - Punti: __ / 4)
*Spuntare solo i campi relativi al ruolo effettivamente ricoperto dallo studente nel Team.*

### [ Area: Sviluppatore Hardware (C/C++ Arduino e Sensori) ]
- [ ] **Elettronica Base:** Cablaggio corretto, senza cortocircuiti o pin analogici usati impropriamente.
- [ ] **No-Delay & Efficienza:** Usa millis() o interrupt logici al posto dei delay() bloccanti.
- [ ] **Protocolli Locali:** Sa recuperare correttamente i dati da un sensore (I2C) o gestire l'hardware di trasmissione (NRF24L01 / IR).
- [ ] **Serializzazione:** Il codice scrive messaggi nel formato ISO/OSI concordato col team Python senza inviare letture grezze.

### [ Area: Sviluppatore Software (Python, Backend, GUI) ]
- [ ] **Acquisizione Dati:** Riceve e decodifica in modo pulito i dati seriali, separando il payload dall'header (Parsing ISO/OSI).
- [ ] **Error Handling:** Gestisce logicamente gli errori (es. timeout di trasmissione, porta disconnessa, messaggi corrotti senza che il programma crashi).
- [ ] **Interfaccia (GUI/Web):** L'interfaccia si aggiorna in real-time senza bloccarsi in attesa (Uso di `.after` su Tkinter o flussi asincroni su Flask).
- [ ] **Usabilita':** L'interfaccia e' presentabile e risponde alle richieste del "Cliente" (mostra allarmi o da' i giusti comandi).

---

## 3. Metodologia e Versionamento (Punti: __ / 2)
Queste competenze si applicano a tutti i membri del team, indipendentemente dal ruolo.
- [ ] **Uso logico di Git (1 pto):** Ha effettuato commit personali con una frequenza ragionevole? I messaggi di commit sono descrittivi ("Aggiunto sensore temp") e non casuali ("asdf")?
- [ ] **Integrazione e Branch (1 pto):** Ha lavorato su rami slegati o ha causato/risolto civilmente i conflitti di merge col repository centrale del gruppo?

---

## 4. Soft Skills & Pitch Aziendale (Punti: __ / 2)
Valutazione dell'esposizione e del problem solving durante la Fase di Consegna (Demo).
- [ ] **Proprieta' di linguaggio (1 pto):** Usa correttamente termini come baud rate, incapsulamento, master/slave, event-driven quando presenta l'architettura.
- [ ] **Troubleshooting / Problem Solving (1 pto):** Di fronte alle domande tecniche del docente (es: "Cosa succede se taglio il cavo durante l'esecuzione?") o a un bug live, sa ragionare sul problema e individuare dove cercare o ha panico/delega la risposta all'Intelligenza Artificiale.

---

### NOTE DOCENTE E VOTO FINALE
**Punteggio Totale Ottenuto:** ______ / 10

*Osservazioni e feedback formativo per lo studente:*
_
_
_
_


---
<div style="page-break-before: always;"></div>

## Guida Operativa per il Docente: Valutare il lavoro con l'A.I.
Durante l'interrogazione (Pitch), usare questi 4 pratici "trucchi" per distinguere chi ha fatto puro copia-incolla rispetto a chi ha usato l'Intelligenza Artificiale come reale strumento di sviluppo.

1. **La Sfida del "Live Coding" (Rompi il giocattolo)**: Chiedere una modifica banale e immediata mentre il codice è in esecuzione (es. *"Fai lampeggiare il LED due volte"* oppure *"Cambia al volo l'header del pacchetto seriale da <TEMP> a <TERMOMETRO> in entrambi i file"*). 
   - *Studente Attivo:* Sa esattamente in quale cartella, file e funzione andare. Effettua la modifica in un minuto.
   - *Copia-Incolla:* Entra in panico logico, non sa da che file partire o dove si trovi fisicamente la variabile interessata.

2. **Cronologia di Git ("L'Ispezione Iterativa")**: Verificare lo storico del repository alla voce 'Commits'.
   - *Studente Attivo:* Avrà molti piccoli commit progressivi che mostrano bug fix, tentativi ed errori risolti, dimostrando di aver provato, testato, corretto insieme all'A.I. (es "corretto bug lettura NRF24").
   - *Copia-Incolla:* Presenterà 1 o massimo 2 commit ciclopici (chiamati spesso "Initial commit") contenenti l'intero sistema software definitivo, incollato in blocco direttamente da ChatGPT.

3. **La Teoria del Costrutto Alieno (Code Review mirata)**: Cercare all'interno del loro codice sintassi mai viste in classe e non in programma (es. *List Comprehensions* in Python `[x for x in data if x > 0]`, comandi come `yield`, moduli esoterici in C++ o metodi anonimi/lambda).
   - *Azione Insegnante:* Indirizzare il dito a quella precisa riga e chiedere: "Molto elegante questa soluzione. Perché non hai usato un classico ciclo `for`? Qual è il vantaggio qui in termini di calcolo?". Se sono stati loro, seppur supportati dall'A.I., sapranno argomentare la scelta tecnica di ottimizzazione.

4. **Focus sulla "Gestione del Disastro" (Edge Cases)**: Spesso l'A.I. di base genera soluzioni funzionanti in caso perfetto (cavo connesso, rete velocissima, nessun disturbo elettrico locale).
   - *Azione Insegnante:* Interrompere la connessione bruscamente sul momento e vedere come il software affronta l'eccezione, oppure domandarglielo ("Se in questo momento il NRF24 si rompe, il ciclo Python si frizza bloccando tutto per sempre?").
   - *Studente Attivo:* Avrà sperimentato il problema dal vivo curando gli *edge cases* (gestendo i blocchi con timeout, `try/except` o controlli incrociati sul payload), oppure quantomeno ti saprà subito rispondere: "Sì proffessor, il codice non è protetto e Python scatterà un TimeoutError chiudendosi!".
