# Documentación del Trabajo - Parte Kibana

## 👤 Autora
**Marta García Fernández**  
Curso de Especialización en Big Data e Inteligencia Artificial  
IES Al-Ándalus · Curso 2024-2025

---

## 🧭 Objetivo
Desarrollar la parte de visualización del proyecto utilizando **Kibana**, mostrando de forma interactiva:
- Los datos indexados por el scraper (alojamientos en Andalucía)
- Los logs de interacción del chatbot
- La monitorización de los servicios desplegados en la infraestructura Swarm

---

## ⚙️ Funcionalidades implementadas

### 🔍 Visualización de hoteles
- Mapa interactivo con coordenadas geográficas (`geo_point`)
- Precio medio por ciudad
- Puntuación media por tipo de alojamiento
- Conteo de alojamientos por tipo
- Visualización del total de alojamientos
- Filtros por ciudad y tipo

📁 Datos procesados por Logstash desde archivos `.json` generados por el scraper y almacenados en el índice `hoteles`.

---

### 📊 Logs del chatbot
- Tabla con todas las interacciones (pregunta, respuesta, tiempo)
- Métricas de número total de consultas y tiempo medio de respuesta
- Donut con errores vs respuestas exitosas
- Frecuencia de preguntas más comunes

📁 Logs enviados desde Filebeat/Logstash al índice `chatbot-2025.05.27`.

---

### 🛡️ Monitorización del stack ELK
- Uso de CPU, memoria y red por host
- Total de eventos recibidos (`event.dataset`)
- Visualización de servicios activos
- Dashboards por defecto de Metricbeat activados

---

## 📂 Archivos generados/importados

- `dashboards_hoteles_chatbot_clean.ndjson`: Dashboards vacíos predefinidos
- `visualizaciones_completas_elk.ndjson`: Visualizaciones para hoteles y chatbot
- `dashboard_completo_elk.ndjson`: Dashboard completo listo para presentación

---

## 💡 Consideraciones
- El archivo `logstash.conf` fue adaptado para datos tipo array JSON con campos anidados
- Se renombraron coordenadas a `location` y se tipificaron como `geo_point` para usar mapas
- Se solucionaron errores comunes al importar (`strict_dynamic_mapping_exception`) eliminando metadatos conflictivos

---

## ✅ Estado actual

- [x] Dashboards funcionales en entorno local y virtual
- [x] Visualizaciones listas y reutilizables
- [x] Monitorización activa con Metricbeat
- [x] Documentación actualizada

---

## 🖼️ Captura de ejemplo

![Booking Dashboard](./captures/dashboard_booking.png)

---
