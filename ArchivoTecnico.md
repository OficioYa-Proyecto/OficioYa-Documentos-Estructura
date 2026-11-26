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
> 🔗 <a href="https://oficioya-front-app-egh6gjc3b0aearhq.chilecentral-01.azurewebsites.net" target="_blank" rel="noopener noreferrer"><strong>Abrir Aplicación Web OficioYa</strong></a>

**OficioYa** conecta de forma directa y equitativa a trabajadores independientes con contratantes locales mediante reputación verificable y gestión de disponibilidad.

---

## 2. Ecosistema de Microservicios

La solución sigue una arquitectura distribuida organizada en **5 dominios funcionales (Squads)** desacoplados:

| Squad | Microservicio(s) | Responsabilidad Principal | Base de Datos / Integración |
| :--- | :--- | :--- | :--- |
| **Squad 1** | **Orchestrator & Identity** | Punto único de entrada (API Gateway), validación de JWT, políticas de acceso, autenticación y registro. | PostgreSQL |
| **Squad 2** | **Users** | Gestión de usuarios, perfiles de contratantes, datos de contacto y administración de cuentas. | PostgreSQL |
| **Squad 3** | **Workers** | Perfiles profesionales, catálogo de oficios, tarifas estimadas, cobertura por zonas y fotos de trabajos. | PostgreSQL |
| **Squad 4** | **Service Request & Notification** | Ciclo de vida de solicitudes de servicio, agenda de disponibilidad y envío de alertas push y correos. | PostgreSQL / Firebase FCM / Gmail |
| **Squad 5** | **Search, Reputation & Reporting** | Búsqueda y filtrado de trabajadores, sistema de reputación/calificaciones y analítica/reportes para administradores. | PostgreSQL (Reputation) / En memoria (Search y Reporting) |

---

## 3. Arquitectura del Sistema (C4 y UML)

### Vista General (Nivel 1 y Nivel 2 - Modelo C4)
* **Diagrama de Contexto:** Interacción entre Cliente (Contratante), Trabajador Independiente, Administrador y servicios externos de notificación (Firebase y Gmail).

  ![Diagrama de Contexto](docs/arquitectura/general/01-c4-contexto.png)

* **Diagrama de Contenedores:** Topología completa de la SPA, API Gateway, microservicios de los 5 squads y motores de persistencia.

  ![Diagrama de Contenedores](docs/arquitectura/general/02-c4-contenedores.png)

### Vista Detallada por Microservicio (Componentes, Clases y Entidad-Relación)
*Haz clic en cada dominio para desplegar sus diagramas internos:*

<details>
<summary><strong>Squad 1: Orchestrator (API Gateway) & Identity Service</strong></summary>
<br>

- **Diagrama de Componentes - Orchestrator (C4 Nivel 3):**
  ![Componentes Orchestrator](docs/arquitectura/squad-1-orchestrator-identity/componentes-orchestrator.png)

- **Diagrama de Componentes - Identity Service (C4 Nivel 3):**
  ![Componentes Identity](docs/arquitectura/squad-1-orchestrator-identity/componentes-identity.png)

- **Diagrama de Clases:**
  ![Clases Identity](docs/arquitectura/squad-1-orchestrator-identity/clases-identity.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Identity](docs/arquitectura/squad-1-orchestrator-identity/er-identity.png)
</details>

<details>
<summary><strong>Squad 2: User Service</strong></summary>
<br>

- **Diagrama de Componentes (C4 Nivel 3):**
  ![Componentes Users](docs/arquitectura/squad-2-users/componentes-users.png)

- **Diagrama de Clases:**
  ![Clases Users](docs/arquitectura/squad-2-users/clases-users.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Users](docs/arquitectura/squad-2-users/er-users.png)
</details>

<details>
<summary><strong>Squad 3: Worker Service</strong></summary>
<br>

- **Diagrama de Componentes (C4 Nivel 3):**
  ![Componentes Workers](docs/arquitectura/squad-3-workers/componentes-workers.png)

- **Diagrama de Clases:**
  ![Clases Workers](docs/arquitectura/squad-3-workers/clases-workers.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Workers](docs/arquitectura/squad-3-workers/er-workers.png)
</details>

<details>
<summary><strong>Squad 4: Service Request & Notification Service</strong></summary>
<br>

- **Diagrama de Componentes - Service Request (C4 Nivel 3):**
  ![Componentes Service Request](docs/arquitectura/squad-4-service-notification/componentes-service.png)

- **Diagrama de Componentes - Notification Service (C4 Nivel 3):**
  ![Componentes Notification](docs/arquitectura/squad-4-service-notification/componentes-notification.png)

- **Diagrama de Clases:**
  ![Clases Service & Notification](docs/arquitectura/squad-4-service-notification/clases-service-notif.png)

- **Diagrama Entidad-Relación (ER):**
  ![ER Service & Notification](docs/arquitectura/squad-4-service-notification/er-service-notif.png)
</details>

<details>
<summary><strong>Squad 5: Search, Reputation & Reporting Services</strong></summary>
<br>

- **Diagrama de Contenedores del Squad:**
  ![Contenedores Squad 5](docs/arquitectura/squad-5-search-reputation-reporting/contenedores-squad5.png)

- **Diagramas de Componentes (C4 Nivel 3):**
  - *Search Service:*
    ![Componentes Search](docs/arquitectura/squad-5-search-reputation-reporting/componentes-search.png)
  - *Reputation Service:*
    ![Componentes Reputation](docs/arquitectura/squad-5-search-reputation-reporting/componentes-reputation.png)
  - *Reporting Service:*
    ![Componentes Reporting](docs/arquitectura/squad-5-search-reputation-reporting/componentes-reporting.png)

- **Diagramas de Clases:**
  - *Search Service:*
    ![Clases Search](docs/arquitectura/squad-5-search-reputation-reporting/clases-search.png)
  - *Reputation Service:*
    ![Clases Reputation](docs/arquitectura/squad-5-search-reputation-reporting/clases-reputation.png)
  - *Reporting Service:*
    ![Clases Reporting](docs/arquitectura/squad-5-search-reputation-reporting/clases-reporting.png)

- **Diagrama Entidad-Relación (ER):**
  - *Reputation Service:*
    ![ER Reputation](docs/arquitectura/squad-5-search-reputation-reporting/er-reputation.png)
  *(Nota: Search y Reporting operan como servicios en memoria sin base de datos propia, consultando a otros dominios en tiempo real).*
</details>

---

## 4. Documentación de APIs (Swagger)

| Microservicio | Squad | Documentación Interactiva | Respaldo Visual |
| :--- | :---: | :--- | :--- |
| **Orchestrator & Identity** | Squad 1 | [Ver Swagger UI](URL_SWAGGER_SQUAD1) | [Ver Captura](docs/swagger-respaldo/swagger-orchestrator-identity.png) |
| **Users** | Squad 2 | [Ver Swagger UI](URL_SWAGGER_USERS) | [Ver Captura](docs/swagger-respaldo/swagger-users.png) |
| **Workers** | Squad 3 | [Ver Swagger UI](URL_SWAGGER_WORKERS) | [Ver Captura](docs/swagger-respaldo/swagger-workers.png) |
| **Service Request** | Squad 4 | [Ver Swagger UI](URL_SWAGGER_SERVICE) | [Ver Captura](docs/swagger-respaldo/swagger-service.png) |
| **Notification** | Squad 4 | [Ver Swagger UI](URL_SWAGGER_NOTIFICATION) | [Ver Captura](docs/swagger-respaldo/swagger-notification.png) |
| **Search** | Squad 5 | [Ver Swagger UI](https://oficioya-search-atgjh5gdfcb5b8h3.mexicocentral-01.azurewebsites.net/swagger-ui/index.html) | [Ver Captura](docs/swagger-respaldo/swagger-search.png) |
| **Reputation** | Squad 5 | [Ver Swagger UI](https://oficioya-reputation-bggabfhkdvaqh4bw.mexicocentral-01.azurewebsites.net/swagger-ui/index.html) | [Ver Captura](docs/swagger-respaldo/swagger-reputation.png) |
| **Reporting** | Squad 5 | [Ver Swagger UI](https://oficioya-reporting-hvehegasb3hrarc9.mexicocentral-01.azurewebsites.net/swagger-ui/index.html) | [Ver Captura](docs/swagger-respaldo/swagger-reporting.png) |

---

## 5. Infraestructura y Despliegues

Cada dominio funcional cuenta con despliegue independiente sobre **Microsoft Azure** y flujos automatizados de integración y entrega continua (**CI/CD**) por repositorio:

| Dominio / Capa | Servicio(s) Desplegado(s) | Proveedor Cloud | Estado |
| :--- | :--- | :---: | :---: |
| **Frontend** | Web App (React + TypeScript) | Microsoft Azure | Activo |
| **Squad 1** | Orchestrator (API Gateway) & Identity Service | Microsoft Azure | Activo |
| **Squad 2** | User Service | Microsoft Azure | Activo |
| **Squad 3** | Worker Service | Microsoft Azure | Activo |
| **Squad 4** | Service Request & Notification Service | Microsoft Azure | Activo |
| **Squad 5** | Search, Reputation & Reporting Services | Microsoft Azure | Activo |

*Haz clic en cada bloque para verificar la evidencia en Azure y su pipeline CI/CD:*

<details>
<summary><strong>Frontend — Web App (React + TypeScript)</strong></summary>
<br>

- **Recurso activo en Azure:**
  ![Azure Frontend](docs/despliegues/azure-frontend.png)
- **Pipeline de despliegue (CI/CD):**
  ![Pipeline Frontend](docs/despliegues/pipeline-frontend.png)
</details>

<details>
<summary><strong>Squad 1 — Orchestrator & Identity Service</strong></summary>
<br>

- **Recursos activos en Azure:**
  ![Azure Squad 1](docs/despliegues/azure-squad1-orchestrator-identity.png)
- **Pipeline de despliegue (CI/CD):**
  ![Pipeline Squad 1](docs/despliegues/pipeline-squad1-orchestrator-identity.png)
</details>

<details>
<summary><strong>Squad 2 — User Service</strong></summary>
<br>

- **Recursos activos en Azure:**
  ![Azure Squad 2](docs/despliegues/azure-squad2-users.png)
- **Pipeline de despliegue (CI/CD):**
  ![Pipeline Squad 2](docs/despliegues/pipeline-squad2-users.png)
</details>

<details>
<summary><strong>Squad 3 — Worker Service</strong></summary>
<br>

- **Recursos activos en Azure:**
  ![Azure Squad 3](docs/despliegues/azure-squad3-workers.png)
- **Pipeline de despliegue (CI/CD):**
  ![Pipeline Squad 3](docs/despliegues/pipeline-squad3-workers.png)
</details>

<details>
<summary><strong>Squad 4 — Service Request & Notification Service</strong></summary>
<br>

- **Recursos activos en Azure:**
  ![Azure Squad 4](docs/despliegues/azure-squad4-service-notif.png)
- **Pipeline de despliegue (CI/CD):**
  ![Pipeline Squad 4](docs/despliegues/pipeline-squad4-service-notif.png)
</details>

<details>
<summary><strong>Squad 5 — Search, Reputation & Reporting Services</strong></summary>
<br>

- **Recursos activos en Azure:**
  ![Azure Squad 5](docs/despliegues/azure-squad5-search-reputation-reporting.png)
- **Pipelines de despliegue (CI/CD):**
  - *Pipeline Search:*
    ![Pipeline Search](docs/despliegues/pipeline-squad5-search.png)
  - *Pipeline Reputation:*
    ![Pipeline Reputation](docs/despliegues/pipeline-squad5-reputation.png)
  - *Pipeline Reporting:*
    ![Pipeline Reporting](docs/despliegues/pipeline-squad5-reporting.png)
</details>

---

## 6. Gestión Ágil (Scrum + Jira)

Seguimiento de sprints, ceremonias y trazabilidad de historias de usuario durante el desarrollo:

* **Cronograma y Roadmap (Timeline):**
  ![Cronograma y Roadmap Jira](docs/scrum-jira/jira-timeline-cronograma.png)
* **Tablero de Sprint:**
  ![Tablero de Sprint Jira](docs/scrum-jira/jira-tablero-sprint.png)
* **Dashboard y Métricas:**
  ![Dashboard de Métricas Jira](docs/scrum-jira/jira-dashboard-metricas.png)
