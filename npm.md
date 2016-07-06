#NPM
*(by RMP)*

##Comandos Importantes:
| Comando | Descripción |
|---------|-------------|
| `npm init`| Crea el archivo package.json a partir de datos solititados |
| `npm init -yes`| Crea el archivo package.json de forma rápida. Sólo pide el nombre del autor |
| `npm install`| Instala los paquetes inclusidos en package.json |
| `npm install express`| Instala el paquete de manera local |
| `npm install express --save` | Instala el paquete de manera local y lo agrega a `package.json`, dentro de *dependencies* |
| `npm install express --save-dev `| Instala el paquete de manera local y lo agrega a `package.json`, dentro de *devDependencies* |
| `npm install express@2.x`| Instala la última subversión de la versión 2 del paquete de manera local |
| `npm uninstall express`| Desinstala el paquete de manera local |
| `npm install -g express`| Instala el paquete de manera global |
| `npm unnstall -g express`| Deinstala el paquete de manera global |
| `npm update express`| Actualiza el paquete de manera local |

##package.json:

Versión de `package.json` mínima
```
{
  "name": "my_package",
  "version": "1.0.0",
  "dependencies": {
    "my_dep": "^1.0.0"
  },
  "devDependencies" : {
    "my_test_framework": "^3.1.0"
  }
}
```

Versión de  `package.json` extendida
```
{
  "name": "my_package",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "ag_dubs",
  "license": "ISC",
  "repository": {
    "type": "git",
    "url": "https://github.com/ashleygwilliams/my_package.git"
  },
  "dependencies": {
    "my_dep": "^1.0.0"
  },
  "devDependencies" : {
    "my_test_framework": "^3.1.0"
  },
  "bugs": {
    "url": "https://github.com/ashleygwilliams/my_package/issues"
  },
  "homepage": "https://github.com/ashleygwilliams/my_package"
}
```
