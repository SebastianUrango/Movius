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

| **ID** | RF-002 |
|--------|---------|
| **Nombre** | Ubicación de buses en tiempo real |
| **Descripción** | El sistema mostrará la ubicación de los buses en un mapa, utilizando los datos GPS enviados desde los vehículos. <br><br>**Entrada:** Datos GPS del bus. <br>**Procesamiento:** Actualización del mapa con la posición del bus. <br>**Salida:** Mapa con posición del bus actualizada. |
| **Prioridad** | Esencial |
| **Estabilidad** | Media |
| **Fuente** | Área de Transporte UMN |
| **Criterios de Aceptación** | 1. El mapa se actualiza cada 10–15 segundos. <br>2. Se muestra si el bus está en movimiento o detenido. <br>3. La ruta del bus es visible para el usuario. |
| **Dependencias** | GPS de buses, red móvil |
| **Comentarios** | Mejora la precisión de la información para los usuarios. |

| **ID** | RF-003 |
|--------|---------|
| **Nombre** | Reserva de cupo |
| **Descripción** | El sistema permitirá a los estudiantes reservar un cupo en rutas de alta demanda antes de la hora de salida. <br><br>**Entrada:** Selección de ruta y confirmación de reserva. <br>**Procesamiento:** Validación de disponibilidad y registro de la reserva. <br>**Salida:** Confirmación visual de la reserva realizada. |
| **Prioridad** | Alta |
| **Estabilidad** | Media |
| **Fuente** | Servicios Estudiantiles |
| **Criterios de Aceptación** | 1. No se permite reservar más cupos de los disponibles. <br>2. Las reservas se asocian a cuentas institucionales válidas. <br>3. El usuario puede cancelar la reserva antes del inicio de la ruta. |
| **Dependencias** | RF-001 (Consulta de rutas), RF-007 (Panel administrativo) |
| **Comentarios** | Ayuda a evitar sobrecupos y mejorar la organización de rutas. |

| **ID** | RF-004 |
|--------|---------|
| **Nombre** | Notificaciones automáticas |
| **Descripción** | El sistema enviará notificaciones sobre retrasos, cancelaciones o emergencias asociadas a las rutas. <br><br>**Entrada:** Evento generado (retraso, cancelación, emergencia). <br>**Procesamiento:** Envío de alerta según la ruta del usuario. <br>**Salida:** Notificación push en el dispositivo. |
| **Prioridad** | Alta |
| **Estabilidad** | Media |
| **Fuente** | Coordinación de Transporte |
| **Criterios de Aceptación** | 1. Las alertas se envían en menos de 30 segundos. <br>2. El usuario recibe notificaciones incluso con la app cerrada. <br>3. Las notificaciones dependen de las rutas seguidas o reservadas. |
| **Dependencias** | Sistema de notificaciones, RF-003 |
| **Comentarios** | Mejora la comunicación y reduce confusiones. |

| **ID** | RF-005 |
|--------|---------|
| **Nombre** | Gestión de programación de rutas |
| **Descripción** | El personal administrativo podrá crear, editar y desactivar rutas y horarios según la operación diaria. <br><br>**Entrada:** Datos de nueva ruta u horario. <br>**Procesamiento:** Registro o modificación en la base de datos. <br>**Salida:** Programación actualizada visible para los usuarios. |
| **Prioridad** | Alta |
| **Estabilidad** | Alta |
| **Fuente** | Área Administrativa UMN |
| **Criterios de Aceptación** | 1. El sistema registra cada cambio con fecha y responsable. <br>2. Las actualizaciones reflejan en menos de 1 minuto. <br>3. Solo personal autorizado puede acceder. |
| **Dependencias** | Inicio de sesión institucional |
| **Comentarios** | Es clave para mantener información actualizada en todo momento. |

| **ID** | RF-006 |
|--------|---------|
| **Nombre** | Registro y trazabilidad de pasajeros |
| **Descripción** | Los usuarios se registrarán al abordar mediante escaneo de un código QR institucional. <br><br>**Entrada:** Código QR del usuario. <br>**Procesamiento:** Validación e ingreso a la base de datos. <br>**Salida:** Confirmación de registro exitoso. |
| **Prioridad** | Media |
| **Estabilidad** | Media |
| **Fuente** | Seguridad UMN |
| **Criterios de Aceptación** | 1. El escaneo se realiza en menos de 2 segundos. <br>2. Solo se permiten cuentas institucionales válidas. <br>3. Se registra fecha, ruta y bus correspondiente. |
| **Dependencias** | RF-001, conexión móvil |
| **Comentarios** | Importante para seguridad y control de aforo. |

| **ID** | RF-007 |
|--------|---------|
| **Nombre** | Panel administrativo |
| **Descripción** | El sistema mostrará métricas operativas como ocupación, puntualidad y eficiencia, accesibles solo para administradores. <br><br>**Entrada:** Datos estadísticos de uso. <br>**Procesamiento:** Cálculo y presentación de indicadores. <br>**Salida:** Dashboard con métricas. |
| **Prioridad** | Media |
| **Estabilidad** | Media |
| **Fuente** | Coordinación de Transporte |
| **Criterios de Aceptación** | 1. Se muestran métricas diarias, semanales y mensuales. <br>2. Los reportes pueden exportarse en Excel o CSV. <br>3. Solo personal autorizado puede ingresar. |
| **Dependencias** | Base de datos, RF-006 |
| **Comentarios** | Facilita la toma de decisiones y la planeación. |

| **ID** | RF-008 |
|--------|---------|
| **Nombre** | Botón de emergencia |
| **Descripción** | El sistema incluirá un botón de pánico que enviará una alerta con la ubicación del usuario al área de seguridad. <br><br>**Entrada:** Presión del botón. <br>**Procesamiento:** Envío de alerta inmediata. <br>**Salida:** Confirmación visual de “alerta enviada”. |
| **Prioridad** | Esencial |
| **Estabilidad** | Alta |
| **Fuente** | Departamento de Seguridad UMN |
| **Criterios de Aceptación** | 1. La alerta se envía en menos de 5 segundos. <br>2. Incluye ubicación aproximada. <br>3. Seguridad recibe la notificación de inmediato. |
| **Dependencias** | GPS, RF-002 |
| **Comentarios** | Requisito crítico para la seguridad de los usuarios. |


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
