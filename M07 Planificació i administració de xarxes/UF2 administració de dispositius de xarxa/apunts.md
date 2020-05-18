# Apunts M07 UF2

## Index

### 0 - Basic commands

- Login

        >enable
        #config t  / #configure terminal
    
- Save current config

        #Copy running-config startup-config
        
- Reboot router   REVISAR

        #reboot

### 1 - Configuració mínima

    Objectiu:
    
    - Configurar minimament un router.
    - Configurar l’adreça IP.
    - Configurar un ordinador per accedir-hi via telnet.
    - Entrar al router.


#### Passos

    Connectem el cable de consola.
    “Enganxem” la configuració mínima.
    Desconnectem la consola, connectem els fuetons i accedim al router via telnet.


#### Seguretat REVISAR
    hostname NOMPERALDISPOSITIU
    enable password USER
    enable secret class
    username USERNAME privilege 15 secret 0 PASSWD 
    line vty 0 4
      password PASSWD
      transport input all
      login 
      no access-class 23 in

#### Assignar IP

##### PC

    sudo ifconfig 192.168.66.20 netmask 255.255.255.0

##### Switch/Router


- Ethernet 0


    interface Ethernet 0
      ip address 192.168.1.80 255.255.255.0
      no shutdown

- Fast Ethernet 0/1


    interface Fast/Ethernet 0/1                     #Accedir a la configuració del port
        ip address 192.168.1.80 255.255.255.0       #Assigna la ip i mascara donada
        no shutdown                                 #Engega el port en cas de que estigui "apagat", norma general per els routers, per defecte els ports venen apagats.


- link donat per el professor: https://docs.google.com/presentation/d/1tLuWNrKSHB87FfXOI5PWnu1zsa-2OOr7PEV57FIG91E/edit#slide=id.p


### 2 Routing / Enrutament


- link donat per el professor: https://docs.google.com/presentation/d/1aEEUGo-kgncIL8TqYrOQp5t9gZD1fQJAUKXk83Ojaj8/edit#slide=id.g10b83b3be1_0_79

### 3 DHCP (Router)

    enable
    conf t
    ip dhcp pool POOL-NAME
        network 			192.168.1.0 255.255.255.0
        default-router 	    192.168.1.1
        dns-server 	    	192.168.1.5 195.170.0.1         #IP1 IP2, es pot utilitzar només una IP
        lease               0 0 10                          #10 minuts  
        exit
        
        
    ip dhcp excluded-address 192.168.1.10                   #Excloure una única IP        
    ip dhcp excluded-address 192.168.1.1 192.168.1.5        #Excloure un rang d'IPs
    service dhcp                                            #Iniciar DHCP


### 5 - Reset Switchs


- link donat per el professor:  https://docs.google.com/document/d/1mdc4qhoJs1b_8YsuQ03g8GaVkWs2PC2dtAgrucDu2XM/edit

### 6 - Reset Router

#### Cisco

##### Using reset button

    1 - With the router powered off, connect the power cord to your router, and plug the power cord into your power source.
    2 - Find the Reset button on the router.
    3 - Press and hold the Reset button while you power on the router.
    4 - Release the Reset button after 10 seconds.
    5 - Wait 5 to 10 minutes for the router to finish booting. You can check the lights on the router — when the lights are solid or blink in repeating patterns, the router is finished booting.
    6 - Power off your router.    
    
- link : https://dcloud-cms.cisco.com/help/reset-router#router-reset-using-button

##### Using commands

    1 - With your router powered off, connect the power cord to the router, and plug the power cord into your power source.
    2 - Connect your laptop to the console port on your router with the console cable.
    3 - Power on the router and wait 5 to 10 minutes for the router to finish booting. You can check the lights on the router — when the lights are solid or blink in repeating patterns, the router is finished booting.
    4 - On your laptop, start the terminal emulator program and use it to access your router’s command line interface (CLI).
    5 - In the router CLI, enter the commands in boldface to erase the existing configuration on your router and reload the factory-default configuration on the router: router> enable
    
        router# write erase
        Erasing the nvram filesystem will remove all configuration files! Continue? [confirm] <Press Enter key>
        router# reload
        Proceed with reload? [confirm] <Press Enter key>
        -OR-
        Would you like to enter the initial configuration dialog? [yes|no] no <Press Enter key>
        –OR–
        Do you want to save the configuration of the AP? [yes|no] no <Press Enter key>
        
    6 - Wait until the reload or erase finishes and a CLI prompt or completion message appears.
    7 - Close the terminal emulator window on your laptop.
    8 - Power off the router.

### 7 - Mostrar Informacio

- Mostrar informació dels ports (Interface | IP | Method |  Status UP/DOWN | Protocol).


    show ip interface brief


- Mostrar tota l'informació en forma d'script.


    show running-config

