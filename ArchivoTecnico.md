<div align="center">
  <img src="docs/branding/banner-oficioya.png" alt="Banner OficioYa" width="100%">
  <h1>OficioYa — Portal Técnico y de Arquitectura</h1>

  <!-- Navegación rápida -->
  <p>
    <a href="#1-acceso-a-la-aplicación">Aplicación</a> •
    <a href="#2-ecosistema-de-microservicios">Microservicios</a> •
    <a href="#3-arquitectura-del-sistema-c4-y-uml">Arquitectura y Diagramas</a> •
    <a href="#4-documentación-de-apis-swagger">APIs (Swagger)</a> •
    <a href="#5-infraestructura-y-despliegues">Despliegues</a> •
    <a href="#6-gestión-ágil-scrum--jira">Gestión Scrum</a>
  </p>
</div>

---

## 1. Acceso a la Aplicación

> [!IMPORTANT]
> **Entorno Productivo:** Puedes explorar la plataforma funcional directamente desde el siguiente enlace:
> 🔗 **[Abrir Aplicación Web OficioYa]([URL_DEL_FRONTEND_AQUI](https://oficioya-front-app-egh6gjc3b0aearhq.chilecentral-01.azurewebsites.net))**

**OficioYa** conecta de forma directa y equitativa a trabajadores independientes con contratantes locales mediante reputación verificable y gestión de disponibilidad.

---

## 2. Ecosistema de Microservicios

La solución sigue una arquitectura distribuida organizada en **5 dominios funcionales (Squads)** desacoplados:

| Squad | Microservicio(s) | Responsabilidad Principal | Base de Datos / Integración |
| :--- | :--- | :--- | :--- |
| **Squad 1** | **API Gateway & Identity** | Punto único de entrada, validación de JWT, políticas de acceso, registro y 2FA/OTP. | PostgreSQL |
| **Squad 2** | **User, Worker & Subscription** | Gestión de perfiles, oficios, tarifas, zonas de cobertura y suscripciones Pro. | PostgreSQL |
| **Squad 3** | **Service Request** | Ciclo de vida de solicitudes y agenda de disponibilidad. | PostgreSQL |
| **Squad 4** | **Reputation & Notification** | Sistema de calificaciones (1–5 estrellas), reseñas y alertas push en tiempo real. | PostgreSQL / MongoDB / Firebase FCM |
| **Squad 5** | **Reporting & Moderation** | Analítica operativa, auditoría y moderación administrativa de disputas. | PostgreSQL / MongoDB |

---

## 3. Arquitectura del Sistema (C4 y UML)

### Vista General (Nivel 1 y Nivel 2 - Modelo C4)
* **Diagrama de Contexto:** Interacción entre Contratante, Trabajador Independiente, Administrador y servicios externos (Gemini API, Firebase FCM y PSE).

  ![Diagrama de Contexto](docs/arquitectura/general/01-c4-contexto.png)

* **Diagrama de Contenedores:** Topología completa de la SPA, API Gateway, microservicios de los 5 squads y motores de persistencia.

  ![Diagrama de Contenedores](docs/arquitectura/general/02-c4-contenedores.png)

### Vista Detallada por Microservicio (Componentes, Clases y Entidad-Relación)
*Haz clic en cada dominio para desplegar sus diagramas internos:*

<details>
<summary><strong>Squad 1: API Gateway (Orchestrator) & Identity Service</strong></summary>
<br>

- **Diagrama de Componentes - API Gateway (C4 Nivel 3):**
  ![Componentes Gateway](docs/arquitectura/squad-1-gateway-identity/componentes-gateway.png)

- **Diagrama de Componentes - Identity Service (C4 Nivel 3):**
  ![Componentes Identity](docs/arquitectura/squad-1-gateway-identity/componentes-identity.png)

- **Diagrama de Clases:**
  ![Clases Identity](docs/arquitectura/squad-1-gateway-identity/clases-identity.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Identity](docs/arquitectura/squad-1-gateway-identity/er-identity.png)
</details>

<details>
<summary><strong>Squad 2: User Service, Worker Service & Subscription Service</strong></summary>
<br>

- **Diagrama de Componentes (C4 Nivel 3):**
  ![Componentes Users & Workers](docs/arquitectura/squad-2-users-workers/componentes-users-workers.png)

- **Diagrama de Clases:**
  ![Clases Users & Workers](docs/arquitectura/squad-2-users-workers/clases-users-workers.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Users & Workers](docs/arquitectura/squad-2-users-workers/er-users-workers.png)
</details>

<details>
<summary><strong>Squad 3: Service Request Service (Core)</strong></summary>
<br>

- **Diagrama de Componentes (C4 Nivel 3):**
  ![Componentes Services](docs/arquitectura/squad-3-services/componentes-services.png)

- **Diagrama de Clases (Core):**
  ![Clases Services](docs/arquitectura/squad-3-services/clases-services.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Services](docs/arquitectura/squad-3-services/er-services.png)
</details>

<details>
<summary><strong>Squad 4: Reputation & Notification Service</strong></summary>
<br>

- **Diagrama de Componentes (C4 Nivel 3):**
  ![Componentes Reputation & Notifications](docs/arquitectura/squad-4-reputation-notifications/componentes-reputation-notif.png)

- **Diagrama de Clases:**
  ![Clases Reputation & Notifications](docs/arquitectura/squad-4-reputation-notifications/clases-reputation-notif.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Reputation & Notifications](docs/arquitectura/squad-4-reputation-notifications/er-reputation-notif.png)
</details>

<details>
<summary><strong>Squad 5: Reporting & Moderation Service</strong></summary>
<br>

- **Diagrama de Componentes (C4 Nivel 3):**
  ![Componentes Reporting & Moderation](docs/arquitectura/squad-5-reporting-moderation/componentes-reporting-mod.png)

- **Diagrama de Clases:**
  ![Clases Reporting & Moderation](docs/arquitectura/squad-5-reporting-moderation/clases-reporting-mod.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Reporting & Moderation](docs/arquitectura/squad-5-reporting-moderation/er-reporting-mod.png)
</details>

---

## 4. Documentación de APIs (Swagger)

| Microservicio | Documentación Interactiva | Respaldo Visual |
| :--- | :--- | :--- |
| **Service Request** | [Ver Swagger UI](URL_SWAGGER_SERVICE) | [Ver Captura](docs/swagger-respaldo/swagger-service-core.png) |
| **API Gateway / Identity Service** | [Ver Swagger UI](URL_SWAGGER_IDENTITY) | [Ver Captura](docs/swagger-respaldo/swagger-gateway-identity.png) |
| **User & Worker Service** | [Ver Swagger UI](URL_SWAGGER_WORKER) | [Ver Captura](docs/swagger-respaldo/swagger-users-workers.png) |
| **Reputation & Notification Service** | [Ver Swagger UI](URL_SWAGGER_REPUTATION) | [Ver Captura](docs/swagger-respaldo/swagger-reputation-notif.png) |
| **Reporting & Moderation Service** | [Ver Swagger UI](URL_SWAGGER_REPORTING) | [Ver Captura](docs/swagger-respaldo/swagger-reporting-mod.png) |

---

## 5. Infraestructura y Despliegues

Evidencia de integración continua (CI/CD) y ejecución en la nube sobre **Microsoft Azure**:

* **Pipelines de Despliegue (Backend & Frontend):**
  - *Pipeline Backend:*
    ![Pipeline Backend](docs/despliegues/pipeline-ci-cd-backend.png)
  - *Pipeline Frontend:*
    ![Pipeline Frontend](docs/despliegues/pipeline-ci-cd-frontend.png)
* **Recursos Activos en Azure:**
  ![Recursos Activos en Azure](docs/despliegues/azure-recursos-activos.png)

---

## 6. Gestión Ágil (Scrum + Jira)

Seguimiento de sprints, ceremonias y trazabilidad de historias de usuario durante el desarrollo:

* **Cronograma y Roadmap (Timeline):**
  ![Cronograma y Roadmap Jira](docs/scrum-jira/jira-timeline-cronograma.png)
* **Tablero de Sprint:**
  ![Tablero de Sprint Jira](docs/scrum-jira/jira-tablero-sprint.png)
* **Dashboard y Métricas:**
  ![Dashboard de Métricas Jira](docs/scrum-jira/jira-dashboard-metricas.png)
