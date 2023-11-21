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

```
