# Esercitazioni Preparatorie: Dalla Breadboard a Python

Questo documento contiene delle esercitazioni mirate e propedeutiche per abituare gli studenti al flusso di lavoro del "Compito di Realtà". L'obiettivo di queste attività più semplici è padroneggiare i singoli sensori e farli dialogare in modo basilare col PC.

---

## Esercitazione 1: Allarme Antincendio Seriale (Sensore di Fiamma)

**Obiettivo Didattico:** Imparare la lettura analogica/digitale e inviare un primo pacchetto strutturato rudimentale su seriale.
**Materiale:** Arduino, Sensore di Fiamma (IR), 1 LED rosso.

**Consegna per gli studenti:**
1. Collegate il sensore di fiamma ad Arduino (usate il pin digitale D0 per la soglia o A0 per il valore analogico).
2. Se il sensore rileva una fiamma, Arduino deve accendere fisicamente il LED rosso sulla breadboard.
3. Allo stesso tempo, Arduino NON deve inviare messaggi continui via Seriale. Deve inviare un pacchetto formattato come `<FIRE:ON>` solo nel momento in cui la fiamma viene accesa, e `<FIRE:OFF>` quando si spegne.
4. **Lato Python:** Scrivete uno script di 10 righe che si mette in ascolto sulla porta COM. Quando riceve `<FIRE:ON>`, stampa a terminale "ATTENZIONE! Rilevamento incendio in corso!".

**Competenza allenata per il progetto finale:** Sincronizzazione degli eventi (comunicare solo quando serve per non intasare la seriale) e primissimo approccio al parsing delle stringhe.

---

## Esercitazione 2: Antifurto per Cassaforte / Contagiri (Sensore di Hall)

**Obiettivo Didattico:** Uso della funzione `millis()` al posto di `delay()` e intercettazione di stati fisici.
**Materiale:** Arduino, Sensore Magnetico di Hall, una calamita.

**Consegna per gli studenti:**
Il sensore di Hall rileva la presenza di campi magnetici. Vogliamo simulare lo "sportello di una cassaforte" (se la calamita viene allontanata dal sensore innesca un allarme).
1. Programmate Arduino in modo tale che, quando la calamita viene allontanata dal sensore (stato HIGH/LOW dipendente dal modulo), inizi a emettere un allarme via seriale inviando la scritta `<ALLARME_PORTA>`.
2. **Vincolo obbligatorio:** La scritta non deve essere "spammata" a velocita' massima bloccando la CPU. Deve essere inviata ESATTAMENTE una volta ogni 500 millisecondi, ma e' ASSOLUTAMENTE VIETATO usare la funzione `delay(500)`. Dovete risolverlo usando la comparazione col timer `millis()`.

**Variante per l'uso dei motori (Contagiri):**
Attaccate la calamita a una ruota e contate quante volte il sensore rileva la calamita per calcolare i giri al minuto (RPM), sempre sfruttando `millis()`.

**Competenza allenata per il progetto finale:** Il No-Delay. Risolvere il problema logico del multitasking senza bloccare il microcontrollore, competenza essenziale se in futuro dovranno leggere sensori e pilotare moduli Radio contemporaneamente.

---

## Esercitazione 3: Monitor ECG Desktop (Sensore Battito Cardiaco)

**Obiettivo Didattico:** Graficare o gestire dati analogici rumorosi in tempo reale su una GUI Python.
**Materiale:** Arduino, Sensore Heartbeat (Pulse Sensor a infrarossi), Interfaccia Python (Tkinter o semplice terminale stampato ad arte).

**Consegna per gli studenti:**
1. Il sensore di battito cardiaco genera segnali molto rumorosi. Arduino deve leggere il pin analogico `A0` e mappare la lettura su un pacchetto rapido in stringa: es `B:850\n`.
2. **Lato Python:** I ragazzi devono creare una mini-vetrina (Tkinter) con una etichetta grande (Label).
3. Lo script Python deve leggere la seriale continuamente tramite una funzione `Window.after(10, lettura_seriale)` in modo che l'interfaccia non vada in blocco totale ('Not Responding').
4. Appena Python legge che il valore analogico supera una "soglia" definita ad arte (simbolizzando il battito o sistole), la Label del programma deve diventare ROSSA per 100 millisecondi, per poi tornare BIANCA.

**Competenza allenata per il progetto finale:** 
- Capire come i "rumori" dei sensori fisici analogici vadano filtrati (tramite codice o calibrazione) prima di poterci fare affidamento.
- Integrare la lettura infinita del `pyserial` all'interno del loop di una finestra grafica senza bloccare il computer del professore/cliente.
