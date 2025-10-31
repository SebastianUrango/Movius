

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
| **Postcondiciones** | 1. Si las credenciales son correctas, el auxiliar de despacho accede al sistema.<br>Si las credenciales son incorrectas, el sistema muestra un mensaje de error y no permite el acceso. |
| **Flujo Principal** | 1. El auxiliar de despacho abre el sistema MOVIUS.<br>2. El auxiliar selecciona la opción “Iniciar sesión”.<br>3. El sistema solicita las credenciales (usuario y contraseña).<br>4. El auxiliar ingresa las credenciales requeridas.<br>4. El sistema valida las credenciales (CU-02 Validar credenciales).<br>6. Si las credenciales son válidas, el sistema concede acceso al usuario.<br>7. El sistema muestra el menú principal del módulo correspondiente. |
| **Flujos Alternativos** | **4a.credenciales no validas**:<br>  4a1. El sistema detecta que las credenciales no son correctas.<br>4a2. El sistema ejecuta el caso de uso CU-03 Notificar credenciales incorrectas.<br>4a3. El auxiliar puede volver a intentar iniciar sesión o cancelar el proceso. |
| **Flujos de Excepción** | **5a. Usuario suspendido o con multas vencidas**:<br>  5a1. El sistema muestra advertencia "Usuario suspendido" o "Usuario tiene multas vencidas por $[monto]"<br>  5a2. El sistema NO permite continuar con el préstamo<br>  5a3. El sistema ofrece opción "Registrar pago de multa"<br>  5a4. Fin del caso de uso<br><br>**11a. Error al registrar préstamo (error de BD)**:<br>  11a1. El sistema muestra mensaje "Error al procesar préstamo. Intente nuevamente"<br>  11a2. El sistema registra el error en log con detalles técnicos<br>  11a3. NO se registra el préstamo<br>  11a4. NO se cambia el estado de los materiales<br>  11a5. El bibliotecario puede reintentar desde el paso 9 o cancelar<br>  11a6. Fin del caso de uso |
| **Requisitos Relacionados** | RF-030 (Registro de préstamo)<br>RF-031 (Validación de disponibilidad)<br>RF-032 (Validación de estado de usuario)<br>RF-033 (Generación de comprobante)<br>RNF-004 (Integridad transaccional)<br>RNFR-001 (Tiempo de respuesta) |
<br>
