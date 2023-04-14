# AosMicroservicio
Este repositorio contiene los archivos necesarios para ejecutar y probar una API REST dedicada a los trabajos que se realizan en un taller, encontrada en el archivo openapi.yaml. 

Para poner en funcionamiento esta api se deben ejecutar los siguientes comandos (esto habrá que quitarlo y sustituirlo por un archivo docker compose, pero dejo aqui de momento los comandos):

1. Comando para ejecutar una imagen de swagger para poder mostrar la api en swagger en el puerto 8080 del PC, con escribir "localhost:8080" en el navegador es suficiente.

docker run -p 8000:8080 --rm --name 'Nombre_contenedor' -e SWAGGER_JSON=/aos/openapi.yaml -v 'Path hasta carpeta contenedora del archivo .yaml (llegar hasta carpeta, no poner archivo)':/aos swaggerapi/swagger-ui

2. Comando para crear un mock de la api al que poder hacer llamadas y que ofrezca respuestas como demostración de funcionamiento. Las llamadas tendrán que hacerse al localhost en el puerto 4010.

docker run --init --rm -it -p 80:4010 --name aos2023_mock -v 'Path hasta carpeta contenedora del archivo .yaml (llegar hasta carpeta, no poner archivo)':/aos stoplight/prism:4 mock --cors -h 0.0.0.0 "/aos/openapi.yaml”
