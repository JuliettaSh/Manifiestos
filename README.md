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
## Clona el repositorio de la página web:
* git clone https://github.com/JuliettaSh/static-website.git
## Clona el repositorio de manifiestos:
* git clone https://github.com/JuliettaSh/Manifiestos.git
# 2. Inicializar Minikube
Iniciar Minikube con un perfil personalizado y habilita metrics-server:
* minikube start -p 0311at --addons=metrics-server
# 3. Aplicar los manifiestos
Dentro del repositorio de manifiestos, aplicar los recursos en el siguiente orden:
* kubectl apply -f namespace.yml
* kubectl apply -f configmap.yml
* kubectl apply -f persistenceVolume.yml
* kubectl apply -f persistenceVolumeClaim.yml
* kubectl apply -f deployment.yml
* kubectl apply -f service.yml
***
  Nota: Tener en cuenta de estar en el contexto del namespace correcto.
# 4. Exponer el servicio
Para exponer el servicio creado y acceder a la página web, ejecutar el siguiente comando donde habilitamos el servicio que está en el perfil creado y el namespace correspondiente:
* minikube service service-0311 -p 0311at -n 0311at-web
***
  Esto abrirá el sitio web en el navegador localmente.
