# Manual de Instalación: Monitoreo con Grafana, Prometheus, Windows Exporter, Alertmanager y MySQL Exporter

## Tabla de Contenidos
1. [Requisitos del Sistema](#requisitos-del-sistema)
2. [Diagrama de Arquitectura](#diagrama-de-arquitectura)
3. [Instalación en Servidor Windows (53.0.0.2/21)](#instalación-en-servidor-windows)
   - [1. Instalación de Prometheus](#1-instalación-de-prometheus)
   - [2. Instalación de Grafana](#2-instalación-de-grafana)
   - [3. Instalación de Alertmanager](#3-instalación-de-alertmanager)
   - [4. Instalación de MySQL Exporter](#4-instalación-de-mysql-exporter)
4. [Instalación en Cliente Windows](#instalación-en-cliente-windows)
   - [1. Instalación de Windows Exporter](#1-instalación-de-windows-exporter)
5. [Configuración de Integraciones](#configuración-de-integraciones)
6. [Verificación y Pruebas](#verificación-y-pruebas)

---

## Requisitos del Sistema
- Servidor Windows (53.0.0.2/21) con:
  - Windows Server 2016/2019/2022
  - 4GB RAM mínimo (8GB recomendado)
  - 100GB de espacio en disco
  - Acceso administrativo
- Cliente Windows con:
  - Windows 10/11 o Windows Server
  - Acceso de red al servidor
- Puertos abiertos:
  - 9090 (Prometheus)
  - 3000 (Grafana)
  - 9093 (Alertmanager)
  - 9100 (Windows Exporter)
  - 9104 (MySQL Exporter)

---

## Diagrama de Arquitectura

![Diagrama de Arquitectura](images/architecture-diagram.png)
*Figura 1: Diagrama de flujo que muestra cómo los componentes interactúan entre sí. Prometheus recolecta métricas de los exporters y Grafana las visualiza.*

---

## Instalación en Servidor Windows

### 1. Instalación de Prometheus

**Función:** Prometheus es el sistema de monitoreo y alertas que recolectará y almacenará las métricas.

**Pasos:**

1. Descargar la última versión de Prometheus para Windows desde [prometheus.io/download](https://prometheus.io/download/)
2. Extraer el archivo ZIP a `C:\Prometheus`
3. Configurar el archivo `prometheus.yml`:

```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']
  - job_name: 'windows_exporter'
    static_configs:
      - targets: ['cliente:9100']
  - job_name: 'mysql_exporter'
    static_configs:
      - targets: ['localhost:9104']
```

4. Crear un servicio Windows para Prometheus:

```powershell
New-Service -Name "Prometheus" -BinaryPathName "C:\Prometheus\prometheus.exe --config.file=C:\Prometheus\prometheus.yml" -DisplayName "Prometheus Monitoring" -StartupType Automatic
Start-Service -Name "Prometheus"
```

![Prometheus Installation](images/prometheus-install.png)
*Figura 2: Captura de pantalla mostrando la instalación exitosa de Prometheus y su servicio corriendo.*

---

### 2. Instalación de Grafana

**Función:** Grafana proporciona dashboards visuales para las métricas recolectadas por Prometheus.

**Pasos:**

1. Descargar el instalador de Grafana para Windows desde [grafana.com/grafana/download](https://grafana.com/grafana/download)
2. Ejecutar el instalador y seguir los pasos
3. Acceder a Grafana via `http://localhost:3000`
4. Configurar el datasource de Prometheus:
   - Ir a Configuration > Data Sources
   - Seleccionar Prometheus
   - URL: `http://localhost:9090`
   - Guardar y probar la conexión

![Grafana Setup](images/grafana-setup.png)
*Figura 3: Interfaz de Grafana mostrando la configuración del datasource de Prometheus.*

---

### 3. Instalación de Alertmanager

**Función:** Alertmanager maneja las alertas generadas por Prometheus y las envía a los canales configurados.

**Pasos:**

1. Descargar Alertmanager desde [prometheus.io/download](https://prometheus.io/download/)
2. Extraer a `C:\Alertmanager`
3. Configurar `alertmanager.yml` (ejemplo para email):

```yaml
route:
  receiver: 'email-notifications'

receivers:
- name: 'email-notifications'
  email_configs:
  - to: 'admin@example.com'
    from: 'alertmanager@example.com'
    smarthost: 'smtp.example.com:587'
    auth_username: 'user'
    auth_password: 'password'
```

4. Crear servicio:

```powershell
New-Service -Name "Alertmanager" -BinaryPathName "C:\Alertmanager\alertmanager.exe --config.file=C:\Alertmanager\alertmanager.yml" -DisplayName "Alertmanager" -StartupType Automatic
Start-Service -Name "Alertmanager"
```

---

### 4. Instalación de MySQL Exporter

**Función:** Exporta métricas de MySQL para ser recolectadas por Prometheus.

**Pasos:**

1. Descargar mysqld_exporter desde [prometheus.io/download](https://prometheus.io/download/)
2. Extraer a `C:\MySQL_Exporter`
3. Crear archivo de configuración `.my.cnf`:

```ini
[client]
user=exporter_user
password=yourpassword
```

4. Crear servicio:

```powershell
New-Service -Name "MySQL_Exporter" -BinaryPathName "C:\MySQL_Exporter\mysqld_exporter.exe --config.my-cnf=C:\MySQL_Exporter\.my.cnf" -DisplayName "MySQL Exporter" -StartupType Automatic
Start-Service -Name "MySQL_Exporter"
```

---

## Instalación en Cliente Windows

### 1. Instalación de Windows Exporter

**Función:** Exporta métricas del sistema Windows para ser recolectadas por Prometheus.

**Pasos:**

1. Descargar el último release desde [GitHub](https://github.com/prometheus-community/windows_exporter/releases)
2. Ejecutar el instalador MSI
3. Verificar que el servicio está corriendo en `http://localhost:9100/metrics`

```powershell
Get-Service -Name "windows_exporter"
```

![Windows Exporter](images/windows-exporter.png)
*Figura 4: Métricas expuestas por Windows Exporter accesibles en el puerto 9100.*

---

## Configuración de Integraciones

1. **Grafana y Prometheus:**
   - Importar dashboards predefinidos desde [Grafana Labs](https://grafana.com/grafana/dashboards/)
   - ID recomendado para Windows: 10467

2. **Alertas en Prometheus:**
   - Configurar reglas de alerta en `C:\Prometheus\rules.yml` y referenciarlas en `prometheus.yml`

```yaml
rule_files:
  - 'rules.yml'
```

---

## Verificación y Pruebas

1. Verificar que todos los servicios están corriendo:

```powershell
Get-Service | Where-Object { $_.Name -in @('Prometheus','Grafana','Alertmanager','MySQL_Exporter') }
```

2. Acceder a las interfaces:
   - Prometheus: `http://53.0.0.2:9090`
   - Grafana: `http://53.0.0.2:3000`
   - Alertmanager: `http://53.0.0.2:9093`

3. Probar alertas simulando alta carga de CPU o disco.

![Final Setup](images/final-dashboard.png)
*Figura 5: Dashboard final en Grafana mostrando métricas de Windows y MySQL.*