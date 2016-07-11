#Gulp
*(by RMP)*

###Requisitos / Dependencias:
1. Descarga e instalación de Nodejs `sudo apt-get install nodejs-legacy`
2. Descarga e instalación de Npm `sudo apt-get install npm`

### Preparación de entorno Gulp
1. Inicializar *npm* si no se encuentra instalado en el proyecto `npm init`
2. Instalar globalmente el paquete Gulp  `sudo npm install -g gulp`
3. Instalar localmente el paquete Gulp (dentro del package.json) `sudo npm install gulp --save-dev`

####Recursos:
- [Sitio oficial de Gulp](https://http://gulpjs.com)

####Referencia:
- [Building with gulp](https://www.smashingmagazine.com/2014/06/building-with-gulp/)

###Comandos Importantes:
| Comando                    | Descripción                                           |
|----------------------------|-------------------------------------------------------|
| `gulp`                     | Ejecuta la task *default*                               |
| `gulp saludar`             | Ejecuta el task *saludar*                               |


###Paquetes de uso frecuente:
Los paquetes se instalan con npm. Por ejemplo `npm install gulp-sass --save-dev`
| Paquete                    | Descripción                                           |
|----------------------------|-------------------------------------------------------|
| `gulp-plumber`             | Previene pipes breakings                              |
| `gulp-uglify`              | Minificar archivos                                    |
| `gulp-rename`              | Renombra archivos *js*                                |
| `gulp-autoprefizer`        | Agregar prejifos a los archivos *css*                 |
| `gulp-sass`                | Compilar archivos sass *sass*                         |
| `del`                      | Elimina archivos y carpetas                           |

###Ejemplos de globs
| Pattern                    | Descripción                                           |
|----------------------------|-------------------------------------------------------|
| `css/*.css`                | Archivos terminados en *.css* dentro del directorio *css* |
| `css/**/*.css`             | Archivos terminados en *.css* dentro del directorio *css* o algunos de sus subdirectorios |
| `!css/style.css`           | Excluir ela rchivo *style.css* dentro del directorio *css* |
| `*.+(js|css)`              | Claquier archivo con extension *.js* o *.css* |



### Ejemplo de archivo gulpfile.js
```
var gulp = require('gulp');

gulp.task('saludar', function () {
    console.log('Hola Mundo!');
});
```
