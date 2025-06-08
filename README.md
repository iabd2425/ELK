# Proyecto ELK - Chatbot Inteligente

Este repositorio contiene la configuración y recursos necesarios para desplegar un stack **ELK (Elasticsearch, Logstash, Kibana)** complementado con **Metricbeat** y **Filebeat**, como parte del desarrollo de un sistema de búsqueda inteligente con datos reales obtenidos mediante scraping. Incluye dashboards de monitorización y visualización de datos de hoteles y logs de interacción con un chatbot.

---

## 📦 Estructura del repositorio

```
ELK/
├── docker-compose.yml        # Orquestación de servicios ELK
├── README.md                 # Documentación del proyecto
├── captures/                 # Capturas de pantallas de dashboards y alertas
├── kibana/
│   ├── dashboards/           # Dashboards en formato NDJSON (hoteles, chatbot, completos)
│   └── alertas/              # Alertas exportadas de Kibana
├── logstash/
│   ├── pipelines.yml         # Definición de múltiples pipelines
│   ├── hoteles.conf          # Pipeline para cargar datos de hoteles desde JSON
│   ├── scraper_logs.conf     # Pipeline para procesar logs del scraper con grok
│   ├── chatbot_logs.conf     # Pipeline para procesar logs del chatbot
│   └── datos/                # JSON de ejemplo y logs
├── filebeat/
│   └── filebeat.yml          # Configuración de Filebeat para recoger logs locales
└── metricbeat/
    ├── metricbeat.yml        # Configuración general de Metricbeat
    └── modules.d/            # Módulos activados (ES, Kibana)
```

---

## 🚀 Puesta en marcha

### 1. Clonar el repositorio

```bash
git clone https://github.com/iabd2425/ELK.git
cd ELK
```

### 2. Arrancar los servicios (Docker)

```bash
docker-compose up -d
```

Esto iniciará los servicios:

* Elasticsearch: [http://localhost:9200](http://localhost:9200)
* Kibana: [http://localhost:5601](http://localhost:5601)

### 3. Parar los servicios

```bash
docker-compose down
```

> ⚠️ Usa siempre `docker-compose up -d` al comenzar tu jornada para tener los servicios activos, y `docker-compose down` al terminar para liberar recursos.

---

## 🔧 Servicios desplegados

### 🔍 Elasticsearch

Motor de búsqueda distribuido que almacena datos del scraper y logs del sistema.

### 📊 Kibana

Interfaz gráfica para crear dashboards interactivos, visualizar logs, métricas del sistema y configurar alertas.

### ⚙️ Logstash

Procesador de datos que transforma e indexa información en Elasticsearch desde archivos `.json` y `.log`.

### 📈 Metricbeat

Monitoriza recursos del sistema ELK como uso de CPU, memoria y tráfico de red.

### 📑 Filebeat

Recolector ligero que envía automáticamente archivos `.log` a Logstash (scraper, chatbot).

---

## 🗺️ Dashboard de Hoteles (Booking)

Este dashboard presenta información agregada y geolocalizada sobre alojamientos de Andalucía:

* Precio medio por ciudad
* Puntuación media por tipo
* Conteo de alojamientos por tipo
* Mapa interactivo (`geo_point` con `location`)
* Total de alojamientos
* Panel de filtro por ciudad o provincia

📂 Archivo: `dashboards_hoteles_chatbot_clean.ndjson`

---

## 📊 Dashboard de Monitorización del stack ELK

Incluye visualizaciones clave generadas por **Metricbeat**:

* Uso de CPU por host
* Uso de memoria por host
* Tráfico de red (entrante/saliente)
* Eventos recibidos por módulo (`event.dataset`)

---

## 💬 Dashboard de Logs del Chatbot

Este dashboard representa información de los archivos `.log` generados por el chatbot:

* Tiempo medio de respuesta (`elapsed_ms`)
* Total de consultas realizadas
* Porcentaje de errores vs éxitos
* Preguntas más frecuentes
* Tabla con interacción completa (pregunta, respuesta, timestamp)

📂 Archivo: `visualizaciones_completas_elk.ndjson` + `dashboard_completo_elk.ndjson`

> Requiere datos indexados en el índice `chatbot-2025.05.27`

---

## 📥 Importación de visualizaciones y dashboards

1. Accede a Kibana: [http://localhost:5601](http://localhost:5601)
2. Ve a *Stack Management > Saved Objects*
3. Pulsa **Import** y selecciona los archivos `.ndjson` desde `kibana/dashboards/`
4. Entra a *Dashboard* y selecciona uno de los disponibles
5. Puedes añadir visualizaciones desde la librería visual o crear nuevas

---

## 🔐 Seguridad y buenas prácticas

* No se activa autenticación en desarrollo (`xpack.security.enabled=false`)
* Filebeat y Logstash usan rutas relativas para facilitar despliegue
* Se recomienda usar `sleep` en Metricbeat para que Kibana esté disponible al iniciar

---

## 📘 Recursos útiles

* [Documentación oficial de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/index.html)
* [Documentación de Kibana](https://www.elastic.co/guide/en/kibana/current/index.html)
* [Documentación de Logstash](https://www.elastic.co/guide/en/logstash/current/index.html)
* [Documentación de Metricbeat](https://www.elastic.co/guide/en/beats/metricbeat/current/index.html)
* [Documentación de Filebeat](https://www.elastic.co/guide/en/beats/filebeat/current/index.html)

---

## 🤝 Autores

**Equipo de especialización en Big Data e IA**    

IES Al-Ándalus · Curso 2024-2025

---

¡Gracias por visitar nuestro proyecto! ✨