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

1. **Ingesta (Capa Bronze):** Captura de eventos crudos mediante un microservicio "Producer" y almacenamiento persistente para recuperación ante fallos.
2. **Procesamiento (Capa Silver y Gold):**
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
2.  **Configurar Cluster de Kafka:** Levantar los servicios de Kafka para habilitar la ingesta en la capa Bronze.
3.  **Configurar Spark:** Asegurar que los jobs de Spark tengan acceso a los tópicos de Kafka para iniciar el procesamiento Medallion.
4.  **Desplegar API Gateway:** Configurar las rutas de acceso para los WebSockets.
5.  **Prueba de Conexión:** Ejecutar el microservicio "Producer" para validar que los datos fluyen desde la interacción del usuario hasta la Capa Gold.
