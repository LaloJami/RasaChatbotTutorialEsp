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
## Action
Es una operacion la cual puede ser ejecutada por el **bot**. Este puede responder con algo, consultar en la base de datos o cualquier otra cosa posible por código.

La accion solo puede ser respondida por código o alguna otra API response.
## Stories
Hay una muestra de interacción entre el usuario y el bot, definida en terminos de catura de intención y ejecución de acciones. Así, el desarrollador puede mensionar que hacer si obtienes una **Input** de alguna **Intent** con/sin algunas **entities**. Es como decir si la **intención(Intent)** del usuario es encontrar el día de la semana y la entity es **(hoy)today**, el bot encontrará el dia de la semana de hoy y responda.
## Domain
Se requiere el conocimiento del dominio para responder a cualquier usuario. Significa que cuando tu respondas algo al usuario tu deberias saber de lo que estas hablando.
