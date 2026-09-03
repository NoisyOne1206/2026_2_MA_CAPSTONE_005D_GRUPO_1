Proyecto Capstone: RID — RepInDepth

Asignatura / Sección: 2026_2_MA_CAPSTONE_005D Grupo: [GRUPO_1 — confirmar identificador de grupo asignado por la coordinación] Institución: DUOC UC

Descripción del Proyecto

RID — RepInDepth es una aplicación móvil de entrenamiento de fuerza cuya diferencia central es que la persona nunca decide cuánto peso levantar: un motor probabilístico en el servidor —filtro de Kalman sobre un modelo de estado de aptitud y fatiga, con predicción conforme adaptativa para acotar el riesgo— prescribe carga, repeticiones y descargas a partir del historial propio de cada usuario. El sistema opera sin generación de lenguaje ni chatbots: cada número que ve la persona es la salida directa y auditable de un modelo estadístico.

El problema que resuelve: quien entrena sin guía profesional no sabe cuánto peso mover — subestimar detiene el progreso, sobrestimar aumenta el riesgo de lesión. Las aplicaciones de entrenamiento existentes registran series; casi ninguna decide la carga por la persona con una base estadística explícita.

Tecnologías principales: TypeScript en modo estricto, Astro y Capacitor en el cliente, PostgreSQL con seguridad a nivel de fila en Supabase, funciones de borde en Deno, y un motor de prescripción propio (@rid/engine) validado con más de 200 pruebas automatizadas, incluidas pruebas basadas en propiedades para el componente estadístico.

Beneficio esperado: una persona que entrena con RID no tiene que saber programar su propia progresión de carga ni arriesgarse a estancarse o lesionarse por una mala estimación propia — el motor lo hace por ella, con un margen de error acotado y ajustado a su propio historial.

Equipo de Trabajo
Fernando Almonacid	Líder de Proyecto 
Favio Pérez	Verificación, Seguridad y Despliegue
Bastian Berrios Backend

Tecnologías Utilizadas

Cliente (dispositivo del usuario, opera sin conexión)

TypeScript 5 en modo estricto
Astro (interfaz, navegación y vistas)
Capacitor (empaquetado nativo para Android e iOS)
SQLite en modo WAL, cifrada, como fuente de verdad local
PowerSync SDK (cola de mutaciones sin conexión, sincronización bidireccional)
Reconocimiento de voz del sistema operativo, con analizador determinista propio

Servidor (servicios gestionados)

Supabase: PostgreSQL 15, Auth, Storage
Seguridad a nivel de fila (RLS) como mecanismo central de aislamiento entre usuarios
Funciones de borde en Deno, con autoridad separada entre clave de usuario y clave de servicio
PowerSync Service (replicación bidireccional)

Cómputo por lotes y calibración

Stan / brms para el ajuste jerárquico nocturno de priors poblacionales
R para el cómputo de la tabla de cocientes entre familias de ejercicio

Infraestructura y herramientas de calidad

Git / GitHub
GitHub Actions para integración continua
Vitest, fast-check (pruebas basadas en propiedades) y Maestro (pruebas de extremo a extremo)
Sentry (trazabilidad de errores de cliente)
Requisitos e Instalación

Prerrequisitos

Node.js 20 LTS o superior, con pnpm o npm
PostgreSQL client (psql) 16 o superior
Deno 2.x (para verificar la función de borde con el runtime real)
Supabase CLI
Git
