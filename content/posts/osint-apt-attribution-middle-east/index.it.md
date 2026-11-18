---
title: "Chi è stato? Attribuire gli hacker statali in Medio Oriente con le fonti aperte"
date: 2026-11-18
draft: true
description: "Come gli analisti attribuiscono gli APT statali in Medio Oriente usando solo fonti aperte, e perché le identità sono il primo bersaglio da proteggere."
categories: ["Cybersecurity", "Geopolitica"]
tags: ["attribuzione", "OSINT", "APT", "Medio Oriente", "IAM", "MITRE ATT&CK"]
---

> **Perimetro:** analisi basata solo su fonti pubbliche (report di vendor, CERT e governi, letteratura accademica, MITRE ATT&CK). Nessun dettaglio operativo, nessun indicatore, nessuno strumento.

## In una frase

Attribuire un'operazione cyber a uno Stato è un giudizio probabilistico, non una prova; la cosa più affidabile che i difensori possono fare è proteggere le identità che questi gruppi continuano a prendere di mira.

## Perché è importante

Quando un ospedale, un ministero o una società energetica subisce una violazione, la domanda "chi c'è dietro?" diventa presto politica: sanzioni, risposte diplomatiche, perfino segnali di deterrenza. Il Medio Oriente è un teatro denso da questo punto di vista: rivalità regionali, dinamiche per procura e gruppi sofisticati legati agli Stati si sovrappongono. Un'attribuzione sbagliata o troppo sicura può far degenerare una crisi, mentre ignorare del tutto l'attribuzione lascia i difensori ciechi su chi probabilmente colpirà dopo. Da studente di studi strategici che lavora nell'IAM, trovo affascinante questo incrocio: l'attribuzione è la domanda *strategica*, la protezione delle identità è la risposta *pratica*.

## Punti chiave

1. L'attribuzione è difficile per costruzione: false flag, strumenti condivisi, contractor e proxy confondono il quadro.
2. L'attribuzione OSINT funziona *raggruppando* le evidenze (infrastruttura, malware, comportamento, bersagli) e dichiarando un **livello di confidenza**, mai una certezza.
3. Le TTP mappate su MITRE ATT&CK durano più degli artefatti tecnici, che costano poco da cambiare.
4. I report pubblici collegano diversi gruppi della regione agli interessi dello Stato iraniano; i nomi cambiano da vendor a vendor, quindi le sovrapposizioni vanno trattate con cura.
5. In tutte queste campagne credenziali e account sono un bersaglio ricorrente: MFA resistente al phishing, gestione degli accessi privilegiati e monitoraggio delle identità ripagano chiunque sia l'attaccante.

## Perché attribuire è difficile

Il classico articolo di Rid e Buchanan descrive l'attribuzione come [un'arte quanto una scienza](https://doi.org/10.1080/01402390.2015.1115975): i livelli tecnico, operativo e strategico danno ciascuno risposte parziali, e la decisione finale è un giudizio in condizioni di incertezza. Diversi fattori la complicano ulteriormente:

- **False flag.** Gli attaccanti possono piazzare deliberatamente indizi fuorvianti. Il caso pubblico più noto è l'incidente "Olympic Destroyer" alle Olimpiadi invernali del 2018, in cui i ricercatori hanno descritto artefatti nel codice falsificati per imitare il gruppo Lazarus, legato alla Corea del Nord; i ricercatori di Kaspersky hanno concluso che si trattava di una false flag deliberata ([analisi Kaspersky](https://securelist.com/olympic-destroyer-is-here-to-trick-the-industry/84295/)). Non riguarda il Medio Oriente, ma la lezione vale anche lì.
- **Proxy e contractor.** I governi possono operare tramite società di facciata od operatori legati in modo informale, il che rende "lo Stato" e "un gruppo criminale" due estremi di uno spettro.
- **Cluster sovrapposti.** Vendor diversi tracciano la stessa attività con nomi diversi, e un solo nome può raggruppare più team.
- **Infrastrutture e strumenti condivisi.** Con strumenti commerciali o pubblicamente disponibili, "stesso strumento" non significa "stesso attore".

## Come funziona davvero l'attribuzione OSINT (ad alto livello)

Gli analisti di fonti aperte, che lavorino per vendor, CERT o università, tendono a seguire una logica simile, spesso ispirata al [Diamond Model](https://www.activeresponse.org/wp-content/uploads/2013/07/diamond.pdf): guardare *avversario*, *capacità*, *infrastruttura* e *vittima*, e vedere quali pezzi stanno insieme.

- **I report pubblici come materia prima.** Gli advisory congiunti dei governi e le analisi dei vendor sono la spina dorsale. Confrontare report indipendenti è la mossa più utile in assoluto: se team scollegati arrivano alla stessa conclusione, la confidenza sale.
- **Vittimologia.** Chi viene colpito (settori, Paesi, tempistica rispetto agli eventi politici) dice molto sugli interessi del probabile mandante.
- **Comportamenti più che artefatti.** Domini e hash dei file scadono in fretta. I comportamenti (come si ottiene l'accesso, come si mantiene la persistenza) sono più stabili, e [MITRE ATT&CK](https://attack.mitre.org/groups/) li cataloga gruppo per gruppo.
- **Dichiarare la confidenza.** I buoni report separano i fatti dalle valutazioni e indicano "confidenza bassa / moderata / alta". Da lettore, controlla sempre quale delle due stai leggendo.

## Alcuni gruppi della regione citati nei report pubblici

Quelli che seguono sono solo esempi, tratti dalle pagine pubbliche dei gruppi su ATT&CK. I nomi variano da vendor a vendor e ATT&CK stesso segnala sovrapposizioni: va letta come una mappa, non come un verdetto.

- [MuddyWater](https://attack.mitre.org/groups/G0069/): descritto nei report pubblici come gruppo di cyber-spionaggio; un [advisory congiunto di FBI, CISA, CNMF dello US Cyber Command e NCSC britannico (AA22-055A)](https://www.cisa.gov/news-events/cybersecurity-advisories/aa22-055a) afferma che è un'articolazione subordinata del Ministero dell'Intelligence e della Sicurezza iraniano (MOIS). È un'attribuzione governativa esplicita, la più forte di questo elenco.
- [OilRig](https://attack.mitre.org/groups/G0049/): gruppo legato all'Iran, segnalato per attacchi a governi e settori in tutto il Medio Oriente. MITRE ATT&CK lo definisce un gruppo iraniano *sospetto*, con un'attribuzione basata su infrastrutture che rimandano all'Iran e su bersagli allineati agli interessi dello Stato: evidenze circostanziali, a confidenza moderata. I legami con il MOIS compaiono in fonti secondarie; non ho verificato una dichiarazione governativa ufficiale [unverified].
- [APT33](https://attack.mitre.org/groups/G0064/) e [Magic Hound](https://attack.mitre.org/groups/G0059/): altri cluster legati all'Iran nei report pubblici (anche qui l'attribuzione è in gran parte dei vendor, quindi va considerata una valutazione, non una prova), con un diverso mix di bersagli nell'aviazione e nell'energia e di intrusioni basate soprattutto sull'ingegneria sociale.

Nota lo schema: nomi, mandanti e confidenza cambiano a seconda della fonte. È proprio per questo che gli analisti incrociano i dati.

## Perché le identità sono il bersaglio ricorrente

Scorrendo le voci ATT&CK di questi gruppi, un filo comune è l'accesso iniziale tramite [phishing](https://attack.mitre.org/techniques/T1566/) e abuso di credenziali, incluso il [password spraying](https://attack.mitre.org/techniques/T1110/003/). Ha senso: un account valido è silenzioso, economico e spesso più potente di un malware. Gli account privilegiati e di servizio valgono ancora di più, perché aprono la porta a tutto il resto.

## Cosa può fare l'IAM (e perché non dipende dall'attaccante)

Il bello della difesa delle identità è che non dipende dall'aver indovinato l'attribuzione:

- **MFA resistente al phishing.** Codici SMS e notifiche push possono essere carpiti o approvati per sfinimento; FIDO2/WebAuthn e le passkey legano l'autenticazione al sito legittimo. CISA pubblica una [scheda su come implementare l'MFA resistente al phishing](https://www.cisa.gov/sites/default/files/2023-01/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf).
- **Gestione degli accessi privilegiati (PAM).** Meno diritti amministrativi permanenti, elevazione just-in-time, credenziali in vault e registrazione delle sessioni riducono ciò che una password rubata può fare.
- **Monitoraggio dei segnali di identità.** Viaggi impossibili, consensi anomali alle applicazioni, nuove registrazioni MFA e schemi di spraying sono rilevabili, se i log vengono raccolti e qualcuno li guarda.
- **Mentalità Zero Trust.** Dare per scontato che le credenziali verranno rubate, quindi verificare di continuo e limitare il raggio d'azione.

## Cosa farei adesso

- Leggere due o tre report pubblici indipendenti sullo stesso gruppo e confrontarne le dichiarazioni di confidenza.
- Mappare alcune delle tecniche ATT&CK citate sui propri controlli di identità e annotare le lacune.
- Per approfondire: confrontare come governi (advisory congiunti) e vendor formulano l'attribuzione, e cosa implica per le risposte politiche.

*Avvertenza: tutto ciò che è scritto qui proviene da fonti pubbliche ed è una semplificazione analitica, non una valutazione di uno specifico incidente o di una specifica organizzazione.*
