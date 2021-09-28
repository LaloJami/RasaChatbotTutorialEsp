<div align="center">
<h1>Rasa Chatbot Tutorial Español</h1>
</div>

Este tutorial fue realizado para tener un punto de partida para todas las personas de habla hispana que deseen aprender sobre Rasa 
Esta basado principalmente del tutorial de [Binod Suman Academy](https://www.youtube.com/watch?v=Z9zTJS6cWiQ)

# ¿Qué es Rasa?
[Rasa](https://rasa.com/) es una machine learning framework de codigo abierto para automatizar conversaciones basadas en texto y voz. Entiende mensajes, mantiene conversaciones y conecta a canales de mensajeria y APIs.

Rasa brinda una solución en la construcción de un chatbot, y nos permite desarrollar un chatbot complejo en minutos.

# Conceptos importantes en chatbot
Para desarrollar un chatbot hay que tener bien en claro los siguientes conceptos:
## Intent
Considerado como el *objetivo* o *proposito* del **user input**. Si el usuario dice "*Quiero ordenar un libro*" o "*Planeo ordenar un libro*". Aqui la **intención (Intent)** seria "*Ordenar*"

Intent representaría el **verbo(verb)** en tus dialogos 

Las aciones que el usuario quiere realizar son las que esperan que tu chatbot cumpla o realize.

Ejemplos de algunos intent:
* Intent:greet (good morning, hi, hello, hey there)
* Intent:deny (no, never, I don't think so, no way)
* Intent:mood_unhappy (sad, unhappy, terrible, not very good)
* Intent:Tech_support (My laptop is broken)
* Intent:search_hotel (show me a room)

## Entity
Considerada como la información util que puede ser extraida del **user input**. Cuando el usuario dice "*Quiero ordenar un libro*". Si extraemos "*libro*" como **entity**, podemos ejecutarla acción en libro.

entity representaría a los **sustantivos(nouns)** en tus dialogos.

Otro ejemplo:
"*Reserve a table at Hilton Colon Hotel tomorrow night*"
* Intent: Reserve a table
* Entity: place: Hilton Colon Hotel and time: tomorrow night