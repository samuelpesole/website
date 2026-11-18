---
title: "Attribuire le operazioni cyber statali in Medio Oriente: fonti aperte, livelli di confidenza e centralità dell'identità nella difesa"
date: 2026-11-18
draft: true
description: "Come si attribuiscono da fonti aperte le operazioni cyber statali in Medio Oriente e perché questa incertezza favorisce una difesa centrata sull'identità."
categories: ["Cybersecurity", "Geopolitica"]
tags: ["attribuzione", "OSINT", "APT", "Iran", "Medio Oriente", "IAM", "analisi di intelligence"]
---

> **Perimetro e metodo.** L'analisi si basa esclusivamente su fonti pubbliche: advisory governativi, report dei vendor, la knowledge base MITRE ATT&CK e la letteratura accademica. Non contiene indicatori di compromissione, strumenti né dettagli operativi.

## Abstract

Attribuire un'operazione cyber a uno Stato non è un accertamento forense. È un giudizio analitico formulato in condizioni di incertezza e comunicato con una finalità politica. L'articolo esamina come l'attribuzione venga costruita a partire da fonti aperte, prendendo come caso di studio i gruppi di intrusione riconducibili all'Iran attivi in Medio Oriente, e sostiene tre tesi. Primo, la documentazione pubblica su questi gruppi è *stratificata*: poche attribuzioni governative formali convivono con un corpus molto più ampio di valutazioni dei vendor, fondate su evidenze indiziarie e su nomenclature non coerenti. Secondo, il valore analitico dell'attribuzione da fonti aperte risiede meno nell'identificazione del mandante che nell'esplicitazione del grado di confidenza di ogni passaggio inferenziale. Terzo, poiché questa incertezza non è eliminabile, gli investimenti difensivi non dovrebbero dipendere da essa. Nei casi esaminati i gruppi convergono su una stessa superficie d'attacco, le identità digitali: per questo i controlli centrati sull'identità restano validi chiunque sia l'avversario.

## 1. Introduzione

Le operazioni cyber attribuite a Stati sono ormai una componente ordinaria della competizione in Medio Oriente. Rivalità regionali, regimi sanzionatori e relazioni per procura creano forti incentivi all'azione coperta nel cyberspazio, mentre i bassi costi di accesso permettono agli Stati di agire tramite unità difficili da ricondurre a loro. Per i decisori politici, la domanda «chi è stato?» precede qualsiasi risposta proporzionata: sanzioni, incriminazioni, démarche diplomatiche o segnali di deterrenza. Per chi difende, la stessa domanda è spesso trattata come presupposto per stabilire le priorità.

L'articolo affronta due domande collegate: *quanto possono effettivamente stabilire le fonti aperte sulla sponsorizzazione statale delle operazioni cyber nella regione?* E *quali conseguenze ne derivano per la difesa, se la risposta è «meno di quanto comunemente si ritenga»?*

## 2. L'attribuzione come problema di giudizio

Il riferimento più influente resta il «Q Model» di Rid e Buchanan, che descrive l'attribuzione come un processo stratificato. Si parte dalle evidenze tecniche (artefatti, infrastruttura), si passa all'analisi operativa (come è stata condotta l'intrusione) e alla valutazione strategica (chi ne trae beneficio e chi potrebbe autorizzarla), fino alla comunicazione verso un pubblico ([Rid & Buchanan, 2015](https://doi.org/10.1080/01402390.2014.977382)). Due implicazioni del modello sono rilevanti. L'attribuzione è una questione di grado e non binaria, e la sua qualità dipende dal giudizio degli analisti e dal contesto politico tanto quanto dalle evidenze tecniche.

Egloff sviluppa questa prospettiva trattando l'attribuzione *pubblica* come un atto politico a sé stante. Gli Stati scelgono se, quando e come attribuire, e lo fanno per perseguire obiettivi come la costruzione di norme, il segnalamento o la mobilitazione degli alleati, non soltanto per riportare un accertamento ([Egloff, 2020](https://doi.org/10.1093/cybsec/tyaa012)). Il quadro normativo riflette questa cautela. Il rapporto 2015 del Gruppo di esperti governativi delle Nazioni Unite, recepito dall'Assemblea Generale, include tra le norme volontarie quella secondo cui gli Stati, nel rispondere agli incidenti, dovrebbero considerare tutte le informazioni rilevanti, compresi il contesto più ampio e le difficoltà di attribuzione nell'ambiente ICT ([doc. ONU A/70/174](https://undocs.org/A/70/174)).

Tre caratteristiche strutturali rendono l'attribuzione difficile nella pratica:

- **Inganno deliberato.** L'operazione «Olympic Destroyer» del 2018 contro i Giochi Olimpici invernali di Pyeongchang conteneva artefatti di codice inseriti per imitare il gruppo Lazarus; i ricercatori di Kaspersky hanno concluso che si trattava di un false flag deliberato ([Kaspersky, 2018](https://securelist.com/olympic-destroyer-is-here-to-trick-the-industry/84295/)). Il caso è esterno alla regione, ma dimostra che gli artefatti tecnici possono essere fabbricati.
- **Agire per interposta persona.** I governi possono operare tramite contractor, società di copertura od operatori legati in modo informale. Il confine tra attore «statale» e «non statale» diventa allora un continuum di controllo, non una categoria.
- **Frammentazione tassonomica.** I vendor raggruppano e denominano l'attività in modo diverso, per cui un'etichetta può comprendere più team e uno stesso team può comparire sotto più etichette.

## 3. Come si costruisce l'attribuzione da fonti aperte

Gli analisti OSINT organizzano tipicamente le evidenze attorno ai quattro vertici del [Diamond Model](https://www.activeresponse.org/wp-content/uploads/2013/07/diamond.pdf) (avversario, capacità, infrastruttura, vittima) e attribuiscono verificando se questi elementi risultano coerenti tra più intrusioni. Le classi di evidenza non sono però equivalenti:

| Classe di evidenza | Esempio | Durata | Esposizione all'inganno |
|---|---|---|---|
| Artefatti tecnici | domini, hash, frammenti di codice | bassa: economici da cambiare | alta: possono essere inseriti ad arte |
| Comportamento (TTP) | schemi di accesso iniziale e persistenza, catalogati in [MITRE ATT&CK](https://attack.mitre.org/groups/) | medio-alta | media |
| Vittimologia | settori, Paesi, tempistiche rispetto a eventi politici | alta | bassa, ma ambigua: molti attori condividono gli stessi interessi |
| Divulgazione ufficiale | advisory governativi congiunti, incriminazioni | n.d. | bassa sul piano tecnico, ma politicamente orientata |

Due salvaguardie metodologiche distinguono l'analisi dall'asserzione. La prima è la *convergenza di fonti indipendenti*: la confidenza dovrebbe crescere solo quando analisti con dati e incentivi diversi giungono a conclusioni compatibili. La seconda è un *linguaggio esplicito sulla confidenza*. Gli standard analitici della comunità di intelligence statunitense impongono di esprimere e motivare l'incertezza e di distinguere le informazioni di base dal giudizio analitico ([ODNI, ICD 203](https://www.dni.gov/files/documents/ICD/ICD-203.pdf)). Tecniche strutturate come l'Analysis of Competing Hypotheses sono nate proprio per contrastare il bias di conferma, a cui l'attribuzione è particolarmente esposta ([Heuer, 1999](https://www.cia.gov/resources/csi/books-monographs/psychology-of-intelligence-analysis-2/)). Davanti a qualsiasi affermazione di attribuzione, il lettore dovrebbe quindi chiedersi: *a quale livello del Q Model si riferisce questa evidenza, e con quale confidenza dichiarata?*

## 4. Caso di studio: i gruppi riconducibili all'Iran in Medio Oriente

La documentazione pubblica collega agli interessi dello Stato iraniano diversi gruppi di intrusione attivi nel Golfo e nella regione più ampia. Letta in modo comparato, però, non è uniforme: è stratificata in base alla solidità dell'attribuzione.

- **Attribuzione governativa formale.** Un advisory congiunto di FBI, CISA, Cyber National Mission Force dello US Cyber Command e NCSC britannico afferma che [MuddyWater](https://attack.mitre.org/groups/G0069/) è un elemento subordinato del Ministero dell'Intelligence e della Sicurezza iraniano (MOIS) ([CISA, AA22-055A](https://www.cisa.gov/news-events/cybersecurity-advisories/aa22-055a)). È l'attribuzione più solida presente nella documentazione pubblica sulla regione: esplicita, multinazionale e riferita a un'organizzazione precisa.
- **Attribuzione valutativa su base indiziaria.** Per [OilRig](https://attack.mitre.org/groups/G0049/), MITRE ATT&CK parla di un gruppo iraniano *sospetto*, citando infrastrutture con riferimenti all'Iran e un targeting coerente con gli interessi statali iraniani. Fonti secondarie lo collegano al MOIS, ma per questo articolo non è stato possibile verificare una dichiarazione governativa ufficiale che stabilisca tale legame [non verificato].
- **Attribuzione prevalentemente di fonte vendor.** [APT33](https://attack.mitre.org/groups/G0064/) e [Magic Hound](https://attack.mitre.org/groups/G0059/) sono ricondotti all'Iran soprattutto attraverso le analisi dei vendor su vittimologia e modus operandi. APT33 è associato ad attacchi ai settori aeronautico ed energetico, Magic Hound a intrusioni fondate in larga misura sull'ingegneria sociale.

Ne derivano tre osservazioni analitiche. Primo, **la documentazione sull'attribuzione nella regione si fonda soprattutto sulla valutazione, non sulla divulgazione**. Solo una piccola parte dell'attività comunemente definita «iraniana» è oggetto di un'attribuzione governativa esplicita, e il resto è dedotto da vittimologia e modus operandi. Si tratta di un'inferenza ragionevole, che però non equivale a un'attribuzione organizzativa. Secondo, **in questo teatro la vittimologia è particolarmente ambigua**, perché diversi attori regionali ed extraregionali hanno interessi sovrapposti verso gli stessi governi, operatori energetici e fornitori di telecomunicazioni. «Un targeting coerente con lo Stato X» restringe quindi il campo meno di quanto sembri. Terzo, **la frammentazione dei nomi nasconde la reale unità di analisi**. Se MuddyWater, OilRig o APT33 corrispondano a organizzazioni distinte, a contractor condivisi o a team sovrapposti non è determinabile da fonti aperte. Le conclusioni politiche che trattano le etichette dei vendor come fatti organizzativi vanno oltre ciò che le evidenze consentono.

## 5. Il bersaglio convergente: l'identità digitale

I gruppi differiscono per mandante, livello di confidenza e nomenclatura, ma il loro comportamento documentato nella fase di accesso iniziale converge. Le schede ATT&CK di questi gruppi registrano ripetutamente [phishing](https://attack.mitre.org/techniques/T1566/), [password spraying](https://attack.mitre.org/techniques/T1110/003/) e l'uso di [account validi](https://attack.mitre.org/techniques/T1078/). La convergenza ha una logica strategica. Un'identità legittima compromessa fornisce un accesso economico, silenzioso e difficile da distinguere dall'attività normale. Offre inoltre negabilità, perché l'attività svolta con credenziali reali lascia pochi artefatti distintivi.

Da qui un argomento di disaccoppiamento. Se la confidenza nell'attribuzione è strutturalmente limitata, e se gli avversari considerati sfruttano tutti la stessa superficie, gli investimenti difensivi non dovrebbero attendere l'attribuzione. I controlli che aumentano il costo della compromissione delle identità funzionano a prescindere dal mandante:

- **Autenticazione resistente al phishing.** FIDO2/WebAuthn vincola l'autenticazione all'origine legittima, neutralizzando il phishing delle credenziali e la MFA fatigue ([scheda CISA](https://www.cisa.gov/sites/default/files/2023-01/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf)).
- **Gestione degli accessi privilegiati (PAM).** Eliminare i privilegi permanenti, adottare l'elevazione just-in-time e custodire le credenziali in vault limita fin dove può arrivare un singolo account compromesso.
- **Rilevamento delle minacce all'identità.** Schemi di spraying, accessi anomali, nuove registrazioni MFA e consensi applicativi insoliti sono segnali osservabili, a patto che i log vengano raccolti e analizzati.

In questa prospettiva, la governance delle identità è il contraltare difensivo del problema dell'attribuzione. L'attribuzione si chiede *chi* con un'incertezza irriducibile, mentre la difesa centrata sull'identità riduce il valore dell'accesso che ogni possibile avversario cerca di ottenere.

## 6. Limiti

L'analisi eredita i bias delle sue fonti. I report dei vendor riflettono la visibilità commerciale di ciascun fornitore, e le divulgazioni dei governi occidentali riflettono scelte politiche su cosa rendere pubblico. Entrambi sottorappresentano l'attività contro bersagli non occidentali e le operazioni non rilevate. Il caso di studio riguarda solo l'attività riconducibile all'Iran, e non esamina altri attori statali presenti nella regione. Infine, la convergenza sull'identità si basa su tecniche catalogate: indica un pattern documentato, non una frequenza misurata.

## 7. Conclusioni

Le fonti aperte possono sostenere un'affermazione ben calibrata sul fatto che un gruppo di intrusione serva gli interessi di un determinato Stato. Solo raramente possono sostenere un'affermazione su quale organizzazione lo abbia diretto, e mai senza una divulgazione ufficiale. Il contributo analitico dell'attribuzione OSINT sta quindi meno nel nominare gli avversari che nel rendere l'incertezza esplicita e tracciabile. Per chi difende, l'implicazione è che la persistente incertezza dell'attribuzione depone a favore di controlli centrati sull'identità, il cui valore non dipende dal risolverla.

## Riferimenti

- CISA et al. (2022). *Iranian Government-Sponsored Actors Conduct Cyber Operations Against Global Government and Commercial Networks* (AA22-055A). [Link](https://www.cisa.gov/news-events/cybersecurity-advisories/aa22-055a)
- CISA (2022). *Implementing Phishing-Resistant MFA* (fact sheet). [Link](https://www.cisa.gov/sites/default/files/2023-01/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf)
- Caltagirone, S., Pendergast, A. & Betz, C. (2013). *The Diamond Model of Intrusion Analysis*. [Link](https://www.activeresponse.org/wp-content/uploads/2013/07/diamond.pdf)
- Egloff, F. J. (2020). Public attribution of cyber intrusions. *Journal of Cybersecurity*, 6(1). [doi:10.1093/cybsec/tyaa012](https://doi.org/10.1093/cybsec/tyaa012)
- Heuer, R. J. (1999). *Psychology of Intelligence Analysis*. CIA Center for the Study of Intelligence. [Link](https://www.cia.gov/resources/csi/books-monographs/psychology-of-intelligence-analysis-2/)
- Kaspersky GReAT (2018). *Olympic Destroyer is here to trick the industry*. [Link](https://securelist.com/olympic-destroyer-is-here-to-trick-the-industry/84295/)
- MITRE ATT&CK. Gruppi G0049, G0059, G0064, G0069; tecniche T1078, T1110.003, T1566. [Link](https://attack.mitre.org/groups/)
- ODNI (2015). *Intelligence Community Directive 203: Analytic Standards*. [Link](https://www.dni.gov/files/documents/ICD/ICD-203.pdf)
- Rid, T. & Buchanan, B. (2015). Attributing Cyber Attacks. *Journal of Strategic Studies*, 38(1–2), 4–37. [doi:10.1080/01402390.2014.977382](https://doi.org/10.1080/01402390.2014.977382)
- Nazioni Unite (2015). *Report of the Group of Governmental Experts on Developments in the Field of Information and Telecommunications in the Context of International Security* (A/70/174). [Link](https://undocs.org/A/70/174)
