# Roadmap del Progetto: Dall'Idea al Prototipo (Metodo RAD)

Questa è la traccia operativa del vostro team. Non perdetevi in muri di testo: seguite i passaggi nell'ordine indicato, spuntate le checklist e non saltate i fondamentali Checkpoint direzionali!

---

## Il Flusso di Lavoro Aziendale

![Flusso di Lavoro Aziendale RAD](grafo_progetto.png)

---

## Gli Step Operativi (Checklist)

### STEP 1: Kick-Off e Formazione Squadra
- [ ] Leggete insieme i 3 problemi posti dal cliente nel documento `compito_di_realta`.
- [ ] Sceglietene **UNO**.
- [ ] Aprite subito un repository su GitHub.
- [ ] Create il primo file `README.md` inserendo i vostri nomi e il problema scelto.

### STEP 2: Brainstorming (Svuotiamo il Magazzino)
*Rispondete a queste tre domande prima di fare qualsiasi altra cosa:*
1. Quale dispositivo sta "sul campo" a leggere i dati grezzi?
2. Quale dispositivo fa da "Cervello" remoto e gestisce lo schermo/reti?
3. Come viaggiano i dati nel vuoto nel mezzo?

### STEP 3: Il Documento di Proposta (FASE 1)
- [ ] Scrivete un breve documento testuale (bastano 1-2 pagine).
- [ ] Disegnate (anche a mano e poi fotografato) lo schema dell'architettura.
- [ ] Giustificate le vostre scelte.

### CHECKPOINT DIREZIONE (Il Pitch)
**Fermatevi qui.** Nessuno tocchi la tastiera per scrivere codice. 
Presentate la vostra idea al Docente (il Cliente). Convincetelo che la vostra architettura ha senso ed è economica e stabile.
*Se ricevete la firma, passate allo step 4.*

### STEP 4: Sviluppo Parallelo assistito da A.I. (FASE 2)
Create rami (branch) separati su Git e dividete il lavoro fisico, simulando il lavoro in team anche se l'utenza sarà la medesima. Usate l'A.I. in modo intelligente per farsi spiegare librerie sconosciute o generare la base del codice:
- **L'Ingegnere Hardware:** Delega all'A.I. la generazione dello sketch di Arduino per inizializzare il modulo Radio NRF24 o i sensori I2C, poi collega fisicamente i componenti. (accetto anche disegni del progetto).
- **Lo Sviluppatore Software:** Chiede all'A.I. la base per un'interfaccia Python (`Flask` o `tkinter`) e come mantenere attivo un ciclo di "ascolto" sulla porta evitando che l'interfaccia si blocchi.
- **L'Architetto di Rete (Tutti insieme):** Definisce su carta **l'esatta struttura del pacchetto ISO/OSI** (es: `<mittente|valore_sensore|checksum>`).

### STEP 5: Test di Integrazione
È il momento della verità. Unite i pezzi da ogni branch.
- [ ] I nodi si accendono senza andare in cortocircuito?
- [ ] Il protocollo ideato funziona? I dati arrivano nel formato stabilito?
- [ ] I cruscotti / l'interfaccia si aggiornano in tempo reale? (Regola d'oro: *No-Delay*).

### STEP 6: Demo e Deliverable (Consegna Finale)
- [ ] Eseguite il Merge finale dei vostri branch chiudendo il cerchio su GitHub.
- [ ] Preparate fisicamente la postazione sui banchi per l'arrivo del committente.
- [ ] Eseguite l'applicativo dimostrando che al verificarsi dell'evento fisico (es. passate la mano sul sensore), l'esito avverrà con successo sullo schermo remoto.
