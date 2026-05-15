#  Algoritmo de búsqueda secuencial

La búsqueda secuencial, también conocida como búsqueda lineal, es uno de los algoritmos más simples para localizar un elemento dentro de una colección de datos. Consiste en recorrer cada elemento de la estructura, uno por uno, hasta encontrar el valor deseado o hasta haber comprobado todos los elementos sin éxito.


---

### ¿Cómo funciona?

Se recorre la lista desde el primer elemento hasta el último. En cada posición se compara el valor actual con el valor buscado. Si coinciden, se retorna la posición. Si se llega al final sin encontrarlo, se indica que no existe.

---

## Análisis de complejidad

La complejidad temporal de la búsqueda secuencial es O(n), donde n es el número de elementos de la lista


| Aspecto                            | Valor                                                           
|------------------------------------|------------------------------------|
| Complejidad Temporal (peor caso)   | O(n)                               |                                             
| Complejidad Temporal (mejor caso)  | O(1) (el elemento está en la primera posición)  |
| Complejidad Espacial               | O(1) (uso constante de memoria)    |           
           


---

## Casos de uso (¿Cuándo es mejor usarlo?)

- Listas cortas o temporales: cuando el conjunto tiene pocas entradas (por ejemplo, una lista de 10–50 elementos) la simpleza supera el coste de buscar; no compensa ordenar ni construir índices.

- Datos no ordenados y sin índice: si no puedes (o no quieres) mantener el conjunto ordenado, la búsqueda secuencial funciona directamente sobre la colección.

- Estructuras con acceso secuencial (listas enlazadas): en listas enlazadas o flujos donde no hay acceso aleatorio por índice, la búsqueda lineal es la opción natural.

- Búsquedas esporádicas: cuando sólo harás muy pocas consultas sobre los datos, el coste de preparación (ordenar o construir una tabla hash) no vale la pena.

- Validaciones y comprobaciones rápidas: comprobar duplicados al insertar en una lista pequeña, verificar existencia en formularios, o validaciones de integridad en procesos puntuales.

- Escenarios en memoria limitada o con baja complejidad: si no quieres usar estructuras adicionales por restricción de memoria o simplicidad de implementación.

- Datos en streaming o secuencias: al procesar una secuencia de datos que llega en tiempo real (sin almacenamiento completo), puedes comparar elemento a elemento hasta encontrar lo que buscas.

- Prototipos y enseñanza: para explicaciones, pruebas rápidas o prototipos, su sencillez la hace ideal para demostrar conceptos antes de optimizar.
En estos casos, el algoritmo requiere menos pasadas de fusión, lo que reduce el tiempo total de ejecución.



## Cuándo no usarla (advertencias)

- Con conjuntos grandes y búsquedas frecuentes: si n es grande y realizas muchas búsquedas, conviene usar búsqueda binaria (si puedes ordenar) o tablas hash/índices para reducir tiempo.

- Cuando la latencia importa: en sistemas interactivos o en tiempo real donde los retrasos por O(n) no son aceptables.

- Si puedes mantener un índice o estructura auxiliar eficiente: invertir en ordenamiento o en un hash suele amortizarse cuando hay muchas operaciones.


---
## Tabla comparativa entre otros algoritmo 


| Características          | Búsqueda secuencial (lineal)                        | Búsqueda binaria                                         | Búsqueda por tabla hash         |
| ------------------------ | --------------------------------------------------- | -------------------------------------------------------- | ------------------------------- |
| Requisito/Tipo de datos  | No requiere orden; lista/colección lineal           | Requiere datos ordenados                                 | Estructura de tabla/hash map    |
| Facilidad de paralelismo | Alta (se puede dividir en segmentos independientes) | Media (divisiones en mitades, limitada por dependencias) | Alta (consultas independientes) |
| Rendimiento promedio     | O(n) (lineal)                                       | O(log n)                                                 | O(1) promedio                   |
| Estabilidad              | Sí (no reordena datos)                              | N/A (requiere orden; no reordena)                        | N/A (estructura por clave)      |
| Espacio extra            | O(1) (sin contar la colección)                      | O(1) (si es iterativa)                                   | O(n) (almacena la tabla)        |

---
## Ejemplo sencillo

Dado el arreglo:

```bash
 [7, 2, 9, 4, 1, 8, 3, 6, 5]
```

Paso 1.Comparar con todos los elementos:

```bash
 [Comparar 7 ≠ 3
```
```bash
 Comparar 2 ≠ 3
```
```bash
 Comparar 9 ≠ 3
```
```bash
 Comparar 4 ≠ 3
```
```bash
 Comparar 1 ≠ 3
```
```bash
 Comparar 8 ≠ 3
```
```bash
 Comparar 3 = 3
```

Paso 2. Resultado indicando posición (segunda parte explicativa, sin código):

- Se encontró el elemento 3 en la 7ª posición del arreglo (contando desde 1).

---

Paso 3. Caso donde no existe el valor (ejemplo de peor caso): buscar 10 en el mismo arreglo — se comparan todos los elementos:

```bash
Comparar 7 ≠ 10
```
```bash
 Comparar 2 ≠ 10
```
```bash
 Comparar 9 ≠ 10
```
```bash
Comparar 4 ≠ 10
```
```bash
Comparar 1 ≠ 10
```
```bash
 Comparar 8 ≠ 10
```
```bash
 Comparar 3 ≠ 10
```
```bash
Comparar 6 ≠ 10
```
```bash
Comparar 5 ≠ 10  ← No hay más elementos; fracaso (no existe 10)
```

Paso 4. Interpretación y conteo de comparaciones:

- Para encontrar 3 hubo 7 comparaciones (mejor caso sería 1, promedio ~n/2, peor caso n).

- Para buscar 10 hubo 9 comparaciones = n (peor caso).


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
