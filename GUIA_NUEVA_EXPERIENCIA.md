# GIUBOL — Portal público y centro de operaciones

## Qué cambia

- `index.php` ahora es el portal público: presentación de servicios, catálogo conectado al inventario activo, explicación del proceso y llamadas a cotizar.
- `solicitar.php` permite que clientes registren sus datos, describan el proyecto y seleccionen productos/servicios del catálogo. La solicitud se registra en una transacción como cliente, proyecto y cotización en borrador para que el equipo la revise.
- El portal incluye un visualizador conceptual que cambia la muestra de acabado según el material elegido y lleva ese material seleccionado al formulario de cotización. Es una referencia de estilo, no un render técnico.
- `auth/login.php` mantiene el acceso del personal con una fotografía de construcción y una presentación de marca dividida.
- `assets/css/portal.css` contiene el diseño adaptable del portal y del formulario público.
- `assets/js/app-navigation.js` realiza navegación parcial entre páginas internas compatibles, manteniendo la estructura global y la posición de desplazamiento. Los formularios y las acciones de estado conservan su envío normal.
- Los módulos existentes de clientes, cotizaciones, ventas, diseños, proyectos, inventario, seguimiento, reportes y configuración se conservan.

## Instalación local

1. Haz una copia de seguridad de la carpeta GIUBOL y de la base de datos antes de sustituir archivos.
2. Coloca la carpeta `GIUBOL` en el directorio web de XAMPP (normalmente `htdocs`).
3. Importa `database/giubol.sql` en MySQL/phpMyAdmin si todavía no existe la base `giubol`. No vuelvas a importar el SQL sobre datos productivos porque incluye registros de demostración.
4. Revisa `config/database.php` y configura host, base de datos, usuario y contraseña de tu entorno.
5. Abre `http://localhost/GIUBOL/`. El portal público es la página inicial; el personal entra desde “Acceso empresas”.

## Flujo de solicitudes públicas

- El catálogo muestra únicamente productos activos de la empresa activa que se selecciona para el portal.
- Los precios son orientativos. Se vuelven a consultar desde la base de datos al recibir el formulario; no se confía en los precios enviados por el navegador.
- La solicitud crea cliente, proyecto en estado `Cotizacion`, cotización `Borrador` y partidas de los productos elegidos, dentro de una transacción.
- Si no se eligen materiales, se crea una partida genérica para que el equipo pueda revisar el alcance y preparar la propuesta.
- El folio web se muestra en la confirmación y también queda en la cotización para que el equipo lo consulte desde el módulo de Cotizaciones.

## Importante antes de publicar en Internet

- Cambia las credenciales de demostración y usa un usuario de MySQL de privilegios mínimos; no publiques una contraseña de demostración.
- Revisa permisos por rol y validaciones de pertenencia a empresa en todos los módulos.
- Configura HTTPS, copias de seguridad y políticas de privacidad/retención para los datos de clientes.
- El formulario público usa token CSRF, campo trampa, validación de datos y transacción. Para exposición pública conviene agregar rate limiting y CAPTCHA/antispam según tráfico.
- La navegación parcial es una mejora de experiencia para enlaces GET de módulos. Formularios y acciones que modifican estados conservan su comportamiento de envío para no romper las funciones actuales.

## Verificación realizada

Se ejecutó `php -l` en todos los archivos PHP del paquete sin errores de sintaxis. La conexión real a MySQL y el flujo de formulario deben probarse en el XAMPP/servidor de destino.
