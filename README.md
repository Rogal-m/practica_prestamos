# Práctica: Préstamo de equipo en Odoo

Nombre: Rolando Arturo Tome Valladares
Cuenta: 1208200200255

# Preguntas.

# Paso 1

1. ¿Qué pasa con un equipo cuando se desmarca el campo Activo? ¿Por qué es mejor que
borrarlo?
-El equipo se archiva: deja de aparecer en listas y búsquedas normales.
-Sigue guardado en la base de datos y se puede recuperar con el filtro Archivados.
-Borrarlo puede romper o perder el historial de los préstamos que lo usaron.

2. ¿Para qué sirve copy=False en el campo codigo?
-Al duplicar un equipo, ese campo no se copia y queda vacío.
-El código de inventario identifica a un solo equipo físico, así que el duplicado debe llevar un código distinto y no repetido.

# Paso 2

1. Este modelo usa _name y _inherit al mismo tiempo. ¿Qué hace cada uno aquí?
_name define un modelo nuevo y _inherit no crea otro modelo, se lo agrega.

2. ¿Qué hace tracking=True en el campo state? Lo verá funcionar en el paso 4.
Hace que Odoo registre en el chatter cada cambio de ese campo con el valor anterior y el nuevo.

# Paso 3

1. En fields.One2many("prestamo.linea", "prestamo_id"), ¿qué indica cada parámetro?
prestamo.linea es el modelo relacionado osea de las líneas.prestamo_id es el campo Many2one de ese modelo y apunta denuevo al préstamo, así Odoo sabe qué líneas pertenecen a cada préstamo.

2. ¿Qué pasa con las líneas cuando se borra un préstamo? ¿Qué parte del código lo define?
Las líneas se borran también y lo define ondelete="cascade" en el campo prestamo_id de la carpeta modelo prestamo.linea.

# Paso 4

1. Los botones ya se ocultan según el estado. ¿Por qué los métodos vuelven a validar el estado?
Ocultar un botón solo cambia lo que se ve en la interfaz, osea la vista es comodidad porque el método es la seguridad.

2. ¿Qué hace prestamo.linea_ids.equipo_id.write(...)? ¿Por qué no hace falta un for para cada equipo?
Obtiene todos los equipos de las líneas del préstamo y aplica el cambio a todos a la vez. No hace falta un for para cada uno porque Odoo trabaja con conjuntos de registros.

# Paso 5

1. El campo equipo_id ya filtra los equipos disponibles. ¿Por qué hace falta el TODO 5?
Porque solo filtra cuando se elige el equipo en la interfaz, despues el equipo puede cambiar de estado y el domain tampoco protege si los datos entran por codigo o importación.

2. ¿En qué momento se ejecuta un método con @api.constrains? ¿Y la validación de action_prestar?
Se ejecuta al guardar, crear o modificar el registro. Y la validacion se ejecuta al pulsar el boton.

# Paso 6

1. ¿Qué pasa si arrastra una tarjeta del kanban a otra columna? ¿Por qué?
El equipo cambia de estado porque son los valores del campo de estado y cambia el registro.

2. El campo prestamo_ids se agregó a res.partner. ¿Se crea una columna nueva en la tabla decontactos? Explique.
No se crea ninguna columna porque One2many no guarda datos en su tabla. La columna de verdad es la partner_id en la tabla de prestamo.prestam, y prestamo_ids busca dentro a los prestamos de cada contacto.