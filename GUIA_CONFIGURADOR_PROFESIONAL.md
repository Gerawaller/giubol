# GIUBOL · Portal y configurador profesional

## Qué incluye
- Portal público con imagen arquitectónica, servicios, catálogo y solicitud de cotización.
- Acceso empresarial separado mediante el login existente y las mismas credenciales de la base de datos. No se cambió el esquema de hash de contraseñas.
- Configurador visual interactivo: tipo de espacio, estilo, acabados de muros y piso, paleta de color y medidas aproximadas. La selección se adjunta a la solicitud para que el equipo pueda revisarla.
- Texturas locales de mármol, madera, concreto, granito, cerámica, ladrillo, acero y pintura.
- Búsqueda instantánea de materiales en el catálogo.
- Navegación empresarial con corrección de posición de scroll para reducir saltos visuales entre módulos.
- Catálogo SQL opcional con materiales, acabados, obra negra, plomería, electricidad, carpintería y servicios profesionales.

## Instalación recomendada
1. Haz copia de seguridad de los archivos actuales y de la base de datos.
2. Descomprime la carpeta `GIUBOL` en el directorio de tu servidor local (por ejemplo `htdocs/GIUBOL`).
3. Conserva tu configuración real en `config/database.php`; no reemplaces credenciales de producción con valores de demostración.
4. Abre `http://localhost/GIUBOL/`. El enlace de acceso empresarial conduce al login y el acceso privado sigue validándose con `auth/validar.php`.
5. Opcional: desde phpMyAdmin, selecciona la base de datos de GIUBOL e importa `database/catalogo_profesional.sql`. Este archivo agrega materiales faltantes sin eliminar productos existentes. Revisa los precios antes de ofrecerlos a clientes: son valores de ejemplo y deben ajustarse a tu mercado/proveedor.

## Configurador y cotización
La previsualización es conceptual: cambia texturas, color, tipo de espacio, estilo y dimensiones para ayudar al cliente a comunicar su preferencia. No genera un render 3D técnico ni planos de obra. Al continuar, la configuración se añade al enlace de solicitud para que el cliente la incluya en la descripción del proyecto. Los precios del catálogo son orientativos; la cotización formal debe validar cantidades, impuestos, mano de obra, mermas, traslados y existencias.

## Seguridad
- Las áreas internas continúan protegidas por `config/auth.php`.
- Las contraseñas existentes siguen verificándose con `password_verify`; no se modifican ni se reemplazan.
- Cambia cualquier contraseña de demostración antes de publicar la aplicación en Internet.
- Configura HTTPS, permisos por rol, copias de seguridad y credenciales de base de datos de mínimo privilegio antes de producción.

## Validación
El paquete se entrega con validación de sintaxis PHP y revisión sintáctica del JavaScript. La conexión real a MySQL y el flujo de cotización deben probarse en el entorno de instalación con una copia de la base de datos.
