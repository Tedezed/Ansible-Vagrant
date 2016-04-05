Ejemplo simple ansible
----------------------

Estructura:
	├── Vagrantconfig <- Archivos de configuración adicionales de la maquina Vagrant.
	│
	├── ansible.cfg <- Configuración de ansible; clave rivada, hostfile, remote user... etc.
	├── group_vars <- Definición de variables por grupos de host.
	│   ├── all
	│   └── dbservers
	├── hosts <- Lista de host y agrupaciones.
	├── site.yml <- playbook donde se definen las tareas.
	└── roles <- tareas por rol.
	    └── common <- Rol common.
	        ├── handlers
	        │   └── main.yml <- Manipuladores, son tareas comunes (reinicio de un servicio). Se llaman desde tasks/tareas.
	        ├── tasks
	        │   └── main.yml <- Fichero de tareas, llama a handlers.
	        └── templates
	            └── ntp.conf.j2 <- Plantillas.


Ejecución:

	ansible-playbook -i hosts site.yml

