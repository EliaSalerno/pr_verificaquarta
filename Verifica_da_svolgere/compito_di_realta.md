# Compito di Realtà: Progettazione di un Sistema IoT Integrato

**Disciplina:** Tecnologie e Progettazione di Sistemi Elettrici ed Elettronici (TPS)
**Metodologia:** RAD (Rapid Application Development)

---

## Scenario e Metodologia di Lavoro

Siete stati assunti da un'agenzia di consulenza tecnologica che fornisce soluzioni IoT personalizzate. Il vostro team lavorerà seguendo la metodologia **RAD (Rapid Application Development)**, che prevede iterazioni veloci, focus immediato sulle esigenze dell'utente e continui confronti per allinearsi alle specifiche del cliente.

**Non avrete una soluzione o un'architettura già pronta.** Dovrete analizzare un problema reale partendo dalle problematiche espresse ("Il Cliente H"), selezionare intuitivamente gli strumenti adatti dal vostro magazzino aziendale e progettare un'architettura funzionante che risolva l'ostacolo.

Il lavoro sarà suddiviso in due passaggi fondamentali:

### FASE 1: Incontro col Cliente e Documento di Proposta (Durata stimata: 2-3 ore)
In questa fase simulerete l'interazione commerciale con il committente. Dopo aver scelto uno dei problemi proposti, redigerete un **Documento di Proposta Tecnico-Commerciale** in cui:
1. Analizzate la criticità e spiegate concettualmente come intendete risolverla (Qual è il piano?).
2. Formulate un'architettura del sistema: decidete quali nodi usare (chi fa il cervello? chi legge i dati?), come comunicheranno (Seriale? Radio? Infrarosso?) e che interfacce fornirete.
3. Giustificate le vostre scelte tecnologiche in funzione delle problematiche e dei costi (Perché usare la Radio e non il Cavo? Perché un Microcontrollore alla porta invece di un Raspberry Pi completo?).

### FASE 2: Progettazione Dettagliata con A.I. (Durata stimata: 4-6 ore)
*Attenzione: Si può accedere a questa fase solo dopo l'approvazione del documento della Fase 1 dal docente/cliente.*
Per lo sviluppo tecnico vi è concesso l'utilizzo di una **Intelligenza Artificiale** come vostro "Assistente Sviluppatore" per esplorare librerie hardware complesse, generare codice boiler-plate, analizzare pattern di programmazione o aiutarvi con il debug. 
In questa fase puntate a realizzare un prototipo basilare e funzionante, focalizzandovi sulla solidità della trasmissione dati e della logica applicativa.

---

## Il Magazzino Aziendale (Risorse a Disposizione)
Per risolvere i problemi, potete attingere ai seguenti macro-strumenti tecnologici. Siete liberi di mixarli come preferite:
* **Hardware:** Microcontrollori (es. Arduino), Microprocessori / Schede Embedded (es. Raspberry Pi), Sensori e Attuatori standard.
* **Componenti di Trasmissione & Reti:** Cavo seriale USB/UART, Moduli Radio NRF24L01, Ricetrasmettitori Infrarossi (IR), Bus I2C.
* **Linguaggi e Software:** C/C++ per lato embedded, Python o script per i nodi logici avanzati (es. interfacce con `Flask` per pagine Web o `tkinter` per GUI desktop), e l'imprescindibile **Git** per il lavoro di squadra e il versionamento in remoto.

---

## I Problemi del Cliente (Scegliete la Vostra Sfida)

Nessuno di questi problemi ha una soluzione unica. Analizzate gli ostacoli logistici e tecnologici.

### Sfida 1: "La Serra Agricola Isolata"
**Il Contesto:** Un'azienda agricola possiede diverse serre posizionate lontano dall'ufficio principale dell'agronomo.
**La Problematica:** L'agronomo necessita di monitorare continuamente i parametri vitali delle serre (temperatura, luce, umidità terra) e di voler forzare l'accensione di ventole o pompe d'acqua a distanza dal suo ufficio. Posare un cablaggio fisico per centinaia di metri tra serra e ufficio per spostare i dati è logisticamente ed economicamente sconveniente. In che modo il "nodo" interno alla serra comunicherà a distanza con la scrivania del direttore?

### Sfida 2: "Nuova Vita Industriale a Vecchi Torni"
**Il Contesto:** Una fabbrica usa macchinari solidi ma vecchi e non "smart", incapaci di segnalare guasti. 
**La Problematica:** La Direzione vuole che su ogni macchina utensile venga appoggiato un sensore che intercetti anomalie di produzione (es. se la rotazione di prova ha problemi). La fabbrica è però satura di rumore e disturbi elettromagnetici o ostacoli fisici. Serve inviare i dati a un sistema informatico locale della fabbrica per esporre un pannello di monitoraggio agli addetti. Come interfacciarsi robustamente alla singola macchina per raccogliere l'avaria, e come fargli trasmettere il suo avviso alla "Torre di Controllo" del magazzino evitando falsi contatti e perdite di messaggi?

### Sfida 3: "Autenticazione Blindata e Remota"
**Il Contesto:** Una banca si è resa conto che i badge magnetici sulla porta della sala server locale sono ormai fragili. Serve un sistema di autenticazione slegato da serrature convenzionali per contingentalo l'ingresso.
**La Problematica:** L'apparecchiatura fisicamente esposta sulla parete fuori dalla sala non può – per ovvie ragioni di sicurezza – contenere in formato leggibile "le password giuste". Deve quindi limitarsi a raccogliere l'imput visivo o radio da chi vuole entrare e inviare la credenziale grezza oltre il muro. Il sistema server "cervello", chiuso a chiave e inavvicinabile, riceverà la credenziale decodificandola e rinviando un ordine ("OK APRI", oppure accendere indicatori di divieto). Come dividiamo e integriamo fisicamente i compiti di "lettura dell'ospite" all'esterno e di "server verificatore" all'interno? E con quali mezzi uniscono le forze senza compromettersi?

---

## I Vincoli Tecnici della Direzione Aziendale

Per garantire standard stabili, il Project Manager ha dettato tre regole fisse per qualsiasi proposta tecnica ideata:

1. **Pacchettizzazione Strutturata (La lezione del modello ISO-OSI):**  
   Non importa che trasmettiate via Infrarossi, Radio NRF o Seriale cablata. È severamente vietato inviare letture grezze (es. spedire solo un numero `25`). Dovete ideare un vostro "protocollo applicativo e di trasporto": i messaggi scambiati tra ricevitori e mittenti dovranno avere un header (chi parla?), un payload (il dato netto) e regole di stop o controllo integrità (es: `<NODE-1:TEMP:25:STOP>`).
2. **Uso di Git e Lavoro Parallelo:**  
   Il software finale dovrà essere il frutto di merging e branch, tracciabile dalla History di GitHub/Git.
3. **Multitasking Logico (No-Delay):**  
   Le architetture devono reagire velocemente a bottoni, eventi in interfaccia o invii radio. Evitate o riducete a zero i delay bloccanti nei programmi, sostituendoli con cicli a evento controllato (`millis()` per tempo trascorso su Arduino o meccaniche Event-Driven lato Python/GUI).
