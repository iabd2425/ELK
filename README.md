# Proyecto ELK - Chatbot Inteligente

Este repositorio contiene la configuración y recursos necesarios para desplegar un stack **ELK (Elasticsearch, Logstash, Kibana)** complementado con **Metricbeat** para monitorización, como parte del desarrollo de un chatbot que consulta datos indexados en tiempo real.

---

## 📦 Estructura del repositorio

```
ELK/
├── docker-compose.yml        # Orquestación de servicios ELK
├── README.md                 # Documentación del proyecto
├── captures/                 # Capturas de pantallas de dashboards y alertas
├── kibana/
│   ├── dashboards/           # Dashboards en formato NDJSON
│   └── alertas/              # Alertas exportadas de Kibana
├── logstash/
│   ├── pipelines.yml         # Definición de múltiples pipelines
│   └── <nombre_modulo>/      # Configuración individual de Logstash
└── metricbeat/
    ├── metricbeat.yml        # Configuración general de Metricbeat
    └── modules.d/            # Módulos activados (ES, Kibana)
```

---

## 🚀 Puesta en marcha

### 1. Clonar el repositorio
```bash
git clone https://github.com/tu-usuario/ELK.git
cd ELK
```

### 2. Arrancar los servicios (Docker)
```bash
docker-compose up -d
```
Esto iniciará los servicios:
- Elasticsearch: http://localhost:9200
- Kibana: http://localhost:5601

### 3. Parar los servicios
```bash
docker-compose down
```

> ⚠️ Usa siempre `docker-compose up -d` al comenzar tu jornada para tener los servicios activos, y `docker-compose down` al terminar para liberar recursos.

---

## 🔧 Servicios desplegados

### 🔍 Elasticsearch
Motor de búsqueda distribuido que almacena y gestiona los datos estructurados del scraper para que el chatbot pueda consultarlos.

### 📊 Kibana
Interfaz gráfica para crear dashboards interactivos, visualizar logs, métricas del sistema y configurar alertas.

### ⚙️ Logstash
Procesador de datos que recibe la información desde el scraper o ficheros y la transforma antes de enviarla a Elasticsearch.

### 📈 Metricbeat
Agente que monitoriza el estado de los servicios ELK y envía métricas sobre su rendimiento y uso de recursos.

---

## 📋 Importación de dashboards y alertas

1. Accede a Kibana: http://localhost:5601
2. Ve a *Stack Management > Saved Objects*
3. Pulsa "Import" y selecciona los archivos `.ndjson` dentro de `kibana/dashboards/` o `kibana/alertas/`


## 🧠 Recursos útiles

- [Documentación oficial de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/index.html)
- [Documentación de Kibana](https://www.elastic.co/guide/en/kibana/current/index.html)
- [Documentación de Logstash](https://www.elastic.co/guide/en/logstash/current/index.html)
- [Documentación de Metricbeat](https://www.elastic.co/guide/en/beats/metricbeat/current/index.html)

---

## 🤝 Autores

**Equipo de especialización en Big Data e IA**
IES Al-Ándalus · Curso 2024-2025

---

¡Gracias por visitar nuestro proyecto! ✨

