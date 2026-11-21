# Práctica: Préstamo de equipo en Odoo

Nombre: Rolando Arturo Tome Valladares
Cuenta: 1208200200255

# Preguntas.

1. ¿Qué pasa con un equipo cuando se desmarca el campo Activo? ¿Por qué es mejor que
borrarlo?
-El equipo se archiva: deja de aparecer en listas y búsquedas normales.
-Sigue guardado en la base de datos y se puede recuperar con el filtro Archivados.
-Borrarlo puede romper o perder el historial de los préstamos que lo usaron.

2. ¿Para qué sirve copy=False en el campo codigo?
-Al duplicar un equipo, ese campo no se copia y queda vacío.
-El código de inventario identifica a un solo equipo físico, así que el duplicado debe llevar un código distinto y no repetido.