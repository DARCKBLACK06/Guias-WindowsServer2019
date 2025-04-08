# Manual de Instalación de Grafana en Windows Server con Windows Exporter y Prometheus

## 1. Instalación de Grafana
### 1.1 Descarga e Instalación
1. Descargue Grafana desde el sitio oficial: [https://grafana.com/grafana/download](https://grafana.com/grafana/download).
2. Seleccione la versión para Windows y descargue el instalador.
3. Extraiga el archivo ZIP en `C:\Program Files\Grafana`.
4. Abra una terminal PowerShell como administrador y ejecute:
   ```powershell
   cd "C:\Program Files\Grafana\bin"
   .\grafana-server.exe
   ```
5. Acceda a Grafana desde el navegador en `http://localhost:3000/`.
6. Inicie sesión con el usuario `admin` y la contraseña `admin`, luego cambie la contraseña.

## 2. Instalación de Windows Exporter
### 2.1 Descarga e Instalación
1. Descargue Windows Exporter desde GitHub: [https://github.com/prometheus-community/windows_exporter/releases](https://github.com/prometheus-community/windows_exporter/releases).
2. Descargue el archivo `windows_exporter-*.msi` y ejecútelo.
3. Durante la instalación, seleccione los módulos necesarios y continúe con la instalación.
4. Una vez instalado, verifique que el servicio esté corriendo:
   ```powershell
   Get-Service windows_exporter
   ```
5. Acceda a `http://localhost:9182/metrics` en el navegador para confirmar que está funcionando.

## 3. Instalación de Prometheus
### 3.1 Descarga e Instalación
1. Descargue Prometheus desde el sitio oficial: [https://prometheus.io/download/](https://prometheus.io/download/).
2. Descargue la versión para Windows y extraiga los archivos en `C:\Program Files\Prometheus`.

### 3.2 Configuración de Prometheus
1. Edite el archivo `C:\Program Files\Prometheus\prometheus.yml` y agregue la configuración de Windows Exporter:
   ```yaml
   global:
     scrape_interval: 15s

   scrape_configs:
     - job_name: 'windows'
       static_configs:
         - targets: ['localhost:9182']
   ```
2. Guarde los cambios y ejecute Prometheus desde PowerShell:
   ```powershell
   cd "C:\Program Files\Prometheus"
   .\prometheus.exe --config.file=prometheus.yml
   ```
3. Acceda a la interfaz web en `http://localhost:9090/`.

## 4. Configuración de Grafana con Prometheus
1. Inicie sesión en Grafana (`http://localhost:3000/`).
2. Vaya a `Configuration > Data Sources`.
3. Haga clic en `Add data source` y seleccione `Prometheus`.
4. En `URL`, ingrese `http://localhost:9090`.
5. Haga clic en `Save & Test`.

## 5. Creación de un Dashboard en Grafana
1. Vaya a `Dashboards > New Dashboard`.
2. Agregue un `Panel` y seleccione la fuente de datos `Prometheus`.
3. Escriba una consulta, por ejemplo:
   ```
   windows_cpu_time_total
   ```
4. Configure las opciones de visualización y guarde el dashboard.

## Conclusión
Con estos pasos, ha instalado Grafana en Windows Server, configurado Windows Exporter y Prometheus para monitorear métricas del sistema. Ahora puede personalizar dashboards según sus necesidades.
