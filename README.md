<div align="center">

# Acredittia · Administración del Negocio

**Proyecto APT · Capstone PTY4614 (sección 300D) · Duoc UC, sede San Joaquín**

Backoffice de una plataforma SaaS que acredita a empresas contratistas en faenas mineras:
consola interna de administración, suscripciones, pagos y control de morosidad.

![Fase](https://img.shields.io/badge/fase%20actual-Fase%202-1F3864)
![Pruebas](https://img.shields.io/badge/pruebas-366%20casos-2E7D32)
![Requerimientos](https://img.shields.io/badge/requerimientos-11%20de%2015-F9A825)
![Stack](https://img.shields.io/badge/stack-FastAPI%20%C2%B7%20PostgreSQL%20%C2%B7%20Next.js-2B41B5)
![Despliegue](https://img.shields.io/badge/despliegue-Azure%20%C2%B7%20Vercel-0078D4)

**[Ver la plataforma en línea](https://acredittia-administracion.vercel.app)**

</div>

---

## Contenido

- [Equipo](#equipo)
- [El proyecto](#el-proyecto)
- [Estado del avance](#estado-del-avance)
- [Documentos por fase](#documentos-por-fase)
- [Estructura del repositorio](#estructura-del-repositorio)
- [Tecnologías](#tecnologías)
- [Despliegue](#despliegue)
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
| Fase 2 · Desarrollo del proyecto | S5 a S15 | 🔄 En curso (MVP entregado en la semana 9; módulo integrado y desplegado en la nube) |
| Fase 3 · Presentación final | S16 a S18 | ⏳ Pendiente |

**Hitos de verificación**

| Hito | Semana | Estado alcanzado | Estado |
|---|---|---|---|
| H0 | S4 | Propuesta del proyecto aprobada | ✅ Cumplido |
| H1 | S6 | Modelo de datos extendido y migrado | ✅ Cumplido |
| H2 | S9 | MVP desplegado (Hito 1 del mandante) | ✅ Cumplido (publicado con Ngrok) |
| H3 | S11 | Plataforma en Docker y desplegada en la nube | ✅ Cumplido (backend en Azure, frontend en Vercel) |
| H4 | S13 | Sistema integrado y probado | ✅ Cumplido (cinco rondas de control de calidad, todas fusionadas en `main`) |
| H5 | S15 | Proyecto documentado (Hito 3 del mandante) | 🔄 En curso (documentación técnica y de integración en el repositorio de entrega; manuales pendientes) |
| H6 | S18 | Proyecto presentado | ⏳ Pendiente |

**Lo que ya funciona (actualizado al 29 de octubre de 2026)**

- **Modelo de datos:** esquema en versión 7 con 45 tablas, aislamiento por empresa con seguridad a nivel de fila (RLS).
- **API de administración:** 10 endpoints propios del panel (`/admin/panel` y el rubro de la empresa) y 20 de la Consola Interna.
- **Suscripciones y pagos:** ciclo prueba, activa, morosa y cancelada; facturas en UF; solo lectura tras 7 días de gracia; una empresa morosa no puede cancelar; pasarela de pago simulada.
- **Consola interna:** resumen global, empresas, cobranza y gestión de planes, salud de clientes, usuarios, auditoría, accesos, buscador, catálogos (faenas, plataformas y plantillas), indicadores y sistemas.
- **Seguridad y auditoría:** acceso del administrador a una empresa solo con motivo registrado (vigente 8 horas), bloqueo tras 5 ingresos fallidos en 15 minutos y registro de ingresos, descargas, búsquedas y cambios de catálogo.
- **Módulo enchufable:** el código de las contratistas queda igual a la entrega de Alloxentric salvo las líneas de conexión, para que otros equipos puedan integrarlo.
- **Calidad:** 366 casos de prueba automatizados del backend, con cinco rondas de control de calidad.
- **Despliegue en la nube:** backend en Azure Container Apps y frontend en Vercel, con datos de demostración cargados.

**Requerimientos (15 en total: 8 del cliente y 7 del portal y la ficha del proyecto)**

| N.º | Requerimiento | Estado |
|---|---|---|
| 1 | Dashboard global | ✅ Terminado |
| 2 | Gestión global de empresas | ✅ Terminado |
| 3 | Buscador global | ✅ Terminado |
| 4 | Métricas SaaS | 🔄 Parcial (falta el tiempo de uso) |
| 5 | Alertas y salud de clientes | ✅ Terminado |
| 6 | Usuarios, roles y permisos | ✅ Terminado |
| 7 | Auditoría y trazabilidad | ✅ Terminado |
| 8 | Seguridad y aislamiento | ✅ Terminado |
| 9 | Inicio de sesión y aprobación de cuentas | ✅ Terminado |
| 10 | Control de morosidad | ✅ Terminado |
| 11 | Sistema de pagos | 🔄 Parcial (pasarela simulada) |
| 12 | Facturación | 🔄 Parcial (existe la descarga, pero nada genera el PDF de la factura) |
| 13 | Gestión de planes | ✅ Terminado (pantalla en la consola) |
| 14 | Catálogos globales | ✅ Terminado (pantalla Catálogos) |
| 15 | Notificación por correo | ⏳ Pendiente |

---

## Documentos por fase

### Fase 1 · Definición del proyecto

| Documento | Ubicación |
|---|---|
| Autoevaluación de competencias (1.1) y diario de reflexión (1.2), por integrante | [`Fase 1/Evidencias Individuales`](Fase%201/Evidencias%20Individuales) |
| Presentación, Guía 1.5 e informe del proyecto | [`Fase 1/Evidencias Grupales`](Fase%201/Evidencias%20Grupales) |

### Fase 2 · Desarrollo del proyecto

| Documento | Tipo | Ubicación |
|---|---|---|
| Diario de reflexión 2.1 y autoevaluación 2.2 | Individual | [`Fase 2/Evidencias Individuales`](Fase%202/Evidencias%20Individuales) |
| Guía 2.4, Guía 2.6, informe de avance, informe final y diario grupal | Grupal | [`Fase 2/Evidencias Grupales`](Fase%202/Evidencias%20Grupales) |
| Presentación del proyecto | Proyecto | [`Fase 2/Evidencias Proyecto`](Fase%202/Evidencias%20Proyecto) |
| Informe de avances del Hito 1 (al 15 de octubre) y documentación de la API | Proyecto | [`Fase 2/Evidencias Proyecto/Evidencias de documentación`](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n) |
| Capturas de la aplicación y del modelo de datos | Proyecto | [`Fase 2/Evidencias Proyecto/Evidencias de sistema`](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20sistema) |

---

## Estructura del repositorio

```text
proyecto-capstone-acredittia-administracion/
├── Fase 1/
│   ├── Evidencias Individuales/           Apellido_Nombre_1.x_APT122_...
│   └── Evidencias Grupales/               Presentación, Guía 1.5 e informe
├── Fase 2/
│   ├── Evidencias Individuales/           Apellido_Nombre_2.x_APT122_...
│   ├── Evidencias Grupales/               Guías 2.4 y 2.6, informes de avance y final, diario grupal
│   └── Evidencias Proyecto/
│       ├── Presentación Proyecto.pptx
│       ├── Evidencias de documentación/
│       └── Evidencias de sistema/
│           ├── Aplicación/
│           └── Base de datos/
└── README.md
```

---

## Tecnologías

| Capa | Tecnologías |
|---|---|
| Backend | Python 3.12 · FastAPI · Pydantic v2 · SQLAlchemy 2 |
| Base de datos | PostgreSQL 16 con seguridad a nivel de fila (RLS) · scripts SQL versionados |
| Trabajos programados | Celery · Redis |
| Frontend | Next.js 15 · React 19 · TypeScript · Tailwind CSS |
| Entorno y despliegue | Docker Compose (7 servicios) · Azure Container Apps · Vercel · Ngrok (MVP) |
| Pruebas | pytest |

---

## Despliegue

| Componente | Plataforma | Dirección |
|---|---|---|
| Frontend (portal y consola) | Vercel | [acredittia-administracion.vercel.app](https://acredittia-administracion.vercel.app) · consola en [`/ops/login`](https://acredittia-administracion.vercel.app/ops/login) |
| API, trabajos programados y base de datos | Azure Container Apps · Azure Database for PostgreSQL · Redis | Se accede a través del frontend |

El frontend reenvía las llamadas a la API desde su mismo dominio, así que el navegador solo habla con Vercel. La infraestructura
de Azure se crea y actualiza con scripts del repositorio de código, y los datos de demostración se cargan con un job.

> Para no consumir el crédito de Azure for Students, el backend se apaga entre demostraciones. Si la plataforma no responde,
> es porque está apagada; se enciende antes de cada revisión.

---

## Evidencias del MVP (15 de octubre de 2026)

| Consola: resumen global | Consola: suscripciones y pagos |
|---|---|
| ![Resumen global](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20sistema/Aplicaci%C3%B3n/01_consola_resumen.png) | ![Suscripciones y pagos](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20sistema/Aplicaci%C3%B3n/03_consola_suscripciones.png) |
| **Consola: auditoría** | **Portal: empresa morosa** |
| ![Auditoría](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20sistema/Aplicaci%C3%B3n/04_consola_auditoria.png) | ![Portal de una empresa morosa](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20sistema/Aplicaci%C3%B3n/05_portal_suscripcion.png) |

Las demás capturas (empresas, documentación de la API, modelo de datos y pruebas) están en
[`Fase 2/Evidencias Proyecto`](Fase%202/Evidencias%20Proyecto).

---

## Repositorios

| Repositorio | Contenido | Acceso |
|---|---|---|
| [proyecto-capstone-acredittia-administracion](https://github.com/Dntex2/proyecto-capstone-acredittia-administracion) | Documentación de Duoc UC por fase (este repositorio) | Público |
| [Acredittia-Administracion](https://github.com/Dntex2/Acredittia-Administracion) | Código del proyecto | Privado |
| [Acredittia-Entrega](https://github.com/Dntex2/Acredittia-Entrega) | Paquete de entrega para Alloxentric: código, modelo de datos y documentación (alcance, técnica, integración y OpenAPI) | Privado |

---

<details>
<summary><b>Ficha inicial del proyecto</b></summary>

<img width="1098" height="1154" alt="Ficha inicial del proyecto" src="https://github.com/user-attachments/assets/3e2dd2f9-f188-49f1-afe5-8101105a914b" />

</details>

<div align="center">
<sub>Duoc UC · Capstone PTY4614 · 2026</sub>
</div>
