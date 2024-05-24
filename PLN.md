# Bootcamp Análisis y Visualización de Datos

## Refinamiento de Técnicas de Análisis de Datos: Técnicas de análisis de datos textuales
El análisis de datos textuales es un campo en crecimiento, lleno de herramientas que ayudan a procesar y entender grandes cantidades de texto.
El lenguaje es una herramienta clave en nuestra vida social y laboral. Nos ayuda a transmitir ideas, información y sentimientos, así como a persuadir o pedir cosas. Sin embargo, el lenguaje humano es complejo y cambia constantemente. Por ejemplo, la frase: "comí una pizza con amigos" tiene un significado diferente a "comí una pizza con aceitunas", aunque tengan la misma estructura. Además, un mismo mensaje puede expresarse de diferentes formas; por ejemplo: "comí una pizza con amigos" puede decirse también como "compartí una pizza con amigos".
Aunque los humanos somos buenos interpretando el lenguaje, entenderlo y describir sus reglas formalmente es difícil. Por eso, el procesamiento del lenguaje natural (NLP por sus siglas en inglés) es un área de estudio en inteligencia artificial que se enfoca en resolver este problema.



## NLTK

#### Es una biblioteca desarrollada por Steven Bird y Edward Loper para el NLP, principalmente en inglés. Incorpora muchas funcionalidades como corpus, recursos léxicos y algoritmos de aprendizaje para el NLP.


pip install jupyter

pip install nltk
pip install matplotlib

import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import cess_esp
from nltk.probability import FreqDist
import matplotlib.pyplot as plt


# Paso 1: Importar NLTK y descargar el corpus cess_esp
nltk.download('cess_esp')
# Paso 2: Cargar el texto del corpus
texto_corpus = ' '.join(cess_esp.words())
# Paso 3: Tokenizar el texto
tokens = word_tokenize(texto_corpus)
# Limpiar la lista de tokens eliminando palabras vacías y signos de puntuación
tokens = [palabra.lower() for palabra in tokens if palabra.isalnum()]
# Paso 4: Realizar análisis de frecuencia
frecuencia = FreqDist(tokens)
print("Palabras más frecuentes:")
for palabra, freq in frecuencia.most_common(20):
print(f"{palabra}: {freq}")

# Paso 5: Visualizar los resultados del análisis de frecuencia
plt.figure(figsize=(10, 5))
frecuencia.plot(20, cumulative=False)
plt.title('Palabras más frecuentes en el corpus cess_esp')
plt.xlabel('Palabra')
plt.ylabel('Frecuencia')
plt.xticks(rotation=45)
plt.show()
