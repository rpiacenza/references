#Git
*(by RMP)*

##Requisitos / Dependencias:
1. Descarga e instalación de Git `sudo apt-get install git`

###Comandos de Startup:
| Comando                                                                   | Descripción                                                             |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| `git config --global user.name "Rodrigo Piacenza"`                        | Establece el nombre del usuario                                         |
| `git config --global user.email <rpiacenza@w3sys.com.ar>`                 | Establece el email del usuario                                          |
| `git init`                                                                | Inicializa git en la carpeta actual creando la carpeta .git y su estructura interna |
| `git clone http://github.com/rpiacenza/nemesis.git`                       | Clona un repositorio remoto en la carpeta actual                                    |

###Comandos de Staging Area:
| Comando                                                                   | Descripción                                                             |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| `git add main.php`                                                        | Agrega el archivo main.php al Staging index                                         |
| `git add .`                                                               | Agrega todos los archivos nuevos al Staging index                                   |
| `git status`                                                              | Verifica el estado de la carpeta actual                                             |
| `git commit`                                                              | Confirma los cambios en la carpeta actual para enviarlos al repositorio             |
| `git rm main.php`                                                         | Marca el archivo main.php para ser eliminado de la carpeta actual                   |
| `git reset HEAD main.php`                                                 | Desmarca un archivo marcado con **git commit**                                      |
| `git checkout -- main.php`                                                | Revierte/Deshace los cambios del archivo a como estaba anteriormente                |
| `git checkout etiqueta`                                                   | Muestra el log de cambios en una sola linea               |

###Comandos de Logs:
| Comando                                                                   | Descripción                                                             |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| `git log`                                                                 | Muestra el log de cambios. (sale con <kbd>Q</kbd> )                |
| `git log --oneline`                                                       | Muestra el log de cambios en una sola linea               |

###Comandos de Branches:
| Comando                                                                   | Descripción                                                             |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| `git branch`                                                              | Muestra el log de cambios. (sale con <kbd>Q</kbd> )                |
| `git branch imprimir`                                                     | Crea un nuevo branch llamado *imprimir*                             |
| `git checkout imprimir`                                                   | Cambia al branch llamado *imprimir*                                 |
| `git checkout -b imprimir`                                                | Crea un nuevo branch llamado *imprimir* y se posiciona en él        |
| `git checkout -d imprimir`                                                | Elimina el branch llamado *imprimir* y se posiciona en él        |
| `git checkout codigo_rama`                                                | Cambia al branch cuyo código es *codigo_rama*               |
| `git checkout etiqueta`                                                   | Cambia al branch cuyo tag es *etiqueta*               |
| `git merge imprimir`                                                      | Fusiona el branch llamado *imprimir* dentro del branch en el que se está posicionado actualmente        |

###Comandos de Tags:
| Comando                                                                   | Descripción                                                             |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| `git tag v1.0`                                                            | Asigna el tag *v1.0* al branch actualmente posicionado        |
| `git tag v1.0 codigo_rama`                                                | Asigna el tag *v1.0* al branch cuyo código sea *codigo_rama*        |

###Comandos de Repositorios Remotos:
| Comando                                                                   | Descripción                                                             |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| `git remote add origin http://github.com/rpiacenza/nemesis.git`           | Establece como repositorio remoto con nombre *origin* la url asignada          |
| `git push origin imprimir`                                                | Envía los cambios de la rama *imprimir* al repositorio remoto *origin*          |
| `git pull origin master`                                                  | Trae los cambios de la rama *master* del repositorio *origin* al repositorio actual         |


##Mensajes en Commits
- Los mensajes existen para explicar qué hace un commit en concreto
- Un mensaje no debe ser ni muy corto ni muy largo, sino que debe describir lo más excatament posible qué hace un commit
- Debe cubrir las siguientes preguntas:
	+ Por qué has hecho ese cambio ?
	+ Qué cosas han cambiado ?
	+ Qué ocurrirá ahora que has hecho éste cambio ?
- La primer linea **siempre** es la linea del resumen
- El resto de las lineas contienen el detalle del mensaje

##Mover archivos en Git
El movimiento de archivos en git es un poco extraño:

- Mover el archivo con el sistema operativo como lo haríamos normalmente
- Al hacer ésto git detectará que se ha eliminado un archivo en origen y se ha creado otro archivo en destino __*con el mismo nombre*__
- Git detectará que los archivos son iguales y los considerará como si se estuviera moviento el archivo.

--- 