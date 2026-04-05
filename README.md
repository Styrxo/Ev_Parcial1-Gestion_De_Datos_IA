# Ev_Parcial1-Gestion_De_Datos_IA


---

## 1. Descripción del proyecto:
Este proyecto consiste en el diseño e implementación de una arquitectura de datos robusta para gestionar un **sistema de nottificaciónes en tiempo real**. El sisetma está diseñado para capturar interacciones de usuarios (likes, comentarios y seguidores) y transformarlos en alertas inmediatas sin comprometer el rendimiento de la plataforma.

**Ojetos clave:**

* **Escalabilidad:** Manejar grandes volúmenes de eventos simultáneos.
* **Flexibilidad:** Adapatarse a cambios funcionales cada dos semanas mediante metodologías ágiles.
* **Baja latencia:** Entrega de notificaciones en milisegundos.

---

## 2. Arquitectura Seleccionada

La solución utiliza un **Pipeline Hibrido Modular**. Está elección permite combinar el procesamiento de flujo (streaming) con una estrucura organizada que garantiza la integridad de los datos.

### Componentes del Flujo de Datos:

1. **Ingesta (Capa Bronze):** Captura de eventos crudos mediante un microservicio "Producer" y almacenamiento persistente para recuperación ante fallos.
2. **Procesamieno (Capa Silver y Gold):**
 * **Silver:** Limpieza, filtrado y validación de tokens.
 * **Gold:** Enriquecimiento y agregación de daos para generar la notificación final lista para el usuario.}
3. **Servicio y Entrega:** Distribución mediante un API Gateway para seguridad y Websockets para mantener una conexión bidireccional activa con el cliente.

---

## 4. Instrucciones de Instalación

1.  **Clonar el repositorio:**
    `git clone https://github.com/Styrxo/Ev_Parcial1-Gestion_De_Datos_IA.git`
2.  **Configurar Cluster de Kafka:** Levantar los servicios de Kafka para habilitar la ingesta en la capa Bronze.
3.  **Configurar Spark:** Asegurar que los jobs de Spark tengan acceso a los tópicos de Kafka para iniciar el procesamiento Medallion.
4.  **Desplegar API Gateway:** Configurar las rutas de acceso para los WebSockets.
5.  **Prueba de Conexión:** Ejecutar el microservicio "Producer" para validar que los datos fluyen desde la interacción del usuario hasta la Capa Gold.
