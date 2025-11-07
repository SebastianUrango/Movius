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

# 4.1 Casos De Uso 
1. CU-011: Gestionar Rutas y Paradas

   
| Campo  |  Descripción |
|---|---|
|   ID	| CU-011  |
| Nombre  | Gestionar Rutas y Paradas  |
| Actores  | Administrador (primario)  |
|  Descripcion | Permite al Administrador crear, modificar, activar, desactivar y eliminar rutas de transporte, definiendo sus puntos geolocalizados de parada y sus horarios asociados.  |
|  Precondiciones  | 1. El Administrador ha iniciado sesión <br> 2. El sistema de geolocalización está operativo.|
|  Postcondiciones (Exito) | 1. Se crea/modifica una ruta con sus paradas y horarios asociados.<br> 2. La configuración se actualiza en la base de datos y es visible para los usuarios.  |
|  Flujo Principal | 1. El Administrador selecciona la opción "Gestión de Rutas".<br> 2. El sistema muestra la lista de rutas.<br>3. El Administrador selecciona "Crear Nueva Ruta".<br>4. El sistema solicita los datos básicos de la ruta (nombre, descripción).<br>5. El Administrador añade Puntos de Parada geolocalizados y define los horarios.<br>6. El sistema valida que las coordenadas de paradas sean únicas.<br>7. El Administrador confirma la creación/modificación.<br>8. El sistema registra la nueva ruta y la activa por defecto.<br>9. Fin del caso de uso.  |
|  Flujos Alternativos  |  3a. Modificar Ruta Existente: El Administrador selecciona una ruta existente. El sistema carga la configuración actual (paradas/horarios). Vuelve al paso 5 para modificar.<br>3b. Desactivar/Eliminar Ruta: El Administrador selecciona una ruta y la desactiva. El sistema verifica que no tenga viajes programados. Si no los tiene, la desactiva (o la elimina si se solicita). |
|  Flujos De Excepcion | 6a. Coordenadas Duplicadas: El sistema detecta que dos paradas tienen coordenadas idénticas. Muestra un error y obliga al Administrador a ajustar una de las coordenadas.  |
| Reglas De Negocio  |  RN-RUT-001: Una ruta debe tener al menos dos Puntos de Parada (origen y destino).<br>RN-RUT-002: Solo se puede eliminar una ruta si su estado es "Inactiva" y no tiene historial de viajes en los últimos 3 meses. |
|  Requisitos Relacionados |  RF-011 (Gestión de Horarios), RF-017 (Configuración de Puntos de Parada), RNF-GEO-001 (Precisión de geolocalización). |

2. CU-012: Iniciar y Finalizar Viaje

 | Campo  |  Descripción |
|---|---|
|  ID | CU-012  |
|  Nombre | Iniciar y Finalizar Viaje  |
|  Actores  | Conductor (primario), Sistema de gestión de flota (secundario)  |
|  Descripcion |  Permite al Conductor registrar el inicio de un viaje asignado, activar el seguimiento GPS en tiempo real y, al finalizar, registrar los datos del trayecto (incluyendo el tiempo total y la hora de llegada). |
|  Precondiciones | 1. El Conductor ha iniciado sesión.<br>2. El Conductor está asignado a un viaje programado y el bus está identificado.  |
|  Postcondiciones(Exito) | 1. Se registra la hora de inicio y fin del viaje.<br>2. Durante el viaje, el estado del bus se actualiza a "En Trayecto" y se transmite la ubicación.<br>3. Se calcula y registra el tiempo total y la puntualidad del viaje.  |
|  Flujo Principal | 1. El Conductor selecciona el viaje programado desde su interfaz.<br>2. El sistema muestra el resumen del viaje (ruta, hora de salida).<br>3. El Conductor presiona "Iniciar Viaje".<br>4. El sistema registra la hora de inicio y activa el módulo GPS.<br>5. Durante el trayecto, el sistema recibe y transmite la ubicación del bus (para CU-013).<br>6. Al llegar al destino final, el Conductor presiona "Finalizar Viaje".<br>7. El sistema registra la hora de fin y desactiva la transmisión GPS.<br>8. Fin del caso de uso.  |
| Flujos Alternativos   | 4a. Retraso en el Inicio: Si el Conductor intenta iniciar el viaje $\text{X}$ minutos después de la hora programada, el sistema genera una alerta y requiere una justificación antes de iniciar.  |
|  Flujos De Excepcion | 5a. Falla de Conexión GPS: Si el sistema detecta la pérdida de señal GPS durante más de 5 minutos, notifica al Conductor y registra el incidente. El viaje puede continuar, pero la ubicación deja de transmitirse.  |
|  Reglas De Negocio | RN-VIA-001: El seguimiento GPS debe estar activo mientras el estado del viaje sea "En Trayecto".<br>RN-VIA-002: El sistema debe calcular la puntualidad del viaje comparando la hora de llegada registrada con la hora de llegada programada.  |
|  Requisitos Relacionados | RF-013 (Seguimiento GPS), RF-018 (Reportes de Eficiencia), RNF-DISP-001 (Disponibilidad de la conexión GPS).  |

3. CU-013: Consultar Ubicación del Bus

| Campo  |  Descripción |
|---|---|
|  ID | CU-013  |
|  Nombre | Consultar Ubicación del Bus  |
|  Actores | Usuario (primario)  |
|  Descripcion | Permite al Usuario ver la ubicación en tiempo real del bus asignado a su ruta y obtener la hora estimada de llegada (ETA) a su parada.  |
|  Precondiciones |  1. El Usuario ha iniciado sesión.<br>2. El bus de la ruta seleccionada está en estado "En Trayecto" (vía CU-012). |
|  Postcondiciones(Exito) | 1. La interfaz del Usuario muestra la ubicación actualizada del bus.<br>2. Se actualiza la ETA a la parada del Usuario.  |
| Flujo Principal  |  1. El Usuario selecciona su ruta o el viaje activo en la aplicación.<br>2. El sistema verifica el estado del bus.<br>3. El sistema recibe las coordenadas GPS del bus y las mapea.<br>4. El sistema calcula el ETA del bus a la parada de interés del Usuario.<br>5. El sistema muestra la ubicación del bus en un mapa junto con el ETA.<br>6. El sistema actualiza la información continuamente.<br>7. Fin del caso de uso. |
|  Flujos Alternativos |  2a. Bus No en Trayecto: Si el bus está "En Terminal" o "Inactivo", el sistema muestra un mensaje indicando el horario de la próxima salida programada.<br>4a. Alta Demanda de Datos: Si la latencia es alta (mayor a RNF-001), el sistema muestra una advertencia sobre el posible retraso en la actualización. |
|  Flujos De Excepcion | 3a. Falla en el Servicio de Mapas: Si el servicio de mapas (ej. Google Maps) falla, el sistema muestra solo la última ubicación conocida en formato de texto.  |
|  Reglas De Negocio | RN-CONS-001: La ubicación solo debe mostrarse a Usuarios que han iniciado sesión y están asociados a la Universidad.<br>RN-CONS-002: El ETA se debe recalcular dinámicamente cada 30 segundos usando la velocidad actual del bus.  |
|  Requisitos Relacionados | RF-013 (Seguimiento GPS), RNF-001 (Tiempo de respuesta < 500ms), RNF-GEO-001 (Precisión de geolocalización).  |

4. CU-014: Registrar Asistencia por Código QR

| Campo  |Descripcion   |
|---|---|
|  ID |  CU-014 |
| Nombre  | Registrar Asistencia por Código QR  |
| Actores  | Conductor (primario), Usuario (secundario)  |
| Descripción  |  Permite al Conductor o a un dispositivo en el bus escanear el código QR del Usuario para registrar su abordaje y descenso en una parada específica, actualizando el número de pasajeros a bordo. |
| Precondiciones  | 1. El viaje está activo (vía CU-012).<br>2. El Usuario tiene su código QR activo en la aplicación.  |
|  Postcondiciones (Éxito) | 1. Se registra la hora, la parada y el tipo de evento (abordaje/descenso) en el historial del Usuario.<br>2. El contador de pasajeros a bordo del bus se actualiza.  |
| Flujo Principal  | 1. El Usuario presenta su código QR.<br>2. El Conductor (o el escáner) inicia la lectura.<br>3. El sistema valida el código QR y el estado del Usuario (activo/suspendido).<br>4. El sistema registra el evento (abordaje) con la hora y la parada actual.<br>5. El sistema incrementa el contador de pasajeros a bordo.<br>6. Se repiten los pasos 1-5 para el descenso (con decremento del contador).<br>7. Fin del caso de uso.  |
| Flujos Alternativos  | 3a. Código QR Inválido/Vencido: El sistema muestra un mensaje de error ("Código Inválido"). El Conductor debe solicitar al Usuario que actualice su código.<br>3b. Usuario Suspendido: El sistema muestra una alerta al Conductor ("Usuario Suspendido - No Permitir Abordaje"). El registro de asistencia NO se realiza.  |
| Flujos de Excepción  | 4a. Falla en la Conexión de Datos: Si no hay conexión, el registro se guarda localmente en el dispositivo del Conductor y se sincroniza automáticamente tan pronto se restablece la conexión.  |
| Reglas de Negocio  | RN-ASIS-001: Un Usuario no puede abordar si su estado es "Suspendido".<br>RN-ASIS-002: El registro debe incluir el ID del Usuario, la parada (ID) y la marca de tiempo (timestamp).  |
|  Requisitos Relacionados |  RF-012 (Registro de Asistencia), RNF-004 (Integridad transaccional), RNF-SINC-001 (Sincronización de datos offline). |
