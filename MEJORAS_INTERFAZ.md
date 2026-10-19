# GIUBOL — actualización de interfaz

## Qué se actualizó

- Identidad visual corporativa en azul marino, blanco y acentos dorados inspirada en el sector de construcción.
- Navegación lateral agrupada por áreas: Inicio, Gestión comercial, Proyectos y operación, Administración.
- Encabezado superior con sección actual, fecha y estado visual del sistema.
- Dashboard con portada ejecutiva, acceso destacado para crear proyectos, accesos rápidos y áreas de alertas.
- Rediseño de botones, tablas, formularios, estados, tarjetas, espacios y estados de enfoque.
- Pantalla de inicio de sesión alineada con el resto de la plataforma.
- Ajustes responsive para escritorio, tablet y móvil.
- Se conservaron las rutas, consultas, módulos de negocio y herramientas de diseño existentes.

## Módulos detectados

- Dashboard y reportes.
- Clientes y expedientes/seguimientos.
- Proyectos.
- Diseños y herramientas interactivas de escenas/materiales.
- Cotizaciones.
- Ventas.
- Inventario, productos y movimientos.
- Configuración de empresa y contraseña de usuario.
- Autenticación y cierre de sesión.

## Instalación

1. Haz una copia de seguridad de la carpeta GIUBOL actual y de la base de datos.
2. Descomprime esta carpeta `GIUBOL` en la misma ubicación de tu servidor local (por ejemplo, `htdocs/GIUBOL` en XAMPP).
3. Conserva la configuración de `config/database.php` que corresponda a tu entorno.
4. No importes otra vez `database/giubol.sql` sobre una base con datos reales: el SQL incluye registros de demostración.
5. Abre la ruta local del sistema e inicia sesión.

## Antes de publicar en producción

Esta entrega prioriza la interfaz y conserva la lógica funcional original. Antes de exponer el sistema a Internet, se recomienda hacer una revisión de seguridad independiente:

- Cambiar la contraseña del usuario de demostración indicada en el SQL y retirar datos de ejemplo.
- Configurar credenciales de base de datos propias, evitando `root` sin contraseña.
- No mostrar mensajes internos de PDO/SQL a los usuarios finales; registrar detalles en un log privado.
- Revisar que cada lectura, edición y eliminación valide que el registro pertenece a `id_empresa` de la sesión, no solamente que el ID exista.
- Incorporar protección CSRF a formularios que modifican datos y revisar permisos por rol en el servidor.
- Publicar únicamente detrás de HTTPS y configurar cookies de sesión seguras.

## Validación realizada

Se ejecutó `php -l` sobre los archivos PHP de la entrega; no se detectaron errores de sintaxis. No se pudo validar la conexión real a MySQL ni probar flujos de usuario sin el entorno de base de datos y servidor del proyecto.
