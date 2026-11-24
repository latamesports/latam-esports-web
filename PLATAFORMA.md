# LATAM ESPORTS — Diseño de plataforma profesional
**Etapa 1: arquitectura funcional y experiencia de usuario**

## Decisiones confirmadas
- Organización: LATAM ESPORTS (LE).
- Lema: EL TALENTO NO TIENE FRONTERAS.
- Panel administrativo privado: **Centro de mando LATAM**.
- Tipos de acceso: jugadores y representantes de equipos; administradores con permisos privados.
- Visibilidad de perfiles: cada jugador elige qué campos mostrar públicamente.
- Primera versión: web adaptable a móviles, en español, con prioridad a Colombia y visión latinoamericana.

## Navegación pública
1. Inicio
2. Torneos
3. Jugadores
4. Equipos
5. Rankings
6. Noticias
7. Iniciar sesión / Crear cuenta

## Espacios autenticados
### Jugador
- Perfil y datos de juego.
- Preferencias de privacidad por campo.
- Equipos e invitaciones.
- Torneos e historial de participación.
- Estadísticas y ranking.

### Representante de equipo
- Crear y editar equipo.
- Invitar y retirar integrantes.
- Administrar plantilla y capitán.
- Solicitar inscripción a torneos.
- Consultar estado de solicitudes y resultados.

### Centro de mando LATAM (administración)
- Resumen general.
- Gestión de cuentas y roles.
- Revisión de equipos.
- Creación y administración de torneos.
- Aprobación/rechazo de inscripciones.
- Publicación y validación de resultados.
- Gestión de noticias y reportes.
- Registro de acciones administrativas.

## Privacidad de perfiles
La cuenta no será pública por defecto. El jugador podrá elegir individualmente si muestra:
- Apodo gamer y nombre público.
- País.
- Foto/avatar.
- Juegos principales.
- Equipo actual.
- Estadísticas y logros.

El correo, credenciales, datos de recuperación y datos privados nunca aparecerán en perfiles públicos. La visibilidad pública no debe permitir editar información de otros usuarios.

## Modelo inicial de datos (Supabase)
- profiles: identidad de cuenta y datos de perfil.
- profile_visibility: preferencias de publicación por campo.
- games: catálogo de videojuegos.
- teams: equipos y sus representantes.
- team_members: integrantes, roles y estado de invitación.
- tournaments: juego, formato, reglas, fechas y estado.
- tournament_entries: solicitudes e inscripciones.
- matches: encuentros y calendario.
- match_results: resultados validados.
- news: noticias y anuncios.
- admin_audit_log: acciones administrativas relevantes.

## Roles y seguridad
- La autenticación se gestionará con Supabase Auth.
- Los permisos se aplicarán en la base de datos mediante Row Level Security (RLS).
- Un usuario no podrá asignarse a sí mismo el rol de administrador.
- Los roles administrativos se asignarán de forma controlada desde el entorno seguro del proyecto.
- Cada jugador podrá modificar su propio perfil y sus preferencias, no las de otros.
- Los representantes solo podrán administrar equipos en los que tengan el permiso correspondiente.
- Las inscripciones y resultados tendrán estados y validaciones; no serán editables libremente por cualquier participante.
- Las claves secretas de servicio nunca se incluirán en el JavaScript público ni en GitHub.

## Etapas posteriores
1. Diseño visual y estructura de pantallas.
2. Proyecto Supabase, tablas, autenticación y políticas RLS.
3. Registro, inicio de sesión y recuperación de cuenta.
4. Perfiles y preferencias de privacidad.
5. Equipos e invitaciones.
6. Torneos, inscripciones y resultados.
7. Rankings, noticias y panel administrativo.
8. Pruebas de seguridad, privacidad y experiencia móvil antes del lanzamiento.

## Estado actual
Este documento define el diseño y las reglas funcionales. La web pública actual todavía es estática y su formulario de interés no almacena registros en una base de datos. No se deben anunciar cuentas, inscripciones, estadísticas ni rankings como activos hasta que las etapas de desarrollo y pruebas estén terminadas.

## Consideraciones de lanzamiento
Antes de recopilar datos reales, LATAM ESPORTS debe publicar una política de tratamiento de datos clara, explicar finalidades y mecanismos de autorización, definir retención y eliminación, y revisar requisitos aplicables a menores de edad. Los torneos solo se abrirán cuando sus reglas, autorizaciones del publisher cuando correspondan, requisitos técnicos y condiciones estén confirmados.
