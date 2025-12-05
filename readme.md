# Sistema de Gestión de Denuncias Ciudadanas (SGDC) - Documentación Técnica

## 0. Portada

<p align="center">
  <img src="logoUNI.png" alt="Logo UNI" width="200"/>
</p>


**Nombre del Proyecto:** Sistema de Gestión de Denuncias Ciudadanas (SGDC)

**Integrantes:**
- Inga Champi Franz Joe – 20231302G
- Albino Soto Christopher Henrry – 20231158C
- Fernández Dueñas Yazid Elio – 20224085D
- Rashuaman Sapallanay Ricco Didier –20231242D


**Curso:** Análisis y Modelamiento de Comportamiento

**Profesor:** JHOSEP ALAN VALENZUELA MATUTTI

**Fecha:** 5/12/2025

---

## 1. Introducción

### 1.1. Objetivo del Documento
El presente documento tiene como objetivo describir de manera detallada el proceso de desarrollo del Sistema de Gestión de Denuncias Ciudadanas (SGDC) utilizando el Modelo de Desarrollo en Cascada Seguro (Secure Waterfall). Incluye los requisitos, el diseño, las prácticas de seguridad aplicadas, las pruebas realizadas y los lineamientos para el despliegue y mantenimiento del sistema. El propósito principal es asegurar que el SGDC se construya bajo estándares que garanticen confidencialidad, integridad, disponibilidad y protección de datos personales.

### 1.2. Alcance del Sistema
El SGDC es una plataforma web destinada a que los ciudadanos puedan:
- Registrar denuncias relacionadas con problemas públicos (basura, alumbrado, inseguridad, entre otros)
- Adjuntar evidencias como fotografías o documentos
- Consultar el estado de su denuncia en tiempo real
- Recibir notificaciones sobre avances, actualizaciones o cierre del caso
- Permitir a la Municipalidad gestionar, asignar, atender y resolver denuncias de manera eficiente

El alcance incluye el análisis, diseño, desarrollo, pruebas y mantenimiento de la solución, integrando controles de seguridad en cada fase del ciclo de vida.

### 1.3. Beneficiarios
**a) Ciudadanos:**
- Acceso sencillo para reportar problemas en su distrito
- Mayor transparencia en el seguimiento de sus denuncias
- Canal de comunicación confiable con la Municipalidad

**b) Municipalidad de Lima:**
- Mejora en la gestión interna de denuncias y asignación de tareas
- Mayor control sobre los tiempos de respuesta
- Disponibilidad de estadísticas e indicadores para la toma de decisiones

**c) Operadores y Administradores del Sistema:**
- Herramientas que permiten revisar, atender y cerrar denuncias eficientemente
- Acceso a paneles y reportes operativos
- Controles de seguridad que protegen la integridad de la información

### 1.4. Normativa y Estándares Considerados
El desarrollo del SGDC se realiza conforme a normas y buenas prácticas de seguridad reconocidas a nivel nacional e internacional:
- **Ley N.° 29733** – Ley de Protección de Datos Personales (Perú)
- **ISO/IEC 27001** – Gestión de Seguridad de la Información
- **ISO/IEC 27005** – Gestión de Riesgos de Seguridad
- **OWASP Top 10** – Lineamientos para prevenir vulnerabilidades críticas en aplicaciones web
- **Principio Security by Design** – Garantiza que la seguridad sea considerada desde las primeras fases del proyecto

---

## 2. Descripción General del Sistema SGDC

### 2.1. Problema que Resuelve
La Municipalidad de Lima enfrenta dificultades en la gestión eficiente de denuncias ciudadanas relacionadas con problemas públicos como acumulación de basura, alumbrado defectuoso, actos de inseguridad, veredas dañadas y otros incidentes urbanos. Actualmente, los procesos manuales o canales dispersos generan:
- Demoras en la atención de denuncias
- Falta de trazabilidad y transparencia en el avance de los casos
- Limitaciones para priorizar incidentes críticos
- Escasa comunicación entre ciudadanos y autoridades

El SGDC busca resolver estas limitaciones proporcionando una plataforma moderna, accesible y segura que centralice todo el proceso de registro, seguimiento y resolución de denuncias.

### 2.2. Funcionalidades Principales
**Para ciudadanos:**
- Registro de denuncias mediante un formulario estructurado
- Adjuntar evidencias (fotografías, documentos, videos)
- Visualizar el estado actual de cada denuncia presentada
- Recibir notificaciones automáticas sobre cambios en el proceso
- Acceso a un historial de denuncias personales

**Para operadores municipales:**
- Bandeja de denuncias pendientes, en proceso y resueltas
- Asignación de casos a equipos o áreas responsables
- Gestión de tiempos de respuesta y prioridades
- Registro de acciones realizadas y cierre de casos
- Generación de reportes operativos y estadísticos

**Para administradores del sistema:**
- Gestión de usuarios, roles y permisos
- Configuración de parámetros del sistema (categorías, zonas, protocolos)
- Supervisión de logs de auditoría y configuración de alertas
- Acceso a paneles de seguridad y monitoreo

### 2.3. Actores del Sistema
**a) Ciudadano:** Usuario externo que registra denuncias y consulta el estado de las mismas
**b) Operador Municipal:** Colaborador autorizado que gestiona las denuncias
**c) Administrador del Sistema:** Usuario con privilegios avanzados encargado de la gestión técnica y operativa

### 2.4. Diagrama General del Flujo del Sistema
A nivel conceptual, el sistema opera mediante el siguiente flujo:
1. **Registro de denuncia:** El ciudadano ingresa al portal, completa el formulario y adjunta evidencias
2. **Validación automática:** El sistema verifica datos obligatorios, formato de archivos, autenticación y seguridad
3. **Clasificación y asignación:** El operador municipal recibe la denuncia, analiza la categoría y la asigna al área encargada
4. **Atención del caso:** El área responsable realiza acciones en campo o gestiona la solución y actualiza el sistema
5. **Notificación al ciudadano:** Cada cambio importante genera notificaciones automáticas
6. **Cierre del caso:** Se registra una solución final, evidencias de atención y se archiva la denuncia
7. **Reporte y análisis:** Administradores y operadores pueden visualizar estadísticas

---

## 3. Modelo de Desarrollo: Secure Waterfall

### 3.1. ¿Qué es el Modelo en Cascada Seguro?
El Modelo en Cascada es una metodología tradicional de desarrollo de software que se organiza en fases secuenciales: Requisitos → Diseño → Implementación → Pruebas → Despliegue → Mantenimiento. El Secure Waterfall es una adaptación donde la seguridad se integra en cada fase del ciclo de vida, asegurando que los riesgos, vulnerabilidades y controles de seguridad sean gestionados desde el inicio del proyecto.

### 3.2. Justificación de su Uso en este Proyecto
1. **Manejo de datos personales sensibles:** Almacena datos ciudadanos que requieren cumplimiento de Ley 29733
2. **Requerimientos de trazabilidad y transparencia:** Necesita registro detallado de accesos y modificaciones
3. **Entorno gubernamental:** Exige documentación formal, procesos claros y auditorías de seguridad
4. **Necesidad de minimizar vulnerabilidades:** Sistemas web municipales pueden ser objetivos de ataques

### 3.3. Seguridad Integrada en Cada Fase
- **🔐 Fase de Requisitos:** Identificación de activos, análisis de riesgos, definición de requisitos de seguridad
- **🏗 Fase de Diseño:** Arquitectura segura, modelado de amenazas, controles perimetrales
- **💻 Fase de Implementación:** Codificación segura, gestión de secretos, validación de entradas
- **🧪 Fase de Pruebas:** Pruebas funcionales y de seguridad, pentesting, validación de controles
- **🚀 Fase de Despliegue:** Hardening de servidores, CI/CD seguro, backups cifrados
- **🔄 Fase de Mantenimiento:** Aplicación de parches, monitoreo continuo, respuesta a incidentes

---

## 4. Fase 1: Requisitos

### 4.1. Requisitos Funcionales
- **RF01 – Registro de Denuncias:** Formulario web con datos mínimos y adjuntos
- **RF02 – Gestión de Denuncias por Operadores:** Clasificación, asignación y actualización de estados
- **RF03 – Seguimiento del Estado por el Ciudadano:** Consulta en tiempo real
- **RF04 – Sistema de Notificaciones:** Envío automático al cambiar estados
- **RF05 – Panel Administrativo:** Gestión de usuarios, roles, reportes y auditoría

### 4.2. Requisitos No Funcionales
- **RNF01 – Rendimiento:** Soporte para 200 solicitudes simultáneas
- **RNF02 – Disponibilidad:** 99% anual
- **RNF03 – Usabilidad:** Interfaz accesible y compatible con móviles
- **RNF04 – Escalabilidad:** Permitir añadir nuevos módulos

### 4.3. Requisitos de Seguridad
- **RS01 – Autenticación Segura:** 2FA, usuario + contraseña
- **RS02 – Cifrado de Datos:** AES-256 para datos sensibles, HTTPS/TLS 1.2+
- **RS03 – Contraseñas Seguras:** Hashing con bcrypt, sal aleatoria
- **RS04 – Control de Acceso:** Principio de menor privilegio basado en roles
- **RS05 – Logs de Auditoría:** Registro de accesos, cambios e intentos fallidos
- **RS06 – Protección contra vulnerabilidades:** Mitigación de SQLi, XSS, CSRF
- **RS07 – Protección de Archivos Adjuntos:** Validación, escaneo y cifrado

### 4.4. Identificación de Activos de Información
| Activo | Descripción | Sensibilidad |
|--------|-------------|--------------|
| Datos personales del ciudadano | Nombres, DNI, contacto | Alta |
| Denuncias registradas | Información del incidente, ubicación | Alta |
| Evidencias adjuntas | Fotos, documentos | Alta |
| Usuarios del sistema | Operadores y administradores | Media |
| Logs del sistema | Auditoría y seguimiento | Alta |
| Arquitectura del sistema | Configuración interna | Media-Alta |

### 4.5. Análisis de Riesgos (ISO/IEC 27005)
- **R1 – Fuga de datos personales:** Acceso no autorizado, falta de cifrado
- **R2 – Manipulación de denuncias:** Usuario interno modifica sin registro
- **R3 – Carga de archivos maliciosos:** Malware en evidencias

### 4.6. Matriz de Riesgos y Controles
| Riesgo | Probabilidad | Impacto | Nivel | Controles |
|--------|--------------|---------|-------|-----------|
| Fuga de datos personales | Media | Alto | Alto | Cifrado, 2FA, control de accesos |
| Inyección SQL | Media | Alto | Alto | Validación, sanitización, ORM |
| XSS | Media | Medio | Medio | Escapado de datos, CSP |
| Acceso de operadores no autorizados | Baja | Alto | Medio | Roles y privilegios |
| Pérdida de evidencias | Baja | Alto | Medio | Backups cifrados |

### 4.7. Cumplimiento Normativo (Ley 29733)
- Consentimiento para tratamiento de datos
- Finalidad específica del uso de información
- Derechos ARCO: acceso, rectificación, cancelación y oposición
- Seguridad lógica y física del entorno
- Registro de banco de datos ante el MINJUSDH

### 4.8. Entregables de la Fase
1. Documento de Requisitos Funcionales
2. Documento de Requisitos No Funcionales
3. Requisitos de Seguridad
4. Inventario de Activos de Información
5. Matriz de Riesgos y Controles
6. Registro de Cumplimiento Normativo
7. Acta de reuniones de levantamiento de información

---

## 5. Fase 2: Diseño del Sistema

### 5.1. Arquitectura General (3 Capas)
1. **Capa de Presentación (Frontend):** Interfaz web con HTML5, CSS3, JavaScript/React
2. **Capa de Aplicación (Backend / API REST):** Framework seguro (Django, Spring Boot)
3. **Capa de Datos:** Base de datos relacional (PostgreSQL/MySQL) con cifrado

### 5.2. Arquitectura Segura
- **🔐 Seguridad en el transporte:** HTTPS/TLS 1.2+, certificados CA confiable
- **🛡 Seguridad perimetral:** Firewall, WAF para mitigar SQLi, XSS, CSRF
- **📦 Seguridad interna:** Segmentación en DMZ, backend aislado
- **🔑 Seguridad en autenticación:** OAuth 2.0 / OpenID Connect, JWT firmados

### 5.3. Diagramas
**a) Casos de Uso:** Ciudadano (registrar denuncia), Operador (clasificar, asignar), Administrador (gestionar usuarios)
**b) Secuencia:** Flujo de registro de denuncia con validaciones y cifrado
**c) Arquitectura Física:** Servidores web, aplicación, base de datos, logs/SIEM

### 5.4. Definición de Roles y Permisos (Menor Privilegio)
1. **Ciudadano:** Registrar denuncias, consultarlas, ver historial
2. **Operador Municipal:** Consultar denuncias asignadas, actualizar estados
3. **Administrador:** Gestión total de usuarios, configuración, auditoría

### 5.5. Threat Modeling (STRIDE)
| Categoría | Amenaza | Ejemplo en SGDC | Control |
|-----------|---------|-----------------|---------|
| S – Spoofing | Suplantación | Falso ciudadano accede | Autenticación 2FA, JWT seguro |
| T – Tampering | Manipulación de datos | Alteración del estado de denuncia | Logs, roles, integridad |
| R – Repudiation | Negación de acciones | Usuario niega actividad | Auditoría inmutable |
| I – Information Disclosure | Fuga de datos | Filtración de datos personales | Cifrado, TLS |
| D – Denial of Service | Caída del sistema | Saturación de peticiones | Rate limiting, WAF |
| E – Elevation of Privilege | Escalada de privilegios | Operador se vuelve admin | RBAC estricto |

### 5.6. Diseño de Controles de Seguridad
- Cifrado en tránsito y reposo
- Tokens con expiración
- Gestión segura de sesiones
- Validación y sanitización de datos
- Hardening de servidores
- Seguridad por capas (defense in depth)

### 5.7. Selección de Frameworks y Tecnologías
- **Backend:** Django, Spring Boot o Node.js con módulos OWASP
- **Frontend:** React o HTML/CSS/JS con sanitización
- **Base de Datos:** PostgreSQL con cifrado
- **Otros:** Sistema de logs centralizado, almacenamiento cifrado, CI/CD seguro

### 5.8. Entregables de la Fase
1. Documento de Arquitectura Segura
2. Diagramas de casos de uso, secuencia y arquitectura
3. Modelo de Roles y Permisos
4. Modelo de Amenazas STRIDE
5. Plan de Seguridad de la Arquitectura
6. Especificación técnica de la API

---

## 6. Fase 3: Implementación (Desarrollo Seguro)

### 6.1. Lineamientos de Codificación Segura (OWASP Top 10)
- **A01 – Broken Access Control:** RBAC estricto, validación de roles
- **A02 – Cryptographic Failures:** AES-256, bcrypt, sin información en logs
- **A03 – Injection:** ORM, sanitización estricta
- **A05 – Security Misconfiguration:** Eliminar endpoints por defecto
- **A07 – Identification and Authentication Failures:** OAuth2 + JWT, rate limiting
- **A08 – Software and Data Integrity Failures:** Validación de dependencias
- **A10 – SSRF:** Restricción de llamadas externas

### 6.2. Control de Versiones y Repositorios (GitLab)
- Acceso basado en roles
- Firma de commits (GPG)
- Ramas protegidas (main, develop)
- Revisión obligatoria de merge requests
- Auditoría automática de cambios

### 6.3. SAST y Revisión de Código (SonarQube, Dependency-Check)
- SonarQube para vulnerabilidades, bugs
- OWASP Dependency-Check para bibliotecas vulnerables
- Corrección antes del despliegue

### 6.4. Gestión de Secretos (Vault, Secret Manager)
- HashiCorp Vault o GCP/AWS Secret Manager
- Variables de entorno cifradas
- Rotación periódica de claves
- Acceso limitado por rol

### 6.5. Gestión de Errores y Logs
- Mensajes genéricos para usuarios
- Registro detallado solo en logs internos
- Sin stack traces en producción
- Sanitización de mensajes

### 6.6. Implementación Segura de:
**Autenticación (OAuth2, JWT):** Tokens firmados, expiración 30 min, refresh tokens
**Cifrado de datos y archivos:** AES-256, TLS 1.2+
**Validación y sanitización de entradas:** Longitud, formatos, caracteres especiales

### 6.7. Entregables de la Fase
1. Código fuente documentado
2. Manual de estilo de codificación segura
3. Resultados del análisis SAST
4. Lista de dependencias y vulnerabilidades corregidas
5. Módulos funcionales del sistema
6. Integración inicial del CI/CD
7. Informe de cumplimiento OWASP Top 10

---

## 7. Fase 4: Pruebas

### 7.1. Plan de Pruebas Funcionales
- Registro de denuncias (campos, archivos, formatos)
- Gestión por operadores (visualización, clasificación, asignación)
- Seguimiento por ciudadano (acceso propio, tiempo real)
- Notificaciones (envío automático, recepción)
- Módulo administrativo (usuarios, roles, parámetros)

### 7.2. Pruebas de Integración
- Frontend ↔ Backend: HTTPS, tokens, JSON
- Backend ↔ Base de Datos: Inserciones cifradas, consultas
- Módulo de Evidencias ↔ Almacenamiento: Carga, validación, cifrado
- Notificaciones ↔ API Externa: Envío de correos/mensajes

### 7.3. Pruebas de Seguridad
**DAST (OWASP ZAP):** SQLi, XSS, CSRF, Path Traversal, Broken Authentication
**Pentesting interno:** Escalación de privilegios, manipulación no autorizada
**Revisión de permisos, sesiones, cifrado:** Expiración, invalidación, cookies httpOnly

### 7.4. Resultados y Correcciones Aplicadas
- Hallazgos identificados y medidas correctivas
- Refuerzo de sanitización, actualización de dependencias
- Ajustes en firewall/WAF

### 7.5. Entregables de la Fase
1. Plan de Pruebas Funcionales e Integración
2. Resultados del Testing Funcional
3. Informe de Pruebas de Seguridad (DAST, Pentesting)
4. Reporte de Vulnerabilidades y Medidas Correctivas
5. Validación de Controles de Seguridad
6. Acta de Aprobación de la Fase de Pruebas

---

## 8. Fase 5: Despliegue en Producción

### 8.1. Preparación del Entorno
- Servidores: Web (DMZ), Aplicación, Base de Datos, Logs/SIEM
- Configuración: SO actualizado, servicios innecesarios deshabilitados
- Firewall: Puertos esenciales (80→443, 443)

### 8.2. Hardening de Servidores y Servicios
- **SO:** SSH solo con claves, cambio de puerto, Fail2Ban
- **Servidor web:** TLS 1.2+, headers de seguridad (CSP, X-Frame-Options)
- **Base de datos:** Acceso limitado, cuentas con privilegios mínimos, cifrado

### 8.3. Configuración de CI/CD Seguro
- Integración con SAST antes del despliegue
- Validación de dependencias
- Firma de artefactos
- Despliegue manual autorizado
- Auditoría de cada despliegue

### 8.4. Backups Cifrados y Restauración
- Backup completo y diferencial
- Cifrado AES-256 en reposo
- Almacenamiento externo seguro
- Pruebas periódicas de restauración

### 8.5. Plan de Puesta en Producción
- Pruebas de aceptación final
- Validación de roles en producción
- Pruebas de rendimiento y seguridad
- Habilitación solo sin vulnerabilidades críticas

### 8.6. Capacitación a Usuarios y Administradores
- **Operadores:** Uso del panel, gestión de denuncias
- **Administradores:** Gestión de usuarios, supervisión de logs, incidentes

### 8.7. Entregables de la Fase
1. Manual de Instalación y Configuración Segura
2. Checklist de Hardening aplicado
3. Pipeline CI/CD documentado
4. Plan de Backups y Restauración
5. Evidencias de Monitoreo y Alertas
6. Informe de Pruebas de Aceptación
7. Acta de Puesta en Producción

---

## 9. Fase 6: Mantenimiento

### 9.1. Plan de Parches y Actualizaciones
- **Críticas:** 24-48 horas
- **Importantes:** 7 días
- **Menores:** Mensualmente
- Pruebas en staging antes de producción

### 9.2. Monitoreo de Seguridad (SIEM, Logs)
- SIEM para correlación de eventos
- IDS/IPS para intrusiones
- Escáneres de vulnerabilidades
- Alarmas del WAF

### 9.3. Gestión de Incidentes (CSIRT Municipal)
1. Identificación: Alertas, reportes
2. Contención: Bloqueo, detención de servicios
3. Erradicación: Eliminar malware, aplicar parches
4. Recuperación: Restaurar desde backups
5. Lecciones aprendidas: Registrar, mejorar procesos

### 9.4. Auditorías Periódicas
- Técnica (seguridad, arquitectura, código)
- Operativa (gestión de usuarios)
- Normativa (Ley 29733, ISO 27001)
- Gestión de riesgos (actualización de matriz)

### 9.5. Bitácora de Vulnerabilidades y Parches
- Fecha de detección
- Descripción de vulnerabilidad
- Riesgo (alto/medio/bajo)
- Acción tomada
- Fecha de solución
- Evidencias de corrección

### 9.6. Entregables de la Fase
1. Plan de mantenimiento anual
2. Registro de parches aplicados
3. Informes de monitoreo y vulnerabilidades
4. Reportes de incidentes de seguridad (CSIRT)
5. Informes de auditorías internas y externas
6. Bitácora de cambios y actualizaciones
7. Revisiones de cumplimiento normativo

---

## 10. Conclusiones

### Qué se Logró
- Desarrollo de una plataforma integral para gestión de denuncias ciudadanas
- Integración de seguridad en todas las fases del ciclo de vida
- Cumplimiento de normativas locales e internacionales
- Implementación de controles robustos para protección de datos

### Importancia de Integrar Seguridad en el Ciclo de Vida
- Reduce costos de corrección posterior
- Minimiza riesgos de incidentes de seguridad
- Asegura cumplimiento normativo desde el inicio
- Fomenta cultura de seguridad en la organización

### Retos y Recomendaciones
**Retos:**
- Complejidad en la integración de múltiples estándares de seguridad
- Capacitación continua del personal técnico y operativo
- Evolución constante de amenazas cibernéticas

**Recomendaciones:**
- Mantener actualizado el análisis de riesgos
- Establecer programas continuos de capacitación
- Implementar monitoreo proactivo 24/7
- Realizar auditorías de seguridad periódicas

---

## 11. Bibliografía

1. Ley N.° 29733 – Ley de Protección de Datos Personales y su Reglamento, aprobado por Decreto Supremo N.° 003-2013-JUS
2. ISO/IEC 27001:2013 – Information technology — Security techniques — Information security management systems — Requirements
3. ISO/IEC 27005:2018 – Information technology — Security techniques — Information security risk management
4. OWASP Foundation. (2021). OWASP Top Ten. Recuperado de https://owasp.org/www-project-top-ten/
5. Ministerio de Justicia y Derechos Humanos del Perú. (2020). Guía de Implementación de la Ley de Protección de Datos Personales
6. Microsoft. (2021). Security Development Lifecycle (SDL)
7. NIST. (2018). Framework for Improving Critical Infrastructure Cybersecurity
8. CIS Controls v8 – Center for Internet Security

---

*Documento elaborado bajo el modelo Secure Waterfall para el Sistema de Gestión de Denuncias Ciudadanas (SGDC)*