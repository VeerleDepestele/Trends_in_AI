# Prompt Engineering

In deze les gaan we een aantal prompt engineering principes gezien voor het gebruik van LLM's. In de voorbeelden gebruiken we ChatGPT en een Llama2 model.

De inzichten in prompts wijzigen nog continue, maar toch zijn een aantal basisconcepten ondertussen te ontwaren.

We vatten de prompt technieken samen in vijf categorieën. Een goede prompt gebruikt één of meerdere van deze categorieën.

- context
- input data
- instructions
- examples
- constraints

Merk op dat de modellen vrij goed gedocumenteerd zijn en dat bij de documentatie meestal ook aandacht besteed wordt aan prompt engineering: \
https://platform.openai.com/docs/guides/prompt-engineering \
https://www.llama.com/docs/how-to-guides/prompting/ \
https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview

## categorieën

### 1. context

De context van een prompt beschrijft meestal op welke manier het LLM zich dient te gedragen, "Je bent een expert JavaScript developer", "Je bent een AI assistent die boeken aanraadt op basis van gebruikers voorkeuren", "Je bent een hogeschool lector die bachelorproefvoorstellen evalueert"

### 2. input data

Input data is de data die beschrijft waar het over gaat bij de prompt, de tekst die moet samengevat worden, de bachelorproef die moet geëvalueerd worden, het stuk code waar uitleg over moet gegeven worden.

### 3. instructions

De instructions beschrijven wat het LLM moet doen. "Geef 5 aanbevelingen voor nieuwe boeken", "Beschrijf alle schrijf- en grammaticale fouten, geef twee verbeterpunten aan waar de student mee aan de slag kan", "Leg uit wat dit stuk code doet"

### 4. examples

Soms loont het om voorbeelden van input en output te geven, zeker als er een zekere structuur verwacht wordt. (JSON data met een specifiek formaat bijvoorbeeld)

In deze context spreken we van 'zero-shot prompting' (wanneer er geen voorbeeld meegegeven wordt) en 'few-shot prompting' (wanneer er voorbeelden meegegeven worden in de prompt).

### 5. constraints

De constraints dienen om af te lijnen waartoe het LLM zich moet beperken. Dit kan zowel gaan om vormelijke beperkingen "Genereer enkel een JSON file met key 'boek' en key 'author'", "Maximaal 100 woorden lang", "in de stijl van Shakespeare"

Maar ook inhoudelijk "Wees vriendelijk", "Eindig met een positieve noot", "Zorg dat de boeken van hetzelfde genre zijn".



## voorbeeld

```
Je bent aan AI assistent die gepersonaliseerde boek aanbevelingen maakt gebaseerd op gebruikersvoorkeuren.

Gebruiker: man van 46 jaar, houdt van science fiction en non-fictie en leest in het Nederlands en Engels
Favoriete boeken: "Predictably Irrational" van Dan Ariely, "Do Androids Dream of Electric Sheep" van Philip K. Dick en "A Random Walk Down Wall Street" van Malkeil Burton

Kan je vijf aanbevelingen formuleren voor deze gebruiker?

Voorbeeld uitvoer: "The Martian" van Andy Weir, omdat je van science fiction houdt

Zorg dat de aanbevelingen in lijn zijn met de genres die de gebruiker graag leest, en die aanleunen bij zijn favoriete boeken. Prijs geen boeken aan uit het voorbeeld. Wees vriendelijk en wek zin op bij de gebruiker om de boeken die je aanbeveelt te beginnen lezen.
```

## role

Bij de meer recente modellen (openAI, recente LLama modellen, ...), dien je in de 'message' zowel een rol als een context mee te geven.

De mogelijke rollen zijn: `system`, `user` of `assistant`. 

De *'User'* is de gebruiker. *'Assistant'* is de chatbot (of ai assistant). Door beide rollen in een 'message' te gebruiken, kan je delen van eerdere conversaties terug als context meesturen bij een volgende vraag.

De context van de *'system'* rol legt vast hoe het systeem zich dient te gedragen.

De voordelen van het specificeren van een rol zijn:
- grotere context: Chatbots hebben een beperkte context, naarmate een conversatie vordert, vergeten ze wat ze eerder zeiden. 
   Door het antwoord van de 'assistent' op te nemen in de volgende context, wordt dit minder snel vergeten.
- standvastigheid: de rol die je vastlegt blijft makkelijker behouden, de chat messages met de gebruiker nadien gaan minder snel 'afleiden'.



### oefening

Zet je per twee en schrijf een uitgebreide prompt die alle categorieën gebruikt om het volgende te bekomen:

1. Bachelorproef voorstellen evalueren naar inhoud en spelling.
2. De werking van Python code uitleggen en eventueel optimalisaties aanprijzen.

(gebruik je eigen bachelorproefvoorstel / een stuk code uit de les Webservices om dit te testen)





