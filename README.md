# Sistema de Recomanació Multi-Domini (Pel·lícules i Llibres) 

Aquest projecte és un **Sistema de Recomanació** desenvolupat completament en Python utilitzant principis sòlids d'enginyeria de programari, com la **Programació Orientada a Objectes (OOP)** i el patró de disseny de responsabilitat única, separant la lògica en mòduls independents.

El sistema és capaç de processar datasets de valoracions (ratings) i recomanar ítems basant-se en diferents algoritmes de *Machine Learning* clàssics, a més d'incloure un sistema de validació per mesurar-ne la precisió.

## Característiques Principals

### 1. Arquitectura Modular i OOP
El projecte està estructurat en diferents mòduls per facilitar-ne l'escalabilitat:
*   **Classes Abstractes (`models.py`)**: S'utilitzen classes base abstractes (`Item`, `Recommender`) mitjançant el mòdul `abc` de Python per definir interfícies clares, sent implementades per classes concretes (`Movie`, `Book`).
*   **Gestor de Dades (`dataset.py`)**: S'encarrega del pretractament de dades, neteja de CSVs i separació entre dades d'entrenament i prova (Train-Test Split).
*   **Avaluador Estadístic (`evaluation.py`)**: Calcula automàticament l'error de les prediccions.

### 2. Algoritmes de Recomanació Implementats (`recommenders.py`)
L'usuari pot seleccionar entre tres motors de recomanació diferents:
*   **Simple (Popularitat):** Calcula un *score* ponderat basat en la mitjana de valoracions d'un ítem respecte a la mitjana global i el nombre de vots. Ideal per solucionar el problema del "Cold Start".
*   **Filtratge Col·laboratiu (User-Based):** Troba usuaris similars calculant la **Similitud del Cosinus (Cosine Similarity)** entre els vectors de valoracions dels usuaris (mètode K-Nearest Neighbors).
*   **Basat en Contingut (Content-Based):** Utilitza tècniques de Processament de Llenguatge Natural (NLP). Construeix una matriu **TF-IDF (Term Frequency-Inverse Document Frequency)** des de zero utilitzant funcions de NumPy per vectoritzar els gèneres/etiquetes i crear perfils d'usuari personalitzats.

### 3. Mètriques d'Avaluació
Per comprovar la precisió dels models, el sistema incorpora càlculs d'error estàndard a la indústria:
*   **MAE (Mean Absolute Error):** Error Absolut Mitjà.
*   **RMSE (Root Mean Square Error):** Arrel de l'Error Quadràtic Mitjà, penalitzant prediccions molt allunyades del valor real.

## Tecnologies Utilitzades
*   Python 3.x
*   **NumPy**: Utilitzat per a càlculs matricials i algebra lineal eficients (càlcul de TF-IDF i vectors de similitud).
*   `statistics`, `math`, `collections` (Standard Library)

## Execució i Ús

1. Assegura't de tenir els arxius de dades (`ratings.csv`, `movies.csv`, `Ratings_books.csv`, `Books.csv`) a la carpeta arrel del projecte.
2. Instal·la les dependències necessàries:
   ```bash
   pip install numpy
   ```
3. Executa l'orquestrador principal:
   ```bash
   python main.py
   ```
4. El sistema et guiarà a través d'una interfície de línia de comandes (CLI) per escollir el dataset, l'algoritme, recomanar i avaluar usuaris específics.
