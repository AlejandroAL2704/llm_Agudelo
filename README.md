# LLM_Documentación


Repositorio de prueba para implementar LLM y una aplicación web

## 1. Instalación

Como primer paso descargamos [Ollama](https://ollama.com/) de su página oficial, y ejecutamos el siguiente comando en la terminal:

### 1.1 Instalación en Linux
```bash
curl -fsSL https://ollama.com/install.sh | sh
````
### 1.2 Ejecutar Ollama
En el menu de terminal se escribira el nombre de la herramienta
````bash
ollama
````
Con esto nos mostrata el manual de comando que trae la herramienta.

Para ejecutar el servidor de API REST de ollama se usa el siguiente comando: 
````bash
ollama serve
````
## 2. Cargue de modelos de lenguaje de alta Escala
Los modelos tienen que descargarse en una nueva terminal no pueden ir en la misma en la que se inicio ollama.

### 2.1 Busqueda de modelos Ollama
Para esto nos dirigimos al apartado de modelos de [Ollama](https://ollama.com/library) , nos aparecera el listado de modelos , la opción de filtrar o en caso de conocer el nombre del modelo, el cuadro de busqueda para encontrarlo directamente.

### 2.2 Descargue o instalacion de modelos 
Una vez seleccionado el modelo que se va a implementar nos dara el codigo de instalación generico de linux para ejecutar en el terminal:
```bash
ollama run Nombre del modelo
````
Para instalarlo es el mismo con reemplazando el run
````bash
ollama pull Nombre del modelo
````
Este es un ejemplo de una descarga completa:
````bash
pulling manifest 
pulling 2af3b81862c6... 100% ▕███████████████████████████████████████████████████████████████████████▏ 637 MB                         
pulling af0ddbdaaa26... 100% ▕███████████████████████████████████████████████████████████████████████▏   70 B                         
pulling c8472cd9daed... 100% ▕███████████████████████████████████████████████████████████████████████▏   31 B                         
pulling fa956ab37b8c... 100% ▕███████████████████████████████████████████████████████████████████████▏   98 B                         
pulling 6331358be52a... 100% ▕███████████████████████████████████████████████████████████████████████▏  483 B                         
verifying sha256 digest 
writing manifest 
success 
````
### 2.3 Ver modelos descargados o instalados
Para esto en la terminal nueva (diferente de donde inicio la herramienta) se usa el comando
````bash
ollama list
````
## 3 Ejecución de modelos
## 3.1 Terminal
En la terminal usaremos el comando:
````bash
ollama run NombredelModelo Intruccion o pregunta
````

## 4 Realizar Request a la API REST

### 4.1 Para solicitar información
Desde el equipo para utilizar APIs se pueden utilizar comandos como:
````bash
curl -X POST http://localhost:11434/api/generate -d '{
  "model": "tinyllama",
  "prompt": "Why is the sky blue?", 
  "stream": false
}' -o salida.md
````
Esta información fue extraida de Ollama en la ventana de Github -> carpeta Docs -> Api.md
 * curl: para utilizar API's por terminal
 * -X POST: Para enviar información al API
 * URI: Direccion y puerto de acceso de Ollama
 * model: Nombre del modelo con el que se quiere contactar.
 * prompt: Mensaje o instrucción a enviar al API
 * -o guardar respuesta en un archivo
 * salida.md Nombre del archivo que se creara para guardar la información. 
 * stream false: Para recibir la respuesta en un solo token

## 5. Para cargar en Github
### 5.1 Para indexar los documentos existentes
Indexa, valida todos los documentos que se tienen:
````bash
git add . 
 ````
 ### 5.2 Para realizar las modificaciones realizadas
 Para cargar las modificaciones realizadas se usa el comando:
 ````bash
git commit -m "UPDATE README.md" 
 ````
 ### 5.3 Para guardar las modificaciones

Para guardar se debe de ejecutar el comando:
````bash
git push -u origin main
````
Esto va a tomar todos los cambios realizados y guardarlos.

## 6. API Rest con GrogCloud

Se ingresa a la pagina principal de [GroqCloud](https://console.groq.com/playground)
### 6.1 Crear API KEY
Una vez se ingresa a GroqCloud al lado derecho en el menu principal existe una ventana llamada API KEYS, es esta ventana debes ingresar y crear un APIKEY con el nombre que se desee y copiar el identificador de la llave en algun sitio que tengamos acceso siempre que se requiera.
### 6.2 Consulta a Groq mediante API REST

Esta es la estructura de una consulta normal a Groq mediante API REST:
````bash
curl "https://api.groq.com/openai/v1/chat/completions" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer ${GROQ_API_KEY}" \
  -d '{
         "messages": [
           {
             "role": "user",
             "content": "¿Por que el cielo es azul?
"
           }
         ],
         "model": "llama3-8b-8192",
         "stream": false
          }'
````
# 7. Importar libreria Python
Se ingresa a [W3SCHOOLS](https://www.w3schools.com/python/module_requests.asp) donde buscaremos las librerias de python.

## 7.1 Busqueda de entorno de trabajo
Cuando se ingresa a esa pantalla en la parte inferior esta la forma de instalacion de los diferentes entornos que presta python para instalarse en este caso POST
## 7.2 Instalación de Python
En nuestro caso que utilizamos post la estructura es esta:
````bash
import requests
import json

url = 'http://localhost:11434/api/generate'
myobj = {
  "model": "tinyllama",
  "prompt": "Why is the sky blue?", 
  "stream": False
}

x = requests.post(url, json = myobj)
x = json.loads(x.text)
print(x["response"])
````
Se agrego la libreria de JSON para poder recibir a pantalla unicamente el response es decir la respuesta a la pregunta solicitada.
 
Para esta prueba en particular se creo en el directorio principal una carpeta de Ejemplos y en la carpeta se creo el archivo py donde se agrego el codigo, luego por terminal se ejecuto con el comando basico de python dentro del directorio donde esta el archivo:
````bash
python3 NombredelArchivopy
````
