


# 100 ejercicios de numpy

Esta es una colección de ejercicios recogidos de distintas fuentes como: numpy mailing list, stackoverflow Y
documentación de numpy. El objetivo de esta colección es ofrecer material para el aprendizaje de numpy.

Este repositorio es una traducción del español del repositorio original en ingles 
[Respositorio de rougier](https://github.com/rougier/numpy-100).
Archivos generados de manera automática. Vea la documentación para cambiar preguntas/respuestas/ayudas (questions/answers/hints)

#### 1. Importa el paquete `numpy` como `np` (★☆☆)
`hint: import … as`

```python
import numpy as np
```
#### 2. Imprima por pantalla la versión y la configuración de numpy (★☆☆)
`hint: np.__version__, np.show_config)`

```python
print(np.__version__)
np.show_config()
```
#### 3. Cree un vector null de tamaño 10 (vector de zeros)(★☆☆)
`hint: np.zeros`

```python
Z = np.zeros(10)
print(Z)
```
#### 4. Como encuentra el tamaño en memoria de un array (★☆☆)
`hint: size, itemsize`

```python
Z = np.zeros((10,10))
print("%d bytes" % (Z.size * Z.itemsize))
```
#### 5. ¿Cómo obtiene la documentación de numpy desde la terminal (comando de línea)? (★☆☆)
`hint: np.info`

```python
%run `python -c "import numpy; numpy.info(numpy.add)"`
```
#### 6. Crea un vector de ceros de tamaño 10 cuyo valor en la quinta posición sea 1 (★☆☆)
`hint: array[4]`

```python
Z = np.zeros(10)
Z[4] = 1
print(Z)
```
#### 7. Crea un vector con sus valores contegan los números del 10 a 49 (★☆☆)
`hint: arange`

```python
Z = np.arange(10,50)
print(Z)
```
#### 8. Obrenga un vector invertido (el primer elemento se convierte en el último) (★☆☆)
`hint: array[::-1]`

```python
Z = np.arange(50)
Z = Z[::-1]
print(Z)
```
#### 9. Crea una matriz 3x3 cuyos valores contengan lo números del 0 al 8 (★☆☆)
`hint: reshape`

```python
Z = np.arange(9).reshape(3, 3)
print(Z)
```
#### 10. Encuentre los elementos cuyos índice no son cero [1,2,0,0,4,0] (★☆☆)
`hint: np.nonzero`

```python
nz = np.nonzero([1,2,0,0,4,0])
print(nz)
```
#### 11. Crea una matriz identidad de 3x3 (★☆☆)
`hint: np.eye`

```python
Z = np.eye(3)
print(Z)
```
#### 12. Crea un vector 3x3x3 con valores aleatorios (★☆☆)
`hint: np.random.random`

```python
Z = np.random.random((3,3,3))
print(Z)
```
#### 13. Crea una matriz 10x10 con valores random y encuentra el valor máximo yel mínimo (★☆☆)
`hint: min, max`

```python
Z = np.random.random((10,10))
Zmin, Zmax = Z.min(), Z.max()
print(Zmin, Zmax)
```
#### 14. Crea un vector de tamaño 30 con valores aleatorios y encuentre el valor promedio (★☆☆)
`hint: mean`

```python
Z = np.random.random(30)
m = Z.mean()
print(m)
```
#### 15. Crea un vector 2D con los valores de 1 en el borde (es decir en la primera y última filas y columnas) con valores de 0 en el interior (★☆☆)
`hint: array[1:-1, 1:-1]`

```python
Z = np.ones((10,10))
Z[1:-1,1:-1] = 0
print(Z)
```
#### 16. ¿Cómo añadir un borde (llenado con ceros) a una matriz existente? (★☆☆)
`hint: np.pad`

```python
Z = np.ones((5,5))
Z = np.pad(Z, pad_width=1, mode='constant', constant_values=0)
print(Z)

# Using fancy indexing
Z[:, [0, -1]] = 0
Z[[0, -1], :] = 0
print(Z)
```
#### 17. ¿Cuál es el resultado de la siguiente expresión? (★☆☆)
```python
0 * np.nan
np.nan == np.nan
np.inf > np.nan
np.nan - np.nan
np.nan in set([np.nan])
0.3 == 3 * 0.1
```
`hint: NaN = not a number, inf = infinity`

```python
print(0 * np.nan)
print(np.nan == np.nan)
print(np.inf > np.nan)
print(np.nan - np.nan)
print(np.nan in set([np.nan]))
print(0.3 == 3 * 0.1)
```
#### 18. Crea una matriz 5x5 con valores 1,2,3,4 justo debajo de la diagonal (★☆☆)
`hint: np.diag`

```python
Z = np.diag(1+np.arange(4),k=-1)
print(Z)
```
#### 19. Crea una matriz 8x8 y llénelo con un patrón similar al del tablero de ajedrez (★☆☆)
`hint: array[::2]`

```python
Z = np.zeros((8,8),dtype=int)
Z[1::2,::2] = 1
Z[::2,1::2] = 1
print(Z)
```
#### 20. Considere un array de dimensiones (6,7,8), ¿Cuáles son los índices (x,y,z) del 100vo elemento? (★☆☆)
`hint: np.unravel_index`

```python
print(np.unravel_index(99,(6,7,8)))
```
#### 21. Cree algo similar a un tablero de ajedez usando la función `tile` (★☆☆)
`hint: np.tile`

```python
Z = np.tile( np.array([[0,1],[1,0]]), (4,4))
print(Z)
```
#### 22. Normalice una matriz de 5x5 que contiene valores aleatorios (normalize los elementos usando la fórmula z-score) (★☆☆)
`hint: (x -mean)/std`

```python
Z = np.random.random((5,5))
Z = (Z - np.mean (Z)) / (np.std (Z))
print(Z)
```
#### 23. Cree un tipo de dato especial (dtype) llamada color que pueda describir el color como cuatro números del tipo unsigned bytes (RGBA) (★☆☆)
Create a custom dtype that describes a color as four unsigned bytes (RGBA) (★☆☆)
`hint: np.dtype`

```python
color = np.dtype([("r", np.ubyte),
                  ("g", np.ubyte),
                  ("b", np.ubyte),
                  ("a", np.ubyte)])
```
#### 24. Multiplique una matriz 5x3 y otra 3x2 (producto cruz) (★☆☆)
`hint:`

```python
Z = np.dot(np.ones((5,3)), np.ones((3,2)))
print(Z)

# Alternative solution, in Python 3.5 and above
Z = np.ones((5,3)) @ np.ones((3,2))
print(Z)
```
#### 25. Dado un array 1D, multiplica por (-1) todos los elementos que esten en el rango 3 a 8 (★☆☆)
Given a 1D array, negate all elements which are between 3 and 8, in place. (★☆☆)
`hint: >, <`

```python
# Autor: Evgeni Burovski

Z = np.arange(11)
Z[(3 < Z) & (Z < 8)] *= -1
print(Z)
```
#### 26. ¿Cuál es resulatdo de la ejecución del siguiente script? (★☆☆)
```python
# Autor: Jake VanderPlas

print(sum(range(5),-1))
from numpy import *
print(sum(range(5),-1))
```
`hint: np.sum`

```python
# Autor: Jake VanderPlas

print(sum(range(5),-1))
from numpy import *
print(sum(range(5),-1))
```
#### 27. Considere un vector de enteros Z, ¿Cuál de las siguientes expresiones son válidas?
Consider an integer vector Z, which of these expressions are legal? (★☆☆)
```python
Z**Z
2 << Z >> 2
Z <- Z
1j*Z
Z/1/1
Z<Z>Z
```
`No hints provided...`

```python
Z**Z
2 << Z >> 2
Z <- Z
1j*Z
Z/1/1
Z<Z>Z
```
#### 28. ¿Cuál es el resultado de las siguientes operaciones? (★☆☆)
```python
np.array(0) / np.array(0)
np.array(0) // np.array(0)
np.array([np.nan]).astype(int).astype(float)
```
`No hints provided...`

```python
print(np.array(0) / np.array(0))
print(np.array(0) // np.array(0))
print(np.array([np.nan]).astype(int).astype(float))
```
#### 29. ¿Cómo redondear alejado de cero en un vector con valores tipo float? (★☆☆)
Es decir que si n = -0.12  redondear a -1 y si n = 1.2 redondear a 2
How to round away from zero a float array ? (★☆☆)
`hint: np.uniform, np.copysign, np.ceil, np.abs, np.where`

```python
# Autor: Charles R Harris

Z = np.random.uniform(-10,+10,10)
print(np.copysign(np.ceil(np.abs(Z)), Z))

# More readable but less efficient
print(np.where(Z>0, np.ceil(Z), np.floor(Z)))
```
#### 30. ¿Cómo encontrar valores comunes entre dos vectores? (★☆☆)
`hint: np.intersect1d`

```python
Z1 = np.random.randint(0,10,10)
Z2 = np.random.randint(0,10,10)
print(np.intersect1d(Z1,Z2))
```
#### 31. ¿Cómo ignorar todos los mensajes de warning de numpy (no recomendado)? (★☆☆)
`hint: np.seterr, np.errstate`

```python
# Ignorar las advertencias
defaults = np.seterr(all="ignore")
Z = np.ones(1) / 0

# Mostrar las advertencias
_ = np.seterr(**defaults)

# Equivalentement usando with
with np.errstate(all="ignore"):
    np.arange(3) / 0
```
#### 32. ¿Es la siguiente expresión verdadera (True)? (★☆☆)
```python
np.sqrt(-1) == np.emath.sqrt(-1)
```
`hint: número imaginario`

```python
np.sqrt(-1) == np.emath.sqrt(-1)
```
#### 33. ¿Cómo obtener las fechas de ayer, hoy y mañana? (★☆☆)
`hint: np.datetime64, np.timedelta64`

```python
yesterday = np.datetime64('today') - np.timedelta64(1)
today     = np.datetime64('today')
tomorrow  = np.datetime64('today') + np.timedelta64(1)
```
#### 34. ¿Cómo obtener todas la fechas correspondientes al mes de Julio del 2016? (★★☆)
`hint: np.arange(dtype=datetime64['D'])`

```python
Z = np.arange('2016-07', '2016-08', dtype='datetime64[D]')
print(Z)
```
#### 35. ¿Cómo calcular ((A+B)*(-A/2)) (sin usar la función `copy`)?
How to compute ((A+B)*(-A/2)) in place (without copy)? (★★☆)
`hint: np.add(out=), np.negative(out=), np.multiply(out=), np.divide(out=)`

```python
A = np.ones(3)*1
B = np.ones(3)*2
np.add(A,B,out=B)
np.divide(A,2,out=A)
np.negative(A,out=A)
np.multiply(A,B,out=A)
```
#### 36. Extraiga la parte entera de valores positivos de un vector que contenga valores aleatorios, usando 4 diferentes métodos (★★☆)
Extract the integer part of a random array of positive numbers using 4 different methods (★★☆)
`hint: %, np.floor, astype, np.trunc`

```python
Z = np.random.uniform(0,10,10)

print(Z - Z%1)
print(Z // 1)
print(np.floor(Z))
print(Z.astype(int))
print(np.trunc(Z))
```
#### 37. Crea una matriz 5x5 con sus valores dentro del rango 0 - 4 (★★☆)
Create a 5x5 matrix with row values ranging from 0 to 4 (★★☆)
`hint: np.arange`

```python
Z = np.zeros((5,5))
Z += np.arange(5)
print(Z)

# without broadcasting
Z = np.tile(np.arange(0, 5), (5,1))
print(Z)
```
#### 38. Cree una función que use "yield" para obtener 10 números enteros y use la función para construir un array(★☆☆)
Consider a generator function that generates 10 integers and use it to build an array (★☆☆)
`hint: np.fromiter`

```python
def generate():
    for x in range(10):
        yield x
Z = np.fromiter(generate(),dtype=float,count=-1)
print(Z)
```
#### 39. Cree un vector de tamaño 10 con los valores en el rango 0 a 1 (0 y 1 excluidos). (★★☆)
`hint: np.linspace`

```python
Z = np.linspace(0,1,11,endpoint=False)[1:]
print(Z)
```
#### 40. Cree un vector de tamaño 10 con valores aleatorios, luego ordénelos (★★☆).
`hint: sort`

```python
Z = np.random.random(10)
Z.sort()
print(Z)
```
#### 41. ¿Cómo se sumaría un pequeño vector de manera que lo haga más rapidamente que usando la función np.sum? (★★☆)
`hint: np.add.reduce`

```python
# Autor: Evgeni Burovski

Z = np.arange(10)
np.add.reduce(Z)
```
#### 42. Considere 2 vectores A y B ¿Cómo verifica que son iguales? (★★☆)
Consider two random array A and B, check if they are equal
`hint: np.allclose, np.array_equal`

```python
A = np.random.randint(0,2,5)
B = np.random.randint(0,2,5)

# Asumiendo un tamaño idéntico y tolerancia para la comparación sus valores
# Assuming identical shape of the arrays and a tolerance for the comparison of values
equal = np.allclose(A,B)
print(equal)

# Verificando en ambos el tamaño y sus valores, sin tolerancia (los valores deben ser exactamente iguales)
# Checking both the shape and the element values, no tolerance (values have to be exactly equal)
equal = np.array_equal(A,B)
print(equal)
```
#### 43. Cree un vector inmutable (de sólo lectura) (★★☆)
Make an array immutable (read-only)
`hint: flags.writeable`

```python
Z = np.zeros(10)
Z.flags.writeable = False
Z[0] = 1
```
#### 44. Cree una maetriz 10x2 con elementos aleatorios,representando coordenadas cartesianas, conviertalas a coordenadas polares (★★☆).
`hint: np.sqrt, np.arctan2`

```python
Z = np.random.random((10,2))
X,Y = Z[:,0], Z[:,1]
R = np.sqrt(X**2+Y**2)
T = np.arctan2(Y,X)
print(R)
print(T)
```
#### 45. Crea un vector con 10 elementos aleatorios y reemplace el valor máximo con 0 (★★☆)
`hint: argmax`

```python
Z = np.random.random(10)
Z[Z.argmax()] = 0
print(Z)
```
#### 46. Crea un vector structurado (structured array) con `x` e `y` como coordenadas, que generen un grilla (meshgrid) en el área [0, 1]x[0, 1] (★★☆)
Create a structured array with `x` and `y` coordinates covering the [0,1]x[0,1] area
`hint: np.meshgrid`

```python
Z = np.zeros((5,5), [('x',float),('y',float)])
Z['x'], Z['y'] = np.meshgrid(np.linspace(0,1,5),
                             np.linspace(0,1,5))
print(Z)
```
#### 47. Dados dos vectores, X, e Y, construya la matriz de Cauchy C (Cij =1/(xi - yj)) (★★☆)
`hint: np.subtract.outer`

```python
# Autor: Evgeni Burovski

X = np.arange(8)
Y = X + 0.5
C = 1.0 / np.subtract.outer(X, Y)
print(np.linalg.det(C))
```
#### 48. Imprima el máximo y mínimo valor representable para un tipo de datos de numpy escalar (★★☆)
`hint: np.iinfo, np.finfo, eps`

```python
for dtype in [np.int8, np.int32, np.int64]:
   print(np.iinfo(dtype).min)
   print(np.iinfo(dtype).max)
for dtype in [np.float32, np.float64]:
   print(np.finfo(dtype).min)
   print(np.finfo(dtype).max)
   print(np.finfo(dtype).eps)
```
#### 49. ¿Cómo imprimir todos los valores de un vector? (★★☆)
(Recuerde que cuando el vector es muy grade numpy suele mostrarlos en secciones o sólo una parte)
`hint: np.set_printoptions`

```python
np.set_printoptions(threshold=float("inf"))
Z = np.zeros((40,40))
print(Z)
```
#### 50. ¿Cómo encontrar el valor más cercano a un valor(valor escalar) en un vector? (★★☆)
`hint: argmin`

```python
Z = np.arange(100)
v = np.random.uniform(0,100)
index = (np.abs(Z-v)).argmin()
print(Z[index])
```
#### 51. Crea un vector estructurada (structured array) representado la posición (x, y) y el color (r, g, b) (★★☆)
`hint: dtype`

```python
Z = np.zeros(10, [ ('position', [ ('x', float, 1),
                                  ('y', float, 1)]),
                   ('color',    [ ('r', float, 1),
                                  ('g', float, 1),
                                  ('b', float, 1)])])
print(Z)
```
#### 52. Considere un vector de elementos aleatorios, de dimensiones 100x2, representado coordenadas (x, y), encuentre las distancias de entre todos los puntos en una matriz 100x100 (★★☆)
`hint: np.atleast_2d, T, np.sqrt`

```python
Z = np.random.random((10,2))
X,Y = np.atleast_2d(Z[:,0], Z[:,1])
D = np.sqrt( (X-X.T)**2 + (Y-Y.T)**2)
print(D)

# Usando scipy (una solución bastante rápida)
import scipy
# Thanks Gavin Heverly-Coulson (#issue 1)
import scipy.spatial

Z = np.random.random((10,2))
D = scipy.spatial.distance.cdist(Z,Z)
print(D)
```
#### 53. ¿Cómo convertir un vector de float(32 bits) a un vector entero (32 bits) ?
`hint: view and [:] =`

```python
# Thanks Vikas (https://stackoverflow.com/a/10622758/5989906)
# & unutbu (https://stackoverflow.com/a/4396247/5989906)
Z = (np.random.rand(10)*100).astype(np.float32)
Y = Z.view(np.int32)
Y[:] = Z
print(Y)
```
#### 54. ¿Cómo podrías convertir el siguiente texto en una matriz de numpy? (★★☆)
```
1, 2, 3, 4, 5
6,  ,  , 7, 8
 ,  , 9,10,11
```
`hint: np.genfromtxt`

```python
from io import StringIO

# Fake file
s = StringIO('''1, 2, 3, 4, 5

                6,  ,  , 7, 8

                 ,  , 9,10,11
''')
Z = np.genfromtxt(s, delimiter=",", dtype=np.int)
print(Z)
```
#### 55. ¿Cuál es el equivalente de la función `enumerate` para vectores numpy? (★★☆)
`hint: np.ndenumerate, np.ndindex`

```python
Z = np.arange(9).reshape(3,3)
for index, value in np.ndenumerate(Z):
    print(index, value)
for index in np.ndindex(Z.shape):
    print(index, Z[index])
```
#### 56. Genera una matriz 2d tipo campana de Gauss (sigma = 1, mu = 0) (2D Gaussian-like array) (★★☆)
`hint: np.meshgrid, np.exp`

```python
X, Y = np.meshgrid(np.linspace(-1,1,10), np.linspace(-1,1,10))
D = np.sqrt(X*X+Y*Y)
sigma, mu = 1.0, 0.0
G = np.exp(-( (D-mu)**2 / ( 2.0 * sigma**2 ) ) )
print(G)
```
#### 57. ¿Cómo poner aleatoriamente p elementos en un array 2d? (★★☆)
`hint: np.put, np.random.choice`

```python
# Autor: Divakar

n = 10
p = 3
Z = np.zeros((n,n))
np.put(Z, np.random.choice(range(n*n), p, replace=False),1)
print(Z)
```
#### 58. Dada una matriz, resta a cada elemento de una fila el promedio de la fila (★★☆)
Subtract the mean of each row of a matrix (★★☆)
`hint: mean(axis=,keepdims=)`

```python
# Autor: Warren Weckesser

X = np.random.rand(5, 10)

# Recent versions of numpy
Y = X - X.mean(axis=1, keepdims=True)

# Older versions of numpy
Y = X - X.mean(axis=1).reshape(-1, 1)

print(Y)
```
#### 59. ¿Cómo ordenar una matriz teniendo como referencia la n ava columna? (★★☆)
How to sort an array by the nth column? (★★☆)
`hint: argsort`

```python
# Autor: Steve Tjoa

Z = np.random.randint(0,10,(3,3))
print(Z)
print(Z[Z[:,1].argsort()])
```
#### 60. ¿Cómo averiguar si una matriz tiene columnas nulas? (★★☆)
`hint: any, ~`

```python
# Autor: Warren Weckesser

# null : 0 
Z = np.random.randint(0,3,(3,10))
print((~Z.any(axis=0)).any())

# null : np.nan
Z=np.array([
    [0,1,np.nan],
    [1,2,np.nan],
    [4,5,np.nan]
])
print(np.isnan(Z).all(axis=0))
```
#### 61. Encuentre el valor más cercano a un valor dado en un vector (★★☆)
`hint: np.abs, argmin, flat`

```python
Z = np.random.uniform(0,1,10)
z = 0.5
m = Z.flat[np.abs(Z - z).argmin()]
print(m)
```
#### 62. Considere 2 arrays con dimensiones (1, 3) y (3, 1), ¿Cómo calcular su suma usando un iterador? (★★☆)
Considering two arrays with shape (1,3) and (3,1), how to compute their sum using an iterator? (★★☆)
`hint: np.nditer`

```python
A = np.arange(3).reshape(3,1)
B = np.arange(3).reshape(1,3)
it = np.nditer([A,B,None])
for x,y,z in it: z[...] = x + y
print(it.operands[2])
```
#### 63. Crea un clase vector (vector class) que tenga name como atributo (★★☆)
Create an array class that has a name attribute (★★☆)
`hint: class method`

```python
class NamedArray(np.ndarray):
    def __new__(cls, array, name="no name"):
        obj = np.asarray(array).view(cls)
        obj.name = name
        return obj
    def __array_finalize__(self, obj):
        if obj is None: return
        self.name = getattr(obj, 'name', "no name")

Z = NamedArray(np.arange(10), "range_10")
print (Z.name)
```
#### 64. Dado un vector Z, ¿Cómo añadir 1 a cada elemento en las posiciones dadas por otro vector I? (tenga cuidado con los índices repetidos) (★★★)
Consider a given vector, how to add 1 to each element indexed by a second vector (be careful with repeated indices)? (★★★)
`hint: np.bincount | np.add.at`

```python
# Autor: Brett Olsen

Z = np.ones(10)
I = np.random.randint(0,len(Z),20)
Z += np.bincount(I, minlength=len(Z))
print(Z)

# Another solution
# Autor: Bartosz Telenczuk
np.add.at(Z, I, 1)
print(Z)
```
#### 65. ¿Cómo acumular (sumar) los elementos de un vector X en un vector F de acuerdo a un vector de posiciones I? (★★★)
```python
X = [1,2,3,4,5,6]
I = [1,3,9,3,4,1]
# Resultado F = [0, 7, 0, 6, 5, 0, 0, 0, 0, 3]
```
`hint: np.bincount`

```python
# Autor: Alan G Isaac

X = [1,2,3,4,5,6]
I = [1,3,9,3,4,1]
F = np.bincount(I,X)
print(F)
```
#### 66. Considere un numpy array de dimensiones (w, h, 3) que representa una imagen, calcule el número de colores únicos (★★☆)
Considering a (w,h,3) image of (dtype=ubyte), compute the number of unique colors (★★☆)
`hint: np.unique`

```python
# Autor: Fisher Wang

w, h = 256, 256
I = np.random.randint(0, 4, (h, w, 3)).astype(np.ubyte)
colors = np.unique(I.reshape(-1, 3), axis=0)
n = len(colors)
print(n)

# Faster version
# Autor: Mark Setchell
# https://stackoverflow.com/a/59671950/2836621

w, h = 256, 256
I = np.random.randint(0,4,(h,w,3), dtype=np.uint8)

# View each pixel as a single 24-bit integer, rather than three 8-bit bytes
I24 = np.dot(I.astype(np.uint32),[1,256,65536])

# Count unique colours
n = len(np.unique(I24))
print(n)
```
#### 67. Considere un array de 4 dimensiones, ¿Cómo obtener la suma de las dos últimas dimensiones ó ejes? (★★★)
Considering a four dimensions array, how to get sum over the last two axis at once? (★★★)
`hint: sum(axis=(-2,-1))`

```python
A = np.random.randint(0,10,(3,4,3,4))
# solution by passing a tuple of axes (introduced in numpy 1.7.0)
sum = A.sum(axis=(-2,-1))
print(sum)
# solution by flattening the last two dimensions into one
# (useful for functions that don't accept tuples for axis argument)
sum = A.reshape(A.shape[:-2] + (-1,)).sum(axis=-1)
print(sum)
```
#### 68. Considere un vector unidimensional D, ¿cómo calcular los promedios de los subsets de D, si se tienen un vector S del mismo tamaño describiendo los índices de las posiciones de las cuáles deben obtenerse los promedios?(★★★)
```python
# Sea por ejemplo D
D = [0.3, 0.5, 0.2, 0.7, 1., -0.6]
# y S
S = [0, 1, 1, 2, 2, 2]
# El vector de los promedios será
R = [0.3, 0.35, 0.36667]
```
`hint: np.bincount`

```python
# Autor: Jaime Fernández del Río

D = np.random.uniform(0,1,100)
S = np.random.randint(0,10,100)
D_sums = np.bincount(S, weights=D)
D_counts = np.bincount(S)
D_means = D_sums / D_counts
print(D_means)

# La solución usando pandas
import pandas as pd
print(pd.Series(D).groupby(S).mean())
```
#### 69. ¿Cómo obtener la diagonal de una matriz que es resultado de la operación entre dos matrices `np.dot(A, B)`? Use las matrices A y B para su respuesta.(★★★)
`hint: np.diag`

```python
# Autor: Mathieu Blondel

A = np.random.uniform(0,1,(5,5))
B = np.random.uniform(0,1,(5,5))

# versión lenta
np.diag(np.dot(A, B))

# versión rápida
np.sum(A * B.T, axis=1)

# versión más rápida
np.einsum("ij,ji->i", A, B)
```
#### 70. Sea el vector [1, 2, 3, 4, 5], ¿Cómo construir un nuevo vector con 3 consecutivos zeros intercalados entre cada valor?  (★★★)
Consider the vector [1, 2, 3, 4, 5], how to build a new vector with 3 consecutive zeros interleaved between each value? (★★★)
`hint: array[::4]`

```python
# Autor: Warren Weckesser

Z = np.array([1,2,3,4,5])
nz = 3
Z0 = np.zeros(len(Z) + (len(Z)-1)*(nz))
Z0[::nz+1] = Z
print(Z0)
```
#### 71. Sea un arrays de dimensiones (5, 5, 3), cómo multiplicarlo por un array de dimensiones (5, 5)? (★★★)
`hint: array[:, :, None]`

```python
A = np.ones((5,5,3))
B = 2*np.ones((5,5))
print(A * B[:,:,None])
```
#### 72. ¿Cómo intercambiar dos filas en un array? (★★★)
`hint: array[[]] = array[[]]`

```python
# Autor: Eelco Hoogendoorn

A = np.arange(25).reshape(5,5)
A[[0,1]] = A[[1,0]]
print(A)
```
#### 73. Sea un set de tripletes describiendo 10 triangulos (con lados compartidos), encuentre el set de las líneas que componen todos lo triangulos. (★★★)
Consider a set of 10 triplets describing 10 triangles (with shared vertices), find the set of unique line segments composing all the  triangles (★★★)
`hint: repeat, np.roll, np.sort, view, np.unique`

```python
# Autor: Nicolas P. Rougier

faces = np.random.randint(0,100,(10,3))
F = np.roll(faces.repeat(2,axis=1),-1,axis=1)
F = F.reshape(len(F)*3,2)
F = np.sort(F,axis=1)
G = F.view( dtype=[('p0',F.dtype),('p1',F.dtype)] )
G = np.unique(G)
print(G)
```
#### 74. Dado un array ordenado C que corresponde a el resultado de un bitcount, ¿cómo producir un array A tal que np.bincount(A) = C ? (★★★)
`hint: np.repeat`

```python
# Autor: Jaime Fernández del Río

C = np.bincount([1,1,2,3,4,4,6])
A = np.repeat(np.arange(len(C)), C)
print(A)
```
#### 75. ¿Cómo calcular los promedios de rango variable sobre un array? (★★★)
```python
# Sea
Z = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
# Sus promedios en un rango de n = 3
[1, 2, 3, 4, 5, 6, 7, 8]
```
`hint: np.cumsum, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# Autor: Jaime Fernández del Río

def moving_average(a, n=3) :
    ret = np.cumsum(a, dtype=float)
    ret[n:] = ret[n:] - ret[:-n]
    return ret[n - 1:] / n
Z = np.arange(20)
print(moving_average(Z, n=3))

# Autor: Jeff Luo (@Jeff1999)
# versión de NumPy >= 1.20.0

from numpy.lib.stride_tricks import sliding_window_view

Z = np.arange(20)
print(sliding_window_view(Z, window_shape=3).mean(axis=-1))
```
#### 76. Sea un vector Z unidimensional, contruya un vector de dos dimensiones (matriz) del cuál su primera fila sea (Z[0],Z[1],Z[2]), su segunda (Z[1],Z[2],Z[3]), es decir que cada siguiente fila empiece con el segundo elementos de la anterior fila, note que (la última fila debería ser (Z[-3],Z[-2],Z[-1]) (★★★)

```python
# Sea Z y R lo que se busca
Z = [0 1 2 3 4]
R = [[0 1 2]
     [1 2 3]
     [2 3 4]]
```
`hint: from numpy.lib import stride_tricks, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# Autor: Joe Kington / Erik Rigtorp
from numpy.lib import stride_tricks

def rolling(a, window):
    shape = (a.size - window + 1, window)
    strides = (a.strides[0], a.strides[0])
    return stride_tricks.as_strided(a, shape=shape, strides=strides)
Z = rolling(np.arange(10), 3)
print(Z)

# Autor: Jeff Luo (@Jeff1999)

Z = np.arange(10)
print(sliding_window_view(Z, window_shape=3))
```
#### 77. ¿Cómo negar un valor boolean, o cambiar el signo de un valor float? (inplace) (★★★)
`hint: np.logical_not, np.negative`

```python
# Autor: Nathaniel J. Smith

Z = np.random.randint(0,2,100)
np.logical_not(Z, out=Z)

Z = np.random.uniform(-1.0,1.0,100)
np.negative(Z, out=Z)
```
#### 78. Sean dos sets puntos P0 y P1 tienen el mismo tamaño, el primer punto de P0 describe un línea con el primer punto de P1 y así con todos los elementos de P0 y P1, también se nos da un punto P. 
¿Cómo calcular la distancia del punto P a cada linea que es descrita por los pares de puntos de los sets? (★★★)
`No hints provided...`

```python
def distance(P0, P1, p):
    T = P1 - P0
    L = (T**2).sum(axis=1)
    U = -((P0[:,0]-p[...,0])*T[:,0] + (P0[:,1]-p[...,1])*T[:,1]) / L
    U = U.reshape(len(U),1)
    D = P0 + U*T - p
    return np.sqrt((D**2).sum(axis=1))

P0 = np.random.uniform(-10,10,(10,2))
P1 = np.random.uniform(-10,10,(10,2))
p  = np.random.uniform(-10,10,( 1,2))
print(distance(P0, P1, p))
```
#### 79. Sean dos sets puntos P0 y P1 tienen el mismo tamaño, el primer punto de P0 describe un línea con el primer punto de P1 y así con todos los elementos de P0 y P1, también se nos da un set de puntos P. 
¿Cómo calcular la distancia de los puntos  de P a cada linea que es descrita por los pares de puntos de los sets? (★★★)
`No hints provided...`

```python
# Autor: Italmassov Kuanysh

# based on distance function from previous question
P0 = np.random.uniform(-10, 10, (10,2))
P1 = np.random.uniform(-10,10,(10,2))
p = np.random.uniform(-10, 10, (10,2))
print(np.array([distance(P0,P1,p_i) for p_i in p]))
```
#### 80. Considere una matriz arbitraria, escriba una función que extraiga una subparte con una forma fija y centrada en un elemento dado (rellene con un 'fill' cuando sea necesario)(★★★)
Consider an arbitrary array, write a function that extract a subpart with a fixed shape and centered on a given element (pad with a `fill` value when necessary) (★★★)
`hint: minimum maximum`

```python
# Autor: Nicolas Rougier

Z = np.random.randint(0,10,(10,10))
shape = (5,5)
fill  = 0
position = (1,1)

R = np.ones(shape, dtype=Z.dtype)*fill
P  = np.array(list(position)).astype(int)
Rs = np.array(list(R.shape)).astype(int)
Zs = np.array(list(Z.shape)).astype(int)

R_start = np.zeros((len(shape),)).astype(int)
R_stop  = np.array(list(shape)).astype(int)
Z_start = (P-Rs//2)
Z_stop  = (P+Rs//2)+Rs%2

R_start = (R_start - np.minimum(Z_start,0)).tolist()
Z_start = (np.maximum(Z_start,0)).tolist()
R_stop = np.maximum(R_start, (R_stop - np.maximum(Z_stop-Zs,0))).tolist()
Z_stop = (np.minimum(Z_stop,Zs)).tolist()

r = [slice(start,stop) for start,stop in zip(R_start,R_stop)]
z = [slice(start,stop) for start,stop in zip(Z_start,Z_stop)]
R[r] = Z[z]
print(Z)
print(R)
```
#### 81. Sea el vector Z = [1,2,3,4,5,6,7,8,9,10,11,12,13,14], ¿Cómo generar el vector R = [[1,2,3,4], [2,3,4,5], [3,4,5,6], ..., [11,12,13,14]]? (★★★)
`hint: stride_tricks.as_strided, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# Autor: Stefan van der Walt

Z = np.arange(1,15,dtype=np.uint32)
R = stride_tricks.as_strided(Z,(11,4),(4,4))
print(R)

# Autor: Jeff Luo (@Jeff1999)

Z = np.arange(1, 15, dtype=np.uint32)
print(sliding_window_view(Z, window_shape=4))
```
#### 82. Obtenga el rango de un matriz (★★★)
`hint: np.linalg.svd, np.linalg.matrix_rank`

```python
# Autor: Stefan van der Walt

Z = np.random.uniform(0,1,(10,10))
U, S, V = np.linalg.svd(Z) # Singular Value Decomposition
rank = np.sum(S > 1e-10)
print(rank)

# alternative solution:
# Autor: Jeff Luo (@Jeff1999)

rank = np.linalg.matrix_rank(Z)
print(rank)
```
#### 83. ¿Cómo encontrar el valor más frecuente en un array? (★★★)
`hint: np.bincount, argmax`

```python
Z = np.random.randint(0,10,50)
print(np.bincount(Z).argmax())
```
#### 84. Extraiga todos los bloques contiguos 3x3 de una matriz de elementos aleatorios 10x10 (★★★)
Extract all the contiguous 3x3 blocks from a random 10x10 matrix (★★★)
`hint: stride_tricks.as_strided, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# Autor: Chris Barker

Z = np.random.randint(0,5,(10,10))
n = 3
i = 1 + (Z.shape[0]-3)
j = 1 + (Z.shape[1]-3)
C = stride_tricks.as_strided(Z, shape=(i, j, n, n), strides=Z.strides + Z.strides)
print(C)

# Autor: Jeff Luo (@Jeff1999)

Z = np.random.randint(0,5,(10,10))
print(sliding_window_view(Z, window_shape=(3, 3)))
```
#### 85. Crea un matriz cuya subclase tenga Z[i,j] = Z[j,i] (★★★)
Create a 2D array subclass such that Z[i,j] == Z[j,i] (★★★)
`hint: class method`

```python
# Autor: Eric O. Lebigot
# Note: only works for 2d array and value setting using indices

class Symetric(np.ndarray):
    def __setitem__(self, index, value):
        i,j = index
        super(Symetric, self).__setitem__((i,j), value)
        super(Symetric, self).__setitem__((j,i), value)

def symetric(Z):
    return np.asarray(Z + Z.T - np.diag(Z.diagonal())).view(Symetric)

S = symetric(np.random.randint(0,10,(5,5)))
S[2,3] = 42
print(S)
```
#### 86. Consideremos un conjunto de p matrices cuya forma (n,n) y un conjunto de p vectores con forma (n,1). ¿Cómo calcular la suma de los productos de la matriz p a la vez? (el resultado tiene forma (n,1))(★★★)
Consider a set of p matrices wich shape (n,n) and a set of p vectors with shape (n,1). How to compute the sum of of the p matrix products at once? (result has shape (n,1)) (★★★)
`hint: np.tensordot`

```python
# Autor: Stefan van der Walt

p, n = 10, 20
M = np.ones((p,n,n))
V = np.ones((p,n,1))
S = np.tensordot(M, V, axes=[[0, 2], [0, 1]])
print(S)

# It works, because:
# M is (p,n,n)
# V is (p,n,1)
# Thus, summing over the paired axes 0 and 0 (of M and V independently),
# and 2 and 1, to remain with a (n,1) vector.
```
#### 87. Sea un 16x16 array, ¿cómo obtener la suma en bloques (tamaño del bloque 4x4)? (★★★)
`hint: np.add.reduceat, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# Autor: Robert Kern

Z = np.ones((16,16))
k = 4
S = np.add.reduceat(np.add.reduceat(Z, np.arange(0, Z.shape[0], k), axis=0),
                                       np.arange(0, Z.shape[1], k), axis=1)
print(S)

# alternative solution:
# Autor: Sebastian Wallkötter (@FirefoxMetzger)

Z = np.ones((16,16))
k = 4

windows = np.lib.stride_tricks.sliding_window_view(Z, (k, k))
S = windows[::k, ::k, ...].sum(axis=(-2, -1))

# Autor: Jeff Luo (@Jeff1999)

Z = np.ones((16, 16))
k = 4
print(sliding_window_view(Z, window_shape=(k, k))[::k, ::k].sum(axis=(-2, -1)))
```
#### 88. ¿Cómo implementar el Juego de la Vida usando numpy arrays? (★★★)
Juego de la Vida (Game Life)
Se trata de un juego de cero jugadores, lo que quiere decir que su evolución está determinada por el estado inicial y no necesita ninguna entrada de datos posterior. El "tablero de juego" es una malla plana formada por cuadrados (las "células") que se extiende por el infinito en todas las direcciones. Por tanto, cada célula tiene 8 células "vecinas", que son las que están próximas a ella, incluidas las diagonales. Las células tienen dos estados: están "vivas" o "muertas" (o "encendidas" y "apagadas"). El estado de las células evoluciona a lo largo de unidades de tiempo discretas (se podría decir que por turnos). El estado de todas las células se tiene en cuenta para calcular el estado de las mismas al turno siguiente. Todas las células se actualizan simultáneamente en cada turno, siguiendo estas reglas:
    Nace: Si una célula muerta tiene exactamente 3 células vecinas vivas "nace" (es decir, al turno siguiente estará viva).
    Muere: una célula viva puede morir por uno de 2 casos:
        Sobrepoblación: si tiene más de tres vecinos alrededor.
        Aislamiento: si tiene solo un vecino alrededor o ninguno.
    Vive: una célula se mantiene viva si tiene 2 o 3 vecinos a su alrededor.
`![Juego de la Vida](https://es.wikipedia.org/wiki/Juego_de_la_vida)`

```python
# Autor: Nicolas Rougier

def iterate(Z):
    # Count neighbours
    N = (Z[0:-2,0:-2] + Z[0:-2,1:-1] + Z[0:-2,2:] +
         Z[1:-1,0:-2]                + Z[1:-1,2:] +
         Z[2:  ,0:-2] + Z[2:  ,1:-1] + Z[2:  ,2:])

    # Apply rules
    birth = (N==3) & (Z[1:-1,1:-1]==0)
    survive = ((N==2) | (N==3)) & (Z[1:-1,1:-1]==1)
    Z[...] = 0
    Z[1:-1,1:-1][birth | survive] = 1
    return Z

Z = np.random.randint(0,2,(50,50))
for i in range(100): Z = iterate(Z)
print(Z)
```
#### 89. ¿Cómo obtener el enésimo (n-avo) valor más grande de un vector? (★★★)
`hint: np.argsort | np.argpartition`

```python
Z = np.arange(10000)
np.random.shuffle(Z)
n = 5

# Slow
print (Z[np.argsort(Z)[-n:]])

# Fast
print (Z[np.argpartition(-Z,n)[:n]])
```
#### 90. Dado un arbitrario número de vectores, contruya el producto cartesiano (la combinación de cada elemento con todos lo elementos) (★★★)
`hint: np.indices`

```python
# Autor: Stefan Van der Walt

def cartesian(arrays):
    arrays = [np.asarray(a) for a in arrays]
    shape = (len(x) for x in arrays)

    ix = np.indices(shape, dtype=int)
    ix = ix.reshape(len(arrays), -1).T

    for n, arr in enumerate(arrays):
        ix[:, n] = arrays[n][ix[:, n]]

    return ix

print (cartesian(([1, 2, 3], [4, 5], [6, 7])))
```
#### 91. ¿Cómo crear un registro a partir de un arrys normal? (★★★)
How to create a record array from a regular array? (★★★)
`hint: np.core.records.fromarrays`

```python
Z = np.array([("Hello", 2.5, 3),
              ("World", 3.6, 2)])
R = np.core.records.fromarrays(Z.T,
                               names='col1, col2, col3',
                               formats = 'S8, f8, i8')
print(R)
```
#### 92. Dado un vector muy largo Z, calcule Z elevado a la potencia 3 usando 3 diferentes métodos (★★★)
`hint: np.power, *, np.einsum`

```python
# Autor: Ryan G.

x = np.random.rand(int(5e7))

%timeit np.power(x,3)
%timeit x*x*x
%timeit np.einsum('i,i,i->i',x,x,x)
```
#### 93. Dados dos arrays A y B de tamaños (8, 3) y (2, 2) repectivamente. Cómo encontrar las fila de A que contengan elementos de cada fila de B 
Consider two arrays A and B of shape (8,3) and (2,2). How to find rows of A that contain elements of each row of B regardless of the order of the elements in B? (★★★)
`hint: np.where`

```python
# Autor: Gabe Schwartz

A = np.random.randint(0,5,(8,3))
B = np.random.randint(0,5,(2,2))

C = (A[..., np.newaxis, np.newaxis] == B)
rows = np.where(C.any((3,1)).all(1))[0]
print(rows)
```
#### 94. Dada una matriz 10x3, extraiga las filas con valores no iguales (Ejemplo [2,2,3]) (★★★)
`No hints provided...`

```python
# Autor: Robert Kern

Z = np.random.randint(0,5,(10,3))
print(Z)
# solution for arrays of all dtypes (including string arrays and record arrays)
E = np.all(Z[:,1:] == Z[:,:-1], axis=1)
U = Z[~E]
print(U)
# solution for numerical arrays only, will work for any number of columns in Z
U = Z[Z.max(axis=1) != Z.min(axis=1),:]
print(U)
```
#### 95. Convierta un vector de enteros a una matriz que represente los enteros en binario (★★★)
Convert a vector of ints into a matrix binary representation (★★★)
`hint: np.unpackbits`

```python
# Autor: Warren Weckesser

I = np.array([0, 1, 2, 3, 15, 16, 32, 64, 128])
B = ((I.reshape(-1,1) & (2**np.arange(8))) != 0).astype(int)
print(B[:,::-1])

# Autor: Daniel T. McDonald

I = np.array([0, 1, 2, 3, 15, 16, 32, 64, 128], dtype=np.uint8)
print(np.unpackbits(I[:, np.newaxis], axis=1))
```
#### 96. Dadas dos matrices, ¿Cómo extraer filas que sean únicas? (★★★)
Given a two dimensional array, how to extract unique rows? (★★★)
`hint: np.ascontiguousarray | np.unique`

```python
# Autor: Jaime Fernández del Río

Z = np.random.randint(0,2,(6,3))
T = np.ascontiguousarray(Z).view(np.dtype((np.void, Z.dtype.itemsize * Z.shape[1])))
_, idx = np.unique(T, return_index=True)
uZ = Z[idx]
print(uZ)

# Autor: Andreas Kouzelis
# NumPy >= 1.13
uZ = np.unique(Z, axis=0)
print(uZ)
```
#### 97. Considere dos vectores A y B, escriba usando `eisum` el equivalente de las funciones `inner`, `sum`, `outer` y `mul` (★★★)
Considering 2 vectors A & B, write the einsum equivalent of inner, outer, sum, and mul function (★★★)
`hint: np.einsum`

```python
# Autor: Alex Riley
# Make sure to read: http://ajcr.net/Basic-guide-to-einsum/

A = np.random.uniform(0,1,10)
B = np.random.uniform(0,1,10)

np.einsum('i->', A)       # np.sum(A)
np.einsum('i,i->i', A, B) # A * B
np.einsum('i,i', A, B)    # np.inner(A, B)
np.einsum('i,j->ij', A, B)    # np.outer(A, B)
```
#### 98. Considere un camino descrito por dos vectores (X,Y), ¿Cómo tomar muestras del mismo usando muestras equidistantes? (★★★)
Considering a path described by two vectors (X,Y), how to sample it using equidistant samples (★★★)?
`hint: np.cumsum, np.interp`

```python
# Autor: Bas Swinckels

phi = np.arange(0, 10*np.pi, 0.1)
a = 1
x = a*phi*np.cos(phi)
y = a*phi*np.sin(phi)

dr = (np.diff(x)**2 + np.diff(y)**2)**.5 # segment lengths
r = np.zeros_like(x)
r[1:] = np.cumsum(dr)                # integrate path
r_int = np.linspace(0, r.max(), 200) # regular spaced path
x_int = np.interp(r_int, r, x)       # integrate path
y_int = np.interp(r_int, r, y)
```
#### 99. Dado un entero n y una matriz X, seleccione de X las filas que pueden ser interpretadas como extraídas de una distribución multinomial con n grados.
Es decir las filas que contengan enteros y que suman n. (★★★)
Given an integer n and a 2D array X, select from X the rows which can be interpreted as draws from a multinomial distribution with n degrees, 
i.e., the rows which only contain integers and which sum to n. (★★★)
`hint: np.logical_and.reduce, np.mod`

```python
# Autor: Evgeni Burovski

X = np.asarray([[1.0, 0.0, 3.0, 8.0],
                [2.0, 0.0, 1.0, 1.0],
                [1.5, 2.5, 1.0, 0.0]])
n = 4
M = np.logical_and.reduce(np.mod(X, 1) == 0, axis=-1)
M &= (X.sum(axis=-1) == n)
print(X[M])
```
#### 100. Calcule con un intervalo de confianza del 95% el promedio de un vector X.
(es decir, volver a muestrear los elementos ddel vector N veces, calcular la media de cada muestra y luego calcular percentiles sobre los promedios). (★★★)
Compute bootstrapped 95% confidence intervals for the mean of a 1D array X 
(i.e., resample the elements of an array with replacement N times, compute the mean of each sample, and then compute percentiles over the means). (★★★)
`hint: np.percentile`

```python
# Autor: Jessica B. Hamrick

X = np.random.randn(100) # random 1D array
N = 1000 # number of bootstrap samples
idx = np.random.randint(0, X.size, (N, X.size))
means = X[idx].mean(axis=1)
confint = np.percentile(means, [2.5, 97.5])
print(confint)
```