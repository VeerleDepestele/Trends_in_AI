# AI gateways

## Wat is een AI gateway?

De groei van geavanceerde AI-technologieën, zoals LLM’s, zorgt ervoor dat steeds meer organisaties AI willen inzetten om innovatie te stimuleren en een concurrentievoordeel te behalen.

Bedrijven hebben daarom infrastructuren nodig die deze snelle evolutie kunnen ondersteunen. (Palladino, 2024; Chattha e.a., 2023)

Een API gateway is een infrastructuurlaag die de interactie met AI-modellen (zoals LLM’s) 
- beheert, 
- beveiligt en 
- optimaliseert.

Een AI-gateway is dus een tussenlaag die:

- het **uitgaande verkeer** van applicaties naar AI-modellen controleert en beveiligt,
- een **uniforme toegang** biedt tot verschillende AI-diensten,
- fungeert als een **centrale beheers- en beveiligingslaag** voor het efficiënt en schaalbaar inzetten van AI binnen organisaties.

Ze vormt daarmee een evolutionaire stap ten opzichte van klassieke API-gateways, aangepast aan de specifieke noden van AI-integratie in bedrijfsomgevingen.

## Wat zijn de kernfunctionaliteiten van een AI-gateway?

### 1. Unified API

Een uniforme interface die toegang biedt tot verschillende AI-modellen van uiteenlopende aanbieders.
- Hierdoor kan eenvoudig geschakeld worden tussen modellen zonder dat de applicatiecode aangepast hoeft te worden.

### 2. Model Lifecycle Management

Het beheren van de levenscyclus van AI-modellen.
- Omvat deployment, versiebeheer en rollbacks, zodat organisaties gecontroleerd nieuwe modelversies kunnen uitrollen of terugdraaien.

### 3. Caching & Semantic Caching
- Opslaan van veelvoorkomende antwoorden om prestaties te verbeteren en kosten te verlagen.
    - Caching: hergebruikt exacte antwoorden van eerdere verzoeken.
    - Semantic caching: herkent inhoudelijk vergelijkbare prompts en hergebruikt ook daarvoor antwoorden.

### 4. Data-integratie

De gateway kan verbinding maken met verschillende databronnen en gegevens voorbereiden of transformeren voor modeltraining of inferentie.
- Dit maakt consistente data-toegang mogelijk voor AI-systemen.

### 5. Load Balancing

Verdeelt inkomende verzoeken over meerdere modellen of servers.
- Houdt prestaties stabiel, voorkomt overbelasting en verhoogt betrouwbaarheid.

### 6. Beveiliging & PII-filtering

Implementeert beveiligingsmaatregelen zoals het filteren van persoonlijke informatie (PII) uit prompts of antwoorden.
- Vermindert risico op datalekken of onbedoelde openbaarmaking van gevoelige gegevens.

### 7. Prompt Guards

Blokkeren van ongepaste, schadelijke of onveilige inhoud voordat deze naar het model wordt gestuurd of van het model wordt ontvangen.
- Draagt bij aan content-moderatie en naleving van ethische richtlijnen.

### 8. Gecentraliseerd Toegangsbeheer

Beheert wie toegang heeft tot welke modellen via autorisatie- en beleidsregels.
- Zorgt dat enkel bevoegde gebruikers bepaalde AI-diensten kunnen aanroepen.

### 9. Rate Limiting

Beperkt het aantal verzoeken dat een gebruiker of toepassing binnen een bepaalde tijd mag uitvoeren.
- Helpt kosten te beheersen en overbelasting van modellen te voorkomen.

### 10. Prompt Enrichment

Voegt extra context, metadata of informatie toe aan prompts voordat ze naar een model worden gestuurd.
- Verhoogt de kwaliteit en relevantie van de gegenereerde antwoorden.

### Samenvattend

AI-gateways fungeren als een slimme, beveiligde en efficiënte tussenlaag tussen gebruikers en AI-modellen, met functies voor beheer, optimalisatie, veiligheid, controle en kwaliteitsverbetering.

## Voordelen van het gebruik van AI-gateways

### 1. Snellere uitrol en testing van AI-toepassingen

- Ontwikkelaars kunnen sneller nieuwe AI-applicaties ontwikkelen, testen en uitrollen, **zonder zelf AI-modellen te moeten beheren**.
Dit versnelt de innovatie en verlaagt de technische drempel voor het gebruik van LLM’s.
*(Schuler, 2024)*

### 2. Betere samenwerking tussen teams

- AI-gateways **bevorderen samenwerking tussen development-, operations- en datateams**, omdat ze eenvoudig te integreren zijn met **CI/CD-pipelines**.
Hierdoor wordt het beheer en de implementatie van AI-diensten beter georganiseerd en gestroomlijnd.
*(Traefiklabs, 2024)*

### 3. Verbeterd kostenbeheer en inzicht in gebruik

- Organisaties krijgen een **duidelijk overzicht van het AI-gebruik**, wat helpt om **kosten te monitoren en te optimaliseren**.
Dit inzicht voorkomt onnodige API-kosten of overbelasting.
*(Duta, 2024)*

###  4. Hogere betrouwbaarheid en stabiliteit van AI-diensten

AI-gateways zorgen voor **stabielere prestaties**, zelfs bij intensief gebruik. \
Ze doen dit via mechanismen zoals **automatic retries**, **failover** en **circuit breakers**, die fouten opvangen en de continuïteit van de dienst garanderen.
*(Duta, 2024)*

### 5. Gecentraliseerde beveiliging en toegangscontrole

De gateway fungeert als een **centrale beveiligingslaag** voor alle LLM-interacties.
Ze ondersteunt **authenticatie**, **access control** en **rate limiting**, waardoor de toegang tot AI-systemen veiliger en controleerbaar blijft.
*(Barla, 2024)*

### Samenvattend

AI-gateways bieden voordelen op vlak van **snelheid, samenwerking, kostenbeheer, betrouwbaarheid en beveiliging**, waardoor organisaties AI-systemen efficiënter en veiliger kunnen inzetten in hun bedrijfsprocessen.

## Voorbeelden

- Portkey AI-gateway
- Kong AI-gateway
- Cloudflare AI-gateway
- Gloo AI-gateway (Solo.io)
- Mosaïc AI-gateway (Databricks)
- IBM AI-gateway
- F5 AI-gateway
- Apigee als een LLM-gateway (Google)
- Azure API-management als een AI-gateway (Microsoft)

** Referenties **
Zie bachelorproef Aron Van Daele: 

"Effectieve integratie van AI-gateways voor het veilig toegankelijk   maken van Large Language Models en vector databases binnen API-architecturen."