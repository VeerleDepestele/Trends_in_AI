# les1: praktisch
## Colab
In deze lessen gaan we gebruik maken van Google Colab.

Google Colab is een cloud-based service die je toelaat om code te schrijven en te draaien in een Jupyter Notebook omgeving, zonder dat je er zelf veel tijd moet insteken om het op te zetten. 

Surf naar https://colab.research.google.com/

Colab maakt gebruik van Goodle Drive om files in op te slaan. Je dient een Gmail account te hebben.
Indien je er geen hebt, maak je een gmail account aan.

In Colab, klik op het folder-icoontje en log in met je Gmail account.

![add_google_drive_to_colab](/img/add_google_drive_to_colab.png) 

![add_google_drive_to_colab_2](/img/add_google_drive_to_colab_2.png)

Open je google drive: drive.google.com. Hierin zit een folder: Colab Notebooks. Daarin zullen de notebooks die je in Colab aanmaakt, opgeslaan worden. 
Als je met een notebook wil werken, kan je hier een notebook selecteren, rechts klikken en die openen in Colab.
## Hugging Face
We zullen met de huggingface hub werken om verschillende modellen te gebruiken.

- Creëer hiervoor een account op https://huggingface.co en login.
- Ga naar je profiel - settings - Access Tokens.
- Creeër daar een token. Gebruik de knop 'Create new token'.
- Je geeft de token een naam, met 'Write' zal je de meest ruime rechten hebben.
  Voor onze lessen is 'Read' voorlopig genoeg. (ref. https://huggingface.co/docs/hub/en/security-tokens)

![HF_create_new_access_token](/img/HF_create_new_access_token.png)
- Bewaar je token ergens in een passwoord manager, zodat je er later aankan.
- Voeg nu je huggingface token toe als secret key in Colab, zodat je via Colab de huggingface modellen kan gebruiken.
![add_google_drive_to_colab_3](/img/add_google_drive_to_colab_3.png)
- Klik op de afbeelding van de sleutel, daarna '+ Add new secret'. De 'Name' dient 'HF_TOKEN' te zijn, in 'Value' kopieer je je hugginface token.
- Eens je secret is ingesteld, kan je hem in een Colab notebook gebruiken door de volgende code uit te voeren:
  from google.colab import userdata
  userdata.get('secretName')
- De code om een model op een vlotte manier te gebruiken, vind je in de 'Model Card' van het geselecteerde model, selecteer 'Deploy' en kies voor Inference API (Serverless).
- Interessante pagina: https://huggingface.co/docs/api-inference/.
- Uitgebreide Hugging Face documentatie: https://huggingface.co/docs.

## Ollama
In WSL terminal: \
ollama --version \
sudo snap install ollama