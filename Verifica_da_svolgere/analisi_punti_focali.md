# Punti Focali per la Verifica Valutativa
> Estratto da `attività.md` — Analisi concetti teorici e pratici

---

## Macro-aree del Progetto

Il percorso didattico copre **tre grandi ambiti**:

| # | Area | Natura |
|---|------|--------|
| 1 | Comunicazione embedded (Arduino) | Teorica + Pratica |
| 2 | Integrazione Python–Hardware | Pratica |
| 3 | Sviluppo applicazioni Python (GUI, Web) | Pratica |
| 4 | Reti e protocolli (ISO/OSI) | Teorica |
| 5 | Versionamento e organizzazione (Git) | Pratica |

---

## Trasmissione Seriale su Arduino

### Teoria
- Cos'è la comunicazione **seriale** (UART/RS-232): definizione, caratteristiche
- Parametri fondamentali: **baud rate**, bit di start/stop, parità
- Come Arduino gestisce la porta seriale (`Serial.begin()`, `Serial.print()`, `Serial.read()`)
- Differenza tra comunicazione **sincrona** e **asincrona**

### Pratica
- Configurare e usare il **Monitor Seriale** dell'IDE Arduino
- Scrivere sketch Arduino che inviano/ricevono dati su seriale
- Verificare il corretto funzionamento con strumenti di debug

---

## I2C su Arduino

### Teoria
- Cos'è il protocollo **I2C** (Inter-Integrated Circuit)
- Architettura **Master/Slave**: come funziona l'indirizzamento (7 bit)
- Segnali **SDA** (dati) e **SCL** (clock)
- Vantaggi rispetto a SPI e UART: numero di pin, distanza, velocità

### Pratica
- Uso della libreria `Wire.h` su Arduino
- Collegamento di dispositivi I2C (sensori, display OLED, ecc.)
- Lettura e scrittura di dati con `Wire.beginTransmission()` / `Wire.read()`

---

## Microcontrollori vs Microprocessori

### Teoria — Punto critico per il test
- **Definizioni** precise: microprocessore (CPU standalone) vs microcontrollore (sistema completo su chip)
- Componenti interni di un microcontrollore: CPU, RAM, ROM/Flash, I/O, timer, ADC
- Confronto su: **costo**, **consumo energetico**, **applicazione tipica**, **programmabilità**
- Esempi concreti: Arduino (ATmega328P) come microcontrollore; Raspberry Pi come sistema con microprocessore

### Pratica
- Saper scegliere il dispositivo giusto per un progetto dato
- Riconoscere i pin e le funzioni di un Arduino

---

## Comunicazione Seriale vs Parallela

### Teoria — Punto critico per il test
- **Comunicazione seriale**: un bit alla volta su un singolo canale
- **Comunicazione parallela**: più bit simultanei su più canali
- Confronto: velocità, costo, distanza, interferenze (crosstalk)
- Perché la seriale ha prevalso nel lungo raggio (USB, SATA, PCIe seriale)
- Protocolli seriali comuni: UART, SPI, I2C, USB, RS-485

### Pratica
- Identificare quale tipo di comunicazione usa un dispositivo
- Collegare correttamente dispositivi seriali su Arduino

---

## Python + Arduino su Seriale

### Teoria
- Come il PC comunica con Arduino tramite porta COM (USB-seriale)
- Il concetto di **handshake** e sincronizzazione tra i due dispositivi
- Struttura di un protocollo di comunicazione semplice (header, payload, fine messaggio)

### Pratica — Punto critico per il test
- Libreria **`pyserial`**: installazione e uso (`serial.Serial()`, `.read()`, `.write()`)
- Ciclo lettura/scrittura tra Python e Arduino
- Gestione degli errori di connessione (porta non disponibile, timeout)
- Parsing dei dati ricevuti dalla seriale

---

## Modello ISO/OSI — Livelli 3 e 7 su Seriale

### Teoria — Punto critico per il test
- Struttura del modello **ISO/OSI** a 7 livelli (breve panoramica di tutti)
- **Livello 3 - Rete**: indirizzamento IP, instradamento, pacchettizzazione
- **Livello 7 - Applicazione**: protocolli di alto livello (HTTP, FTP, MQTT, ecc.)
- Come questi livelli si applicano a una comunicazione su seriale fisica
- Concetto di **incapsulamento** dei dati (pacchetto con header + payload)

### Pratica
- Progettare un semplice **protocollo applicativo** per la comunicazione Arduino–PC
- Strutturare un pacchetto dati con: identificatore, lunghezza, payload, checksum

---

## GUI con Python (tkinter)

### Teoria
- Cos'è una **GUI** (Graphical User Interface) e perché migliorano l'usabilità
- Architettura **event-driven**: il programma risponde agli eventi utente
- Widget principali: Label, Button, Entry, Frame, Canvas

### Pratica — Punto critico per il test
- Struttura di un'app tkinter: `Tk()`, `mainloop()`
- Creazione di widget e gestione degli **eventi** (command, bind)
- Integrazione della lettura seriale in un'app tkinter (uso di `after()` per non bloccare il loop)
- Layout manager: `pack()`, `grid()`, `place()`

---

## Python Web con Flask

### Teoria
- Cos'è un **web framework** e il pattern **MVC/MTV**
- Architettura **client–server** su HTTP
- Cos'è un **endpoint** (route) e come funziona una richiesta HTTP (GET, POST)
- Concetto di **template** (Jinja2)

### Pratica — Punto critico per il test
- Struttura minima di un'app Flask: `app = Flask(__name__)`, `@app.route()`, `app.run()`
- Creazione di route e restituzione di risposte HTML/JSON
- Uso dei template HTML con Jinja2 (`render_template()`)
- Passaggio di dati tra Python e HTML (`{{ variabile }}`, `{% for %}`)
- Integrazione Flask + dati da Arduino (es. esporre un sensore su API REST)

---

## Comandi Git

### Teoria
- Cos'è il **versionamento** e perché è fondamentale nello sviluppo
- Concetti: **repository**, **commit**, **branch**, **merge**, **remote**

### Pratica — Punto critico per il test
- Comandi essenziali: `git init`, `git clone`, `git add`, `git commit`, `git push`, `git pull`
- Gestione dei branch: `git branch`, `git checkout`, `git merge`
- Risoluzione dei conflitti base
- Uso di `.gitignore`

---

## Riepilogo Punti Focali per il Test

| Priorità | Argomento | Tipo |
|----------|-----------|------|
| 🔴 Alta | Comunicazione seriale vs parallela | Teoria |
| 🔴 Alta | Python + pyserial con Arduino | Pratica |
| 🔴 Alta | Flask: route, template, GET/POST | Pratica |
| 🔴 Alta | GUI tkinter: eventi e integrazione seriale | Pratica |
| 🔴 Alta | Livelli ISO/OSI 3 e 7 + pacchettizzazione | Teoria |
| 🟡 Media | Microcontrollori vs microprocessori | Teoria |
| 🟡 Media | I2C: architettura master/slave | Teoria |
| 🟡 Media | Git: comandi base e workflow | Pratica |
| 🟢 Base | UART e parametri seriali (baud rate) | Teoria |
| 🟢 Base | tkinter widget e layout | Pratica |

---

## Suggerimento per la Struttura del Test

```
Sezione A — Teoria (30%)
  - Domande a risposta multipla su ISO/OSI, seriale/parallela, microcontrollori

Sezione B — Analisi di codice (40%)
  - Leggere uno snippet Python (pyserial / Flask / tkinter) e spiegarne il funzionamento

Sezione C — Progettazione (30%)
  - Progettare l'architettura di un sistema Arduino + Python con GUI o interfaccia web
  - Descrivere il protocollo di comunicazione usato
```

---

## TODO — Da completare al prossimo accesso

- [ ] Generare bozza completa del test con domande per ogni sezione
- [ ] Aggiungere esempi di codice da analizzare (Sezione B)
- [ ] Definire il punteggio per ogni domanda
- [ ] Aggiungere i PDF mancanti per I2C, microcontrollori, seriale/parallela, Git
