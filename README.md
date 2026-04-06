# Ev_Parcial1-Gestion_De_Datos_IA


---

## 1. Descripción del proyecto:
Este proyecto consiste en el diseño e implementación de una arquitectura de datos robusta para gestionar un **sistema de notificaciónes en tiempo real**. El sistema está diseñado para capturar interacciones de usuarios (likes, comentarios y seguidores) y transformarlos en alertas inmediatas sin comprometer el rendimiento de la plataforma.

**Objetos clave:**

* **Escalabilidad:** Manejar grandes volúmenes de eventos simultáneos.
* **Flexibilidad:** Adaptarse a cambios funcionales cada dos semanas mediante metodologías ágiles.
* **Baja latencia:** Entrega de notificaciones en milisegundos.

---

## 2. Arquitectura Seleccionada

La solución utiliza un **Pipeline Híbrido Modular**. Está elección permite combinar el procesamiento de flujo (streaming) con una estructura organizada que garantiza la integridad de los datos.

### Componentes del Flujo de Datos:

1. **Ingesta (Apache Kafka):** Captura de eventos crudos mediante un microservicio "Producer" y almacenamiento persistente para recuperación ante fallos. Es un sistema de mensajería tipo pub/sub que captura miles de eventos por segundo con baja latencia en tiempo real. Además, asegura que los datos no se pierdan si un componente del pipeline falla o se actualiza.

2. **Procesamiento (Capa Bronze, Silver y Gold):**
 * **Bronze:** La capa Bronze almacena los datos crudos e históricos de la red social tal como llegan de la fuente. Su función es asegurar la persistencia y permitir el re-procesamiento de la información si las reglas del negocio cambian cada 15 días.
 * **Silver:** Limpieza, filtrado y validación de tokens.
 * **Gold:** Enriquecimiento y agregación de datos para generar la notificación final lista para el usuario.
3. **Servicio y Entrega:** Distribución mediante un API Gateway para seguridad y Websockets para mantener una conexión bidireccional activa con el cliente.

---

## 3. Requisitos y Configuración del Entorno Técnico
Para desplegar y desarrollar este proyecto, el desarrollador debe contar con las siguientes herramientas:

* **Apache Kafka:** Motor de mensajería para la ingesta y persistencia temporal.
* **Apache Spark:** Motor de procesamiento distribuido para las transformaciones de las capas Silver y Gold.
* **WebSockets:** Para la comunicación en tiempo real entre el servidor y la aplicación.
* **API Gateway:** Para la centralización de seguridad y gestión de microservicios.
* **Firebase / APNs:** Integración opcional mencionada para el envío de notificaciones Push a dispositivos móviles.
* **Docker (Recomendado):** Para la orquestación de contenedores de Kafka y Spark.
* **Git:** Para el control de versiones del código fuente.

---

## 4. Instrucciones de Instalación

1.  **Clonar el repositorio:**
    `git clone https://github.com/Styrxo/Ev_Parcial1-Gestion_De_Datos_IA.git`
2.  **Copiar el ReadMe.md y configurarlo en base a tu propio proyecto.**

