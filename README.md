#  Algoritmo de búsqueda secuencial

La búsqueda secuencial, también conocida como búsqueda lineal, es uno de los algoritmos más simples para localizar un elemento dentro de una colección de datos. Consiste en recorrer cada elemento de la estructura, uno por uno, hasta encontrar el valor deseado o hasta haber comprobado todos los elementos sin éxito.


---

### ¿Cómo funciona?

Es un método de ordenamiento que:

- Detecta runs o secuencias naturales de elementos ya ordenados.


- Divide la lista en estas subsecuencias.


- Luego las va mezclando (merge) sucesivamente hasta obtener una lista ordenada completa.


A diferencia del Merge Sort tradicional, no divide la lista a la mitad, sino que identifica automáticamente las porciones ya ordenadas para optimizar el número de pasadas.


---

## Análisis de complejidad

La complejidad de un algoritmo describe cuánto trabajo se necesita realizar en función del tamaño de los datos de entrada (n). 
Se expresa mediante la notación Big O, que indica cómo crece el tiempo de ejecución conforme aumenta dicho tamaño.


| Aspecto                            | Valor                                                           
|------------------------------------|------------------------------------|
| Complejidad Temporal (peor caso)   | O(n)                               |                                             
| Complejidad Temporal (mejor caso)  | O(1) (el elemento está en la primera posición)  |
| Complejidad Espacial               | O(1) (uso constante de memoria)    |           
           

---

---

## Aplicaciones

El método de mezcla natural es especialmente útil en situaciones donde los datos presentan cierto grado de orden o cuando se trabaja con grandes volúmenes de información almacenados en archivos. 
A diferencia de otros algoritmos de ordenamiento, este método no ignora el estado inicial de los datos, sino que lo aprovecha para optimizar el proceso.

Se recomienda utilizar este algoritmo en los siguientes casos:

- **Archivos muy grandes**  
  Cuando los datos no caben completamente en memoria principal, es necesario utilizar memoria secundaria (como disco). La mezcla natural está diseñada como un método de ordenamiento externo, por lo que permite trabajar eficientemente con archivos grandes sin necesidad de cargar toda la información en memoria.

-  **Datos parcialmente ordenados**  
  Si los datos contienen subsecuencias ya ordenadas (runs), el algoritmo puede identificarlas automáticamente y reducir significativamente el número de operaciones necesarias para ordenar el conjunto completo.

- **Procesamiento de datos externos**  
  Es ampliamente utilizado en sistemas que manejan grandes cantidades de información, como bases de datos, archivos de registros (logs) o sistemas de procesamiento masivo de datos, donde el acceso secuencial es más eficiente que el acceso aleatorio.

- **Optimización de recursos**  
  Permite disminuir el número de pasadas de fusión al aprovechar el orden existente en los datos, lo que reduce el costo computacional en comparación con métodos que siempre dividen los datos sin analizar su estructura.

  - **Procesos secuenciales de lectura**  
  Es ideal en contextos donde los datos se leen de manera continua (por ejemplo, desde archivos), ya que puede detectar y procesar runs en una sola pasada inicial.

### ¿Cuándo es mejor usarlo?

El método de mezcla natural es más eficiente cuando los datos no están completamente desordenados, ya que puede alcanzar un rendimiento cercano a O(n) si existen pocas subsecuencias desordenadas. 
En estos casos, el algoritmo requiere menos pasadas de fusión, lo que reduce el tiempo total de ejecución.


---
## Tabla comparativa entre otros métodos

| Características                     | Mezcla Natural                      | QuickSort                          | Bubble Sort                    |
|------------------------------------|------------------------------------|------------------------------------|--------------------------------|
| Tipo de ordenamiento               | Externo                            | Interno                            | Interno                        |
| Facilidad de paralelismo           | Alta (subarreglos independientes)  | Media (depende del pivote)         | Muy baja (cada paso depende del anterior) |
| Rendimiento medio                  | Levemente más lento por copias     | Más rápido en la práctica          | El más lento de los tres       |
| Estabilidad                        | Sí                                 | Depende de la implementación       | Sí                             |
| Espacio extra                      | O(n) (usa arreglo auxiliar)        | O(log n) (uso de pila)             | O(1) (no requiere extra)       |

---
## Ejemplo sencillo

Dado el arreglo:

```bash
 [3, 4, 6, 1, 2, 8, 5, 7]
```

Paso 1.Identificación de runs naturales:

```bash
 [3, 4, 6]
```
```bash
 [1, 2, 8]
```
```bash
 [5, 7]
```
Paso 2. Distribución en archivos:

```bash
 A → [3,4,6], [5,7]
```
```bash
 B → [1,2,8]
```
Paso 3. Primera mezcla:

```bash
 Resultado → [1,2,3,4,6,8,5,7]
```
Paso 4. Segunda identificación de runs:

```bash
[1,2,3,4,6,8]
```
```bash
[5,7]
```
Paso 5. Segunda mezcla → lista final ordenada

```bash
[1,2,3,4,5,6,7,8]
```

## Ejemplo en Python 


```bash
def busqueda_secuencial():
    lista = [3, 7, 1, 9, 5]
    valor_buscado = int(input("Ingrese el valor a buscar: "))
    encontrado = False
    i = 0
    n = len(lista)

    while i < n and not encontrado:
        if lista[i] == valor_buscado:
            encontrado = True
        else:
            i += 1

    if encontrado:
        print(f"El valor {valor_buscado} se encontró en la posición {i + 1}")
    else:
        print(f"El valor {valor_buscado} no se encuentra en la lista.")

busqueda_secuencial()
```
## Ejemplo de salida en consola

```bash
Ingrese el valor a buscar: 1
El valor 1 se encontró en la posición 3
Ingrese el valor a buscar: 4
El valor 4 no se encuentra en la lista.
```

## Autores 
1. Cob Baas Naili Esmeralda
2. Pool Pech Sharon Rhichell deñ Rosario
3. Sulub Narvaez Angel Gabriel
