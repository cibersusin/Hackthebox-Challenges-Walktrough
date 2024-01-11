# Red Miners - Very easy (HTB Challenge)
Red Miners (Mineros rojos) es un reto "muy fácil" para desofuscar la flag que se encuentra en un script Powershell

# Descripción del reto (Traducción oficial)
En la carrera por Vitalium en Marte, la malvada Junta de Arodor recurrió a medidas desesperadas, necesitando fondos para sus intentos de minería. Idearon una botnet diseñada específicamente para extraer criptomonedas de forma encubierta. Nos topamos con una muestra del instalador del minero de Arodor en nuestro servidor. 

Reconociendo la gravedad de la situación, iniciamos una investigación exhaustiva. Contigo como líder, necesitas **desentrañar el funcionamiento interno del mecanismo de instalación**. El descubrimiento sirvió como un punto de inflexión y reveló el alcance de la desesperación de Arodor. Sin embargo, la batalla por Vitalium continuó, instándonos a permanecer alerta y adaptar nuestras ciberdefensas para contrarrestar futuras amenazas.

# Preparación del entorno
En nuestro Kali Linux nos descargamos el fichero zip, y lo descomprimimos.

# Solución 
Visualizamos el archivo con cat, divisamos varias cadenas a las que se le aplica un descodificación en base 64, por lo que después de probar algunas vemos que hay ir recolectando varias cadenas y unirlas.
Tenemos que tener claro que las cadenas en Base64 suelen acabar con 2 espacios. 


### Parte 1:
Se encuentra al final, en el crontab
```
echo -n cGFydDE9IkhUQnttMW4xbmciCg==|base64 -d
```
part1="HTB{m1n1ng"


### Parte 2: 
Se encuentra como parte de la cadena tossacoin.htb
```
echo -n "cGFydDI9Il90aDMxcl93NHkiCg==" | base64 -d 
```
part2="_th31r_w4y"

### PARTE 3: 
Forma parte de la variable dest.
```shell
echo "X3QwX200cnN9Cg=="|base64 -d
```
_t0_m4rs}

### Parte 4:
Es una cadena que en el bashrc del usuario.
```
echo "ZXhwb3J0IHBhcnQ0PSJfdGgzX3IzZF9wbDRuM3R9Ig==" | base64 -d
```
export part4="_th3_r3d_pl4n3t}"

### Solución final
Si reconstruimos las cadenas formamos: **"HTB{m1n1ng_th31r_w4y_t0_m4rs_th3_r3d_pl4n3t}**

