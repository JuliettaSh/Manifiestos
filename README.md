# Proyecto Kubernetes - Despliegue de Página Web Estática
## Descripción
Este proyecto es del despliegue de una página web estática dentro de un clúster de Kubernetes local usando Minikube. Usamos diferentes recursos como el Namespace, ConfigMap, PersistentVolume, PersistentVolumeClaim, Deployment y Service para hacer lo antes mencionado.
________________________________________
Requisitos
* Git
* Minikube
* kubectl
* Docker instalado en tu máquina.
________________________________________
Pasos para reproducir el entorno
# 1. Clonar los repositorios
## Clona el repositorio de la página web pero en este usando tu clave SSH si quieres hacer un push y que los cambios se actualicen:
* git clone git@github.com:JuliettaSh/Manifiestos.git
* Te va a pedir la frase de tu contraseña
* Si se quiere hacer un cambio se deben seguir los comandos de git add, git commit y git push (que te va a pedir la contraseña)
## Clona el repositorio de manifiestos en una carpeta:
* git clone https://github.com/JuliettaSh/Manifiestos.git
# 2. Inicializar Minikube
Iniciar Minikube con un perfil personalizado y habilita metrics-server:
* minikube start -p 0311at --addons=metrics-server
# 3. Aplicar los manifiestos
Dentro del repositorio de manifiestos haciendo: cd Manifiestos, aplicar los recursos en el siguiente orden:
* kubectl apply -f namespace.yml
* kubectl apply -f configmap.yml
* kubectl apply -f persistenceVolume.yml
* kubectl apply -f gitPVC.yml
* kubectl apply -f persistenceVolumeClaim.yml
* kubectl apply -f deployment.yml
* kubectl apply -f service.yml
***
  Nota: Tener en cuenta de estar en el contexto del namespace correcto si se quiere hacer algun cambio importante o ver logs.
# 4. Exponer el servicio
Para exponer el servicio creado y acceder a la página web, ejecutar el siguiente comando donde habilitamos el servicio que está en el perfil creado y el namespace correspondiente:
* minikube service service-0311 -p 0311at -n 0311at-web
***
  Esto abrirá el sitio web en el navegador localmente.
# 5. Añadir cambios a la pagina
Si se hizo un cambio no olvidarse de hacer el git push (añadiendo la contraseña)
* una vez en el navegador esperamos a que pasen unos segundos y refrescamos la página, los cambios deberian verse.
