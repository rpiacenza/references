#Vagrant
*(by RMP)*

##Características:
- Vagrant trabaja dentro de una virtualbox.
- Soluciona el problema de automatiziicón de instalación de software en las virtualboxes
- Sólo se usan archivos de configuración. Por lo que no es necesario mandar gigabytes

##Requisitos / Dependencias:
1. Descarga e instalación de Virtualbox en el guest `sudo apt-get install virtualbox`
2. Descarga e instalación de Vagrant `sudo apt-get install virtualbox`
3. Descarga e instalación de Puppet `sudo apt-get install puppet puppetmaster facter`


##Comandos Importantes:
| Comando                    | Descripción                                           |
|----------------------------|-------------------------------------------------------|
| `vagrant init`             | Crea el archivo Vagrantfile                           |
| `vagrant box list`         | Muestra las boxes instaladas                          |
| `vagrant up`               | Arranca la máquina virtual                            |
| `vagrant ssh`              | Inicia sesión con shell dentro de la máquina virtual  |
| `vagrant halt`             | Detiene la máquina virtual                            |
| `vagrant destroy`          | **Destruye** la máquina virtual                       |
| `vagrant provission`       | Rearma el aprovisionamiento de una máquina virtual    |
| `vagrant status`           | Indica el estado de la máquina virtual                |

---


####Recursos:
[Boxes ya disponibles de vagrant](https://atlas.hashicorp.com/boxes/search)
[Recursos Puppet](https://docs.puppet.com/puppet/latest/reference/type.html)
[Módulos Puppet ya disponibles para usar](https://forge.puppetlabs.com/)

####Referencias:
[Cómo crear un entorno de desarrollo con Vagrant y Puppet](http://developerlover.com/crear-un-entorno-de-desarrollo-con-vagrant-y-puppet/)
[Cómo utilizar módulos con Puppet](http://developerlover.com/como-crear-y-utilizar-los-modulos-de-puppet-con-vagrant/)
[Libro de cocina rápido para Puppet](http://www.puppetcookbook.com/)

---


####Ejemplo de ``Vagrantfile`` para dos procesadores y puppet
```
# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure('2') do |config|
  # Sistema operativo
  config.vm.box = 'ubuntu/trusty64'
  # IP privada
  config.vm.network 'private_network', ip: '10.0.0.100'
  # Configuración de VirtualBox
  config.vm.provider :virtualbox do |vb|
    # Nombre de la máquina virtual
    vb.name = 'nemesis'
    # Memoria
    vb.memory = 2048
    # Número de procesadores
    vb.cpus = 2
  end
  # Habilitar aprovisionamiento por Puppet
  config.vm.provision :puppet do |puppet|
    # Localización de los ficheros de configuración manifiestos
    # puppet.manifests_path = 'puppet/manifests'
    # Nombre del manifiesto que se va a ejecutar inicialmente
    puppet.manifest_file = 'default.pp'
    # Opciones de Puppet. Se activa el modo debug y verbose
    puppet.options = [
      '--verbose',
      '--debug',
    ]
  end
end
```

#### Ejemplo de archivo puppet `default.pp`  para entorno LAMP
```
# Actualizar los repositorios de paquetes
exec { "apt-get update":
    command => "/usr/bin/apt-get update"
}
 
# Instalación de Apache
package { "apache2":
    ensure => present,
    require => Exec["apt-get update"]
}
 
# Arrancar el servicio de Apache
service { "apache2":
    ensure => running,
    require => Package["apache2"]
}
 
# Lista de paquetes de PHP para instalar
$packages = [
    "php5",
    "php5-cli",
    "php5-mysql",
    "php5-dev",
    "php5-curl",
    "php-apc",
    "libapache2-mod-php5"
]
 
# Instalación de los paquetes de PHP
package { $packages:
    ensure => present,
    require => Exec["apt-get update"],
    notify => Service["apache2"]
}
 
# Instalación del servidor de MySQL
package { "mysql-server":
    ensure => present,
    require => Exec["apt-get update"]
}
 
# Arrancar el servicio de MySQL
service { "mysql":
    ensure => running,
    require => Package["mysql-server"]
}
```