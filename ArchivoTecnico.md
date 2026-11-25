<div align="center">
  <!-- Aquí irá el banner o logotipo oficial de OficioYa -->
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
> 🔗 **[Abrir Aplicación Web OficioYa](URL_DEL_FRONTEND_AQUI)**

**OficioYa** conecta de forma directa y equitativa a trabajadores independientes con contratantes locales mediante reputación verificable, gestión de disponibilidad y búsqueda asistida por inteligencia artificial.

---

## 2. Ecosistema de Microservicios

La solución sigue una arquitectura distribuida organizada en **5 dominios funcionales (Squads)** desacoplados:

| Squad | Microservicio(s) | Responsabilidad Principal | Base de Datos / Integración |
| :--- | :--- | :--- | :--- |
| **Squad 1** | **API Gateway & Identity** | Punto único de entrada, validación de JWT, políticas de acceso, registro y 2FA/OTP. | PostgreSQL  |
| **Squad 2** | **User, Worker & Subscription** | Gestión de perfiles, oficios, tarifas, zonas de cobertura y suscripciones Pro. | PostgreSQL  |
| **Squad 3** | **Service Request & Search AI** | Ciclo de vida de solicitudes, agenda de disponibilidad y búsqueda en lenguaje natural. | PostgreSQL |
| **Squad 4** | **Reputation & Notification** | Sistema de calificaciones (1–5 estrellas), reseñas y alertas push en tiempo real. | PostgreSQL / MongoDB / Firebase FCM |
| **Squad 5** | **Reporting & Moderation** | Analítica operativa, auditoría y moderación administrativa de disputas. | PostgreSQL / MongoDB |

---

## 3. Arquitectura del Sistema (C4 y UML)

### Vista General (Nivel 1 y Nivel 2 - Modelo C4)
* **Diagrama de Contexto:** Interacción entre Contratante, Trabajador Independiente, Administrador y servicios externos (Gemini API, Firebase FCM y PSE).
  *(Espacio para imagen: Diagrama de Contexto)*
* **Diagrama de Contenedores:** Topología completa de la SPA, API Gateway, microservicios de los 5 squads y motores de persistencia.
  *(Espacio para imagen: Diagrama de Contenedores)*

### Vista Detallada por Microservicio (Componentes, Clases y Entidad-Relación)
*Haz clic en cada dominio para desplegar sus diagramas internos:*

<details>
<summary><strong>Squad 1: API Gateway (Orchestrator) & Identity Service</strong></summary>
<br>
- **Diagrama de Componentes (C4 Nivel 3):** *(Imagen)*
- **Diagrama de Clases:** *(Imagen)*
- **Diagrama Entidad-Relación (ER):** *(Imagen)*
</details>

<details>
<summary><strong>Squad 2: User Service, Worker Service & Subscription Service</strong></summary>
<br>
- **Diagrama de Componentes (C4 Nivel 3):** *(Imagen)*
- **Diagrama de Clases:** *(Imagen)*
- **Diagrama Entidad-Relación (ER):** *(Imagen)*
</details>

<details>
<summary><strong>Squad 3: Service Request & Search AI Service (Core)</strong></summary>
<br>
- **Diagrama de Componentes (C4 Nivel 3):** *(Imagen)*
- **Diagrama de Clases:** *(Imagen)*
- **Diagrama Entidad-Relación (ER):** *(Imagen)*
</details>

<details>
<summary><strong>Squad 4: Reputation & Notification Service</strong></summary>
<br>
- **Diagrama de Componentes (C4 Nivel 3):** *(Imagen)*
- **Diagrama de Clases:** *(Imagen)*
- **Diagrama Entidad-Relación (ER):** *(Imagen)*
</details>

<details>
<summary><strong>Squad 5: Reporting & Moderation Service</strong></summary>
<br>
- **Diagrama de Componentes (C4 Nivel 3):** *(Imagen)*
- **Diagrama de Clases:** *(Imagen)*
- **Diagrama Entidad-Relación (ER):** *(Imagen)*
</details>

---

## 4. Documentación de APIs (Swagger)

| Microservicio | Documentación Interactiva |
| :--- | :--- |
| **Service Request & Search AI (Principal)** | [Ver Swagger UI](URL_SWAGGER_SERVICE) |
| **API Gateway / Identity Service** | [Ver Swagger UI](URL_SWAGGER_IDENTITY) |
| **User & Worker Service** | [Ver Swagger UI](URL_SWAGGER_WORKER) |
| **Reputation & Notification Service** | [Ver Swagger UI](URL_SWAGGER_REPUTATION) |
| **Reporting & Moderation Service** | [Ver Swagger UI](URL_SWAGGER_REPORTING) |

---

## 5. Infraestructura y Despliegues

Evidencia de integración continua (CI/CD) y ejecución en la nube sobre **Microsoft Azure**:

* **Pipelines de Despliegue (Backend & Frontend):** *(Capturas de GitHub Actions / Azure DevOps en verde)*
* **Recursos Activos en Azure:** *(Capturas del grupo de recursos / contenedores de todos los microservicios operando)*

---

## 6. Gestión Ágil (Scrum + Jira)

Seguimiento de sprints, ceremonias y trazabilidad de historias de usuario durante el desarrollo:

* **Cronograma y Roadmap (Timeline):** *(Captura de pantalla de Jira Timeline)*
* **Tablero de Sprints y Métricas:** *(Captura de pantalla del Dashboard de Jira)*
```[cite: 3, 4, 5]

