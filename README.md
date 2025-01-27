# PHARMALINK 
Team di sviluppo:
- Davide Sgroi  
- Francesco Paolo Rosone  
- Salvatore Viganò  

---

## **Obiettivo del sistema**  

Il sistema **PHARMALINK** ha l'obiettivo di supportare un'azienda farmaceutica nella gestione di informazioni, produzione, stoccaggio e distribuzione di farmaci per una o più catene di farmacie.  

### **Tipologie di utenti**  
Gli utenti del sistema sono suddivisi in tre categorie principali:  
1. **Farmacista**  
   - Può ordinare farmaci (da banco e non) e gestire il carico/scarico degli stessi.  
2. **Fattorino**  
   - Si occupa della consegna dei lotti ai farmacisti e della registrazione delle avvenute consegne.  
3. **Magazziniere**  
   - Gestisce eventuali errori negli ordini e può aggiungere nuovi farmaci al database aziendale.  

---

## **Sistema attuale**  

Si ipotizza che non esista un sistema informatico preesistente. Le attività di gestione degli utenti e degli ordini vengono effettuate manualmente. Il sistema dovrà quindi interagire direttamente con i clienti per supportare la gestione delle ordinazioni.  

---

## **Requisiti funzionali**  

Il sistema deve prevedere tre tipologie di utenti, ciascuno con funzionalità specifiche:  

### **Utente Generico**  
- **Autenticazione**: accesso tramite credenziali fornite dall'azienda.  
- **Recupero credenziali**: possibilità di recuperare la password tramite email.  

### **Farmacista**  
- **Ordina Farmaco**: possibilità di richiedere uno o più farmaci.  
- **Visualizza Catalogo**: accesso all'elenco dei farmaci disponibili nel database aziendale.  
- **Visualizza Ordini**: consultazione degli ordini effettuati (in corso e conclusi).  
- **Modifica Ordine**: possibilità di modificare o annullare un ordine fino a 3 giorni prima della consegna prevista.  
- **Modifica Parametri**: gestione della quantità di farmaci da banco e dei tempi di consegna.  
- **Carica Ordini**: conferma dell'avvenuta ricezione dei lotti entro le ore 20:00 della data di consegna.  

### **Magazziniere**  
- **Aggiungi Farmaco**: inserimento di nuovi farmaci nel database aziendale.  
- **Supervisiona Ordini**: verifica e correzione di ordini segnalati come errati.  

### **Fattorino**  
- **Firma Consegna**: registrazione della consegna con firma digitale del farmacista tramite credenziali.  

---

## **Requisiti non funzionali**  

1. **Distribuzione del sistema**  
   - Deve essere implementato su tre dispositivi:  
     - **PC** nelle farmacie.  
     - **PC** presso l'azienda.  
     - **Tablet** per i fattorini.  
   - La comunicazione tra dispositivi avviene esclusivamente tramite un **DBMS** comune.  

2. **Vincoli operativi**  
   - Linguaggio di programmazione: **Java**.  
   - Solo i farmaci da banco possono essere ordinati periodicamente; gli altri farmaci sono ordinabili solo su richiesta.  
   - Il controllo del sistema sui carichi avviene ogni giorno alle ore 20:00.  
   - Gli ordini non periodici possono essere annullati solo se mancano almeno 2 giorni alla consegna prevista.  
   - Al momento dell'ordine, il farmacista viene avvisato in caso di farmaci in scadenza (meno di 2 mesi di validità).  
   - La ricezione dei farmaci deve essere caricata nel sistema entro le ore 20:00 del giorno di consegna. In caso contrario:  
     - Viene segnalato un errore.  
     - L'azienda contatta la farmacia il giorno successivo per risolvere il problema.  

---

## **Requisiti di sistema**  

- **Continuità del servizio**: il sistema deve essere operativo in ogni momento.  
- **Sicurezza**: deve garantire un alto livello di protezione per i dati degli utenti.  

---

## **Modelli di sistema**  

- Ogni interfaccia utente include un pulsante **"Torna indietro"**, che consente di:  
  - Tornare alla schermata precedente.  
  - Effettuare il logout.  

- In caso di errore durante la comunicazione con il DBMS (es. caduta connessione), il sistema invoca il caso d'uso "Gestione errore connessione".  
