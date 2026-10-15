<div align="center">

# Acredittia · Administración del Negocio

**Proyecto APT · Capstone PTY4614 (sección 300D) · Duoc UC, sede San Joaquín**

Backoffice de una plataforma SaaS que acredita a empresas contratistas en faenas mineras:
consola interna de administración, suscripciones, pagos y control de morosidad.

![Fase](https://img.shields.io/badge/fase%20actual-Fase%202-1F3864)
![Pruebas](https://img.shields.io/badge/pruebas-339%20aprobadas-2E7D32)
![Requerimientos](https://img.shields.io/badge/requerimientos-9%20de%2015-F9A825)
![Stack](https://img.shields.io/badge/stack-FastAPI%20%C2%B7%20PostgreSQL%20%C2%B7%20Next.js-2B41B5)

</div>

---

## Contenido

- [Equipo](#equipo)
- [El proyecto](#el-proyecto)
- [Estado del avance](#estado-del-avance)
- [Documentos por fase](#documentos-por-fase)
- [Estructura del repositorio](#estructura-del-repositorio)
- [Tecnologías](#tecnologías)
- [Evidencias del MVP](#evidencias-del-mvp)
- [Repositorios](#repositorios)

---

## Equipo

**Grupo 4** · Carrera de Ingeniería en Informática

| Integrante | Rol en el proyecto |
|---|---|
| **David Martinez** | Modelo de datos, integración y despliegue |
| **Jean Arriagada** | Módulo de administración (API y consola interna) |
| **Oscar Bustamante** | Módulo de suscripciones y pagos |

| | |
|---|---|
| **Docente** | Claudia Reinoso Hurtado |
| **Mandante** | Alloxentric |
| **Contraparte del cliente** | Gonzalo Vera |

---

## El proyecto

**Problema.** En Acredittia, el equipo interno aprueba empresas, mantiene los catálogos, cobra las suscripciones en UF y vigila
el estado de cada cliente a mano. Eso genera lentitud y riesgo: empresas que siguen operando con pagos atrasados o accesos a
datos de un cliente que no quedan registrados.

**Objetivo general.** Desarrollar el backend y el frontend del módulo de administración del negocio de Acredittia, integrando
a la plataforma la gestión de empresas y catálogos, el ciclo de suscripciones y pagos, y una consola interna de administración
con auditoría de accesos.

**Objetivos específicos**

1. Extender el modelo de datos para soportar la consola interna, la auditoría y el ciclo de cobro, manteniendo el aislamiento entre empresas.
2. Desarrollar la API de administración: aprobación de empresas, catálogos, vistas globales y auditoría de accesos con motivo obligatorio.
3. Implementar el ciclo de suscripciones con facturación periódica, conciliación de pagos y solo lectura por morosidad.
4. Desarrollar el frontend: consola interna y pantallas de suscripción, pago y aviso de morosidad del portal.
5. Validar el sistema con pruebas automatizadas y desplegarlo en contenedores Docker en la nube.

**Usuarios.** El equipo interno de Acredittia, en la consola de administración, y las empresas contratistas, en las pantallas
de suscripción y pago del portal.

**Metodología.** Scrum adaptado: sprints de 2 semanas, seguimiento semanal del equipo, reunión semanal con la docente, y
revisión y retrospectiva al cierre de cada sprint. Cada funcionalidad se desarrolla en su rama y se integra a `main` solo si
pasa la suite de pruebas.

---

## Estado del avance

| Fase | Semanas | Estado |
|---|---|---|
| Fase 1 · Definición del proyecto | S1 a S4 | ✅ Completada |
| Fase 2 · Desarrollo del proyecto | S5 a S15 | 🔄 En curso (MVP entregado en la semana 9) |
| Fase 3 · Presentación final | S16 a S18 | ⏳ Pendiente |

**Hitos de verificación**

| Hito | Semana | Estado alcanzado | Estado |
|---|---|---|---|
| H0 | S4 | Propuesta del proyecto aprobada | ✅ Cumplido |
| H1 | S6 | Modelo de datos extendido y migrado | ✅ Cumplido |
| H2 | S9 | MVP desplegado (Hito 1 del mandante) | ✅ Cumplido (publicado con Ngrok) |
| H3 | S11 | Plataforma en Docker y desplegada en la nube | 🔄 Docker listo; Azure y Vercel pendientes |
| H4 | S13 | Sistema integrado y probado | ⏳ Pendiente |
| H5 | S15 | Proyecto documentado (Hito 3 del mandante) | ⏳ Pendiente |
| H6 | S18 | Proyecto presentado | ⏳ Pendiente |

**Lo que ya funciona (semana 9)**

- **Modelo de datos:** esquema en versión 7 con 45 tablas, aislamiento por empresa con seguridad a nivel de fila (RLS).
- **API de administración:** 8 endpoints propios del panel y 20 de la Consola Interna; 7 de los 8 requerimientos de Gonzalo Vera completos.
- **Suscripciones y pagos:** ciclo prueba, activa, morosa y cancelada; facturas en UF; solo lectura tras 7 días de gracia; pasarela de pago simulada.
- **Consola interna:** resumen global, empresas, cobranza, salud de clientes, usuarios, auditoría, accesos, buscador, indicadores y sistemas.
- **Calidad:** 339 pruebas automatizadas aprobadas, 65 de ellas de los módulos propios.

---

## Documentos por fase

### Fase 1 · Definición del proyecto

| Documento | Ubicación |
|---|---|
| Informe del proyecto | [`FASE 1/01_Informe_y_Guia`](FASE%201/01_Informe_y_Guia) |
| Guía 1.5 · Definición del proyecto APT | [`FASE 1/01_Informe_y_Guia`](FASE%201/01_Informe_y_Guia) |
| Autoevaluaciones (1.1) y diarios de reflexión (1.2) | [`FASE 1/02_Autoevaluaciones_y_Diarios`](FASE%201/02_Autoevaluaciones_y_Diarios) |
| Presentación | [`FASE 1/03_Presentacion`](FASE%201/03_Presentacion) |

### Fase 2 · Desarrollo del proyecto

| Documento | Tipo | Ubicación |
|---|---|---|
| Informe de avance Fase 2 | Grupal | [`FASE 2/01_Informe_y_Guia`](FASE%202/01_Informe_y_Guia) |
| Guía 2.4 · Desarrollo del proyecto APT | Grupal | [`FASE 2/01_Informe_y_Guia`](FASE%202/01_Informe_y_Guia) |
| Diario de reflexión 2.1 | Grupal | [`FASE 2/02_Diario_Reflexion_Grupal`](FASE%202/02_Diario_Reflexion_Grupal) |
| Autoevaluación 2.2 | Individual | [`FASE 2/03_Autoevaluaciones`](FASE%202/03_Autoevaluaciones) |
| Presentación del avance | Grupal | [`FASE 2/04_Presentacion`](FASE%202/04_Presentacion) |
| Capturas del MVP e informe de avances del Hito 1 | Evidencias | [`FASE 2/05_Avances_y_Evidencias`](FASE%202/05_Avances_y_Evidencias) |

---

## Estructura del repositorio

```text
proyecto-capstone-acredittia-administracion/
├── FASE 1/
│   ├── 01_Informe_y_Guia/                 Informe del proyecto y Guía 1.5
│   ├── 02_Autoevaluaciones_y_Diarios/     Una carpeta por integrante
│   └── 03_Presentacion/
├── FASE 2/
│   ├── 01_Informe_y_Guia/                 Informe de avance y Guía 2.4
│   ├── 02_Diario_Reflexion_Grupal/        Diario 2.1
│   ├── 03_Autoevaluaciones/               Autoevaluación 2.2, una carpeta por integrante
│   ├── 04_Presentacion/
│   └── 05_Avances_y_Evidencias/           Capturas del MVP e informe de avances del Hito 1
└── README.md
```

---

## Tecnologías

| Capa | Tecnologías |
|---|---|
| Backend | Python 3.12 · FastAPI · Pydantic v2 · SQLAlchemy 2 |
| Base de datos | PostgreSQL 16 con seguridad a nivel de fila (RLS) · scripts SQL versionados |
| Trabajos programados | Celery · Redis |
| Frontend | Next.js 14 · React · TypeScript · Tailwind CSS |
| Entorno y despliegue | Docker Compose (7 servicios) · Ngrok · Azure Container Apps y Vercel (previsto) |
| Pruebas | pytest |

---

## Evidencias del MVP

| Consola: resumen global | Consola: suscripciones y pagos |
|---|---|
| ![Resumen global](FASE%202/05_Avances_y_Evidencias/01_consola_resumen.png) | ![Suscripciones y pagos](FASE%202/05_Avances_y_Evidencias/03_consola_suscripciones.png) |
| **Consola: auditoría** | **Portal: empresa morosa** |
| ![Auditoría](FASE%202/05_Avances_y_Evidencias/04_consola_auditoria.png) | ![Portal de una empresa morosa](FASE%202/05_Avances_y_Evidencias/05_portal_suscripcion.png) |

Las demás capturas (empresas, documentación de la API, modelo de datos y pruebas) están en
[`FASE 2/05_Avances_y_Evidencias`](FASE%202/05_Avances_y_Evidencias).

---

## Repositorios

| Repositorio | Contenido | Acceso |
|---|---|---|
| [proyecto-capstone-acredittia-administracion](https://github.com/Dntex2/proyecto-capstone-acredittia-administracion) | Documentación de Duoc UC por fase (este repositorio) | Público |
| [Acredittia-Administracion](https://github.com/Dntex2/Acredittia-Administracion) | Código del proyecto | Privado |

---

<details>
<summary><b>Ficha inicial del proyecto</b></summary>

<img width="1098" height="1154" alt="Ficha inicial del proyecto" src="https://github.com/user-attachments/assets/3e2dd2f9-f188-49f1-afe5-8101105a914b" />

</details>

<div align="center">
<sub>Duoc UC · Capstone PTY4614 · 2026</sub>
</div>
