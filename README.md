# AosMicroservicio
Este repositorio contiene los archivos necesarios para ejecutar y probar una API REST dedicada a los trabajos que se realizan en un taller, encontrada en el archivo openapi.yaml. 

Para poner en funcionamiento esta api se debe ejecutar el archivo 'docker-compose.yml', que contiene las imagenes usadas. Estas son:

1. Swagger_ui -> Como su nombre indica, ofrece una interfaz para visualizar la API en un entorno más "user friendly".
2. Prism -> Esta imagen crea un 'mock' de la API que permite ofrecer respuestas cuando se realizan llamadas siguiendo los paths especificados en la API.


Para desplegar con Kubernetes se ha utilizado Minikube junto con Docker.

Por tanto una vez instalado en la maquina minikube y con Docker abierto, ejecutaremos el comando:

- minikube start

una vez arrancado minikube queremos montar el volumen que contiene los ficheros de las api de la siguiente manera:

- minikube mount 'RutaAbsolutaAlRootDelProyecto':/openapi

como ejemplo podriamos tener algo similar a esto:

minikube mount /Users/Test/Development/AosMicroservicio_Grupo1:/openapi

una vez montado el volumen y dejando esa terminal abierta, ejecutaremos el comando:

- kubectl apply -f k8.yaml

desde el root del proyecto, con esto se crearán todos los pods, servicios y volumens persistentes.

Podemos comprobar el estado de los pods utilizando 

- kubectl get pods

Una vez estén todos en running y habiendo esperado al menos 1 minuto para que los pods arranquen y carguen los .yaml en prism, volvemos a minikube para ejecutar.

- minikube service --all

Esto creará un tunnel para cada servicio existente permitiendo así acceder desde nuestro navegador, se abrirán todos los enlaces en el navegador por defecto y ya podemos empezar a probar.
