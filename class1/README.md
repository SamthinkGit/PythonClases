# Teoria Básica
## Compilado vs Interpretado

Python no es un lenguaje compilado, es **interpretado**, esto implica que no puedes detectar errores hasta ejecutarlos.

Comparemos lo que pasaria en `C++`
```c++
int main(int argc, String[] argv) {

  int a = 1                            // Creamos un int
  std::cout < "Funciona" < std::endl   // Imprimimos Funciona
  exit()                               // Salimos
  a += "Miaw"                          // Creamos un error

}
```
```sh
Output: Error en linea 2:
"a" no puede ser asignado a un String
# Fijate como el programa NO compila si existen errores
```


De la misma forma creemos un codigo equivalente pero en `Python`:
```python
if __name__ == "__main__":
  a = 1               # Hacemos una variable
  print("Funciona")   # Imprimimos Funciona
  exit(0)             # Salimos
  a = int("Miaw")     # Creamos un error
```
```sh
Output: Funciona
# No ha llegado a ejecutar el error, no detecta que existe
```

## Todo es un objeto en Python
En python todas las variables son objetos, es decir, siempre vamos a tener las propiedades de POO para cada variable (funciones, atributos, etc.)
```python
a = 1
a.to_bytes()
```

## Tipado Fuerte vs Tipado Suave
Python tiene tipado suave, es decir, solo importa el TIPO de la variable si lo especificamos. Asi pues, podemos cambiar una variable de tipo en tiempo de ejecucion sin ningun problema como vemos en el siguiente ejemplo:
```python
a = 1
a = "Miaw"
```
Sin embargo hay que recordar en tipado SUAVE implica que el tipo PUEDE ser importante si asi lo especificamos (Si no sigues las reglas, la version en la que estes puede jugarte malas pasadas):
```python
def func(num: int):
  print(num)

func(True)
```
```sh
python2 miprograma.py
-> SyntaxError
python3 miprograma.py
-> output: True
```

# Variables
Hagamos un repasito rapido de todas las variables importantes que se usan en Python:
```python
# Numeros
i = 1      # int
f = 1.1    # float
b = True   # Bool
b = False  # Bool

# Conjuntos
arr = [1,2,3,4]  # Array
arr2 = [ [1,2], [3,4] ] # 2D-arr
tup = (3,4)  # Tuple  (Modificame una vez creado y hare PUM)
dict = {
  4: "Cuatro",
  mivar: "Variable",
  2: True,
}

# Strings
t = "Miaw"
t = "Miaw"
t = 'Mew'
t = '''
Miw
pero con Enter
'''
t = ' "Mow" pero entre comillas '
string_pro = f"Muestra la variable {var} y despues {var2.toUpperCase()}"

# Especiales
None # Variable que indica que no somos nada, util para inicializar variables
```

# Condiciones
Practicamente igual que en otros lenguajes pero aqui tenemos palabras para simplificarnos la vida
```python
# Clasicos
if a == 1:
if a != 1
if a is None
if a is not None

# Booleanos
if boolan:
if not boolean:

# Comparaciones
if a > 1:
if a < 1:
if a >= 1:
if a <= 1:
```

**OJO CUIDAO'**:  Realmente no es lo mismo el comando `is` que el comando `==`. El primero hace referencia a si son el **mismo objeto**, el segundo a si **son iguales** Veamoslo:
```python
gato1 = Gato()
gato2 = Gato()

if gato 1 == gato2:
  # Voy a ejecutar, somos iguales (gatos)

if gato1 is gato2:
  # No ejecuto :' no somos el mismo gato
```

**Consejo para Pro's**: Si es un if muy simple, utiliza un `if` anidado. Queda re-profesional:
```python
sam = Gato()

print( "Es un GATO!" if sam is Gato() else "Ka pasao primo" )
mivar = Gato() if sam is Gato() else None
```

# Loops
El clasico loopeo. Hay tantas formas en python que es imposible aprenderlas todas. Vamos a por las importantes. Empezando por mi favorita, el `for`:
```python
# --- Iteracion Clasica ---
for i in range(5)
  # i = 0,1,2,3,4,5

for i in ["Sam", "Angela"]:
  # i = "Sam", "Angela"

arr = ["Sam", "Angela"]
for i in range(len(arr)):
  # i = 0,1

for idx, name in enumerate(arr)
  #  idx = 0,1
  #  name ) Sam, Angela


# --- Diccionarios ---
Angela = 10
Sam = 9
dict = {
  "NotaSam" : Sam,
  "NotaAngela" : Angela
}
for value in dict.values():
  # value = 10, 9

for key in dict.keys():
  # key = "NotaSam", "NotaAngela"

for key, value in dict.items():
  # value = 10, 9
  # key = "NotaSam", "NotaAngela"
```

Consejo para Pro's: Utilizar de vez de cuando `for` anidados si es un for muy simple (No complicarsus la vida). Eso si, siempre tienes que guardar el resultado en un array.
```python
nums = [1,2,3,4]

arr = [ i += 1 for i in nums ]
# arr = [2,3,4,5]

arr = [ i += 1 for i in range(len(nums)) ]
# arr = [ 1, 2, 3, 4 ]
```

Ahora vamos a por los while:
```python
# No uses while
```

```python
# Nah ahora si, basta con que memorices 2 tipos:

while True:
  # Forever

while condition.is_true_each_iteration():
  # Who knows
```

# Palabras Clave
Hay algunas cosicas que son cuanto menos utiles y en otros lenguajes no existen. Unos muy conocidos y si comunes en c++ o cosas asi es `continue` y `break`:
```python

while True:
  
  if me_muero():
    break  # Rompemos el bucle

for name in ["Angela", "Sam"]:

  if name == "Sam":
    continue  # Me salto una iteracion

  if me_muero_otra_vez():
    break

  # Consejo pro: No uses else a menos que sea estrictamente necesario. Aqui por ejemplo es imposible que llege "Sam",
  # por lo que no usamos else
  print(name)
```

Tambien hay otra instruccion un pelin boba, pero muy util mas adelante. Hablamos de `pass`. Basicamente no hace nada.
```python
if name == "Sam":
  es_gato()
else:
  pass  # No hace na'
```

Si queremos forzar el tipado de una variable (Tipado Suave) entonces puedes usar las siguientes variables clave:
```python
int()  # El segundo mas usado
float()
bool()
str() # El mas usado
double()
...

fl = 2.2
print(int(fl)) # Esto me devuelve 2

arr = [1,2]
text = str(arr) # Ahora text = '[ 1, 2 ]'
```
**Ojo cuidao'**: En python todo son objetos. INCLUIDAS las funciones, eso implica que podemos cargarnos funciones basicas del sistema si no nos acordamos de esta regla:
```python
str = "Hola"
print(str([1,2]))
# ERROR AL CANTO

# Ahora str es "Hola" NO es una funcion basica. Pero esto funciona con todo
print(str) # -> Hola

range = [1,2]
for i in range(5):
  # A la puta
```

Finalmente esta la variable `_`. Muy utilizada para definir que algo no importa:
```python
for _ in range(5):
  print("miaw")
# No nos importa i la vd
```

# Funciones
Ya acabamos con la teoria, dont worry. Esto es Easy-peacy funciona igual que en el resto:
```python
def sumar(A,B):
  num = A + B
  return num
```

Hagamos algo un poco mas pro ahora. Asigancion en cadena:
```python
def numeros():
  return [1,2,3]

a, b, c = numeros()
```

Compliquemos un poco mas, forcemos tipado fuerte:
```python
def(a:int, b: int):
  return a+b
```
**¿Pero para que weas quiero esto?** Fasil, para ser buena persona con la humanidad y contigo misma. Fijate, cuando usas tipado fuerte, tu IDE te sabe ayudar:
![image](https://github.com/SamthinkGit/PythonClases/assets/92941012/aa67ee09-2907-4c64-9caf-e077502c639f)

Pero si no utilizases tipado...

![image](https://github.com/SamthinkGit/PythonClases/assets/92941012/bf1f03aa-a70e-48a7-a571-de8d29a6caf9)

Ahora vayamos a por truquitos que empiezan a destacarte como programadora pro. (Im rlly, si ves codigo de ppl no usan esto, no le saben):
```python
# Usa -> para tipar la SALIDA
def my_name() -> str:
  return "Angela"

# Aqui no devuelva nada, no tipas
def my_name():
  print("Miaw")

# No sabes que vas a devolver? Truco ULTRA-MEGA PRO atenta que esta no se la saben:
from typing import Any
def miw() -> Any:
  return who_knows()


# Creamos variables predeterminadas o con valores por defecto:
def info(cute: bool = True, var: Any = Gato()):
  return Gato() if cute else Perro()

# Agregamos una pequeña descripcion utilizando formato estandar:
def build_a_cat(paws: int = 4, is_cute: bool) -> Gato:
  """
  Builds a new cat with paws and maybe cute
  :param paws: num of paws
  :param is_cute: Should be cute?
  :returns: A cat
  """
  return Gato(paws=paws,is_cute=is_cute)

# Si algun parametro es opcional lo marcamos para que el usuario lo sepa
from typing import Optional
def sam_es_mono(Optional[bool]: mentir = None):
  if mentir is not None
    return true
  else
    return true

# Finalmente podemos indentar y agregar algunos tipados extra (Trucazo, dejo aqui los imports) y tenemos nuestra funcion ultra pro:
from typing import Any, Optional, List, Dict
def milkshake(
  water: Water = Water(50),
  milk: Milk = Milk(30),
  chocolat: bool = True,
  toppings: Optional(List[Toppings]) = None,
  clients: Dict[str, Any] = None
) -> Milkshake:
  """
  Builds a milkshake
  :param water: The water
  :param milk: The milk
  :param chocolat: Should it have chocolat?
  :param toppings: A list of toppings, Example: [Cookies(), Oreos()]
  :param clienss: A dict with the clients. Example: {"Angela": Gata(), "Sam": Gato()}
  :returns: The milkshake
  """
  return build_milkshake()

# Podriamos usarlo tal que asi
milkshake(clients={'Angela': Gata()})
```

Ahora que ya tenemos todo tipado, ya el IDE sabra trabajar con ello y darnos predicciones automaticas ademas de que podra darnos muchisima info sobre cada funcion (ademas de incluso auto-generacion de documentos informativos):

![image](https://github.com/SamthinkGit/PythonClases/assets/92941012/c4f910ca-b618-43cd-882f-be62c5809443)

# Matematicas y Numpy
Ok es momento de ponerse manos a la obra, sumar restar, multiplicar, etc etc.
```python
from numpy import np
```
Primero veamos que pasa si intentamos hacer mates sin numpy
```python
# Cosas que estan bien
a = 1 + 1  # a=2
a += 1     # a=3
a -= 1     # a=2
5 % 3      # 2
5 / 3      # 1.666...
5 * 3      # 15
[5] * 3    # [5,5,5]
[5] + [1]  # [5,1]

# Cosas que estan mal
(3) + 1      # Runtime Error
[1,2,3] + 1  # Syntax Error
[5] * [3]    # Syntax Error
2^3          # Esto significa 00000010 & 00000011 = 00000001 = 1 movidas complejas xD
```

Ahora ya podemos probar a crear un array con numpy y ver sus nuevas propiedades:
```python
array = [2,2,2]
vector = np.array(array)

vector * 2      # [4,4,4]
vector / 2      # [1,1,1]
vector*vector   # [4,4,4]
vector + 1      # [3,3,3]
np.sum(vector)  # 6
np.mean(vector) # 2
vector.transpose()  # [2,2,2] En el fondo en vd es lo mismo para un vector
vector.append(2) # [2,2,2,2]
np.loquetedigaelIDE() # Hay mil funciones puedes buscar en google

matrix = np.mat([1,1,1],[2,2,2],[3,3,3])
matrix*matrix   # Bro no lo voy a calcular xD
np.sum(matrix)  # [3,6,9]
np.sum(np.sum(matrix))  # 18
matrix.transpose()...

Y si quieres hacer un print, consejito pro:
from pprint import pprint
pprint(matrix)
```

## Buenas Practicas
Python es un lenguage que te obliga a indentar las variables o funcinoes anidadas, sin embargo, eso no implica que el estandar sea solo esto. Un codigo bonito indenta siempre de forma legible tal que asi:
```python
# Esto es un poco feucho, prueba asi:
mifuncion(mi_var1, mivar2, mivar3, True,
  [i for i in myarray])

# --- Bonito ----
# 1. Separa variables:
arr = [i for i in myarray]

# Enseña parametros e indenta
mifuncion(
  name=mi_var1,
  nums=mivar2,
  argv=mivar3,
  is_hard=True,
)
```

La **notacion Camello** es el formato estandar de nombrado de variables. Todo buen codigo utiliza este formato. Simplemente con ver el nombre de una variables puedes obtener informacion sobre que es:

```python
variable = 5       # Todo minusculas
variable_nueva = 5 # Se acepta
variableNueva      # Mejor

gato = Gato()         # gato es una variable que apunta a un objeto. Gato es el objeto, va con mayusculas
gatoRojo = GatoRojo() # Esta bien
gatoRojo = gato_Rojo  # Horrible

CONSTANTE = 4   # Esto no va a cambiar, lo dejamos todo con mayus
CONSTANTE_2 = 2 # Perfecto

def sumar_nums():  # Bien, comun en python
def sumarNums():   # Bien
def SumarNums():   # Mal, no es un objeto

variable_privada # Mejorable eh
_variable        # Mucho mejor
__variable       # Nope, esto significa perteneciente al sistema

def num_to_string():  # Bien
def num2string():     # Esto es mas pro
def to_string(self):  # Usando POO, best option

class miClase():  # Nope
class MiClase():  # Si, es un objeto/clase

def funcion_no_usar():  # Weird
def _funcion():         # Esto si

def sumar_y_multiplicar():  # No, cada funcion hace UNA cosa
# Mejor:
def sumar():
def multiplicar():

multiply([4,3,2],[1,2,3],[1,1,1],[2,2,2])  # Meh
multiply(
  [4,3,2],
  [1,2,3],
  [1,1,1],
  [2,2,2]
) # Mejor

#Comentario feo
# Comentario mejor

a=4   # Nope
a = 4 # Sep

func(a=4)   # Bien
func(a = 4)  # Bien

# --- Meh ---
function1() # Esto hace A
# Esto hace B
funcion2(a,b,c)

# --- Mejor ---
# Esto hace A y B
funcion1()
funcion2(a,b,c)

# --- O esto ---
funcion1()      # A
funcion2(a,b,c) # B

[1,1,1,1,1,1]    # Un poco largo
[1] * 6          # Mas pro

i = get_columns()       # Generalmente no, solo en loops, y no acostumbrarse demasiado
columns = get_columns() # Mejor
```
Y por ahora con esto tenemos la clase 1 bro, ya mañana te hago mas. Te dejare en este repo algunos ejercicios.
