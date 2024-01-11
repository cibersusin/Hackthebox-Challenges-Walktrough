# Red Miners - Very easy (HTB Challenge)
Red Miners (Mineros rojos) es un reto "muy fácil" para desofuscar la flag que se encuentra en un script Powershell

# Descripción del reto (Traducción oficial)
En la carrera por Vitalium en Marte, la malvada Junta de Arodor recurrió a medidas desesperadas, necesitando fondos para sus intentos de minería. Idearon una botnet diseñada específicamente para extraer criptomonedas de forma encubierta. Nos topamos con una muestra del instalador del minero de Arodor en nuestro servidor. 

Reconociendo la gravedad de la situación, iniciamos una investigación exhaustiva. Contigo como líder, necesitas **desentrañar el funcionamiento interno del mecanismo de instalación**. El descubrimiento sirvió como un punto de inflexión y reveló el alcance de la desesperación de Arodor. Sin embargo, la batalla por Vitalium continuó, instándonos a permanecer alerta y adaptar nuestras ciberdefensas para contrarrestar futuras amenazas.

# Preparación del entorno
En nuestro Kali Linux nos descargamos el fichero zip, y lo descomprimimos.

# Solución 
Visualizamos el archivo con cat, divisamos varias cadenas a las que se le aplica un descodificación en base 64, por lo que después de probar algunas vemos que hay ir recolectando varias cadenas y unirlas.

Cadena 1:
```shell
echo -n cGFydDE9IkhUQnttMW4xbmciCg==|base64 -d
part1="HTB{m1n1ng"
```
