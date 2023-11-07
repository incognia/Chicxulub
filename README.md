# Cráter de Chicxulub

## Ubicación

![Cráter de Chicxulub](https://upload.wikimedia.org/wikipedia/commons/5/57/Cr%C3%A1ter_de_Chicxulub.jpg)

- País: México
- Estado: Yucatán
- Ciudad cercana: Chicxulub
- Coordenadas: 21°24'00"N 89°31'00"O

## Conversor de coordenadas geográficas

El código proporcionado convierte las coordenadas geográficas en grados, minutos y segundos (tanto de latitud como de longitud) ingresadas por el usuario en coordenadas en grados decimales. Utiliza una función llamada `degrees_to_decimal` para realizar la conversión y luego muestra las coordenadas en ambos formatos.

### Explicación por bloques

Este bloque define la función degrees_to_decimal, que toma los valores de grados, minutos, segundos y dirección, y los convierte en coordenadas en grados decimales, teniendo en cuenta la dirección sur u oeste, si es aplicable:

```python
def degrees_to_decimal(degrees, minutes, seconds, direction):
    # Convierte coordenadas en grados, minutos y segundos a grados decimales
    decimal_degrees = degrees + (minutes / 60) + (seconds / 3600)
    # Si la dirección es 'S' o 'O', invierte el signo de las coordenadas
    if direction in ['S', 'O']:
        decimal_degrees = -decimal_degrees
    return decimal_degrees
```

Este bloque solicita al usuario ingresar los componentes de la latitud en grados, minutos, segundos y dirección, y almacena los valores en variables:

```python
lat_degrees = float(input("Ingresa los grados de latitud: "))
lat_minutes = float(input("Ingresa los minutos de latitud: "))
lat_seconds = float(input("Ingresa los segundos de latitud: "))
lat_direction = input("Especifica 'N' para norte o 'S' para sur: ")
```

Este bloque solicita al usuario ingresar los componentes de la longitud en grados, minutos, segundos y dirección, y almacena los valores en variables:

```python
lon_degrees = float(input("Ingresa los grados de longitud: "))
lon_minutes = float(input("Ingresa los minutos de longitud: "))
lon_seconds = float(input("Ingresa los segundos de longitud: "))
lon_direction = input("Especifica 'E' para este o 'O' para oeste: ")
```

En este bloque se calculan las coordenadas en grados decimales para la latitud y la longitud utilizando la función `degrees_to_decimal`:

```python
lat_decimal = degrees_to_decimal(lat_degrees, lat_minutes, lat_seconds, lat_direction)
lon_decimal = degrees_to_decimal(lon_degrees, lon_minutes, lon_seconds, lon_direction)
```

En este último bloque, el programa imprime las coordenadas ingresadas en grados, minutos y segundos, así como las coordenadas en grados decimales para la latitud y la longitud, en un formato legible para el usuario:

```python
print(f'Coordenadas de latitud en grados, minutos y segundos: {lat_degrees}° {lat_minutes}\' {lat_seconds}" {lat_direction}')
print(f'Coordenadas de longitud en grados, minutos y segundos: {lon_degrees}° {lon_minutes}\' {lon_seconds}" {lon_direction}')

print(f'Coordenadas de latitud en grados decimales: {lat_decimal} grados')
print(f'Coordenadas de longitud en grados decimales: {lon_decimal} grados')
```

### Código completo

```python
def degrees_to_decimal(degrees, minutes, seconds, direction):
    decimal_degrees = degrees + (minutes / 60) + (seconds / 3600)
    if direction in ['S', 'O']:
        decimal_degrees = -decimal_degrees
    return decimal_degrees

# Solicitar al usuario las coordenadas de latitud
lat_degrees = float(input("Ingresa los grados de latitud: "))
lat_minutes = float(input("Ingresa los minutos de latitud: "))
lat_seconds = float(input("Ingresa los segundos de latitud: "))
lat_direction = input("Especifica 'N' para norte o 'S' para sur: ")

# Solicitar al usuario las coordenadas de longitud
lon_degrees = float(input("Ingresa los grados de longitud: "))
lon_minutes = float(input("Ingresa los minutos de longitud: "))
lon_seconds = float(input("Ingresa los segundos de longitud: "))
lon_direction = input("Especifica 'E' para este o 'O' para oeste: ")

# Calcular las coordenadas en grados decimales
lat_decimal = degrees_to_decimal(lat_degrees, lat_minutes, lat_seconds, lat_direction)
lon_decimal = degrees_to_decimal(lon_degrees, lon_minutes, lon_seconds, lon_direction)

# Imprimir las coordenadas en grados y grados decimales
print(f'Coordenadas de latitud en grados, minutos y segundos: {lat_degrees}° {lat_minutes}\' {lat_seconds}" {lat_direction}')
print(f'Coordenadas de longitud en grados, minutos y segundos: {lon_degrees}° {lon_minutes}\' {lon_seconds}" {lon_direction}')

print(f'Coordenadas de latitud en grados decimales: {lat_decimal} grados')
print(f'Coordenadas de longitud en grados decimales: {lon_decimal} grados')
```

### Salida

Ejemplo de la salida usando las coordenadas: 21°24'00"N 89°31'00"O

```
Ingresa los grados de latitud:  21
Ingresa los minutos de latitud:  24
Ingresa los segundos de latitud:  00
Especifica 'N' para norte o 'S' para sur:  N
Ingresa los grados de longitud:  89
Ingresa los minutos de longitud:  31
Ingresa los segundos de longitud:  00
Especifica 'E' para este o 'O' para oeste:  O
Coordenadas de latitud en grados, minutos y segundos: 21.0° 24.0' 0.0" N
Coordenadas de longitud en grados, minutos y segundos: 89.0° 31.0' 0.0" O
Coordenadas de latitud en grados decimales: 21.4 grados
Coordenadas de longitud en grados decimales: -89.51666666666667 grados
```

## Convertir distancia a grados de longitud

Esta fórmula se utiliza para calcular los grados de longitud que corresponden a una determinada distancia en kilómetros en la superficie de la Tierra, teniendo en cuenta la latitud en la que te encuentras. Esta fórmula es útil en la navegación y en la cartografía, donde se necesitan conversiones entre distancias lineales y medidas angulares, como grados.

$$
Grados\ de\ longitud = \frac{Distancia\ en\ kilómetros}{Radio\ de\ la\ Tierra \cdot \cos(latitud)}
$$

Aquí está una explicación detallada de los componentes de la fórmula:

1) **Grados de longitud**: Esta es la cantidad de longitud terrestre que corresponde a una cierta distancia en kilómetros a lo largo de la superficie de la Tierra. La longitud se mide en grados, y un grado de longitud representa la distancia angular entre dos meridianos (líneas de longitud) adyacentes. La fórmula te permite calcular cuántos grados de longitud corresponden a una distancia dada.

2) **Distancia en kilómetros**: Esto es la distancia lineal que deseas convertir a grados de longitud. Puedes medir esta distancia en kilómetros entre dos puntos en la superficie de la Tierra, como ciudades, puntos de referencia, o cualquier otra ubicación.

3) **Radio de la Tierra**: El radio de la Tierra es una constante que representa la distancia desde el centro de la Tierra hasta su superficie. El valor típico utilizado es aproximadamente 6,371 kilómetros, aunque el valor real puede variar ligeramente debido a la forma no perfectamente esférica de la Tierra.

4) **Cos(latitud)**: Este término incorpora la latitud del lugar donde se realiza el cálculo. La latitud es la coordenada que especifica la posición norte-sur de un punto en la superficie de la Tierra, medida en grados desde el ecuador. La función coseno (cos) se aplica a la latitud, y esto se debe a que la circunferencia de la Tierra disminuye a medida que te alejas del ecuador. El coseno ajusta la distancia en kilómetros para tener en cuenta la curvatura de la Tierra en latitudes más altas.

Entonces, para calcular los grados de longitud necesitas dividir la distancia en kilómetros entre el radio de la Tierra multiplicado por el coseno de la latitud. El resultado será la cantidad de grados de longitud que corresponden a esa distancia a lo largo de la superficie de la Tierra en la latitud especificada. Esto es útil para convertir distancias en la superficie de la Tierra en medidas angulares, lo que es especialmente importante en navegación y cartografía.

Este código en Python convierte una distancia en kilómetros a grados de longitud en función de una latitud de referencia. Luego, permite al usuario especificar una longitud de referencia y calcula la suma y la resta de la longitud de referencia con los grados de longitud calculados.

## Aplicar la fórmula usando Python (longitud)

Este código en Python convierte una distancia en kilómetros a grados de longitud en función de una latitud de referencia. Luego, permite al usuario especificar una longitud de referencia y calcula la suma y la resta de la longitud de referencia con los grados de longitud calculados.

### Explicación por bloques

En este bloque, se importa el módulo `math`, que proporciona funciones matemáticas, como `cos` y `radians`, necesarias para realizar cálculos trigonométricos en el código:

```python
import math
```

Este bloque define una función llamada `km_to_degrees_longitude`, que calcula la cantidad de grados de longitud que corresponden a una distancia en kilómetros a lo largo de la superficie de la Tierra, dada una latitud de referencia. La función toma dos argumentos: `kilometers` (kilómetros) y `reference_latitude` (latitud de referencia). Utiliza el radio promedio de la Tierra en kilómetros (aproximadamente 6371) para realizar el cálculo. La fórmula se basa en la relación entre la longitud y la distancia en un círculo y ajusta el valor teniendo en cuenta la latitud de referencia. Luego, la función devuelve los grados de longitud:

```python
def km_to_degrees_longitude(kilometers, reference_latitude):
    earth_radius_km = 6371  # Radio promedio de la Tierra en kilómetros
    degrees_longitude = (kilometers / (earth_radius_km * math.cos(math.radians(reference_latitude))))
    return degrees_longitude
```

En estos bloques, el programa solicita al usuario ingresar la distancia en kilómetros y la latitud de referencia:

```python
# Solicitar al usuario la distancia en kilómetros y la latitud de referencia
distance_in_km = float(input("Ingresa la distancia en kilómetros: "))
reference_latitude = float(input("Ingresa la latitud de referencia en grados: "))
```

Este bloque calcula la cantidad de grados de longitud utilizando la función `km_to_degrees_longitude` y luego convierte el resultado en grados mediante la función `math.degrees`. El resultado se almacena en la variable `degrees`:

```python
degrees = math.degrees(km_to_degrees_longitude(distance_in_km, reference_latitude))
```

Este bloque imprime el resultado del cálculo en una frase legible para el usuario:

```python
print(f'{distance_in_km} kilómetros tomando como referencia {reference_latitude} grados de latitud son aproximadamente {degrees} grados de longitud.')
```

En este bloque, el programa solicita al usuario ingresar la longitud de referencia:

```python
# Solicitar al usuario la longitud de referencia
reference_longitude = float(input("Ingresa la longitud de referencia en grados: "))
```

En este último bloque, el programa calcula la suma y la resta de la longitud de referencia con los grados de longitud calculados y muestra ambos resultados al usuario:

```python
# Calcular la suma y la resta
sum_longitude = reference_longitude + degrees
diff_longitude = reference_longitude - degrees

print(f'Suma con longitud de referencia: {sum_longitude} grados de longitud')
print(f'Resta con longitud de referencia: {diff_longitude} grados de longitud')
```

### Código completo

```python
import math

def km_to_degrees_longitude(kilometers, reference_latitude):
    earth_radius_km = 6371  # Radio promedio de la Tierra en kilómetros
    degrees_longitude = (kilometers / (earth_radius_km * math.cos(math.radians(reference_latitude))))
    return degrees_longitude

# Solicitar al usuario la distancia en kilómetros y la latitud de referencia
distance_in_km = float(input("Ingresa la distancia en kilómetros: "))
reference_latitude = float(input("Ingresa la latitud de referencia en grados: "))

degrees = math.degrees(km_to_degrees_longitude(distance_in_km, reference_latitude))

print(f'{distance_in_km} kilómetros tomando como referencia {reference_latitude} grados de latitud son aproximadamente {degrees} grados de longitud.')

# Solicitar al usuario la longitud de referencia
reference_longitude = float(input("Ingresa la longitud de referencia en grados: "))

# Calcular la suma y la resta
sum_longitude = reference_longitude + degrees
diff_longitude = reference_longitude - degrees

print(f'Suma con longitud de referencia: {sum_longitude} grados de longitud')
print(f'Resta con longitud de referencia: {diff_longitude} grados de longitud')
```

### Salida

Ejemplo de la salida usando una distancia de 90 km y las coordenadas 21.4 de latitud y -89.51666666666667 de longitud:

```
Ingresa la distancia en kilómetros:  90
Ingresa la latitud de referencia en grados:  21.4
90.0 kilómetros tomando como referencia 21.4 grados de latitud son aproximadamente 0.8693242999368848 grados de longitud.
Ingresa la longitud de referencia en grados:  -89.51666666666667
Suma con longitud de referencia: -88.64734236672979 grados de longitud
Resta con longitud de referencia: -90.38599096660354 grados de longitud
```

## Convertir distancia a grados de latitud

Para convertir kilómetros a grados de latitud tomando como referencia la longitud, puedes utilizar la siguiente fórmula:

$$
Grados\ de\ latitud = \frac{Kilómetros}{Radio\ de\ la\ Tierra}
$$

Donde:

1) **Kilómetros** es la distancia en kilómetros que deseas convertir a grados de latitud.
2) **Radio de la Tierra** es el radio promedio de la Tierra, que es aproximadamente 6,371 kilómetros.

Esta fórmula asume que estás calculando la conversión en un lugar específico de la Tierra y no tiene en cuenta la variación en la longitud de un grado de latitud, que varía según la ubicación. Para cálculos más precisos que toman en cuenta la ubicación exacta, se utilizarían fórmulas más complejas que dependen de la latitud y la longitud de la ubicación de referencia.

## Aplicar la fórmula usando Python (latitud)

Este código en Python permite al usuario ingresar una distancia en kilómetros y especificar si la latitud es norte ('N') o sur ('S'). Luego, convierte esta distancia en coordenadas de latitud en grados, minutos, segundos y grados decimales. También permite al usuario ingresar una latitud de referencia y calcula la suma y la resta de la latitud de referencia con las coordenadas calculadas.

### Explicación por bloques

En este bloque, se importa el módulo `math` que se utiliza para realizar cálculos matemáticos, como la conversión entre grados y radianes.

```python
import math
```

Este bloque define una función llamada `km_to_latitude` que toma dos argumentos: `kilometers` (kilómetros) y is_north, que es un booleano que indica si la latitud es norte o sur. La función calcula las coordenadas de latitud en grados decimales a partir de la distancia en kilómetros. Luego, convierte estos grados decimales en grados, minutos y segundos, y también devuelve los grados decimales:

```python
def km_to_latitude(kilometers, is_north):
    earth_radius_km = 6371  # Radio promedio de la Tierra en kilómetros

    # Calcular los grados decimales
    decimal_degrees = kilometers / earth_radius_km
    if not is_north:
        decimal_degrees = -decimal_degrees

    # Convertir de radianes a grados
    degrees = math.degrees(decimal_degrees)

    # Calcular grados, minutos y segundos
    degrees_int = int(degrees)
    decimal_minutes = (degrees - degrees_int) * 60
    minutes = int(decimal_minutes)
    seconds = (decimal_minutes - minutes) * 60

    return degrees, minutes, seconds, decimal_degrees
```

Este bloque solicita al usuario ingresar la distancia en kilómetros:

```python
# Solicitar al usuario la distancia en kilómetros
distance_in_km = float(input("Ingresa la distancia en kilómetros: "))
```

En este bloque, el programa solicita al usuario especificar si la latitud es norte ('N') o sur ('S'). La función upper() se utiliza para convertir la entrada del usuario en mayúsculas para que sea insensible a mayúsculas y minúsculas:

```python
# Preguntar si la latitud es norte o sur
latitude_direction = input("Especifica 'N' para norte o 'S' para sur: ").upper()
```

Aquí se verifica si la dirección de latitud ingresada por el usuario es válida ('N' o 'S'). Si no es válida, el programa muestra un mensaje de error:

```python
if latitude_direction not in ['N', 'S']:
    print("Dirección de latitud no válida. Debe ser 'N' o 'S.")
```

En este bloque, si la dirección de latitud es válida, el programa calcula las coordenadas de latitud en grados, minutos, segundos y grados decimales utilizando la función km_to_latitude y muestra los resultados:

```python
else:
    is_north = (latitude_direction == 'N')

    degrees, minutes, seconds, decimal_degrees = km_to_latitude(distance_in_km, is_north)

    # Imprimir los resultados
    print(f'Latitud en grados, minutos y segundos: {degrees}° {minutes}\' {seconds}" {latitude_direction}')
    print(f'Latitud en grados decimales: {decimal_degrees} grados')
```

En este bloque, el programa solicita al usuario ingresar una latitud de referencia:

```python
# Solicitar al usuario la latitud de referencia en grados
reference_latitude = float(input("Ingresa la latitud de referencia en grados: "))
```

Finalmente, el programa calcula la suma y la resta de la latitud de referencia con las coordenadas de latitud calculadas y muestra ambos resultados al usuario:

```python
# Calcular la suma y la resta
sum_latitude = reference_latitude + degrees
diff_latitude = reference_latitude - degrees

print(f'Suma con latitud de referencia: {sum_latitude} grados')
print(f'Resta con latitud de referencia: {diff_latitude} grados')
```

## Código completo

```python
import math

def km_to_latitude(kilometers, is_north):
    earth_radius_km = 6371  # Radio promedio de la Tierra en kilómetros

    # Calcular los grados decimales
    decimal_degrees = kilometers / earth_radius_km
    if not is_north:
        decimal_degrees = -decimal_degrees

    # Convertir de radianes a grados
    degrees = math.degrees(decimal_degrees)

    # Calcular grados, minutos y segundos
    degrees_int = int(degrees)
    decimal_minutes = (degrees - degrees_int) * 60
    minutes = int(decimal_minutes)
    seconds = (decimal_minutes - minutes) * 60

    return degrees, minutes, seconds, decimal_degrees

# Solicitar al usuario la distancia en kilómetros
distance_in_km = float(input("Ingresa la distancia en kilómetros: "))

# Preguntar si la latitud es norte o sur
latitude_direction = input("Especifica 'N' para norte o 'S' para sur: ").upper()

if latitude_direction not in ['N', 'S']:
    print("Dirección de latitud no válida. Debe ser 'N' o 'S.")
else:
    is_north = (latitude_direction == 'N')

    degrees, minutes, seconds, decimal_degrees = km_to_latitude(distance_in_km, is_north)

    # Imprimir los resultados
    print(f'Latitud en grados, minutos y segundos: {degrees}° {minutes}\' {seconds}" {latitude_direction}')
    print(f'Latitud en grados decimales: {decimal_degrees} grados')

    # Solicitar al usuario la latitud de referencia en grados
    reference_latitude = float(input("Ingresa la latitud de referencia en grados: "))

    # Calcular la suma y la resta
    sum_latitude = reference_latitude + degrees
    diff_latitude = reference_latitude - degrees

    print(f'Suma con latitud de referencia: {sum_latitude} grados')
    print(f'Resta con latitud de referencia: {diff_latitude} grados')
```

### Salida

Ejemplo de salida usando una distancia de 90 km y una latitud de 21.4 Norte:

```
Ingresa la distancia en kilómetros:  90
Especifica 'N' para norte o 'S' para sur:  N
Latitud en grados, minutos y segundos: 0.8093894453268575° 48' 33.802003176687094" N
Latitud en grados decimales: 0.014126510751844295 grados
Ingresa la latitud de referencia en grados:  21.4
Suma con latitud de referencia: 22.209389445326856 grados
Resta con latitud de referencia: 20.59061055467314 grados
```