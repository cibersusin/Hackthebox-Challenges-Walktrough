# MarketDump - Easy (HTB Challenge)
MarketDump (invasión alienigena) es un reto "fácil" para analizar ficheros de tráfico.

## DESCRIPCIÓN DEL RETO (Traducción oficial)
Nos informaron que un pirata informático logró ingresar a nuestra red interna después de navegar a través de la plataforma web que se ejecuta en la Internet pública. Logró eludir nuestra plataforma de registro de existencias de productos pequeños y luego obtuvo el archivo de nuestra base de datos de clientes. Creemos que sólo uno de nuestros clientes fue el objetivo. **¿Puedes averiguar quién era el cliente?**

## Preparación del entorno
En nuestro Kali Linux nos descargamos el fichero zip, y lo descomprimimos encontrando un pcapng

# Enumeración
Recopilamos y entendemos de que se trata la información de tráfico buscando de una forma ordenada.
## Equipos
Lo primero es saber entre que equipos se están efectuando el tráfico de red, por lo que listaremos los equipos: En el panel superior vamos a "Statistics" > "Endpoints", y en la pestaña IPv4 identificamos 2.
- 10.0.2.3 : Cliente  
- 10.0.2.15 : Servidor

Hayamos de una forma muy rápida que se ha producido una enumeración de puertos en el servidor, ya que vemos una clara secuencia de un paquete enviado, aquellos que la información de Bytes es diferente a 134B es que está abierto o filtrado. Puertos como el 23 (ftp) y el 53 (dns) responden.


## Solución
De una forma muy rápida vemos comunicación por FTP, también que en el paso anterior hayamos visto paquetes circulando... así que ha habido comunicación, por lo que hacemos un filtrado: **tcp.port==23**
