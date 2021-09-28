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

# ¿Cómo definimos todo esto en código?
nlu.yml (Intent and entity)
```python
nlu:
- intent: greet
  examples: |
    - hey
    - hello
- entity: book
  examples:
		- Odisea
```
stories.yml (Story (Dialogue Management))
```python
stories:
- story: generic happy path
  steps:
  - intent: greet
  - action: action_greet
  - intent: select_price
  - action: action_select_upper_price
  - intent: select_purpose
  - action: action_select_purpose
  - intent: select_brand
  - action: action_select_brand
```
domain.yml (Actual output (Hard Code) [All intents, entity, action, response])
```python
responses:
  utter_greet:
  - text: "Hey! How are you?"

  utter_cheer_up:
  - text: "Here is something to cheer you up:"
    image: "https://i.imgur.com/nGF1K8f.jpg"
```
actions.py (Custom reply)
```python
class ActionGreet(Action):
    def name(self) -> Text:
        return 'action_greet'

    def run(self, dispatcher: CollectingDispatcher,
            tracker: Tracker,
            domain: Dict[Text, Any]) -> List[Dict[Text, Any]]:
        dispatcher.utter_message(template='utter_greet')
        dispatcher.utter_message(template='utter_price')
        return []
```

El ``domains.yml`` es el que conecta a todos los archivos, es el que va a tener toda la información de los [All intents, entity, action, templates, response]

# Herramientas importantes
## Rasa NLU
Es una libreria para NLU el cual toma el input user e intenta inferir la intención y extraer las entidades disponibles y ayuda al bot a entender lo que el usuario esta intentando decir.

### El principal trabajo de la NLU
* Training data format
* Lenguage support
* Choosing a Pipeline
* Entity Extraction

ejemplo:
"*I am looking for a Mexican restaurant in the centre of town*"

```json
{
	"intent": "search_restaurant",
	"entities": {
		"cuisine": "Mexican",
		"location": "center"
	}
}
```
# Rasa Core
(Manejo del dialogo) es un dialog management ML based solution, el cual toma la estructura del input del NLU e intenta construir un modelo de probabilidad el cual decide el conjunto de acciones para ejecutar en base a los conjuntos previos de los user inputs 
### Rasa core trabaja:
* Dialog Engine
* Stories
* Domain
* Response
* Action
* Slots
* Form
* Knowledge Base Actions
# Arquitectura de Rasa
Los pasos son:
1. el mensaje es recibido y pasado a un interprete, el cual lo convierte en un diccionario incluyendo el texto original, la intención, y cualquier entidad que encontremos. Esta parte es manejada por la NLU.
2. El **Tracker** es el objeto el cual guarda track del estado de la conversación. Esta recibe la informacion de que un nuevo mensaje a llegado
3. El **policy** recibe el estado actual del **Tracker**
4. El **policy** escoge la acción a tomar acontinuación.
5. La **action** escogida es registrada por el **tracker**
6. Una respuesta es enviada al usuario.
# Install Rasa

Recomiendo crear un env en conda, Rasa trabaja bien con python 3.7 y 3.8, por ahora no hay soporte para python 3.9
```
$ conda create --name <env_name> python=3.7
```
una vez creado el env activarlo
```
$ conda activate <env_name>
```
instala rasa
```
$ pip install rasa
```
inicia un proyecto en rasa
```
$ rasa init --no-prompt
```
Una vez iniciado el proyecto puedes interactuar con el bot usando el siguiente comando
```
rasa shell
```
si tu data o tu domain cambia necesitaras reentrenar tu modelo para ver los cambios

### Observaiones
Al iniciar el proyecto se nos crearon nuevos directorios como actions, data, models, tests, y otros archivos 

* **actions**: En este directorio encontraremos el archivo ``actions.py`` donde podemos programar en codigo la respuesta del bot.
* **data**: En este directorio encontraremos los archivos ``nlu.yml``, ``rules.yml`` y ``stories.yml`` los cuales contendran las reglas e información escencial para el funcionamiento del chatbot.
* **models**: Directorio donde se guardara los datos compilados del entrenamiento en archivos tipo .tar.gz
* **Archivos**: estos archivos son generados por rasa
	* **domain.yml**: es el archivo que va a tener toda la información de los [All intents, entity, action, templates, response]

