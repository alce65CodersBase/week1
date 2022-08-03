# MonoRepo

Aprende a migrar tus repositorios a una estructura de monorepositorio multipaquete para mejorar la mantenibilidad de tu código, compartir dependencias de NPM y configuraciones

Esto lo puedes lograr con npm workspaces, una nueva funcionalidad disponible a partir de la **versión 7 de npm**.

-   Creación de estructura de directorios para el monorepo
    -   proyecto -> package.json (private = true)
        -   app -> package.json
        -   api -> package.json
-   Unificando elementos de configuración:
    -   linter: pasa a la raíz desde ambos proyectos
    -   un único repositorio git (en raíz)
-   Usando npm workspaces

    -   package.json global
        "workspaces": ["api", "app"]
    -   no existirán node-modules / package-loc de app y api (node-modules solo global)
        (si existen por ser una migración, se eliminan)
    -   si se instalan nuevos paquetes se utiliza el modificador --workspace
        Crea la dependencia localmente pero instala en node_modules global
    -   npm install desde el nivel superior: aplana las dependencias :
        actualiza node-modules global con todas las dependencias de los workspaces

-   Probando que funcionan los paquetes API y App

    -   probamos los scripts de los sub-proyectos app y api
    -   app: test: posible aviso de error de dependencia-compartida
        -   "babel-jest"
        -   uso de SKIP... en .env - start y build

    14:50 - Sirviendo la app desde el servidor - los estaticos de express apuntan a la build de la app
    16:25 - Usando rutas relativas en la app - la app busca la api en una url absoluta: localhost ...
    la sustituimos por /api... - rehacemos la build - en desarrollo, el acceso a la api deja de funcionar:
    se añade un proxy en package.json de app:
    "proxy": "http:// localhost:3xxx" (dirección eliminada para la api)
    20:30 - Usando scripts para nuestros paquetes en la raíz
    añadimos al script el modificador --workspace=<x>
    los build / start se usaran en deploy - build npm run build --workspace=app - start npm run start --workspace=api
    23:30 - Subiendo el monorepo a un repositorio de GitHub
    25:28 - Añadir configuración de deploy en Heroku y variables de entorno
    29:12 - Deploy con Heroku - heroku create -> crea la aplicación - engines en packge json: npm 7.9.0 - variables de entorno paradas en el script del build - heroku config:set KEY=VALUE o config vars en la web - git push heroku main (master)
    30:32 - Arreglando errores del linter - corregir erroes del linter unificado - indicar que ignore build
    en eslintConfig (package) ignorePattern: build
    32:31 - Disfrutando de nuestro monorepo en producción
