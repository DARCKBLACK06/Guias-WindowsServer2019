Manual de Instalación de OpenSSH en Windows Server usando PowerShell

1. Verificar la Disponibilidad de OpenSSH

Ejecuta el siguiente comando para verificar si OpenSSH ya está disponible en el sistema:

Get-WindowsCapability -Online | Where-Object Name -Like "OpenSSH*"

Si OpenSSH no está instalado, procede con la instalación.

2. Instalar el Servidor OpenSSH

Ejecuta el siguiente comando para instalar el servicio OpenSSH Server:

Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0

Una vez instalado, verifica que la instalación fue exitosa:

Get-WindowsCapability -Online | Where-Object Name -Like "OpenSSH*"

3. Configurar OpenSSH

Para definir el shell predeterminado en PowerShell, usa el siguiente comando:

New-ItemProperty -PATH "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force

4. Iniciar y Configurar el Servicio OpenSSH

Para iniciar el servicio OpenSSH inmediatamente, usa:

Start-Service sshd

Para verificar el estado del servicio:

Get-Service -Name sshd

Para asegurarte de que OpenSSH se inicie automáticamente con el sistema, configura el servicio en modo automático:

Set-Service -Name sshd -StartupType Automatic

5. Verificación Final

Confirma que el servicio esté corriendo correctamente:

Get-Service -Name sshd

Si todo está correcto, OpenSSH Server estará instalado y listo para aceptar conexiones SSH en Windows Server.

6. Prueba de Conexión con PuTTY

Una vez que el servidor OpenSSH está en ejecución, puedes probar la conexión usando PuTTY.

Pasos:

1. Descarga e instala PuTTY desde https://www.putty.org.


2. Abre PuTTY y en la sección "Host Name (or IP address)", ingresa el nombre de tu DNS o la IP de tu servidor. Por ejemplo:

Host Name: netsecure.com

Port: 22

Connection Type: SSH



3. Haz clic en Open.


4. Si es la primera vez que te conectas, aparecerá una advertencia sobre la clave del servidor. Acepta para continuar.


5. Ingresa tus credenciales (usuario y contraseña del servidor).



Si la conexión es exitosa, tendrás acceso remoto a tu servidor a través de SSH.

