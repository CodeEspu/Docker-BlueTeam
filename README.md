# 🛡️ Docker Blue Team

Un entorno de ciberseguridad defensiva **"Blue Team"** desplegado con Docker Compose que integra **Suricata, Wazuh y el ELK Stack.**
En este sistema, Suricata funciona como un IDS que monitorea el tráfico de la red local y envía los eventos detectados a Wazuh, donde se recopilan y filtran aplicando reglas avanzadas de correlación. Luego, Wazuh transmite la información procesada al stack ELK (Elasticsearch, Logstash y Kibana), que permite visualizar y monitorear las alertas mediante dashboards interactivos en Kibana, facilitando una respuesta rápida y eficiente ante incidentes de seguridad.

---

## 🧩 Componentes

| Servicio   | Descripción |
|------------|-------------|
| **Suricata** | Motor NIDS/IPS de alto rendimiento que analiza el tráfico de red en tiempo real. |
| **Wazuh Manager** | Monitorea logs, archivos, integridad y amenazas de endpoints. |
| **Filebeat** | Envía logs desde Suricata/Wazuh a Logstash. |
| **Logstash** | Procesa, filtra y enruta los logs hacia Elasticsearch. |
| **Elasticsearch** | Motor de búsqueda y almacenamiento de logs. |
| **Kibana** | Dashboard web para visualizar los logs y eventos de seguridad. |

---

## 🚀 Instalación

### 1. Clona el repositorio

```bash
git clone https://github.com/tu-usuario/docker-blue-team.git
cd docker-blue-team
```
### 2. Configura los archivos necesarios

Edita los archivos de configuración para adaptar el entorno a tus necesidades:

- `suricata/suricata.yaml` – Configuración y reglas de Suricata.
- `wazuh/wazuh-manager.conf` – Configuración de Wazuh.
- `.env` – Variables de entorno (puertos, rutas, etc.).
- `logstash/logstash.conf` – Pipeline de Logstash para procesar logs.
- `kibana/kibana.yml` – Configuración de Kibana.
- `elasticsearch/elasticsearch.yml` – Configuración de Elasticsearch.

### 3. Levanta los contenedores con Docker Compose

```bash
docker-compose up -d
```
---

## 📊 Acceso a Interfaz Web

| Servicio         | URL por defecto              |
|------------------|-----------------------------|
| Kibana           | http://localhost:5601        |
> Si ejecutas Docker en un servidor remoto, reemplaza `localhost` por la IP o dominio de tu host.

---

## 📂 Estructura del Proyecto

```plaintext
.
├── docker-compose.yml
├── suricata/
│   └── suricata.yaml
├── wazuh/
│   └── wazuh-manager.conf
├── logstash/
│   └── logstash.conf
├── kibana/
│   └── kibana.yml
├── elasticsearch/
│   └── elasticsearch.yml
├── .env
└── README.md
```
---

## 🔐 Funcionalidades de Seguridad

- Detección en tiempo real de intrusiones y anomalías en la red con Suricata.
- Análisis avanzado y correlación de eventos con Wazuh.
- Almacenamiento escalable y búsqueda rápida con Elasticsearch.
- Visualización interactiva de alertas y métricas en Kibana.
- Posibilidad de configurar alertas automáticas (email, Slack, Telegram, etc.).

---

## ⚙️ Requisitos del Sistema

- Docker y Docker Compose instalados.
- CPU: mínimo 2 núcleos.
- RAM: mínimo 4 GB (recomendado 8 GB para un rendimiento óptimo).
- Acceso a puertos configurados en `.env` (5601 para Kibana, 55000 para Wazuh Dashboard, etc.).

---

## ✅ Checklist de Primer Uso

- [x] Verificar que todos los contenedores estén corriendo (`docker ps`).
- [x] Acceder a Kibana y confirmar que los dashboards se cargan correctamente.
- [x] Generar tráfico de red para probar la detección de Suricata.
- [x] Confirmar que Wazuh recibe y procesa los eventos.
- [x] Configurar reglas personalizadas según necesidades.

---

