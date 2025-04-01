# Manual de Git como Controlador de Versiones en Windows Server 2019

## 1. Instalación de Git

1. **Descargar Git:**  
   Ve a la página oficial de Git [https://git-scm.com/downloads](https://git-scm.com/downloads) y descarga la versión más reciente para Windows.

2. **Instalar Git:**  
   Sigue las instrucciones del instalador. Asegúrate de seleccionar la opción para agregar Git al PATH durante la instalación.

3. **Verificar la instalación:**  
   Una vez instalado, abre PowerShell o CMD y ejecuta el siguiente comando para verificar que Git esté correctamente instalado:

    ```bash
    git --version
    ```

Esto debería mostrarte la versión instalada de Git.

---

## 2. Crear un Repositorio Local

Una vez instalado Git, puedes empezar a trabajar con un repositorio local.

1. **Navegar a tu proyecto:**  
   Ve a la carpeta de tu proyecto usando el Explorador de Archivos de Windows.

2. **Inicializar el repositorio:**  
   En la carpeta del proyecto, haz clic derecho y selecciona “Git Bash Here” para abrir la terminal de Git Bash, o abre PowerShell y navega hasta la carpeta del proyecto. Luego, ejecuta:

    ```bash
    git init
    ```

Este comando crea un repositorio Git en tu proyecto, que rastreará todos los cambios que hagas en los archivos del proyecto.

---

## 3. Agregar Archivos al Repositorio

Una vez que hayas realizado cambios en los archivos de tu proyecto, Git necesita saber qué archivos quieres seguir y almacenar en el historial de versiones.

1. **Agregar archivos al área de preparación:**  
   Usa el siguiente comando para agregar archivos específicos o todos los archivos modificados:

    ```bash
    git add archivo.txt
    ```

   O si deseas agregar todos los archivos modificados:

    ```bash
    git add .
    ```

---

## 4. Realizar un Commit

Un **commit** guarda una "instantánea" del proyecto en su estado actual.

1. **Realizar un commit:**  
   Una vez que hayas agregado los archivos, realiza un commit para guardar el estado del proyecto:

    ```bash
    git commit -m "Descripción de los cambios realizados"
    ```

El mensaje entre comillas debe ser una descripción clara de los cambios realizados en ese commit.

---

## 5. Conectar con un Repositorio Remoto en GitHub

Para almacenar tu código en GitHub y colaborar con otros, necesitas conectar tu repositorio local con un repositorio remoto.

1. **Crear un repositorio en GitHub:**  
   Dirígete a [GitHub](https://github.com) y crea una cuenta si no tienes una. Luego, crea un nuevo repositorio desde el panel de control.

2. **Conectar tu repositorio local con GitHub:**  
   Una vez creado el repositorio en GitHub, ejecuta el siguiente comando en Git Bash o PowerShell para agregar el repositorio remoto:

    ```bash
    git remote add origin https://github.com/TuUsuario/TuRepositorio.git
    ```

Este comando vincula tu repositorio local con el repositorio en GitHub.

---

## 6. Subir Cambios a GitHub

1. **Subir los cambios al repositorio remoto en GitHub:**  
   Una vez que hayas realizado un commit y quieras que los cambios estén disponibles en GitHub, ejecuta:

    ```bash
    git push origin main
    ```

Esto subirá los cambios a la rama principal de tu repositorio en GitHub.

---

## 7. Clonar un Repositorio Existente

Si alguien más ya tiene un repositorio en GitHub y quieres trabajar con él, puedes clonarlo a tu máquina.

1. **Clonar el repositorio:**  
   Para obtener una copia del repositorio remoto, usa:

    ```bash
    git clone https://github.com/TuUsuario/TuRepositorio.git
    ```

Esto descargará todos los archivos y el historial del proyecto en tu máquina local.

---

## 8. Ver el Estado del Repositorio

Para saber si tienes archivos modificados que no han sido agregados o committeados, puedes usar:

```bash
git status
```
Este comando te mostrará los archivos que han sido modificados, los que aún no han sido añadidos al área de preparación, y otra información relevante.


---

9. Ver el Historial de Cambios

Para ver todos los cambios realizados en el repositorio, incluyendo detalles sobre los commits, usa:

git log

Este comando te mostrará el historial de commits con información sobre el autor, la fecha y el mensaje del commit.


---

10. Obtener los Cambios de Otros Colaboradores

Si otras personas están trabajando en el mismo proyecto, es importante mantener tu repositorio actualizado. Para obtener los cambios más recientes desde el repositorio remoto, usa:

git pull origin main

Este comando descargará los últimos cambios del repositorio remoto y los fusionará con tu repositorio local.


---

11. Trabajar con Ramas (Branches)

Las ramas te permiten trabajar en características o cambios de manera aislada, sin interferir con el desarrollo principal.

1. Crear una nueva rama:

git branch nueva-rama


2. Cambiar a la nueva rama:

git checkout nueva-rama



Una vez que hayas terminado de trabajar en la rama, puedes combinarla con la rama principal:

git checkout main
git merge nueva-rama


---

Resumen del Uso de Git

git init: Inicializa un repositorio en tu proyecto.

git add: Agrega archivos al área de preparación.

git commit: Guarda los cambios en el historial.

git push: Sube los cambios al repositorio remoto en GitHub.

git pull: Obtiene los cambios de otros colaboradores desde GitHub.

git log: Muestra el historial de commits.

git branch: Crea y gestiona ramas para desarrollo paralelo.
