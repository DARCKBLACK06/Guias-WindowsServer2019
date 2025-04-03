# Pasos para github

Quick setup ¿ if you¿ve done this kind of thing before
or	
```bash
https://github.com/DARCKBLACK06/Guias-WindowsServer2019.git
```
Get started by creating a new file or uploading an existing file. We recommend every repository include a README, LICENSE, and .gitignore.

¿or create a new repository on the command line
echo "# Guias-WindowsServer2019" >> README.md
```bash
git init
```
```bash
git add README.md
```
```bash
git commit -m "first commit"
```
```bash
git branch -M main
```
```bash
git remote add origin https://github.com/DARCKBLACK06/Guias-WindowsServer2019.git
```
```bash
git push -u origin main
```
¿or push an existing repository from the command line
```bash
git remote add origin https://github.com/DARCKBLACK06/Guias-WindowsServer2019.git
```
```bash
git branch -M main
```
```bash
git push -u origin main
```
---------------------

# **Manual Básico de Git y GitHub desde Consola**  
*(Guía rápida para subir cambios a GitHub)*  

## **1. Configuración Inicial (Solo primera vez)**  
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

## **2. Subir cambios nuevos a un repositorio existente**  

### **📌 Pasos para actualizar tu repositorio**  

1. **Verificar cambios locales**  
   ```bash
   git status
   ```
   - Muestra archivos modificados o nuevos (en rojo si no están *staged*).  

2. **Agregar archivos al *staging area***  
   - Para **todos los archivos**:  
     ```bash
     git add .
     ```
   - Para un **archivo específico**:  
     ```bash
     git add archivo.txt
     ```

3. **Guardar cambios con un *commit***  
   ```bash
   git commit -m "Mensaje descriptivo de los cambios"
   ```
   - Ejemplo:  
     ```bash
     git commit -m "Agregué nuevas funciones JS"
     ```

4. **Subir cambios a GitHub (*push*)**  
   ```bash
   git push origin main
   ```
   - Si tu rama tiene otro nombre (ej: `master` o `develop`), cámbialo:  
     ```bash
     git push origin nombre_de_rama
     ```

---

## **3. Comandos Adicionales Útiles**  

| Comando | Descripción |
|---------|-------------|
| `git pull origin main` | Descarga cambios de GitHub a tu PC. |
| `git log` | Muestra historial de commits. |
| `git branch` | Lista las ramas del repositorio. |
| `git remote -v` | Verifica la URL de tu repositorio remoto. |

---

## **4. Solución de Problemas Comunes**  

### **🔹 Error: «No está configurado el upstream»**  
Si `git push` falla, usa:  
```bash
git push --set-upstream origin main
```

### **🔹 ¿Primera vez en un repositorio existente?**  
Clónalo con:  
```bash
git clone https://github.com/usuario/repositorio.git
```

---

## **📌 Ejemplo Completo**  
```bash
git status
git add .
git commit -m "Se corrigió el diseño responsive"
git push origin main
```

---

### **🎉 ¡Listo! Tus cambios ya están en GitHub.**  
👉 *¿Necesitas más ayuda? Revisa la [documentación oficial de Git](https://git-scm.com/doc).*  

```markdown
**Nota:** Puedes guardar este manual en un archivo `README.md` o `GIT_GUIDE.md` en tu repositorio. 😊
```  

---  
**🔗 Más recursos:**  
- [GitHub Docs](https://docs.github.com)  
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)  

---  
*✍️ ¿Quieres personalizar esta guía? ¡Edita este archivo Markdown!* 🚀