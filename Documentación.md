# Módulo: Configuración
## 1. Gestión de Usuarios
### 1.1. Propósito
Permitir al administrador la creación, modificación y administración del acceso del personal al sistema.
### 1.2. Flujo de Creación de Usuario
El administrador debe ingresar los siguientes datos para el registro de una nueva cuenta:
* **Nombre Completo**
* **Email**
* **Rol:** (Selección única entre Administrador, Ventas, Producción y Operario).
### 1.3. Seguridad Inicial (Pre-Requisito)
* **Contraseña Predeterminada:** Al crear la cuenta, el sistema asignará automáticamente una contraseña inicial estándar (ej. `12345678`).
* **Cambio Obligatorio:** El usuario deberá cambiar esta contraseña predeterminada obligatoriamente en su primer inicio de sesión.
### 1.4. Visualización y Gestión (Tabla de Usuarios)
La interfaz de gestión debe listar los usuarios con las siguientes columnas:

| Columna      | Descripción                                                                         |
| :----------- | :---------------------------------------------------------------------------------- |
| **Usuario**  | Nombre Completo del colaborador.                                                    |
| **Email**    | Correo electrónico de la cuenta.                                                    |
| **Rol**      | Rol asignado (Administrador, Ventas, Producción, Operario).                         |
| **Estado**   | Indicador del estado actual de la cuenta (ver **Duda 1** en Puntos Pendientes).     |
| **Acciones** | Conjunto de acciones de gestión (CRUD: Crear, Consultar, **Editar**, **Eliminar**). |

---
## 2. Configuración del Negocio
### 2.1. Propósito
Centralizar la modificación de los datos corporativos de la empresa, asegurando que la información utilizada en documentos y reportes esté actualizada.
## 2.2. Campos Configurables
El sistema permitirá la edición de los siguientes datos, con un botón único de "Actualizar" para guardar todos los cambios:
* **Nombre de Empresa**
* **Dirección**
* **Teléfono**
* **Email Corporativo**
* **RUC** (Registro Único de Contribuyentes)
* **Tipo de Moneda:** (Selección única entre Soles, Dólar y Euro).
---
## 3. Roles y Permisos
### 3.1. Propósito
Definir y administrar las capacidades de acceso y las acciones permitidas para cada **Rol** (Administrador, Ventas, Producción y Operario) dentro del sistema.
### 3.2. Alcance de la Administración
Los permisos se gestionarán a nivel de **Módulo** y a nivel de **Acciones Sensibles**.
#### 3.2.1. Permisos por Módulo (Acceso General)
* Dashboard
* Agenda
* Pedidos
* Clientes
* Inventario
* Activos
* Gastos
* Producción
* Contratos
* Reportes
#### 3.2.2. Permisos por Acciones Sensibles
Se requiere definir qué acciones específicas (ej. "Eliminar Pedido", "Modificar Costo Unitario") son consideradas sensibles y deben ser administrables por rol (ver **Duda 2**).
### 3.3. Funcionalidades de Gestión
* **Guardar Permisos:** Persistir las modificaciones realizadas a los permisos del rol seleccionado.
* **Restablecer por Defecto:** Opción para restaurar todos los permisos del rol a su configuración inicial predeterminada.
---
## 4. Puntos Pendientes y a Clarificar (Dudas)

| ID         | Área                                      | Descripción y Requerimiento de Decisión                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| :--------- | :---------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Duda 1** | **Gestión de Usuarios - Estado**          | **Definición de Estados de Usuario:** Se requiere confirmar el conjunto y la lógica para la columna "Estado" de la tabla de usuarios, proponiéndose la siguiente clasificación: <ul><li>**ACTIVO:** ¿El usuario debe considerarse ACTIVO cuando ha iniciado sesión recientemente (conectado) o simplemente cuando la cuenta está habilitada?</li><li>**INACTIVO:** ¿El estado INACTIVO se aplica cuando el usuario no ha iniciado sesión en un periodo prolongado (no conectado)?</li><li>**PENDIENTE DE CONFIGURACIÓN:** ¿Este estado se aplica específicamente cuando el usuario aún no ha cambiado su contraseña inicial predeterminada?</li><li>**BLOQUEADO:** (Opcional) ¿Se debe incluir un estado para cuentas suspendidas manualmente por el administrador o por fallos de inicio de sesión?</li></ul> |
| **Duda 2** | **Roles y Permisos - Acciones Sensibles** | **Definición de Acciones Sensibles:** Es necesario consultar y especificar qué operaciones dentro del sistema se clasificarán como "Acciones Sensibles" (por ejemplo, Eliminar Registros, Anular Movimientos, Modificar Precios/Costos).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

***
# Módulo: Mi Perfil
## 1. Propósito
Permitir a cada usuario visualizar sus datos personales y métricas de rendimiento individual, además de gestionar la seguridad y la información de su propia cuenta.
## 2. Componentes de la Vista

| Sección                    | Contenido                                                                                                                  |
| :------------------------- | :------------------------------------------------------------------------------------------------------------------------- |
| **Datos Personales**       | Muestra el Nombre, Email, Teléfono, Rol, Dirección y Biografía del usuario.                                                |
| **Estado de Cuenta**       | Incluye un indicador de "Cuenta Verificada" y las fechas de registro y última conexión al sistema.                         |
| **Estadísticas Mensuales** | Indicadores de rendimiento del mes actual: Pedidos Procesados, Clientes Atendidos, Sesiones Realizadas y Horas Trabajadas. |
| **Actividad Reciente**     | Lista cronológica de los eventos y acciones recientes del usuario con su marca de tiempo.                                  |
## 3. Acciones de Usuario (Autogestión)
### 3.1. Cambiar Email
Requiere que el usuario ingrese y confirme los siguientes datos para la actualización:
* Contraseña Actual (para verificación de identidad)
* Nuevo Email
* Confirmar Nuevo Email
### 3.2. Cambiar Contraseña
Requiere que el usuario ingrese y confirme los siguientes datos:
* Contraseña Actual
* Nueva Contraseña
* Confirmar Nueva Contraseña
### 3.3. Editar Perfil
Permite la modificación directa de los siguientes campos personales:
* Nombre
* Email
* Teléfono
* Dirección
* Biografía
---
# Módulo: Reportes
## 1. Funcionalidad Común
### 1.1. Exportación de Datos
El módulo debe proporcionar la capacidad de exportar los datos visibles en las vistas de reportes en los siguientes formatos:
* **Excel**
* **PDF**
**Duda de Alcance:** Se requiere definir si la exportación aplicará a **todos los datos del reporte visible** o si se debe agregar una **opción de selección de categoría/vista** para la exportación.
### 1.2. Filtrado por Periodo de Tiempo
El módulo debe permitir la aplicación de filtros de tiempo sobre los datos mostrados.
#### 1.2.1. Rango Personalizado
* **Fecha a Fecha:** Filtro que permite seleccionar un rango específico de inicio y fin.
	#### 1.2.2. Opciones Predeterminadas
* Hoy
* Esta Semana
* Este Mes
* Este Trimestre
* Este Año
---
## 2. Categorías de Reportes
### 2.1. Ventas
#### 2.1.1. Métricas (Tarjetas de Resumen)

| Métrica                 | Definición                                                                                                                         | Requerimiento de Clarificación                                                                                                                                                                                                                                                                                                                                                    |
| :---------------------- | :--------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ventas Totales**      | Suma total del monto de Ventas combinadas de todos los tipos de producto en el periodo filtrado.                                   | El campo es claro?                                                                                                                                                                                                                                                                                                                                                                |
| **Pedidos Completados** | Conteo de registros en el Módulo de Pedidos que tienen el estado "Completado".                                                     | El campo es claro?                                                                                                                                                                                                                                                                                                                                                                |
| **Ticket Promedio**     | Valor promedio de los pedidos realizados en el periodo filtrado.                                                                   | **Clarificación:** El origen de este cálculo debe ser definido (ej. la suma total de ventas dividida entre el número de pedidos completados).                                                                                                                                                                                                                                     |
| **Crecimiento**         | Indicador de la variación porcentual de las ventas con respecto a un periodo anterior comparable (ej. este mes vs. el mes pasado). | **Clarificación Funcional y Cálculo:** ¿Cómo se define exactamente un "Ticket" en este cálculo (entendiéndose como **una boleta o transacción de venta final**)? Se requiere confirmar la fórmula: ¿El cálculo debe ser la $\frac{\text{Suma Total de Ventas}}{\text{Cantidad de Transacciones de Venta (Boletas/Facturas Emitidas)}}$ para obtener el valor promedio por ticket? |

#### 2.1.2. Tablas de Detalle
**Tabla 1: Ventas por Tipo de Producto**
El tipo de producto incluye: Enmarcados, Minilab, Graduaciones, Corte Láser y **(Requerido: ¿Incluir Accesorios?)**.

| Columna              | Descripción                                                                                |
| :------------------- | :----------------------------------------------------------------------------------------- |
| **Tipo de Producto** | Categoría del producto.                                                                    |
| **Cantidad**         | Número total de ítems vendidos por cada tipo de producto.                                  |
| **Monto**            | Precio total sumado de la cantidad vendida de cada tipo de producto.                       |
| **% del Total**      | Proporción del monto de ventas de este tipo de producto respecto al Monto Total de Ventas. |

**Tabla 2: Top (10) Clientes del Periodo**

| Campo           | Descripción                                                              |
| :-------------- | :----------------------------------------------------------------------- |
| **Cliente**     | Nombre del cliente con el mayor número de pedidos.                       |
| **Pedidos**     | Cantidad de pedidos realizados (ordenado de mayor a menor).              |
| **Monto Total** | Suma total de todos los pedidos realizados por el cliente en el periodo. |

---
### 2.2. Inventario
#### 2.2.1. Métricas (Tarjetas de Resumen)

| Métrica                       | Definición                                                                                                                            | Requerimiento de Clarificación                                                                                                |
| :---------------------------- | :------------------------------------------------------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------- |
| **Valor Total de Inventario** | Suma total del valor monetario (costo total) de todos los ítems en el modulo inventario.                                              | El campo es claro?                                                                                                            |
| **Ítems Bajo Stock**          | Suma total de todos los ítems de inventario cuyo Stock Actual es igual o menor al Stock Mínimo.                                       | El campo es claro?                                                                                                            |
| **Sin Movimiento**            | Conteo o valor total de los ítems de inventario que no han tenido movimientos (entrada o salida) en un periodo de tiempo determinado. | **Clarificación:** Se requiere definir el periodo de inactividad (ej. 90 días) para clasificar un ítem como "Sin Movimiento". |
#### 2.2.2. Tablas de Detalle
**Tabla 1: Inventario por Categoría**
Las categorías incluyen: Enmarcados, Minilab, Graduaciones, Corte Láser y **(Requerido: Incluir Accesorios)**.

| Columna        | Descripción                                                                                 | Requerimiento de Clarificación                                                                 |
| :------------- | :------------------------------------------------------------------------------------------ | :--------------------------------------------------------------------------------------------- |
| **Categoría**  | Clasificación del inventario.                                                               | El campo es claro?                                                                             |
| **Valor**      | Suma total del Costo Total de todos los ítems bajo esa categoría.                           | El campo es claro?                                                                             |
| **Ítems**      | Suma total de unidades (incluyendo subcategorías) dentro de la categoría.                   | El campo es claro?                                                                             |
| **Stock Bajo** | Cantidad total de ítems de la categoría cuyo stock actual es igual o menor al stock mínimo. | **Clarificación:** Esta métrica debe ser calculada como un contador de las unidades en alerta. |

**Tabla 2: Alertas de Reabastecimiento** (Datos obtenidos directamente del Módulo de Inventario)

| Columna          | Descripción                                                 |
| :--------------- | :---------------------------------------------------------- |
| **Producto**     | Ítem cuyo Stock Actual es igual o inferior al Stock Mínimo. |
| **Categoría**    | Clasificación del producto.                                 |
| **Stock Actual** | Cantidad física en el inventario.                           |
| **Stock Mínimo** | Umbral definido para la alerta de reposición.               |

---
### 2.3. Producción

#### 2.3.1. Métricas (Tarjetas de Resumen)

| Métrica             | Definición                                                                                                | Requerimiento de Clarificación                         |
| :------------------ | :-------------------------------------------------------------------------------------------------------- | :----------------------------------------------------- |
| **Órdenes Activas** | Cantidad de pedidos que se encuentran actualmente en estado de "Proceso" dentro del Módulo de Producción. | El campo es claro?                                     |
| **Completados**     | Cantidad de pedidos que han alcanzado el estado "Terminado" en el periodo filtrado.                       | El campo es claro?                                     |
| **Atrasados**       | Cantidad de órdenes de producción que han excedido su fecha límite de entrega establecida.                | El campo es claro?                                     |
| **Tiempo Promedio** | El tiempo promedio que toma completar una orden de producción.                                            | **Clarificación:** Explicar como funciona esta tarjeta |
#### 2.3.2. Tablas de Detalle
**Tabla 1: Desempeño por Operario**

| Columna             | Descripción                                                                | Requerimiento de Clarificación                                                                                                                  |
| :------------------ | :------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Operario**        | Nombre del empleado con el rol "Operario".                                 | El campo es claro?                                                                                                                              |
| **Completados**     | Suma total de pedidos o tareas terminadas por el operario en el periodo.   | El campo es claro?                                                                                                                              |
| **Tiempo Promedio** | El tiempo promedio que le toma al operario completar sus tareas asignadas. | **Clarificación:** Necesita una definición de la medición (ej. horas/tarea, o tiempo total dividido por tareas). ¿Cómo es esto?                 |
| **Eficiencia**      | Métrica de rendimiento del operario.                                       | **Clarificación:** Se requiere definir la fórmula (posiblemente la relación entre el tiempo real vs. tiempo estándar o la tasa de completados). |

**Tabla 2: Mermas y Desperdicios** (Relacionado con Inventario)

| Columna      | Descripción                                                                    |
| :----------- | :----------------------------------------------------------------------------- |
| **Producto** | El ítem del inventario que fue clasificado como merma o defectuoso.            |
| **Cantidad** | El total de unidades del producto que se consideran defectuosas.               |
| **Costo**    | La suma total del costo (Costo Unitario x Cantidad) de los productos de merma. |
| **Motivo**   | Descripción del problema o causa de la merma.                                  |

---
### 2.4. Clientes

#### 2.4.1. Métricas (Tarjetas de Resumen)

| Métrica | Definición |
| :--- | :--- |
| **Total de Clientes** | Suma total de clientes registrados en el sistema. |
| **Clientes Activos** | Clientes que han realizado al menos un pedido que se encuentra o ha pasado por el Módulo de Producción en el periodo filtrado. |
| **Clientes Nuevos** | Clientes registrados por primera vez en el sistema dentro del periodo filtrado. |
| **Inactivos** | Clientes que no han realizado ningún pedido que haya llegado a Producción en el periodo filtrado. |
#### 2.4.2. Tablas de Detalle

**Tabla 1: Segmentación de Clientes**

| Columna             | Descripción                                                          |
| :------------------ | :------------------------------------------------------------------- |
| **Tipo de Cliente** | Las 3 clasificaciones: Particular, Colegio y Empresa.                |
| **Cantidad**        | Suma total de clientes bajo esa clasificación.                       |
| **Ventas Totales**  | Suma total de los montos de venta generados por ese tipo de cliente. |
| **Ticket Promedio** | El monto promedio de los pedidos generados por ese tipo de cliente.  |

**Tabla 2: Mejores Clientes (LTV)**

| Columna           | Descripción                                                                                                                                                            | Requerimiento de Clarificación |
| :---------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------- |
| **Cliente**       | Nombre del cliente.                                                                                                                                                    | El campo es claro?             |
| **Pedidos**       | Total de pedidos histórico realizados por el cliente (registrados en el Modulo Cliente).                                                                               | El campo es claro?             |
| **Total Compras** | Suma total de todos los montos de pedido del cliente (ordenado de mayor a menor).                                                                                      | El campo es claro?             |
| **Última Compra** | Fecha del pedido más reciente del cliente.                                                                                                                             | El campo es claro?             |
| **LTV**           | **Clarificación:** LTV (LifeTime Value) se refiere al **Valor de Vida del Cliente**, que es la ganancia total proyectada que una empresa puede esperar de ese cliente. | El campo es claro?             |

	---
### 2.5. Financiero

#### 2.5.1. Métricas (Tarjetas de Resumen)

| Métrica              | Definición                                                                                           | Requerimiento de Clarificación                                                                                                                                                                                    |
| :------------------- | :--------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ingresos Totales** | Suma total de la columna "Ingresos" de la tabla de rentabilidad.                                     | El campo es claro?                                                                                                                                                                                                |
| **Costos Totales**   | Suma total de la columna "Costos" de la tabla de rentabilidad.                                       | El campo es claro?                                                                                                                                                                                                |
| **Utilidad Bruta**   | Suma total de la columna "Utilidad" de la tabla de rentabilidad.                                     | El campo es claro?                                                                                                                                                                                                |
| **Margen Bruto**     | La utilidad bruta total dividida entre el número de tipos de producto (filas) mostrados en la tabla. | **Clarificación:** La fórmula estándar es $\frac{\text{Utilidad Bruta Total}}{\text{Ingresos Totales}} \times 100$. Se sugiere confirmar si la intención es usar esta fórmula o el promedio por tipo de producto. |

**Apartado Visual:** Muestra la cantidad pendiente de cobro y una estimación porcentual de los ingresos del periodo.
#### 2.5.2. Tabla de Detalle
**Tabla 1: Rentabilidad por Tipo de Producto**
Los tipos de producto incluyen: Enmarcados, Minilab, Graduaciones, Corte Láser y **(Requerido: Incluir Accesorios)**.

| Columna              | Descripción                                                                                          |
| :------------------- | :--------------------------------------------------------------------------------------------------- |
| **Tipo de Producto** | Categoría del producto.                                                                              |
| **Ingresos**         | Monto total de ventas generadas por este tipo de producto.                                           |
| **Costos**           | Costo total de los materiales (Inventario) y recursos asociados a la venta de este tipo de producto. |
| **Utilidad**         | Ingresos - Costos.                                                                                   |
| **Margen**           | Utilidad / Ingresos (expresado en porcentaje).                                                       |

---
### 2.6. Contratos
#### 2.6.1. Métricas (Tarjetas de Resumen)

| Métrica                   | Definición                                                                                                            |
| :------------------------ | :-------------------------------------------------------------------------------------------------------------------- |
| **Contratos Activos**     | Cantidad de contratos que se encuentran en el estado "Activo" en el Módulo de Contratos.                              |
| **Valor Total**           | Suma total de la columna "Valor" de la tabla de estado de contratos.                                                  |
| **Próximo a Vencer**      | Cantidad de contratos cuya fecha de vencimiento está dentro de un rango próximo (filtrado por fecha).                 |
| **Cumplimiento de Pagos** | Métrica relacionada con la frecuencia o porcentaje de pagos realizados antes de la fecha de vencimiento del contrato. |
#### 2.6.2. Tabla de Detalle
**Tabla 1: Estado de Contratos**

| Columna         | Descripción                                                      |
| :-------------- | :--------------------------------------------------------------- |
| **Nº Contrato** | Código de identificación único del contrato.                     |
| **Cliente**     | Nombre del cliente asociado al contrato.                         |
| **Valor**       | El precio total acordado del contrato.                           |
| **Pagado**      | La cantidad de dinero que ya ha sido abonada.                    |
| **Saldo**       | La cantidad pendiente de pago (Valor - Pagado).                  |
| **Vencimiento** | Fecha límite para el cumplimiento del contrato o el último pago. |

---
# Módulo: Gestión de Contratos
## 1. Propósito y Alcance
El Módulo de Contratos formaliza los acuerdos de servicio con los clientes. Su objetivo es gestionar el ciclo de vida completo de cada acuerdo, desde el borrador hasta su cierre, manteniendo un control estricto sobre las vigencias y los flujos de pago.
### 1.1. Atributos del Contrato

| Atributo             | Descripción                                                       | Notas de Integración                                |
| :------------------- | :---------------------------------------------------------------- | :-------------------------------------------------- |
| **Cliente**          | Entidad con la que se formaliza el acuerdo.                       | Relacionado directamente con el Módulo de Clientes. |
| **Servicio**         | Descripción del servicio u objeto del contrato.                   |                                                     |
| **Tipo de Contrato** | Define la duración o naturaleza del acuerdo.                      | Opciones: Anual, Semestral, Mensual, Por Proyecto.  |
| **Responsable**      | Usuario interno asignado a la supervisión del contrato.           | El campo es claro?                                  |
| **Fecha de Inicio**  | Fecha de entrada en vigor del acuerdo.                            | El campo es claro?                                  |
| **Fecha de Fin**     | Fecha de terminación de la vigencia.                              | El campo es claro?                                  |
| **Valor Total**      | Precio total del acuerdo.                                         | El campo es claro?                                  |
| **Monto Pagado**     | Cantidad de dinero recibido hasta la fecha.                       | El campo es claro?                                  |
| **Saldo**            | Monto pendiente de pago (Cálculo: Valor Total - Monto Pagado).    | El campo es claro?                                  |
| **Nro. Estudiantes** | Indicador opcional del alcance del servicio (si aplica).          | El campo es claro?                                  |
| **Observaciones**    | Campo de texto libre para notas internas.                         | El campo es claro?                                  |
| **Cláusulas**        | Texto legal o resumen de las condiciones específicas del acuerdo. | El campo es claro?                                  |
## 2. Métricas de Resumen (Tarjetas)
La vista principal del módulo incluye tarjetas que resumen el estado financiero y la actividad de los contratos:

| Métrica             | Definición                                                                              | Cálculo                                               |
| :------------------ | :-------------------------------------------------------------------------------------- | :---------------------------------------------------- |
| **Total Contratos** | Cantidad total de contratos registrados en el sistema, independientemente de su estado. | Conteo de todos los registros.                        |
| **Activos**         | Cantidad de contratos que se encuentran en estado **'Activo'** o **'En Ejecución'**.    | Conteo de registros con el estado relevante.          |
| **Valor Total**     | La suma total del valor monetario de todos los contratos registrados.                   | Suma del campo `Valor Total` de todos los contratos.  |
| **Total Pagado**    | La suma total de todos los montos recibidos a cuenta de los contratos.                  | Suma del campo `Monto Pagado` de todos los contratos. |

## 3. Estados del Ciclo de Vida (Workflow)

El campo **Estado** debe permitir la transición a cualquiera de los siguientes valores para reflejar la etapa actual del contrato:
* Borrador
* Firmado
* Activo
* En Ejecución
* Finalizado
* Entregado
* Pagado
* Cerrado
* Pendiente
* Completado
* Vencido
¿No se supone que estos estados deben estar dentro al registrar un contrat?
## 4. Funcionalidades y Acciones
* **CRUD Completo:** El módulo debe soportar las operaciones de Crear, Consultar, Modificar (Editar) y Eliminar.
* **Descarga:** Opción para descargar el documento del contrato en formato **PDF**.
* **Visualización Interconectada:** Se debe permitir la consulta de datos relacionados con el contrato desde las siguientes vistas: **Pagos**, **Agenda**, **Pedidos** y **Producción**.
* **Cálculo de Progreso de Pago:** Se requiere que el sistema calcule el porcentaje de pago realizado para visualización en las tarjetas de detalle: $$\text{Progreso de Pago} = \frac{\text{Monto Pagado}}{\text{Valor Total}} \times 100$$
* **Botón de Reset de Datos:** Funcionalidad para **eliminar todos los contratos** registrados en el sistema (requiere alerta de confirmación).
### 4.1. Filtros
* **Búsqueda General:** Por Cliente o por Servicio.
* **Por Estado:** Filtrar por cualquiera de los estados listados en la Sección 3.
* **Por Tipo:** Filtrar por Anual, Semestral, Mensual o Por Proyecto.

---
# Módulo: Gestión de Producción
## 1. Propósito y Alcance
Permite planificar, ejecutar y monitorear el flujo de trabajo asociado a los pedidos de los clientes, gestionando la asignación de recursos y el seguimiento de los tiempos.
### 1.1. Atributos de la Orden de Producción (OP)

| Atributo           | Descripción                                                          | Notas                                                                                                                                    |
| :----------------- | :------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------- |
| **N° OP**          | Identificador único de la orden de producción.                       | El campo es claro?                                                                                                                       |
| **Pedido**         | Referencia al pedido que originó la orden.                           | El campo es claro?                                                                                                                       |
| **Cliente**        | Entidad a la que corresponde la producción.                          | Relacionado con el Módulo de Clientes.                                                                                                   |
| **Descripción**    | Detalles del trabajo a realizar.                                     | El campo es claro?                                                                                                                       |
| **Tipo**           | Categoría del servicio de producción.                                | Opciones: Enmarcado, Minilab, Graduación, Corte Láser, Edición Digital, Otro. **Pendiente de Clarificación: ¿Falta incluir Accesorios?** |
| **Estado**         | Etapa actual del trabajo.                                            | Opciones: Pendiente, En Proceso, Terminado, Entregado.                                                                                   |
| **Prioridad**      | Nivel de urgencia de la OP.                                          | Opciones: Baja, Normal, Media, Alta.                                                                                                     |
| **Operario**       | Usuario asignado a la ejecución del trabajo.                         | **Requerimiento:** Debe ser un usuario con el rol o cargo de "Operario".                                                                 |
| **Fecha Estimada** | Fecha de compromiso para la finalización o entrega de la producción. | **Clarificación:** Se asume que es la fecha límite de entrega al cliente.                                                                |
### 1.2. Gestión y Visualización
#### 1.2.1. Tabla de Órdenes de Producción
La tabla de gestión debe listar las Órdenes de Producción con las siguientes columnas:
* N° OP
* Pedido
* Cliente
* Descripción
* Tipo
* Estado
* Prioridad
* Operario
* Fecha Estimada
* **Acciones:** (Ver, Editar, Eliminar)
#### 1.2.2. Vistas (Pestañas)
La interfaz debe organizarse mediante pestañas para facilitar el monitoreo del flujo:
* Todos
* Pendientes
* En Proceso
* Terminados
* Entregados
**Funcionalidad de Pestañas:**
1.  Cada pestaña debe llenarse **automáticamente** en función del **Estado** de la Orden de Producción.
2.  Se debe permitir la opción de **adición manual** de una orden de producción a través de un botón.
#### 1.2.3. Búsqueda
Se debe implementar un campo de búsqueda eficiente por los siguientes criterios:
* N° OP
* Cliente
* Pedido
* Descripción
* Otros campos de texto libre.
---
# Módulo: Gestión de Gastos
## 1. Propósito y Alcance
Este módulo permite el registro y control financiero de los gastos operativos de la empresa, específicamente categorizados en **Gastos de Personal** (Nómina) y **Gastos de Servicios y Suministros**.
### 1.1. Métricas de Resumen (Tarjetas)
La vista principal debe mostrar el estado financiero de los gastos pendientes y vencidos:
1.  **Nómina Pendiente:** Suma total del **Salario Neto** de los gastos de personal que se encuentran en estado **Pendiente**.
2.  **Servicios Pendientes:** Suma total del **Monto** de los gastos de servicios que se encuentran en estado **Pendiente**.
3.  **Servicios Vencidos:** Suma total del **Monto** de los gastos de servicios que se encuentran en estado **Vencido**.
### 1.2. Gasto de Personal (Nómina)

| Campo               | Descripción                            | Requerimiento de Clarificación                                                                                                                |
| :------------------ | :------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- |
| **Código**          | Identificador del trabajador/nómina.   | El campo es claro?                                                                                                                            |
| **Nombre Completo** | Identificación del empleado.           | El campo es claro?                                                                                                                            |
| **Cargo**           | Puesto del empleado.                   | El campo es claro?                                                                                                                            |
| **Salario Base**    | Remuneración fija.                     | El campo es claro?                                                                                                                            |
| **Bonificaciones**  | Ingresos adicionales.                  | El campo es claro?                                                                                                                            |
| **Descuentos**      | Deducciones aplicables.                | El campo es claro?                                                                                                                            |
| **Fecha de Pago**   | Fecha programada o ejecutada del pago. | El campo es claro?                                                                                                                            |
| **Estado**          | Estado del pago.                       | Opciones: Pendiente y Pagado. **Clarificación:** ¿Se debe incluir el estado **Atrasado** para pagos que no se realizaron en la Fecha de Pago? |
**Dato Extra (Cálculo):** El sistema debe generar y almacenar el campo **Salario Neto**, calculado mediante la operación: $\text{Salario Neto} = (\text{Salario Base} + \text{Bonificaciones}) - \text{Descuentos}$.
### 1.3. Servicios y Suministros

| Campo                    | Descripción                                                                             |
| :----------------------- | :-------------------------------------------------------------------------------------- |
| **Código**               | Identificador del gasto de servicio.                                                    |
| **Tipo de Servicio**     | Clasificación del gasto. Opciones: Alquiler, Luz, Agua, Internet, Teléfono, Gas y Otro. |
| **Proveedor**            | Entidad o empresa que presta el servicio.                                               |
| **Monto**                | Valor monetario del gasto.                                                              |
| **Fecha de Vencimiento** | Fecha límite para realizar el pago.                                                     |
| **Fecha de Pago**        | Fecha en la que se realizó la transacción.                                              |
| **Estado**               | Estado de la obligación. Opciones: Pendiente, Pagado y Vencido.                         |
| **Periodo**              | Mes o rango de tiempo al que corresponde el gasto.                                      |
### 1.4. Gestión y Visualización
#### 1.4.1. Tabla de Gestión de Gastos
La tabla de visualización debe unificar ambos tipos de gastos con las siguientes columnas, adaptando la información según el tipo de gasto (Personal o Servicio):
* **Código**
* **Tipo/Nombre/Proveedor:** Muestra el tipo de servicio (si es servicio) o el nombre del empleado/proveedor (si es personal/servicio).
* **Monto:** Muestra el Salario Neto (si es personal) o el Monto (si es servicio).
* **Estado**
* **Fechas (Vencimiento/Pago):** Muestra la Fecha de Vencimiento o la Fecha de Pago, según sea más relevante o aplicable.
* **Acciones:** (CRUD completo: Crear, Consultar, Editar, Eliminar).
#### 1.4.2. Filtro
* **Búsqueda General:** Permitir la búsqueda por **servicio** (aplicable a ambos tipos de gasto si se considera el empleado como un "servicio" de personal).
---
# Módulo: Gestión de Activos Fijos 
## 1. Descripción General y Estructura
Este módulo es responsable de la **gestión integral de los activos fijos** de la empresa (maquinaria, equipos, herramientas). Se divide en cuatro submódulos interconectados para controlar el ciclo de vida del activo, desde su adquisición hasta su mantenimiento y el control de sus repuestos asociados.
### 1.1. Lógica de Interconexión (Backend Flow)
La información fluye a través de los submódulos de la siguiente manera:
1.  **Activación de Flujos:** El registro de un nuevo activo en **Activos** inicia el flujo de datos.
2.  **Financiamiento:** Se genera un registro automático si el campo `Tipo de Pago` del activo es **Financiado** o **Leasing**.
3.  **Mantenimientos:** Se genera un registro automático si el campo `Estado` del activo es **Mantenimiento**.
4.  **Repuestos:** Es un submódulo **independiente** que se gestiona únicamente de forma manual.
***
## 2. Gestión de Activos (Submódulo Activos)
### 2.1. Atributos de Creación

| Atributo                      | Descripción                                              | Notas de Backend                                                                |
| :---------------------------- | :------------------------------------------------------- | :------------------------------------------------------------------------------ |
| **Nombre del Activo**         | Nombre descriptivo (Ej: Impresora Láser).                | El campo es claro?                                                              |
| **Categoría**                 | Clasificación del activo.                                | El campo es claro?                                                              |
| **Proveedor**                 | Empresa que vendió o suministró el activo.               | El campo es claro?                                                              |
| **Fecha de Compra**           | Fecha de adquisición.                                    | El campo es claro?                                                              |
| **Costo Total (S/)**          | Monto total de adquisición.                              | El campo es claro?                                                              |
| **Tipo de Pago**              | Método de adquisición.                                   | Define Flujo a Financiamientos.                                                 |
| **Vida Útil (meses)**         | Duración esperada del activo (Ej: 60 meses).             | El campo es claro?                                                              |
| **Depreciación Mensual (S/)** | Monto mensual calculado de la pérdida de valor.          | **Cálculo Automático:** $$\frac{\text{Costo Total}}{\text{Vida Útil (meses)}}$$ |
| **Estado**                    | Condición actual del activo (Ej: Activo, Mantenimiento). | Define Flujo a Mantenimientos.                                                  |
### 2.2. Listado de Activos

| Columna | Descripción |
| :--- | :--- |
| **ID** | Código o identificador numérico único. |
| **Nombre** | Nombre descriptivo del activo. |
| **Categoría** | Clasificación del activo. |
| **Proveedor** | Empresa que suministró el activo. |
| **Costo Total** | Monto total de adquisición. |
| **Tipo de Pago** | Contado, Financiado o Leasing. |
| **Estado** | Condición actual del activo. |
| **Acciones** | (Observar, Editar, Eliminar). |
***
## 3. Financiamientos (Submódulo Financiamientos)

### 3.1. Propósito
Gestionar y monitorear las deudas asociadas a la adquisición de activos.
### 3.2. Atributos de Creación

| Atributo                  | Descripción                                               | Notas de Backend                                                                  |
| :------------------------ | :-------------------------------------------------------- | :-------------------------------------------------------------------------------- |
| **Activo**                | Activo que está siendo financiado.                        | Relación obligatoria 1:1 con un activo.                                           |
| **Tipo de Pago**          | Tipo de esquema de crédito (Financiado, Leasing).         | El campo es claro?                                                                |
| **Entidad Financiera**    | Institución que otorga el crédito (Ej: Banco de Crédito). | El campo es claro?                                                                |
| **Monto Financiado (S/)** | Cantidad total sujeta a crédito.                          | El campo es claro?                                                                |
| **Cuotas Totales**        | Número total de cuotas del financiamiento (Ej: 24).       |                                                                                   |
| **Cuota Mensual (S/)**    | Monto periódico a pagar.                                  | **Cálculo Automático:** $$\frac{\text{Monto Financiado}}{\text{Cuotas Totales}}$$ |
| **Fecha de Inicio**       | Fecha de inicio de los pagos.                             | El campo es claro?                                                                |
| **Fecha de Fin**          | Fecha de finalización del financiamiento.                 | **Cálculo Automático:** Suma la duración (Cuotas Totales) a la Fecha de Inicio.   |
| **Estado**                | Estado actual del financiamiento (Ej: Activo).            | El campo es claro?                                                                |
### 3.3. Listado de Financiamientos

| Columna              | Descripción                                    |
| :------------------- | :--------------------------------------------- |
| **Código**           | Código asociado al financiamiento.             |
| **Activo**           | Nombre del activo financiado.                  |
| **Entidad**          | Institución que otorga el crédito.             |
| **Monto Financiado** | Cantidad total financiada.                     |
| **Cuota Mensual**    | Monto periódico a pagar.                       |
| **Cuotas Pagadas**   | Progreso de pagos (Ej: 20 / 24).               |
| **Próximo Pago**     | Fecha del siguiente vencimiento de cuota.      |
| **Estado**           | Estado actual del financiamiento (Ej: Activo). |
| **Acciones**         | (Observar, Editar, Eliminar).                  |
***
## 4. Mantenimientos (Submódulo Mantenimientos)
### 4.1. Propósito
Gestionar y programar los mantenimientos preventivos o correctivos requeridos.
### 4.2. Atributos de Creación

| Atributo                        | Descripción                                          | Notas de Backend                                                                 |
| :------------------------------ | :--------------------------------------------------- | :------------------------------------------------------------------------------- |
| **Activo**                      | Activo al que se aplica el mantenimiento.            | Relación obligatoria 1:1 con un activo.                                          |
| **Tipo de Mantenimiento**       | Clasificación (Preventivo, Correctivo).              | El campo es claro?                                                               |
| **Costo (S/)**                  | Costo del servicio de mantenimiento.                 | El campo es claro?                                                               |
| **Proveedor**                   | Empresa o técnico que brinda el servicio.            | El campo es claro?                                                               |
| **Fecha de Mantenimiento**      | Fecha programada o realizada del servicio.           | El campo es claro?                                                               |
| **Estado del Mantenimiento**    | Condición del registro (Ej: Programado, Completado). | El campo es claro?                                                               |
| **Estado del Activo**           | Condición que adoptará el activo principal.          | **Requiere actualizar el campo 'Estado' del Activo principal.**                  |
| **Próximo Mantenimiento**       | Fecha del siguiente mantenimiento sugerido.          | **Cálculo Automático:** Se asume un cálculo basado en la Fecha de Mantenimiento. |
| **Descripción**                 | Detalles del mantenimiento.                          | El campo es claro?                                                               |
| **Repuestos/Insumos Asociados** | Ítems del Módulo Repuestos utilizados.               | **Requiere decremento de stock en el Módulo Repuestos.**                         |
### 4.3. Listado de Mantenimientos

| Columna | Descripción |
| :--- | :--- |
| **Código** | Código asociado al registro de mantenimiento. |
| **Activo** | Nombre del activo. |
| **Tipo** | Clasificación del mantenimiento. |
| **Fecha** | Fecha programada o realizada. |
| **Costo** | Costo del servicio. |
| **Proveedor** | Empresa o técnico que brinda el servicio. |
| **Estado** | Condición del mantenimiento (Ej: Programado, Completado). |
| **Acciones** | (Observar, Editar, Eliminar). |
***
## 5. Repuestos (Submódulo Repuestos)

### 5.1. Propósito
Gestionar el inventario de repuestos e insumos críticos para los activos.
### 5.2. Atributos de Creación

| Atributo                | Descripción                         |
| :---------------------- | :---------------------------------- |
| **Nombre del Repuesto** | Nombre descriptivo.                 |
| **Categoría**           | Clasificación.                      |
| **Proveedor**           | Empresa que suministra el repuesto. |
| **Código**              | Identificador único del repuesto.   |
| **Stock Actual**        | Cantidad actual disponible.         |
| **Stock Mínimo**        | Nivel umbral para la alerta.        |
| **Costo Unitario (S/)** | Costo individual de adquisición.    |
| **Ubicación**           | Lugar de almacenamiento.            |
| **Descripción**         | Descripción detallada del repuesto. |
### 5.3. Listado de Repuestos

| Columna            | Descripción                         |
| :----------------- | :---------------------------------- |
| **Código**         | Identificador único del repuesto.   |
| **Nombre**         | Nombre del repuesto o insumo.       |
| **Categoría**      | Clasificación.                      |
| **Stock**          | Cantidad actual disponible.         |
| **Mínimo**         | Nivel de stock para la alerta.      |
| **Costo Unitario** | Costo individual del repuesto.      |
| **Proveedor**      | Empresa que suministra el repuesto. |
| **Ubicación**      | Lugar de almacenamiento.            |
| **Acciones**       | (Observar, Editar, Eliminar).       |

---
# Módulo: Dashboard
## 1. Propósito y Alcance

El Dashboard es la vista principal del sistema, diseñada para proporcionar al administrador una visión general consolidada y en tiempo real del estado operativo, financiero y de producción del negocio.
### 1.1. Filtros Temporales (Alcance de Datos)
El usuario debe poder aplicar un filtro temporal para modificar el alcance de todas las métricas que dependen del tiempo:

| Filtro | Alcance de Datos |
| :--- | :--- |
| **Hoy** | Datos generados o con fecha de vencimiento del día actual. |
| **Semana** | Datos generados o con fecha de vencimiento de la semana actual. |
| **Mes** | Datos generados o con fecha de vencimiento del mes actual. |
Estos filtros solo afectaran a las 4 primeras tarjetas métricas.

---
## 2. Panel de Alertas Rápidas (Panel Superior)
Muestra notificaciones críticas que requieren acción inmediata o próxima, con un límite de visualización definido por el diseño de la UI (ej. 3 o 5 alertas).

| Alerta                       | Fuente de Datos                    | Lógica de Disparo                                                                                                                |
| :--------------------------- | :--------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- |
| **Stock Crítico**            | Módulo de **INVENTARIO**           | Se activa cuando el `Stock Disponible` de cualquier material es menor o igual al `Stock Mínimo` definido.                        |
| **Mantenimiento Preventivo** | Módulo de **ACTIVOS**              | Muestra el próximo mantenimiento programado cuya `Fecha de Mantenimiento` esté dentro de un rango cercano (ej. próximos 7 días). |
| **Entregas Urgentes**        | Módulo de **AGENDA** / **PEDIDOS** | Muestra pedidos cuya `Fecha de Entrega` está próxima a vencer (ej. próximos 2 días).                                             |

---
## 3. Vistas de Tarjetas Métricas (Fila Superior)
Estas métricas son cálculos directos basados en los filtros temporales aplicados.

| Métrica                 | Definición / Fuente   | Lógica de Cálculo y Clarificación                                                                                                                                                                                                                                                                                            |
| :---------------------- | :-------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ingresos de Hoy**     | Módulo **PEDIDOS**    | Suma total de la columna `A Cuenta` (Monto Pagado) de los pedidos que tienen un estado **Completado** y cuya fecha de completado coincide con el filtro temporal (Hoy/Semana/Mes).                                                                                                                                           |
| **Pedidos Activos**     | Módulo **PEDIDOS**    | Conteo de pedidos que se encuentran en estado: `Pendiente` y `En Proceso`.                                                                                                                                                                                                                                                   |
| **Entregados a Tiempo** | Módulo **PEDIDOS**    | **Requerimiento de Decisión (Falta Opción):** La métrica debe mostrar la distribución de entregas. Se debe añadir la métrica de **"Entregado con Retraso"**. La lógica de la métrica sería: Conteo de pedidos con estado **Completado** cuya `Fecha de Entrega Real` sea **menor o igual** a la `Fecha de Entrega Estimada`. |
| **Valor de Inventario** | Módulo **INVENTARIO** | Suma de la columna `Costo Total (S/)` de todas las molduras (listones) y demás insumos. Debe mostrar el conteo de ítems con `Stock Bajo` (Stock $\le$ Mínimo).                                                                                                                                                               |

---
## 4. Vistas de Tarjetas de Estado (Fila Central)
Estas tarjetas muestran la distribución de entidades clave por estado.
### 4.1. Estado de Producción
**Fuente:** Módulo **PRODUCCIÓN** (Columna 6: Estado).

| Estado          | Definición                                                                         |
| :-------------- | :--------------------------------------------------------------------------------- |
| **Pendiente**   | Órdenes de Producción (OP) registradas pero aún no iniciadas.                      |
| **En Proceso**  | OP en ejecución activa.                                                            |
| **Completadas** | OP finalizadas satisfactoriamente.                                                 |
| **Atrasadas**   | OP que excedieron su `Fecha Estimada` sin haber sido `Completadas` o `Entregadas`. |
### 4.2. Clientes
**Fuente:** Módulo **CLIENTES**.

| Métrica             | Definición                                                                                   | Requerimiento de Clarificación                                                                                                                                                                                                                       |
| :------------------ | :------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Totales**         | Conteo de todos los clientes registrados.                                                    | El campo es claro?                                                                                                                                                                                                                                   |
| **Nuevos este mes** | Conteo de clientes cuya fecha de registro se encuentra dentro del **último mes** (30 días) . | El campo es claro?                                                                                                                                                                                                                                   |
| **Activos**         | Conteo de clientes.                                                                          | **Definición Técnica (Confirmación):** Un cliente se considera **Activo** si tiene al menos **un pedido** en estado `Pendiente`, `En Proceso` o `Completado` dentro del periodo de tiempo considerado (o un pedido en `Producción` como se sugiere). |
| **Inactivos**       | Conteo de clientes.                                                                          | **Definición Técnica (Confirmación):** Clientes registrados que **no cumplen la condición de 'Activo'** (es decir, que no tienen pedidos activos o recientes).                                                                                       |
|                     |                                                                                              |                                                                                                                                                                                                                                                      |
### 4.3. Contratos
**Fuente:** Módulo **CONTRATOS**.

| Métrica               | Definición                                        | Lógica de Cálculo                                                                                                                                        |
| :-------------------- | :------------------------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Valor Total**       | Valor financiero total de todos los contratos.    | Suma total de la columna `Valor Total` de **todos** los contratos registrados.                                                                           |
| **Contratos Activos** | Conteo de contratos en estado vigente.            | Conteo de contratos cuyo estado **NO** es `Completado`, `Cerrado` o `Vencido`.                                                                           |
| **Pagos Pendientes**  | Suma total de los montos no pagados.              | Suma total de la columna `Saldo` de **todos** los contratos registrados.                                                                                 |
| **Por Vencer**        | Conteo de contratos que están cerca de finalizar. | Conteo de contratos cuya `Fecha de Fin` se encuentra dentro del rango de alerta (ej. Próximos 7 días) y que no están en estado `Completado` o `Cerrado`. |

---
## 5. Vistas de Detalle (Secciones Inferiores)
### 5.1. Productos Más Vendidos

**Fuente:** Módulo **PRODUCCIÓN**.
**Lógica:** Listar los productos (Tipos de Servicio) con el **mayor conteo de pedidos** en el período de tiempo seleccionado. Se muestra el **Monto Total acumulado** y el **Conteo de Ventas** para el producto.
### 5.2. Pedidos Recientes

**Fuente:** Módulo **PEDIDOS**.
**Lógica:** Listar los pedidos ordenados de forma descendente por la **Columna `Fecha Inicio`** (columna 2), mostrando los más recientes primero. Se visualiza la información clave: `N° de Pedido`, `Monto Total`, `Cliente` y `Estado`.

### 5.3. Entregas Programadas Hoy

**Fuente:** Módulo **AGENDA**.
**Lógica:** Conteo y listado de pedidos cuya `Fecha de Entrega` programada coincide exactamente con el **día actual**.

---
# Módulo: Agenda
## 1. Propósito y Alcance
El Módulo de Agenda permite al administrador planificar, gestionar y visualizar todas las citas, sesiones fotográficas, entregas y recordatorios. Su objetivo es asegurar el cumplimiento de plazos y la optimización del tiempo.
### 1.1. Visualización Principal
La interfaz principal es un **calendario de eventos** que permite visualizar las actividades programadas con etiquetas por día y hora. Al hacer clic en una etiqueta, se acceden a los detalles del evento.
### 1.2. Filtro General de Eventos
El listado de eventos (aplicable a la agenda y a las tarjetas de Próximos Eventos) debe poder filtrarse por:
* Todos
* Sesión Fotográfica
* Entrega
* Recordatorio
---
## 2. Creación de Nuevo Evento
### 2.1. Atributos del Evento
El formulario **"Nuevo Evento"** requiere los siguientes campos para el registro:

| Atributo             | Descripción                                               | Notas                                                                                                                    |
| :------------------- | :-------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------- |
| **Cliente / Título** | Nombre del cliente o título descriptivo del evento.       | Se asume que es el campo principal de identificación.                                                                    |
| **Tipo de Evento**   | Clasificación del evento.                                 | Opciones: Sesión Fotográfica, Entrega, Recordatorio.                                                                     |
| **Descripción**      | Detalles del evento a realizar.                           | El campo es claro?                                                                                                       |
| **Fecha y Hora**     | Fecha y hora exactas de inicio del evento.                | El campo es claro?                                                                                                       |
| **Ubicación**        | Lugar donde se realizará el evento o la actividad.        | El campo es claro?                                                                                                       |
| **Estado**           | (Se asume un estado inicial, ej. Pendiente o Programado). | **Pendiente de Clarificación:** Definir el set de estados posibles (ej. Programado, Reprogramado, Realizado, Cancelado). |
### 2.2. Flujo de Guardado
El evento se registra presionando el botón **"Guardar Evento"**. Si el usuario presiona **"Cancelar"**, el formulario se cierra sin guardar.

---
## 3. Visualización y Navegación de la Agenda

### 3.1. Filtros de Vista (Zoom de la Agenda)
El administrador debe poder cambiar el nivel de visualización del calendario:

| Filtro         | Visualización                                                | Comportamiento sin Eventos                                                   |
| :------------- | :----------------------------------------------------------- | :--------------------------------------------------------------------------- |
| **Día**        | Muestra la agenda de la fecha actual (o fecha seleccionada). | Debe mostrar el mensaje: "No hay eventos para este día".                     |
| **Semana**     | Muestra las actividades a realizar en la semana actual.      | El campo es claro?                                                           |
| **Mes**        | Muestra las actividades a realizar en el presente mes.       | El campo es claro?                                                           |
| **Trimestral** | Muestra el mes actual y los dos meses siguientes.            | La visualización de detalles se obtiene haciendo clic en la tarjeta del día. |
### 3.2. Detalles del Evento (CRUD)
Al hacer clic en la etiqueta de un evento en la Agenda, se debe mostrar una vista detallada con la siguiente información:
* Cliente
* Tipo de Evento
* Fecha y Hora
* Ubicación
* Descripción
* Estado
**Acciones Permitidas:**
* **Editar:** Permite modificar todos los campos registrados.
* **Eliminar:** Elimina el registro del evento de la Agenda.
---
## 4. Próximos Eventos (Tarjetas de Listado)
Esta sección lista los eventos de forma secuencial y cronológica.
### 4.1. Lógica de Listado
* **Ordenamiento:** Los eventos deben estar ordenados de manera ascendente por **Fecha y Hora**, mostrando primero los más próximos a realizarse.
* **Visualización:** Se muestran como "tarjetas" con la información clave.
### 4.2. Atributos de la Tarjeta

| Atributo | Fuente |
| :--- | :--- |
| **Nombre del Cliente** | Campo `Cliente / Título`. |
| **Número de Evento** | Identificador único del evento (ej. EVT-XXXX). |
| **Tipo de Evento** | Clasificación (Sesión Fotográfica, Entrega, Recordatorio). |
| **Hora del Evento** | Hora programada. |
### 4.3. Paginación y Barra de Eventos Registrados
* **Paginación:** La interfaz debe mostrar hasta **16 tarjetas** de eventos por pestaña/página.
* **Navegación:** Se debe implementar un sistema de navegación (botones "Anterior" / "Siguiente") para ver las siguientes páginas de eventos.
---
# Módulo: Gestión de Pedidos
## 1. Propósito y Alcance
El Módulo de Pedidos gestiona el ciclo de vida de las órdenes de trabajo, desde la cotización (Proforma) hasta la venta final (Nota de Venta o Contrato), controlando el estado de producción y los flujos financieros.
## 2. Flujo de Creación (Nuevo Pedido)
El formulario de `Nuevo Pedido` se estructura según el tipo de cliente (`Particular`, `Colegio`, `Empresa`) y el tipo de documento (`Proforma`, `Nota de Venta`, `Contrato`).
### 2.1. Estructura de Datos Común
Todos los tipos de pedido comparten las siguientes secciones de datos:

| Sección                                   | Atributos Comunes                                                             |
| :---------------------------------------- | :---------------------------------------------------------------------------- |
| **Detalle del Pedido**                    | Listado de `Productos disponibles` (ej. Marcos, Vidrios, Cuadros Graduación). |
| **Detalles Adicionales/Servicios Extras** | Campo de texto libre para notas, servicios adicionales o especificaciones.    |
### 2.2. Lógica de Pago y Documento
El **Resumen de Pago** y el botón de acción cambian según el `Tipo de Documento` seleccionado:
¿como funciona?

| Tipo de Documento | Campos de Pago Visualizados | Botón de Acción      | Lógica de Transacción                                                                                              |
| :---------------- | :-------------------------- | :------------------- | :----------------------------------------------------------------------------------------------------------------- |
| **Proforma**      | Total, Saldo                | **Guardar Proforma** | Solo calcula el costo. No afecta inventario ni genera ingresos.                                                    |
| **Nota de Venta** | Total, A Cuenta, Saldo      | **Procesar Venta**   | Genera comprobante, registra ingreso (`A Cuenta`), y **actualiza el inventario**.                                  |
| **Contrato**      | Total, A Cuenta, Saldo      | **Crear Contrato**   | El sistema crea un registro en el Módulo **CONTRATOS** con el saldo pendiente y programa eventos en la **AGENDA**. |
### 2.3. Datos del Cliente (Estructura por Tipo)
#### A. Particular
| Atributo            | Descripción                      |
| :------------------ | :------------------------------- |
| **Nombre Completo** | Nombre del cliente.              |
| **DNI**             | Documento Nacional de Identidad. |
| **Teléfono**        | Número de contacto.              |
| **Email**           | Correo electrónico.              |
| **Dirección**       | Dirección completa del cliente.  |
#### B. Colegio
| Atributo | Descripción |
| :--- | :--- |
| **Nombre de la I.E.** | Nombre de la Institución Educativa. |
| **Contacto (Encargado)** | Persona de contacto. |
| **Teléfono** | Número de contacto de la I.E. |
| **Email** | Correo electrónico de la I.E. |
| **Dirección** | Dirección del colegio. |
| **Nivel**, **Grado**, **Sección** | Datos específicos del grupo. |
#### C. Empresa
| Atributo | Descripción |
| :--- | :--- |
| **Razón Social** | Nombre legal de la empresa. |
| **RUC** | Registro Único de Contribuyentes. |
| **Representante** | Nombre del representante legal o contacto. |
| **Teléfono** | Número de contacto. |
| **Email** | Correo electrónico. |
| **Dirección** | Dirección de la empresa. |
### 2.4. Fechas Programadas (Para Contratos)
Los pedidos que deriven en `Contrato` (Colegio y Empresa) deben registrar las siguientes fechas para su integración con la **AGENDA**:
* **Fecha Compromiso:** Fecha límite de entrega/finalización (Día/Mes/Año).
* **Sesiones Fotográficas:** Fecha y Hora de la Sesión Fotográfica (Genera un evento en AGENDA).
* **Entregas:** Fecha y Hora de la Entrega (Genera un evento en AGENDA).
---
## 3. Registro de Pedidos (Tabla de Gestión)
### 3.1. Funcionalidades de Búsqueda y Filtro
* **Búsqueda:** Barra de búsqueda por `Cliente`, `Número de Pedido` o `Teléfono`.
* **Filtros por Tipo de Documento:** Todos, Proforma, Nota de Venta, Contrato.
* **Filtros por Estado:** Todos, Completado, En Proceso, Pendiente, Cancelado.
* **Limpiar Filtros:** Botón para restaurar los parámetros de búsqueda.
### 3.2. Estructura de la Tabla
La tabla principal de gestión de pedidos muestra los siguientes datos:

| Columna          | Descripción                                                                                             |
| :--------------- | :------------------------------------------------------------------------------------------------------ |
| **Número**       | Identificador único del pedido (ej. V001-24).                                                           |
| **Fecha Inicio** | Fecha de registro del pedido.                                                                           |
| **Cliente**      | Nombre del cliente o razón social.                                                                      |
| **Tipo**         | Tipo de documento generado (Proforma, NV, Contrato).                                                    |
| **Estado**       | Etapa actual del pedido (ej. Completado, En Proceso, Pendiente). (creo que falta un estado de atrasado) |
| **F. Entrega**   | Fecha de Entrega comprometida.                                                                          |
| **Total**        | Monto total del pedido.                                                                                 |
| **A Cuenta**     | Monto pagado por el cliente.                                                                            |
| **Saldo**        | Monto pendiente de pago.                                                                                |
| **Acciones**     | Observar (Ver Detalles), Editar, Eliminar.                                                              |
|                  |                                                                                                         |
### 3.3. Totales de Resumen
En la parte inferior del registro:
* **Total Absoluto:** Suma total de la columna `Total` de todos los pedidos mostrados.
* **Saldo Absoluto:** Suma total de la columna `Saldo` de todos los pedidos mostrados.      
# Módulo: Clientes
## 1. Gestión de Clientes (Base de Datos Central)
### 1.1. Nuevo Cliente (Formulario de Creación)
El administrador inicia el registro haciendo clic en el botón `+ NUEVO CLIENTE`. El formulario es dinámico y ajusta los campos según el `Tipo de Cliente` seleccionado.
#### A. Tipo: Particular

| Atributo | Campo en UI | Notas |
| :--- | :--- | :--- |
| **Nombre Completo** | Nombre Completo* | Nombre de la persona natural. |
| **DNI** | DNI* | Documento de Identidad. |
| **Teléfono** | Teléfono de Contacto* | Número de contacto principal. |
| **Email** | Email | Correo electrónico. |
| **Dirección** | Dirección | Dirección física registrada. |
| **Inst. / Empresa** | Institución Educativa (opcional) | Campo opcional para referencia. |
| **Detalles Adicionales** | Detalles Adicionales | Notas o mensajes sobre el cliente. |
#### B. Tipo: Colegio

| Atributo | Campo en UI | Notas |
| :--- | :--- | :--- |
| **Nombre Completo** | Nombre Completo* | Nombre de la persona de contacto principal. |
| **Nombre de la I.E.** | (Asumido en el campo Institución Educativa) | Razón social o nombre del colegio (ej. I.E. San Martín de Porres). |
| **RUC** | (Asumido en el campo DNI/RUC) | Número de identificación fiscal (ej. 20516154321). |
| **Teléfono** | Teléfono de Contacto* | Número de contacto de la I.E. |
| **Email** | Email | Correo electrónico. |
| **Dirección** | Dirección | Dirección física registrada. |
| **Detalles Adicionales** | Detalles Adicionales | Notas o mensajes sobre el cliente. |
#### C. Tipo: Empresa

| Atributo | Campo en UI | Notas |
| :--- | :--- | :--- |
| **Nombre Completo** | Nombre Completo* | Nombre de la persona de contacto. |
| **Razón Social** | (Asumido en el campo Institución Educativa) | Nombre legal de la empresa (ej. Empresa TechSolutions SAC). |
| **RUC** | (Asumido en el campo DNI/RUC) | Número de identificación fiscal (ej. 20555444333). |
| **Teléfono** | Teléfono de Contacto* | Número de contacto de la empresa. |
| **Email** | Email | Correo electrónico. |
| **Dirección** | Dirección | Dirección física registrada. |
| **Detalles Adicionales** | Detalles Adicionales | Notas o mensajes sobre el cliente. |

---
## 2. Búsqueda y Filtros
El administrador debe poder localizar clientes de forma eficiente a través de dos mecanismos:
### 2.1. Buscador
Barra de búsqueda unificada para encontrar un cliente por:
* Nombre
* Teléfono
* Email
* DNI o RUC
### 2.2. Filtros Avanzados
El botón `Filtros` permite refinar la lista por:
* **Tipos de Cliente:** Todos, Particular, Colegio, Empresa.
* **Acción:** Botón `Limpiar Filtros` para restablecer los criterios.
---
## 3. Listado de Clientes (Tabla)
El listado presenta la información de los clientes de manera tabular:

| Columna        | Definición                                                                    | Fuente/Lógica de Cálculo                                       |
| :------------- | :---------------------------------------------------------------------------- | :------------------------------------------------------------- |
| **CLIENTE**    | Muestra el nombre o razón social y debajo su número de documento (DNI o RUC). | Atributos de registro.                                         |
| **TIPO**       | Etiqueta de color que identifica la categoría (Colegio, Particular, Empresa). | Atributo `Tipo de Cliente`.                                    |
| **CONTACTO**   | Número de teléfono principal.                                                 | Atributo `Teléfono de Contacto`.                               |
| **DIRECCIÓN**  | Dirección física registrada.                                                  | Atributo `Dirección`.                                          |
| **PEDIDOS**    | Cantidad total de pedidos realizados por el cliente.                          | Conteo de registros en el Módulo Pedidos asociados al cliente. |
| **T. GASTADO** | Suma total de dinero gastado por el cliente (en S/).                          | Suma de la columna `Total` de todos los pedidos asociados.     |
| **U. PEDIDO**  | Fecha del último pedido realizado por el cliente.                             | Fecha del pedido con la entrada más reciente.                  |
| **ACCIONES**   | Conjunto de iconos para gestión (Observar, Editar, Eliminar).                 | Funcionalidades CRUD.                                          |
### 3.4. Acciones (CRUD)
* **Observar (Ver Detalles):** Muestra el reporte de datos completo del cliente.
* **Editar:** Permite modificar la información del cliente.
* **Eliminar:** Borra el registro. **Requisito:** Debe mostrar una alerta de confirmación antes de la eliminación definitiva.
--- 
# MÓDULO: INVENTARIO 

## 1. Descripción General
El Módulo de Inventario es el encargado de la gestión y control de materiales, molduras y recursos utilizados en los procesos de enmarcado, producción y venta.

- **Su objetivo principal es:**
    - Registrar y mantener actualizado el stock.
    - Controlar los costos unitarios y totales.
    - Garantizar la disponibilidad de insumos para la producción.
    - Evitar faltantes mediante alertas de stock mínimo.
## 2. Funcionalidades y Métricas Principales
El módulo principal presenta métricas clave en la cabecera:

| Métrica                           | Definición                                                                                                                 | Requisito de Alerta |
| :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------- | :------------------ |
| **Total Productos**               | Cantidad total de productos (SKUs únicos) registrados en el módulo.                                                        |                     |
| **Stock de Productos**            | Suma total de unidades de stock disponibles.                                                                               |                     |
| **Alertas de Stock**              | **Se activa** cuando un producto tiene una cantidad **igual o menor al Stock Mínimo** configurado.                         |                     |
| **Valor Generales de Inventario** | Muestra las alertas de stock te notifican cuando un producto tiene una cantidad igual o menor al stock mínimo configurado. |                     |
## 3. Estructura y Registro de Productos (Inventario)
El inventario está segmentado en pestañas que representan las categorías de producto/servicio.
### 3.1. Categoría: Enmarcados
Gestiona las materias primas y semielaborados esenciales para el enmarcado.
#### A. Subcategoría: Moldura (Listón)
* **Flujo:** Permite registrar y controlar cada tipo de moldura (listón).
* **Formulario:** "Añadir Moldura (Listón)".

| Campo                   | Requisito     | Tipo              | Notas                             |
| :---------------------- | :------------ | :---------------- | :-------------------------------- |
| **Nombre de moldura**   | Obligatorio   | Dropdown          | (Ej: Clásica, Moderna)            |
| **Ancho (pulgadas)**    | Obligatorio   | Dropdown          | (Ej: "1", 1.5")                   |
| **Color**               | Obligatorio   | Dropdown          | (Ej: "Dorado", "Plateado")        |
| **Material**            | Obligatorio   | Entrada de Moneda | (Ej: "Madera", "Aluminio")        |
| **Stock disponible**    | Obligatorio   | Entrada de Moneda |                                   |
| **Costo unitario (S/)** | Obligatorio   | Entrada de Moneda |                                   |
| **Costo total (S/)**    | **Calculado** | Moneda            | Costo unitario * Stock disponible |
| **Stock mínimo**        | Opcional      | Entrada de Número | Para alertas de reposición.       |

#### B. Subcategoría: Moldura Prearmada
* **Flujo:** Control de molduras ya preparadas (ensambladas) para venta o producción.
* **Formulario:** "Añadir Moldura Prearmada".

| Campo                   | Requisito       | Tipo              | Notas                      |
| :---------------------- | :-------------- | :---------------- | :------------------------- |
| **Nombre del Producto** | **OBLIGATORIO** | Entrada de Texto  | *Falta añadir este campo*  |
| **Dimensiones**         | Obligatorio     | Dropdown          | (Ej: 20x25cm, 30x40cm)     |
| **Color**               | Obligatorio     | Dropdown          | (Ej: "Dorado","Plateado" ) |
| **Material**            | Obligatorio     | Dropdown          | (Ej: "Madera","Aluminio" ) |
| **Stock**               | Obligatorio     | Entrada de Número |                            |
| **Costo unitario (S/)** | Obligatorio     | Entrada de Moneda |                            |
#### C. Subcategoría: Vidrio o Tapa MDF
* **Flujo:** Gestión de insumos complementarios (vidrios y tapas).
* **Formulario:** "Añadir Vidrio o Tapa MDF".

| Campo                   | Requisito       | Tipo              | Notas                     |
| :---------------------- | :-------------- | :---------------- | :------------------------ |
| **Nombre del Producto** | **OBLIGATORIO** | Entrada de Texto  | *Falta añadir este campo* |
| **Tipo de Material**    | Obligatorio     | Dropdown          | (Vidrio, Tapa MDF)        |
| **Tipo de Vidrio**      | Condicional     | Dropdown          | (comun, antireflejo)      |
| **Grosor (mm)**         | Obligatorio     | Dropdown          | 2mm, 3mm                  |
| **Tamaño (cm)**         | Obligatorio     | Dropdown          | (Ej: 20x25cm, 30x40cm)    |
| **Costo unitario (S/)** | Obligatorio     | Entrada de Moneda |                           |
| **Costo unitario (S/)** | Obligatorio     | Entrada de Moneda |                           |
#### D. Subcategoría: Paspartú
* **Flujo:** Control de láminas para acabados personalizados.
* **Formulario:** "Añadir Paspartú".

| Campo                   | Requisito       | Tipo              | Notas                  |
| :---------------------- | :-------------- | :---------------- | :--------------------- |
| **Nombre del Producto** | **OBLIGATORIO** | Entrada de Texto  | (Ej: 20x25cm, 30x40cm) |
| **Tipo de Material**    | Obligatorio     | Dropdown          | (Estándar, Premium)    |
| **Tamaño (cm)**         | Obligatorio     | Dropdown          | (Ej: 30x40cm, 40x50cm) |
| **Grosor (mm)**         | Obligatorio     | Dropdown          | 1.5mm, 2mm             |
| **Color**               | Obligatorio     | Dropdown          | blanco, crema          |
| **Cantidad**            | Obligatorio     | Entrada           |                        |
| **Costo unitario (S/)** | Obligatorio     | Entrada de Moneda |                        |
| **Stock Mínimo**        | Obligatorio     | Entrada de Número |                        |

### 3.2. Categoría: Minilab

* **Flujo:** Gestión de insumos específicos para la impresión (Minilab).
* **Formulario:** "Añadir Minilab".

| Campo                   | Requisito       | Tipo              | Notas                                                     |
| :---------------------- | :-------------- | :---------------- | :-------------------------------------------------------- |
| **Nombre del Producto** | **OBLIGATORIO** | Entrada de Texto  | *Falta añadir este campo*                                 |
| **Tipo Insumo**         | Obligatorio     | Dropdown          | papel, y hay 2 que creo son similares (quimica y quimico) |
| **Nombre Tipo**         | Obligatorio     | Dropdown          | papel lustre, papel mate, revelador RA - 4, blanqueador   |
| **Tamaño/Presentación** | Obligatorio     | Dropdown          | 10x15 cm, 20x30 cm, kit 5L, 1 Litro                       |
| **Cantidad Stock**      | Obligatorio     | Entrada de Número |                                                           |
| **Fecha Compral**       | Obligatorio     | Entrada           |                                                           |
| **Costo Unitario**      | Obligatorio     | Entrada           |                                                           |
| **Stock Mínimo**        | Obligatorio     | Entrada de Número |                                                           |
| **Costo Total**         | Obligatorio     | Entrada           |                                                           |
### 3.3. Categoría: Graduaciones
Gestiona el stock de productos finales asociados a la línea de negocio de Graduaciones.
#### A. Subcategoría: Cuadro
* **Formulario:** "Añadir Cuadro".

| Campo                   | Requisito       | Tipo              | Notas                     |
| :---------------------- | :-------------- | :---------------- | :------------------------ |
| **Nombre del Producto** | **OBLIGATORIO** | Entrada de Texto  | *Falta añadir este campo* |
| **Formato**             | Obligatorio     | Dropdown          | (Horizontal, Vertical)    |
| **Dimensiones**         | Obligatorio     | Dropdown          | 20x25, 30x40cm            |
| **Material**            | Obligatorio     | Dropdown          | canvas, papel fotografico |
| **Cantidad**            | Obligatorio     | Entrada de Número |                           |
| **Costo Unitari**       | Obligatorio     | Entrada de Número |                           |
| **Stock Mínimo**        | Obligatorio     | Entrada de Número |                           |
#### B. Subcategoría: Anuario
* **Formulario:** "Añadir Anuario".

| Campo                   | Requisito       | Tipo              | Notas                     |
| :---------------------- | :-------------- | :---------------- | :------------------------ |
| **Nombre del Producto** | **OBLIGATORIO** | Entrada de Texto  | *Falta añadir este campo* |
| **Formato**             | Obligatorio     | Dropdown          | A4, A5                    |
| **Páginas**             | Obligatorio     | Dropdown          | 50, 100                   |
| **Tipo de Tapa**        |                 | Dropdown          | tapa dura, tapa blanda    |
| **Cantidad**            | Obligatorio     | Entrada de Número |                           |
| **Costo Unitario**      | Obligatorio     | Entrada de Número |                           |
| **Stock Mínimo**        | Obligatorio     | Entrada de Número |                           |
### 3.4. Categoría: Corte Láser
* **Flujo:** Gestión de materiales utilizados para el servicio de corte láser.
* **Formulario:** "Añadir Corte Láser".

| Campo                   | Requisito       | Tipo             | Notas                                                                                                                                  |
| :---------------------- | :-------------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre del Producto** | **OBLIGATORIO** | Entrada de Texto | *pide añadir nombre de este producto aunque hay un campo*                                                                              |
| **Producto**            | Obligatorio     | Dropdown         | Plancha MDF Jeans,<br>Plancha Acrílico 3mm,<br>Cartón Microcorrugado,<br>Lámina MDF Crillada,<br>Lente de Enfoque,<br>Espejo Reflector |
| **tipo**                | Obligatorio     | Dropdown         | MDF<br>Acrilico<br>Cartón<br>Lámina Crillada<br>Lente<br>Espejo                                                                        |
| **tamaño**              | Obligatorio     | Dropdown         | 60x70cm<br>60x40cm<br>2.5"<br>1"                                                                                                       |
| **Color**               | Obligatorio     | Dropdown         | Natural<br>Transparente<br>Blanco<br>Natural<br>Transparente<br>Plateado                                                               |
| **Unidad**              | Obligatorio     | Dropdown         | plancha,pieza                                                                                                                          |
| **Stock**               | Obligatorio     | Entrada          |                                                                                                                                        |
| **Stock Mínimo**        | Obligatorio     | Entrada          |                                                                                                                                        |
| **Costo Unitario**      | Obligatorio     | Entrada          |                                                                                                                                        |
| **Proveedor**           | Opcional        | Dropdown         |                                                                                                                                        |
### 3.5. Categoría: Accesorios
Gestiona herramientas y elementos auxiliares.
#### A. Subcategoría: Marco y Accesorio
* **Formulario:** "Añadir Marco y Accesorio".

| Campo                 | Requisito   | Tipo     | Notas             |
| :-------------------- | :---------- | :------- | :---------------- |
| **Nombre de moldura** | Obligatorio | Entrada  |                   |
| **tipo de moldura**   | Obligatorio | Dropdown | gancho, soporte   |
| **Material**          | Obligatorio | Dropdown | metal, plastico   |
| **Color**             | Obligatorio | Dropdown | dorado , plateado |
| **Dimensiones**       | Obligatorio | Entrada  |                   |
| **costo unitario**    | Obligatorio | Entrada  |                   |
| **Stock**             | Obligatorio | Entrada  |                   |
#### B. Subcategoría: Herramienta General

* **Formulario:** "Añadir Herramienta General".

| Campo                 | Requisito   | Tipo             | Notas                                     |
| :-------------------- | :---------- | :--------------- | :---------------------------------------- |
| **Nombre de moldura** | Obligatorio | Entrada de Texto | *Representa el Nombre de la Herramienta.* |
| **Marca**             | Obligatorio | Dropdown         | Stanley,  bosch                           |
| Tipo de Material      | Obligatorio | Dropdown         | cortador, regla                           |
| **Costo Unitario**    | Obligatorio | Entrada          |                                           |
| Stock                 | Obligatorio | Entrada          |                                           |
| Stock Mínimo**        | Obligatorio | Entrada          |                                           |
## 5. Relación con Otros Módulos

| Módulo         | Relación con Inventario                                                                              |
| :------------- | :--------------------------------------------------------------------------------------------------- |
| **Pedidos**    | **Descarga de Stock:** El registro de una Nota de Venta consume y actualiza el stock del Inventario. |
| **Activas**    | Actualiza stock al consumir repuestos/insumos en proyectos de mantenimiento.                         |
| **Gastos**     | Sincronización de costos de adquisición para mantener actualizado el costo unitario y total.         |
| **Producción** | Controla materiales que pasan del inventario a órdenes de trabajo (producción).                      |
| **Reportes**   | Genera informes detallados sobre stock, costos, y alertas de reposición.                             |
|                |                                                                                                      |
## 6. Beneficios del Módulo de Inventario
- Optimización en la gestión de insumos.
- Control detallado de costos unitarios y totales.
- Prevención de faltantes gracias al sistema de stock mínimo.
- Trazabilidad completa de materiales por línea de negocio (Enmarcados, Minilab, etc.).
