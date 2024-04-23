# Preprocesamiento de datos
El preprocesamiento y la limpieza de datos son pasos cruciales en el análisis de datos, ya que la calidad de los datos afecta directamente la precisión de los resultados analíticos. Aquí te detallo los puntos más importantes a considerar al limpiar datasets, específicamente para archivos JSON y CSV, y cómo abordar cada uno de ellos.

## Puntos clave para la limpieza de datasets en formatos JSON y CSV
#### 1. Detección y manejo de valores faltantes:
· JSON: Valores faltantes pueden aparecer como null. Puedes decidir si eliminar estos elementos, dejarlos como null, o imputarlos con un valor promedio, mediano, o el más frecuente.

· CSV: Los valores faltantes suelen representarse como celdas vacías o con marcas específicas como NA. Utiliza funciones en pandas como fillna() para imputar valores o dropna() para eliminar filas/columnas con valores faltantes.
#### 2. Corrección de tipos de datos:
· JSON: Asegúrate de que cada campo tiene el tipo de dato correcto (int, float, string). Utiliza json.loads() y especifica el tipo de dato si es necesario.

· CSV: Utiliza pandas para cargar el CSV y verifica los tipos de datos con df.dtypes. Cambia los tipos de datos con astype() si es necesario.
#### 3. Detección y eliminación de duplicados:
· JSON y CSV: Carga los datos en un DataFrame de pandas y utiliza drop_duplicates() para eliminar registros duplicados.
#### 4. Tratamiento de errores y valores atípicos:
· JSON y CSV: Identifica valores que no sean realistas o que sean errores de captura. Puedes usar técnicas estadísticas para detectar valores atípicos, como el método de IQR (rango intercuartílico).

· Elimina o corrige estos valores según el contexto del análisis.
#### 5. Normalización y estandarización:
· JSON y CSV: Para características numéricas, normaliza o estandariza los datos si vas a utilizar técnicas de aprendizaje automático que sean sensibles a la escala de los atributos.

· Usa StandardScaler o MinMaxScaler de sklearn.preprocessing.
#### 6. Codificación de variables categóricas:
· JSON y CSV: Convierte variables categóricas en formatos numéricos usando técnicas como one-hot encoding (get_dummies en pandas) o label encoding (LabelEncoder en sklearn).
#### 7. Corrección de formatos de datos:
· JSON: Asegúrate de que las fechas, números y otros formatos especiales sean coherentes y correctos. Utiliza pd.to_datetime() para convertir cadenas en fechas.

· CSV: Similar al JSON, asegura la consistencia de formatos, especialmente en columnas de fechas y números.
#### 8. Verificación de Formato Correcto:
· JSON: Verifica que el archivo JSON sea un objeto o un arreglo válido. Utiliza herramientas o librerías que identifiquen errores de formato (como corchetes o llaves faltantes, comas mal colocadas, etc.). Utiliza bloques try-except al cargar JSON para capturar errores y manejar archivos mal formateados.

· CSV: Asegúrate de que el delimitador y las comillas sean consistentes a lo largo del archivo. Pandas permite especificar estos caracteres al leer el archivo con pd.read_csv().
Verifica que todas las filas tengan el mismo número de columnas que los encabezados.
#### 9. Manejo de Archivos Mal Formateados:
· JSON: Para archivos JSON que contengan múltiples objetos sin estar en un arreglo, procesa el archivo como texto y divide y carga los objetos uno por uno, como se explicó anteriormente.

· CSV: Identifica y maneja o elimina filas que no cumplan con el formato esperado, como número incorrecto de campos, usando las opciones error_bad_lines y warn_bad_lines en pd.read_csv().
#### 10. Corrección de separadores decimales y otros formatos numéricos:
· JSON y CSV: Realiza conversiones de formatos numéricos, como cambiar comas por puntos en decimales. Usa métodos de cadena en Python o funcionalidades específicas de pandas para hacer estas transformaciones antes de convertir las cadenas a números.
#### 11. Normalización de datos textuales:
Asegúrate de que los datos textuales estén en formatos coherentes, como mayúsculas/minúsculas uniformes, eliminación de espacios extra y corrección de errores ortográficos conocidos.
