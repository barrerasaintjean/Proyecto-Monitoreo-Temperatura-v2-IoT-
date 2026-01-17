# 🌡️ IoT Temperature System V2: De Excel a Infraestructura Inmortal

> **"La evolución de un sensor: De la fragilidad del Excel a la robustez del Open Source Stack."**

## 📝 Visión del Proyecto
Este proyecto nace de la convergencia entre mi experiencia previa en monitoreo térmico y lo aprendido en la **Pipeline de Extracción de Datos (Sector Machas)**. La problemática inicial era crítica: la volatilidad de los datos, la falta de escalabilidad de los archivos planos (.xlsx) y la dependencia de mantener un PC de escritorio encendido 24/7.

Para solucionar esto, decidí utilizar mi experiencia con **Raspberry Pi** y **Docker** para crear un servidor de bajo consumo que garantiza la disponibilidad de los datos en cualquier momento y lugar.

---
## 🗂️ Estructura del Repositorio

### 📁 `base_de_datos_en_raspberry`
*Documentación técnica sobre la configuración del entorno servidor.*

* **Persistencia:** Implementación de volúmenes de **Docker** para garantizar la integridad de los datos ante reinicios o fallos de energía.
* **Escalabilidad:** Arquitectura diseñada para soportar el crecimiento modular de múltiples nodos sensores.
* **Acceso Remoto:** Configuración de túneles o VPN para el monitoreo ubicuo del servidor desde cualquier red externa.

### 📁 `apartado_sensores`
*Lógica de captura y despliegue de hardware.*

* **Configuración ESP32:** Código fuente optimizado para microcontroladores bajo el framework de Arduino/C++.
* **Protocolos:** Pipeline de comunicación mediante peticiones **HTTP/JSON** dirigidas a flujos de automatización en **n8n**.
* **Hardware:** Esquemas de conexión física, diagramas de pines y especificaciones de los sensores utilizados.

### 📁 `apartado_graficos`
*El "front-end" de los datos y capa analítica.*

* **Grafana:** Dashboards dinámicos con visualización avanzada.
* **Análisis:** Configuración de métricas históricas, cálculo de promedios y sistemas de alertas ante anomalías térmicas.

## 🛠️ El Diagrama de Flujo (Data Journey)

```text
  [ ENTORNO FÍSICO ]          [ SERVIDOR RASPBERRY PI (DOCKER) ]          [ VISUALIZACIÓN ]
  
   🌡️ Sensor Temp/Hum              📥 n8n Webhook (ETL)                  📊 Grafana Dashboard
          |                             |                                     ^
          v                             v                                     |
   🐍 ESP32 / Python   ------>   🐘 PostgreSQL DB      -----------------------+
   (Lectura 1 min)            (Persistencia 24/7)             (Análisis de Tendencias)

---

## 🚀 Impacto del Proyecto

* **Eficiencia Energética:** Reducción drástica del consumo eléctrico al migrar la carga de trabajo de un PC convencional a una **Raspberry Pi 4**.
* **Integridad de Datos:** Disponibilidad 24/7 que elimina los "huecos" de información en las gráficas, asegurando una base de datos continua.
* **Capacidad de Análisis:** Transición estratégica de reportes estáticos en Excel hacia un **dashboard profesional interactivo** con capacidad de respuesta inmediata.

---

## 🏁 Conclusión

> "No solo capturo el dato, aseguro su existencia y lo transformo en valor estratégico."

Este proyecto demuestra que la tecnología es el mejor aliado de la estrategia comercial. Al eliminar las barreras de infraestructura, el sistema permite pasar de **"ver datos del pasado"** a **"monitorear el presente"** en tiempo real. Esta arquitectura no solo soluciona el control térmico actual, sino que funciona como una **Prueba de Concepto (PoC)** escalable para cualquier sistema de inteligencia de negocios futuro.
