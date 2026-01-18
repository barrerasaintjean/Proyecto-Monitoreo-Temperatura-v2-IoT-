# 🌡️ IoT Temperature System V2: De Excel a Infraestructura Inmortal

> **"Donde hay una limitación técnica, hay una oportunidad de optimización"**

## 📝 Visión del Proyecto
Este proyecto nace de la convergencia entre mi experiencia previa en monitoreo térmico y lo aprendido en la **Pipeline de Extracción de Datos (Sector Machas)**. 

La problemática principal era la gestión del volumen de datos: con lecturas cada minuto, generamos **1,440 registros diarios**, una cifra que en un año sería impensable de manejar en un Excel. Aunque la solución fácil sería espaciar las lecturas, optamos por otro camino: migrar los datos a una base de datos profesional. 

A diferencia de proyectos anteriores, la infraestructura ya no depende de un PC convencional. Dado que los datos se suben con alta frecuencia, si el PC se apaga, se pierde esa continuidad. Para solucionar esto, utilicé mi experiencia con **Raspberry Pi** y **Docker** para crear un servidor de bajo consumo que garantiza la disponibilidad de los datos 24/7.

---

## 🛠️ Herramientas Utilizadas
* **Hardware:** Raspberry Pi 4 (4GB RAM), ESP32 y sensores del proyecto pasado.
* **Infraestructura:** Docker (para contenedores aislados y persistentes).
* **Orquestación:** n8n (flujo de automatización vía Webhooks).
* **Base de Datos:** PostgreSQL.
* **Visualización:** Grafana.
---

## 🗂️ Estructura del Repositorio

* ### 📁 `base_de_datos_en_raspberry`
    Información detallada sobre la configuración de la Raspberry Pi y el despliegue de contenedores con Docker.
* ### 📁 `apartado_sensores`
    Código fuente y lógica de captura. Se incluye la base del proyecto pasado con las actualizaciones necesarias en el código para la nueva infraestructura.
* ### 📁 `apartado_graficos`
    Documentación sobre la conexión de la base de datos y la visualización de métricas en tiempo real mediante Grafana.

---

## 🚀 Impacto del Proyecto

* **Eficiencia Energética:** Reducción drástica del consumo eléctrico al migrar la carga de trabajo de un PC convencional a una **Raspberry Pi 4**.
* **Integridad de Datos:** Disponibilidad 24/7 que elimina los "huecos" de información en las gráficas, asegurando una base de datos continua.
* **Capacidad de Análisis:** Transición exitosa de datos planos a una base de datos relacional robusta.

---

## 🏁 Conclusión

> **"Es importante saber cuáles son las limitantes de cada proyecto para saber cómo mejorarlas en el futuro."**

La mejora de este proyecto permite alargar la supervisión de la cámara de frío, facilitando análisis comparativos entre estaciones. La práctica de combinar Docker, Raspberry Pi y bases de datos es una combinación poderosa para bajar el consumo energético y mantener activa la base de datos. Con el tiempo, se podrán sumar más sensores e ir transformando el entorno en una **industria inteligente**.

## 🛠️ El Diagrama de Flujo (Data Journey)

```text
  [ ENTORNO FÍSICO ]           [ SERVIDOR RASPBERRY PI (DOCKER) ]          [ VISUALIZACIÓN ]
  
   🌡️ Sensor Temp/Hum           📥 n8n Webhook (ETL)                 📊 Grafana Dashboard
          |                             |                                     ^
          v                             v                                     |
   🐍 ESP32 / Python   ------>   🐘 PostgreSQL DB      -----------------------+
   (Lectura 1 min)            (Persistencia 24/7)             (Análisis de Tendencias)
