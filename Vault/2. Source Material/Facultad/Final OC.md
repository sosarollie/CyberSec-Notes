#### Repasar
Operaciones en punto flotante
error absoluto :LiCheck:
funcion logica
diseño de circuitos logicos "suma de productos"
elementos de instruccion
modo de direccionamiento salto condicional
punto de memoria
cálculos para almacenar bytes con colores

### Punto flotante
- Notación exponencial, la que usan las calculadoras para representar números muy grandes o muy pequeños

punto flotante por que la coma que marca decimales no esta fija

mantisa = parte del numero

mantisa entera BCS (binario con signo) 4bits
exp. BSS 3bits

  -"base"

0110010-2 = ?-10

mantisa = 0110 = 6
exp. = 010 = 2* 2
6 x 2 * 2 = 24



### Complemento a uno
- Si el numero empieza con 0, interpreto BSS
- Si el numero empieza con 1, complemento (doy vuelta los bits), acordandome que el número es negativo
	-  100 => 011 = 3,   101 => 010 = 2


BCS y CA1 tienen doble 0, es un problema

el CA2 soluciona este problema

### Complemento a dos
- Si el numero empieaz con 0, interpreto BSS
- Si el numero empieza con 1, 
	- Complemento a 1, invierto digitos
	- Le sumo 1
	- Interpreto BSS (el núm es negativo)

![2. Source Material/Career/Images/Pasted image 20250311140739.png](../../7.%20Images/Pasted%20image%2020250311140739%201.png)
Si tenemos una cadena entera en CA2 y la quiero pasar a decimal, puedo copiar hasta el primer 1 inclusive, y despues invertir todos los numeros
![2. Source Material/Career/Images/Pasted image 20250311140903.png](../../7.%20Images/Pasted%20image%2020250311140903%201.png)

## Exceso a dos
Positivos comienzan con 1, y negativos con 0, a diferencia del resto de sistemas de representación

Un sistema en exceso esta determinado para una cantidad de bits determinada
![2. Source Material/Career/Images/Pasted image 20250311141732.png](../../7.%20Images/Pasted%20image%2020250311141732%201.png)


Primero
- Interpreto BSS
Luego
- Resto el exceso

![2. Source Material/Career/Images/Pasted image 20250311141835.png](../../7.%20Images/Pasted%20image%2020250311141835%201.png)

![2. Source Material/Career/Images/Pasted image 20250311142004.png](../../7.%20Images/Pasted%20image%2020250311142004%201.png)
*otros ejemplos*

## Error Absoluto

Resolución = Distancia entre numero que podemos calcular y su siguiente
Rango = Maximo y mínimo que podemos representar

El error absoluto es la distancia entre un número que esta dentro del rango del sistema pero NO esta dentro de los números que puedo representar

###### Formula para calcular error absoluto

![2. Source Material/Career/Images/Pasted image 20250311143215.png](../../7.%20Images/Pasted%20image%2020250311143215%201.png)

---
Cuando represento la resolución en el limite inferior positivo, utilizar la potencia mas chica posible

Mantisa en BCS = 4 resoluciones
- Lim inf negativo
- Lim sup negativo
- Lim inf positivo
- Lim sup positivo


Mantisa normalizada = El único valor que me interesa en el sistema es cuando el primer bit es 1 (En BCS el bit de signo no cuenta)
![2. Source Material/Career/Images/Pasted image 20250313112437.png](../../7.%20Images/Pasted%20image%2020250313112437%201.png)
