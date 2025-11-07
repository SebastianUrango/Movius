  # 2.1Perspectiva del producto 

MoviUs es una plataforma digital que busca modernizar la gestión del transporte en la Universidad Metropolitana del Norte (UMN). Reemplaza los procesos manuales con una herramienta centralizada donde los usuarios pueden consultar rutas, horarios y disponibilidad de buses, mientras el personal administra la operación en tiempo real.

El sistema se integrará con el inicio de sesión institucional para mayor seguridad y ofrecerá una interfaz simple, adaptable y accesible para todos. En pocas palabras, MoviUs hará que el transporte universitario sea más ágil, ordenado y confiable.

# Funciones del producto

* El sistema MoviUs cubrirá las siguientes funciones principales:

* Consulta de rutas y horarios: Los usuarios podrán visualizar recorridos, horarios actualizados y ubicación de buses en tiempo real.

* Reserva de cupo: Los estudiantes podrán reservar un lugar en rutas de alta demanda.

* Notificaciones automáticas: Se enviarán alertas por retrasos, cancelaciones o emergencias.

* Gestión operativa: El personal de transporte podrá asignar rutas, monitorear buses activos y registrar novedades.

* Panel administrativo: Se mostrarán indicadores de ocupación, puntualidad y eficiencia.

* Trazabilidad: Se registrará la identificación de pasajeros al abordar los buses.

* Atención a emergencias: Se incluirá un botón de pánico con notificación inmediata al área de seguridad.

* Estas funciones buscan resolver los principales problemas actuales: falta de comunicación, planificación ineficiente y ausencia de información en tiempo real.

#  Restricciones
Técnicas

* El sistema debe permitir a los usuarios iniciar sesión con su cuenta institucional, evitando la creación de nuevos usuarios o contraseñas.

* La aplicación móvil deberá funcionar sin conexión a internet por cortos periodos, de manera que las operaciones básicas (como verificar rutas o registrar asistencia) sigan disponibles.

* Los buses contarán con dispositivos GPS y conexión a internet para actualizar su ubicación en tiempo real dentro del sistema.

* El sistema permitirá exportar reportes e información en formatos fáciles de usar, como Excel o CSV, para análisis y control administrativo.

* Se busca que el sistema sea ligero, rápido y compatible con la mayoría de los teléfonos Android en uso por el personal de transporte.

De negocio

* Presupuesto máximo: $78,000,000 COP.

* Entrega del MVP: 4 meses antes del inicio del siguiente semestre.

* Capacitación breve para conductores y auxiliares.

* Disponibilidad del sistema: 99% durante el horario operativo (6:00 a.m. – 10:00 p.m.).

* Legales y normativas

* Cumplimiento de la Ley 1581 de 2012 (protección de datos personales).

* Confidencialidad de ubicación y datos de usuarios.

* Cumplimiento de la Ley 769 de 2002 y el Decreto 1079 de 2015 sobre transporte de personas.

# Suposiciones y dependencias

* Todos los buses contarán con GPS y conexión móvil antes del despliegue.

* Dependencia del servidor institucional AWS y la red universitaria.

* Conductores capacitados para usar la aplicación móvil.

* Comunicación con usuarios mediante correo institucional y notificaciones push.

* El éxito del sistema depende de la actualización constante de datos por parte del área administrativa.

# Requisitos futuros

* A futuro, MoviUs podría incorporar nuevas funciones como:

* Optimización de rutas mediante inteligencia artificial.

* Integración con apps de movilidad urbana (Moovit, Google Maps).

* Pagos digitales o descuentos automáticos en matrícula según uso.

* Sistema de recompensas para fomentar el uso responsable.

* Chatbot inteligente para atención rápida y soporte.

* Aplicación nativa para iOS y Android con mejor rendimiento.

Estas mejoras fortalecerán el sistema, ampliarán su alcance y ofrecerán una experiencia más completa a toda la comunidad universitaria.



| **ID** | RF-001 |
|--------|---------|
| **Nombre** | Consulta de rutas y horarios |
| **Descripción** | El sistema permitirá a los usuarios (auxiliares de despacho, estudiantes y docentes) consultar las rutas disponibles con sus respectivos horarios, puntos de origen y destino, y el estado actual del bus (en servicio, retrasado o cancelado). <br><br>**Entrada:** Selección de ruta o fecha de consulta por parte del usuario. <br>**Procesamiento:** El sistema busca la información en la base de datos de programación y estado de flota. <br>**Salida:** Muestra la lista de rutas y horarios actualizados en pantalla, con información legible y sincronizada en tiempo real. |
| **Prioridad** | Esencial |
| **Estabilidad** | Alta |
| **Fuente** | Dirección de Servicios Estudiantiles / Auxiliar de despacho |
| **Criterios de Aceptación** | 1. El usuario puede visualizar todas las rutas activas del día seleccionado. <br>2. El sistema actualiza los horarios y estados de los buses en menos de 60 segundos. <br>3. La información se presenta en un formato claro, ordenado y comprensible. |
| **Dependencias** | RF-002 (Ubicación de buses en tiempo real), RF-005 (Gestión de programación de rutas) |
| **Comentarios** | Este requisito es esencial para la operación diaria, ya que permite consultar la programación de buses y verificar su disponibilidad de manera eficiente. |


| Campo | Descripción |
|-------|-------------|
| **ID** | CU-07 |
| **Nombre** | [Revisar lista de buses] |
| **Actores** | [Axuliar de despaco] |
| **Descripción** | [Permite al auxiliar de despacho visualizar y verificar la lista de buses programados para la jornada, asegurando que la información esté correcta y completa antes del inicio de las rutas.] |
| **Precondiciones** | [El auxiliar ha iniciado sesión correctamente en el sistema MOVIUS, La base de datos de rutas y buses está actualizada.] |
| **Postcondiciones** | [Se verifica la lista completa de buses programados,Se registran las novedades encontradas. ] |
| **Flujo Principal** | 1. El auxiliar de despacho selecciona la opción “Revisar lista de buses”.<br>2. El sistema muestra la lista de buses programados para el día, incluyendo información de conductor, ruta y hora de salida.<br>3. El auxiliar verifica que la información sea correcta y completa.<br>4. Si se detectan inconsistencias o novedades, el auxiliar las registra en la bitácora (CU-08).<br>5. El sistema valida los datos actualizados.<br>6. El auxiliar confirma que la revisión ha sido completada.<br>7. El sistema guarda el registro de la revisión. |
| **Flujos Alternativos** | **2a**. No hay buses programados:<br>2a1. El sistema muestra mensaje “No existen buses programados para la fecha seleccionada”.<br>2a2. El auxiliar puede seleccionar otra fecha o finalizar el proceso. |
| **Flujos de Excepción** | **3a** Error de conexión o acceso a base de datos:<br>3a1. El sistema muestra mensaje “Error al obtener la lista de buses. Intente nuevamente”.<br>3a2. El sistema registra el error en el log del sistema.<br>3a3. El auxiliar puede reintentar o cerrar sesión.<br>3a4. Fin del caso de uso. |
| **Requisitos Relacionados** | RF-007 (Consulta de programación de buses)<br>RF-008 (Registro de novedades en bitácora)<br>RF-009 (Notificación de cambios a usuarios)<br>RNF-002 (Disponibilidad del sistema)<br>RNFR-001 (Tiempo de respuesta en consulta) |






| Campo | Descripción |
|-------|-------------|
| **ID** | CU-01 |
| **Nombre** |inisiar sesion  |
| **Actores** |Auxiliar de despacho |
| **Descripción** | Permite al auxiliar de despacho acceder al sistema MOVIUS ingresando sus credenciales (usuario y contraseña). El sistema valida la información proporcionada y permite el acceso solo si las credenciales son correctas. En caso contrario, se notifica al usuario.. |
| **Precondiciones** | 1. El sistema MOVIUS debe estar disponible.<br>El auxiliar de despacho debe tener una cuenta activa y credenciales válidas registradas. |
| **Postcondiciones** | 1.El usuario accede correctamente al sistema y se habilitan las opciones del menú principal según su rol. En caso de credenciales incorrectas, se genera una notificación de error. |
| **Flujo Principal** | 1. El auxiliar de despacho abre el sistema MOVIUS.<br>2. El sistema muestra la pantalla de inicio de sesión.<br>3. El auxiliar ingresa su nombre de usuario y contraseña.<br>4. El sistema incluye el caso de uso UC-02 Validar credenciales.<br>5. Si las credenciales son correctas, el sistema concede acceso al panel principal.<br>6. El sistema registra el inicio de sesión exitoso. |
| **Flujos Alternativos** | 4a. Credenciales inválidas:<br>4a1. El sistema extiende el caso de uso UC-03 Notificar credenciales incorrectas.<br>4a2. Se muestra el mensaje “Usuario o contraseña incorrectos”.<br>4a3. El auxiliar puede reintentar el inicio de sesión. |
| **Flujos de Excepción** | 1a. Falla de conexión con el servidor:<br>1a1. El sistema muestra el mensaje “Error de conexión. Intente nuevamente más tarde”.<br>1a2. Se registra el error en el log del sistema.<br>1a3. Fin del caso de uso. |
| **Requisitos Relacionados** | 	RF-001 (Gestión de autenticación de usuarios)<br>RF-002 (Validación de credenciales)<br>RF-003 (Notificación de errores de acceso)<br>RNF-001 (Seguridad de acceso)<br>RNFR-002 (Tiempo máximo de respuesta del sistema) |
<br>

hola mundo 
