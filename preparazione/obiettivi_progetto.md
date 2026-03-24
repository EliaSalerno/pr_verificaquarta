# Obiettivi del Progetto e Competenze Necessarie

Questo documento definisce gli obiettivi principali del progetto, mettendo in particolare rilievo i fondamenti teorici su cui si basa e le competenze tecniche necessarie per affrontarlo con successo.

## Obiettivi del Progetto

Il progetto mira alla realizzazione di un sistema integrato hardware-software in cui un dispositivo embedded (Arduino) comunica in modo stabile con un sistema di controllo (PC con Python) attraverso una connessione seriale. L'obiettivo finale è raccogliere dati dal mondo fisico (sensori), comandare periferiche (attuatori) e fornire all'utente un'interfaccia di monitoraggio e controllo, di tipo grafico (GUI desktop) o web.

In sintesi, il progetto si prefigge di:
1. Stabilire una comunicazione affidabile bidirezionale tra microcontrollore e PC.
2. Strutturare i dati scambiati secondo le logiche di pacchettizzazione dei protocolli di rete.
3. Creare un ecosistema software completo, che spazi dal basso livello (firmware) all'alto livello (interfaccia utente web/desktop), interamente organizzato in modo modulare e versionato.

---

## La Teoria del Progetto (Fondamenti Teorici)

La solida comprensione teorica dell'architettura è il prerequisito indispensabile per l'implementazione del progetto. Di seguito i pilastri teorici da padroneggiare:

### 1. Architetture di Calcolo: Microcontrollori vs Microprocessori
* **Architetture a confronto**: Comprendere le differenze strutturali e funzionali. Cos'è un sistema *System-on-a-Chip* (come Arduino, basato su ATmega328P) completo di memorie flash/RAM e periferiche I/O integrate, e quando è preferibile a una pura architettura basata solo su microprocessore o a sistemi embedded con S.O. (come un Raspberry Pi).
* Valutazione in base ad application domain, consumi energetici e programmabilità real-time.

### 2. Sistemi e Metodi di Trasmissione dei Dati
* **Comunicazione Seriale vs Parallela**: Conoscere le differenze prestazionali, di costo e di casistica d'uso tra il trasferire bit uno alla volta (seriale) rispetto a più bit simultanei (parallela).
* **Trasmissione Seriale Asincrona (UART/RS-232)**: Principi del trasferimento asincrono di dati (senza clock condiviso). Parametri critici: *baud rate*, bit di start/stop, controlli di parità ed handshake.
* **Protocollo I2C**: Studio del bus di comunicazione seriale standard per componenti a corto raggio. L'architettura logica ad indirizzamento (Master/Slave) e i ruoli di differenziazione meccanica dei due segnali vitali: SDA (dati) e SCL (clock).

### 3. Modelli di Rete, Pacchettizzazione e Protocolli (ISO/OSI)
* **Incapsulamento e Modello ISO/OSI**: Studio dell'impostazione logica a strati dei protocolli di rete moderni.
* **Trasposizione Seriale (Livelli 3 e 7)**: Adattare la teoria dei grandi protocolli allo scambio seriale grezzo. Come incapsulare i dati utili applicativi (Livello 7 - Applicazione) in pacchetti dotati di header, delimitatori e codici di controllo che ne garantiscano la corretta consegna e instradamento (Livello 3 - Rete).

---

## Competenze Necessarie (Technical e Soft Skills)

Per realizzare praticamente il progetto, lo studente deve saper mettere in campo le seguenti competenze:

### 1. Programmazione Embedded (Arduino in C/C++)
* Configurazione dei pin in modalità Input/Output per interagire fisicamente coi sensori e gli attuatori.
* Inizializzazione corretta del bus di comunicazione seriale (`Serial.begin()`) e lettura/scrittura ciclica e **non bloccante**.
* Conoscere le librerie standard embedded come `Wire.h` per interfacciarsi con l'hardware I2C.

### 2. Programmazione Backend e Scripting (Python)
* Sviluppo di logiche per instaurare un bridge software col microcontrollore tramite specifiche librerie (es. `pyserial`).
* Competenze logico-matematiche per le operazioni di parsing e spacchettamento dei dati (es: estrazione del payload dall'header pacchettizzato).
* Error handling (gestione di disconnessioni, timeout e timeout logico).

### 3. Sviluppo Interfacce Grafiche (GUI Desktop)
* Comprendere il paradigma della programmazione *Event-Driven* (guidata dagli eventi dell'utente).
* Competenze nell'utilizzo di librerie a finestre (come `tkinter` in Python) combinando il rendering della finestra (mainloop) in parallelo od integrato in modo sicuro con i processi di poll della porta seriale continua.

### 4. Sviluppo Applicazioni Web
* Padronanza dell'architettura di base del web: i protocolli basati su *Client-Server* e i fondamenti del protocollo HTTP (richieste GET, POST).
* Conoscenza pratica di un framework web leggero in Python (come **Flask**).
* Creazione di endpoint, interfacciamento con pagine dinamiche (tramite meccanismi come il template engine *Jinja2*) per portare in rete, online e visualizzabili in un browser, i dati estratti dai sensori fisici hardware hardware.

### 5. Versionamento e Controllo del Codice (Git)
* Utilizzo del tool **Git** per tracciare il ciclo di vita dello sviluppo del software salvando lo storico.
* Uso dei comandi fondamentali da linea di comando (`init`, `add`, `commit`, `status`, `.gitignore`).
* Capacità logica di isolare lo sviluppo di singole funzionalità lavorando per branch separati e risolvendone successivamente il merge.
