#Bower
*(by RMP)*

###Requisitos / Dependencias:
1. Descarga e instalación de Nodejs `sudo apt-get install nodejs-legacy`
2. Descarga e instalación de Npm `sudo apt-get install npm`
2. Descarga e instalación de Git `sudo apt-get install git`
3. Descarga e instalación de Bower `sudo npm install -g bower`

### Preparación de entorno Bower
1. Inicializar *bower* si no se encuentra instalado en el proyecto `bower init`
1. Inicializar *git* si no se encuentra instalado en el proyecto `git init`
2. Instalar paquetes `bower install jquery angular backbone --save`

####Recursos:
- [Sitio oficial de Bower](https://bower.io/)

###Comandos Importantes:
| Comando                    | Descripción                                           |
|----------------------------|-------------------------------------------------------|
| `bower init` | Inicializa bower en la carpeta actual |
| `bower install jquery angular --save` | Instala los paquetes jquery y angular |
| `bower uninstall angular --save` | Desinstala el paquete jquery |
| `bower list` | Busca actualizaciones de dependiencias y muestra la lista de paquetes instalados |
| `bower list --paths` | Muestra los paquetes con sus ubicaciones dentro del proyecto |


### Estructura del archivo bower.json
```
{
  "name": "app",
  "description": "",
  "main": "",
  "license": "MIT",
  "homepage": "",
  "ignore": [
    "**/.*",
    "node_modules",
    "bower_components",
    "test",
    "tests"
  ],
  "dependencies": {
    "angular": "^1.5.7",
    "backbone": "^1.3.3"
  }
}
```

