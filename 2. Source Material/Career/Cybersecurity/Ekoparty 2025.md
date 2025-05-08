(notes in Spanish, ekoparty is a security conference-event hosted in Buenos Aires)
# Wardiving

es buscar redes wireless de acceso publico en un vehiculo en movimiento

Hermanito menor del Wardialing, se utilizaba en su momento para hacer mapeos de numeros de telefono (bluebox)

IEEE 802.11  = WIFI

![2. Source Material/Career/Images/Pasted image 20250206191501.png](../../../7.%20Images/Pasted%20image%2020250206191501%201.png)
*normativas*

El rate teorico si bien va incrementando depende de la cantidad de hosts que esten conectadas a la misma porque se reparten el ancho de banda.

![2. Source Material/Career/Images/Pasted image 20250206191844.png](../../../7.%20Images/Pasted%20image%2020250206191844%201.png)
*empiezan a existir los protocolos de seguridad*

![2. Source Material/Career/Images/Pasted image 20250206192122.png](../../../7.%20Images/Pasted%20image%2020250206192122%201.png)
*Forward Handshake* (WPA2 Y WPA)
Access Point
1) se manda un numero aleatorio del AP al supplicant
2) hace exactamente lo mismo y genera un Snonce (numero aleatorio) + message integrity code
3) para formar el PTK que es el mensaje que se va a enviar, se requiere el Anonce, el snonce, el PSK (pre shared key, la contraseña) la mac del supplicant y la mac del access point
4) acknowledge

Como crackearlo: se intenta de-auntenticar a los dispostivios conectados al access point, el supplicant va a intentar volver a conectarse y nosotros vamos a estar escuchando los mensajes que manda, cuando mande esos mensajes (encriptados) 
como se desencripta? separamos todas las partes (anonce, snonce, psk), se intenta separar las cosas que van a ser fijas de las que son dinamicas, como es la contraseña. Agarramos el mensaje y corremos un diccionario con distintas contraseñas, cuando el resultado sea exactamente igual al handshake, descubrimos cual es la contraseña.

Tenemos un monton de caracteres que no entendemos, es imposible de leer, se separa lo que ya sabemos, y pasamos el diccionario por donde no sabemos

Es un ataque de fuerza bruta

---
![2. Source Material/Career/Images/Pasted image 20250206193119.png](../../../7.%20Images/Pasted%20image%2020250206193119%201.png)
*canales 2.4GHZ*

podemos visualizar el solapamiento de los canales, separacion de 22mhz por canal
los que no tienen solapamiento son el 11, el 6 y el 1.

hoy en dia se pueden combinar canales para reducir disponibilidad y los routers modernos se adaptan a la capacidad de los canales

---
Hands on
- Que necesitamos?
	- un NIC, los que tienen capacidad de modo a monitor y que tenga capacidad de inyeccion de paquetes, (ALFA network)
	- https://articulo.mercadolibre.com.ar/MLA-1103677032-adaptador-de-red-wi-fi-usb-30-banda-dual-1900-mbps-_JM  / https://es.aliexpress.com/item/1005005537887765.html?spm=a2g0o.productlist.main.1.187749e0FYAUpn&algo_pvid=2400f383-1ec6-4539-806b-e05f657e87a9&algo_exp_id=2400f383-1ec6-4539-806b-e05f657e87a9-0&pdp_ext_f=%7B%22order%22%3A%229%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21ARS%21290904.28%21159997.36%21%21%211999.00%211099.45%21%402101ef5e17388818674916293e808b%2112000033457919161%21sea%21AR%210%21ABX&curPageLogUid=58BslXpG4Mff&utparam-url=scene%3Asearch%7Cquery_from%3AALFA AC1900
	- https://articulo.mercadolibre.com.ar/MLA-620233910-kit-auditoria-antena-yagi-24-dbi-usb-wifi-modo-monitor-_JM#polycard_client=search-nordic&position=9&search_layout=stack&type=item&tracking_id=6e8155e5-6f44-4299-9742-c1b14e13895b ralink
	- no conectar sin antena puesta

https://www.wirelesshack.org/best-kali-linux-compatible-usb-adapter-dongles.html
---
Aplicaciones
Kismet- Airodump- Wigle (android)
![2. Source Material/Career/Images/Pasted image 20250206194645.png](../../../7.%20Images/Pasted%20image%2020250206194645%201.png)
*kismet*

(no capturamos trafico porque es ilegal, solamente logeamos los beacons de announcements de los access points, informacion publica)

![2. Source Material/Career/Images/Pasted image 20250206194917.png](../../../7.%20Images/Pasted%20image%2020250206194917%201.png)
*wiggle*

---
## Geoposicionamiento
- dongle gps 
- ![2. Source Material/Career/Images/Pasted image 20250206195044.png](../../../7.%20Images/Pasted%20image%2020250206195044%201.png)
- GPSD dentro de linux
- se puede usar el del celular
---
*datos de años anteriores*
![2. Source Material/Career/Images/Pasted image 20250206195225.png](../../../7.%20Images/Pasted%20image%2020250206195225%201.png)

![2. Source Material/Career/Images/Pasted image 20250206195447.png](../../../7.%20Images/Pasted%20image%2020250206195447%201.png)
*2012*

![2. Source Material/Career/Images/Pasted image 20250206195526.png](../../../7.%20Images/Pasted%20image%2020250206195526%201.png)
*2018*
![2. Source Material/Career/Images/Pasted image 20250206195559.png](../../../7.%20Images/Pasted%20image%2020250206195559%201.png)
*2014*

en 2018 entre 20 a 25mil redes en BSAS

![2. Source Material/Career/Images/Pasted image 20250206195800.png](../../../7.%20Images/Pasted%20image%2020250206195800%201.png)
*2021

---
## Warchalking
- Marcado de redes inalambricas en el mundo fisico
- hobo symbols

![2. Source Material/Career/Images/Pasted image 20250206200248.png](../../../7.%20Images/Pasted%20image%2020250206200248%201.png)
*ejemplos*

---
## Hands on en kali
![2. Source Material/Career/Images/Pasted image 20250206200815.png](../../../7.%20Images/Pasted%20image%2020250206200815%201.png)
![2. Source Material/Career/Images/Pasted image 20250206200921.png](../../../7.%20Images/Pasted%20image%2020250206200921%201.png)
sudo airmon-ng check kill para que no interfieran procesos con la placa de red y nos borre el progreso

kismet viene instalado

![2. Source Material/Career/Images/Pasted image 20250206201126.png](../../../7.%20Images/Pasted%20image%2020250206201126%201.png)



