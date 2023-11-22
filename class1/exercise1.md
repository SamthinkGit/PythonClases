# Exercise 1: Testing model running time
## Descripcion General
Objetivo: Crear un script de python que sea capaz de analizar un modelo de ML en un dataset dado. Las caracteristicas a analizar seran el comportamiento de precision y tiempo de ejecucion en multiples ejecuciones distintas.

Para completar este ejercicio es necesario vamos a dividirlo en varios pasos que se pueden completar de forma independiente. Para practicar buenas practicas de Python se van a aplicar algunas **restricciones** de diseño al codigo. Entre las que destacan las siguientes:
1. **Anidamiento maximo de 3 niveles**: Siempre que anidamos (metemos dentro de) un `if`, `for`, etc. dentro de otra estructura, aumentamos la complejidad del sistema. Python es suficientemente robusto como para poder evitar, de forma general, tener que realizar 3 anidamientos sin separacion. Este sera entonces el maximo permitido para este ejercicio:
```python
# Niveles de Anidamiento
if condition:        # Level 1
  if condition2:     # Level 2
    if condition3:   # Level 3
      if condition4: # Level 4
      ...
```
```python
# --- Incorrecto ---
# Se alcanza el nivel 4
for _ in range(N):
  if condition1:
    if condition2:
      func1()
    else:
      func2()
  else:
    func3()
```
```python
# --- Correcto ---
# Sin encastillamiento ni redundancia

for _ in range(N):

  if condition1 and condition2:
    func1()
    continue

  if condition2:
    func2()

  func3()  
```

2. Numero de lineas reducido: No hay limite concreto pero hay que optimizar el codigo para que ejecute en el MENOR numero de lineas posible (for's anidados en arrays, reutilizacion de variables, reciclaje de funciones...). En caso de duda prima la limpieza de codigo sobre reducción
3. Notacion Camello obligatoria: Indentacion a elegir sin embargo uso de nombrado de variables y funciones obligatorio. Tipado fuerte recomendado si no entorpece la ejecucion

## Estructura
Para completar el ejercicio se tienen que seguir los siguientes pasos (Puedes usar docs o ChatGTP para informacion no incluida, researching):
______

### Preparacion
1.  Crear una cuenta en [Google Colab](https://colab.google/), donde crearemos un cuaderno en el que trabajar con suficiente potencia
2.  Descargar la funcion load_data() del Classroom, junto a los dataset de prueba. (Utilizaremos dataset1.csv)
3.  Importar dichos ficheros en la raiz del sistema y conseguir realizar ```python X, Y = load_data("dataset.csv")```. **No se puede copiar el codigo directamente al cuaderno!**

______

### Creacion de Interfaz
1. Crear una nueva Seccion nada mas al comienzo donde estaran todos los import. No se puede importar en otro lugar de codigo que no sea aqui. Como buena practica debe seguir el siguiente orden:
```python
from libreriagatuna.gatos import Gato, Gatito
from libreriagatuna.libros import Libro

from milibreria import RGB
from mifichero import func as mifunc

import bola_de_lana as lana
import milibreria.lana as milanesa

import gatos as cats
import mifich
```
2. Crear una nueva Sección de codigo donde guardaremos las variables mutables. Es decir aquellas que podemos cambiar para definir el comportamiento del sistema. Todas las variables mutables (que son modificables por un usuario, ej: num. de iteraciones) deben residir aqui.
3. Crear una nueva Seccion de inicializacion de variables o constantes no mutables (ej: arr = []), opcional.
______

### Definicion de Funciones:
1. Definiremos una funcion `train(model, X, Y, split_size, preprocessor)` (donde split_size y preprocessor son opcionales) que realizara los siguientes pasos:
  - Crea una semilla aleatoria con `random.randint()` de la libreria `random`
  - Ahora podemos particionar el conjunto de datos X, Y utilizando la siguiente funcion:
```python
X_train, X_test, Y_train, Y_test = train_test_split( X, Y, test_size, random_state)
```
  - Si es necesario, agregaremos al modelo nuestro preprocesador con ```python pipe = make_pipeline(preprocessor, model)```. Nota, tambien se podrian encadenar preprocessors asi.
  - Utilizamos la funcion `model.fit(x,y)` para entrenar a nuestro modelo con el conjunto de datos

2. Definiremos una nueva funcion `eval_predict(model, X, Y)` que retornara un diccionario con los siguientes elementos:
  - **'prediction'**: Salida de `model.predict(X)`
  - **'accuracy'**: Salida de `accuracy_score(y_real, y_pred)` de `sklearn.metrics`
  - **'precission'**: Salida de `precision_score(y_real, y_pred, average='weighted', zero_division=0)` de `sklearn.metrics`

3. Definiremos una funcion `eval_in_batch(model, X, Y, split_size, iter, preprocessor)` que evaluara el comportamiento del modelo en `iter` iteraciones. Para ello:
  - Debe retornar un pandas DataFrame con la informacion de todas las ejecuciones (entrenamiento + prediccion). Pandas es una libreria estandarizada a dia de hoy para trabajar con conjuntos de datos, puedes usarla tal que:
```python
# Build dataframe
df = pd.DataFrame(columns=["Iteration", "Cat-uracy", "Paws"])

# Add some rows
df.loc[len(df.index)] = [ 1, "0.99", "4" ]
df.loc[len(df.index)] = [ 2, "0.2", "4" ]

# Print it as a table
print(df)
```
  - Asegurate de que los valores del df esten redondeados a 3 decimales
  - Asegurate de medir los tiempos de entrenamiento utilizando `t = time.time()` para comenzar un reloj y `time.time() - t` para terminarlo

4. Definiremos una funcion `plot_results` que utilizara graficara el tiempo de ejecucion comportamiento. Como ejemplo de como plottear y manejar df's puedes ver el siguiente ejemplo:
```python
df[['ColA', 'ColB']].plot(kind='line')  # Also can use kind='bar'
plt.xlabel(...)
plt.title(...)
plt.show()
```
______
### Ejecucion y Analisis
Crea una nueva seccion donde se ejecutara el programa principal. Este debe:
- Leer un dataset dado
- Crear un modelo SVC con kernel lineal o sigmoid desde `sklearn.svm`

- Crear un preprocesador `MinMaxScaler` o `StandardScaler` de `sklearn.preprocessing`
- Imprimir una tabla y grafica con el comportamiento del modelo a lo largo de 10 iteraciones distintas

______
### Bonus
Agrega una barra de carga mientras el modelo esta entrenando usando (truco pro) la libreria `tqdm`
```python
from tqdm import tqdm
# Ejemplo 1
for i in tqdm(range(10)):
    time.sleep(0.5)  # Simulando una tarea

# Ejemplo 2
for key, value in tqdm(ejemplo_dict.items()):
    time.sleep(0.5)  # Simulando una tarea

# Ejemplo 3:
with tqdm(ejemplo_dict.items(), desc="Training Models") as t:
  t.set_description("Model 1")
  ...
  t.write("✅")
```
