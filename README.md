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
``bash
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
5.1 Para indexar los documentos existentes
````bash
 git add . Indexa, valida todos los documentos que se tienen
 ````
 git commit -m "UPDATE README.md" para modificar los archivos

 Para guardar gir push -u origin main Esto va a tomar todos los cambios realizados y guardarlos.