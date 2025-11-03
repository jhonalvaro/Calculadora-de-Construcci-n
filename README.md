# Calculadora de Construcción

Esta es una aplicación web estática que proporciona calculadoras para diversos cálculos en construcción, especialmente para trabajo con tubos, metales y geometría aplicada en edificación y metalurgia.

## Descripción

La aplicación incluye 11 funciones de cálculo basadas en el archivo `codo.js`, originalmente desarrollado para WebVI. Cada función realiza cálculos específicos para elementos como codos, barandas, pasamanos, etc., utilizados en construcción y fabricación.

## Funciones Disponibles

1. **codoWithJSLI**: Calcula el descuento, desarrollo, tangente y biset para la fabricación de codos en tubos.
   - Parámetros: Ángulo, tubo, radio, factor K, eje.
   - Resultados: Descuento, desarrollo, tangente, biset.

2. **ejeWithJSLI**: Calcula resultados basados en arreglos de entrada y salida para ejes.
   - Parámetros: Arreglo de entrada [longitud, eje], arreglo de salida.
   - Resultados: Dos valores calculados.

3. **contravuelcoWithJSLI**: Calcula dimensiones para contravuelcos, incluyendo ancho, ángulo de patas, lados y marcas.
   - Parámetros: Ángulo, marca centro, rodillo, largo, altura, tubo, eje in.
   - Resultados: Ancho, ángulo patas, lado pendiente, lado centro, marca pendiente, centro.

4. **productopuntoWithJSLI**: Calcula el producto punto (dot product) entre dos vectores.
   - Parámetros: Dos vectores (arreglos numéricos).
   - Resultado: Valor escalar del producto punto.

5. **anguloWithJSLI**: Calcula el ángulo entre dos vectores en grados.
   - Parámetros: Dos vectores (arreglos numéricos).
   - Resultado: Ángulo en grados.

6. **angulovectorWithJSLI**: Calcula el ángulo entre vectores utilizando un tercer vector de referencia.
   - Parámetros: Tres vectores (arreglos numéricos).
   - Resultado: Ángulo en grados.

7. **puntaangulorWithJSLI**: Calcula desarrollo, marcas y dimensiones para puntas angulares roladas.
   - Parámetros: Diámetro, tubo, ángulo, altura centro, factor K, sobra.
   - Resultados: Desarrollo, marca centro, marca recto, ancho rest, altura rest, borr.

8. **barandaWithJSLI**: Calcula desarrollo, marcas y descuento para barandas.
   - Parámetros: Ángulo, tubo, rodillo, ancho, altura, factor K.
   - Resultados: Desarrollo, marca AL, marca CT, descuento, altura EJE.

9. **dosaguasWithJSLI**: Calcula ápice, marca lado, ángulo inferior y lado para techos a dos aguas.
   - Parámetros: Ángulo, tubo, rodillo, ancho, factor K.
   - Resultados: Apice, marca lado, ángulo inferior, lado.

10. **pasamanoWithJSLI**: Calcula desarrollo y marcas para pasamanos.
    - Parámetros: Rodillo, tubo, largo, pata1, ángulo1, pata2, ángulo2, factor K.
    - Resultados: Desarrollo, marca pata1, marca pata2, marca largo.

11. **parchoqueWithJSLI**: Calcula desarrollo, marcas y descuento para parchoques.
    - Parámetros: Ángulo, tubo, rodillo, ancho, altura, factor K.
    - Resultados: Desarrollo, marca AL, marca CT, descuento.

## Fórmulas y Cálculos Detallados

A continuación, se detallan las fórmulas matemáticas utilizadas en cada función, basadas en el código de `codo.js`. Las fórmulas implementan principios de geometría, trigonometría y metalurgia para cálculos de construcción.

### 1. codoWithJSLI
Calcula dimensiones para doblar tubos en codos.
- **Tangente**: \( \text{tangente} = \frac{\text{radio} + \text{eje} \times \text{tubo} / 2}{\tan(\text{ángulo} \times \pi / 360)} \)
- **Desarrollo**: \( \text{desarrollo} = (\text{radio} + \text{tubo} \times \text{factork}) \times (90 - \text{ángulo}/2) \times \pi / 180 \)
- **Descuento**: \( \text{descuento} = \text{tangente} - \text{desarrollo} \)
- **Biset**: \( \text{biset} = \frac{\text{radio} + \text{eje} \times \text{tubo} / 2}{\sin(\text{ángulo} \times \pi / 360)} - (\text{radio} + \text{eje} \times \text{tubo} / 2) \)

### 2. ejeWithJSLI
Ajustes basados en posiciones de entrada y salida.
- **Resu1**: \( \text{resu1} = \text{entrada}[0] + \text{salida}[0] \times (\text{salida}[1] - \text{entrada}[1]) \)
- **Resu2**: \( \text{resu2} = \text{entrada}[0] + \text{salida}[0] \times (\text{salida}[1] - \text{entrada}[1]) / 2 \)

### 3. contravuelcoWithJSLI
Cálculos para estructuras en V invertida.
- Utiliza `codoWithJSLI` para descuento.
- **Centro**: \( \text{centro} = \text{marcacentor} + 2 \times \text{descuento}[0] \)
- **Lado**: \( \text{lado} = \sqrt{\text{largo}^2 + \text{altura}^2} \)
- **Lado pendiente**: \( \text{ladopendiente} = \text{lado} / \cos((\text{ángulo} - 90) \times \pi / 180) \)
- **Lado centro**: \( \text{ladocentro} = \text{lado} \times \tan((\text{ángulo} - 90) \times \pi / 180) \)
- **Ancho**: \( \text{ancho} = (\text{ejein} - 1) \times \text{tubo} + \text{centro} + 2 \times \text{lado} \times \tan((\text{ángulo} - 90) \times \pi / 180) \)
- **Ángulo patas**: \( \text{anguloPatas} = 90 + \arcsin(\text{altura} / \text{ladopendiente}) \times 180 / \pi \)
- **Marca pendiente**: \( \text{marcapendiente} = \text{ladopendiente} - \text{descuento}[0] - \text{descuento1}[0] \)

### 4. productopuntoWithJSLI
Producto punto de dos vectores.
- \( \text{suma} = \sum (\text{vector1}[i] \times \text{vector2}[i]) \)

### 5. anguloWithJSLI
Ángulo entre dos vectores.
- **Producto punto**: Ver función 4.
- **Módulo1**: \( \sqrt{\sum \text{vector1}[i]^2} \)
- **Módulo2**: \( \sqrt{\sum \text{vector2}[i]^2} \)
- **Ángulo**: \( \arccos(\text{producto} / (\text{módulo1} \times \text{módulo2})) \times 180 / \pi \)

### 6. angulovectorWithJSLI
Ángulo usando tres vectores.
- Calcula productos punto y ortogonales, luego ángulo entre ortogonales.

### 7. puntaangulorWithJSLI
Dimensiones para puntas angulares.
- **Marcacentro**: \( \text{marcacentro} = (\text{diámetro}[0] + \text{tubo}[0] \times (0 - \text{diámetro}[1]) + \text{factork} \times 2 \times \text{tubo}[0]) \times (180 - \text{ángulo}) \times \pi / 360 \)
- **Alturest**: \( \text{alturest} = \text{alturaCentro}[0] - (\text{diámetro}[0] + \text{tubo}[0] \times (\text{alturaCentro}[1] - \text{diámetro}[1])) \times \sin((180 - \text{ángulo}) \times \pi / (4 \times 180))^2 \)
- **Anchorest**: Compleja fórmula trigonométrica para ancho restante.
- **Desarrollo**: \( \text{desarrollo} = \text{sobra} + (\text{diámetro}[0] + \text{tubo}[0] \times (1 - \text{diámetro}[1])) \times (180 - \text{ángulo}) \times \pi / 360 + 2 \times \text{alturest} / \cos(\text{ángulo} \times \pi / (2 \times 180)) \)
- **Mar carecto**: \( \text{marcarecto} = (\text{desarrollo} - \text{marcacentro}) / 2 \)

### 8. barandaWithJSLI
Dimensiones para barandas.
- **TuboH**: \( \text{tuboH} = \text{tubo}[0] \times \cos((\text{ángulo} - 90) \times \pi / 180) \)
- **TuboAL**: \( \text{tuboAL} = \text{tubo}[0] \times \sin((\text{ángulo} - 90) \times \pi / 180) \)
- **TuboV**: \( \text{tuboV} = \text{tubo}[0] / \tan(\text{ángulo}/2 \times \pi / 180) \)
- **Alineado**: \( \text{alineado} = \text{altura}[0] / \cos((\text{ángulo} - 90) \times \pi / 180) \)
- **Descuento**: Llama a `codoWithJSLI`.
- **MarcaAL**: \( \text{marcaAL} = (\text{alineado} + \text{tuboV} \times (\text{tubo}[1] - \text{altura}[1])/2) - \text{descuento}[0] \)
- **AlturaEJE**: Compleja fórmula para altura del eje.
- **MarcaCT**: \( \text{marcaCT} = (\text{ancho}[0] + \text{tuboH} \times (\text{tubo}[1] - \text{ancho}[1])) - 2 \times \text{alturaEJE} \times \tan((\text{ángulo} - 90) \times \pi / 180) - 2 \times \text{descuento}[0] \)
- **Desarrollo**: \( \text{desarrollo} = 2 \times \text{marcaAL} + \text{marcaCT} \)

### 9. dosaguasWithJSLI
Para techos a dos aguas.
- **Anginferior**: \( \text{anginferior} = 180 - (\text{ángulo}/2) \)
- Llama a `codoWithJSLI` dos veces.
- **Apice**: \( \text{apice} = \text{ancho}[0] / (2 \times \tan(\text{ángulo}/2 \times \pi / 180)) - \text{codo1}[3] \)
- **Lado**: \( \text{lado} = \text{ancho}[0] / (2 \times \sin(\text{ángulo}/2 \times \pi / 180)) \)
- **MarcaLado**: \( \text{marcaLado} = \text{lado} - (\text{codo1}[0] + \text{codo2}[0]) \)

### 10. pasamanoWithJSLI
Para pasamanos.
- **TuboV1/V2**: Similar a baranda.
- Llama a `codoWithJSLI` dos veces.
- **Marcapata1/2**: Cálculos de marcas basados en patas y ángulos.
- **Marcalargo**: Marca longitudinal.
- **Desarrollo**: Suma de marcas.

### 11. parchoqueWithJSLI
Similar a baranda, con fórmulas equivalentes para desarrollo, marcas y descuento.

Estas fórmulas combinan trigonometría (seno, coseno, tangente), geometría euclidiana y ajustes específicos para materiales metálicos. Las unidades son consistentes (radianes para cálculos internos, grados para entradas).

## Cómo Usar

1. Abre el archivo `index.html` en cualquier navegador web moderno.
2. Navega a la sección correspondiente al cálculo que deseas realizar (cada sección tiene un título claro como "Codo", "Baranda", etc.).
3. Ingresa los valores requeridos en los campos de entrada. Todos los valores son numéricos:
   - Longitudes en milímetros (mm).
   - Ángulos en grados.
   - Factores como números decimales (ej. 0.5 para factor K).
4. Haz clic en el botón "Calcular" para procesar los datos.
5. Los resultados se mostrarán inmediatamente debajo del botón, con etiquetas descriptivas.
6. Si necesitas recalcular, cambia los valores y haz clic nuevamente.
7. Las imágenes CAD en cada sección ayudan a visualizar el elemento que se está calculando.

### Notas Importantes para el Uso
- Asegúrate de que los valores estén en las unidades correctas (mm para longitudes, grados para ángulos).
- Algunos cálculos requieren arreglos de valores; en la interfaz, se manejan como campos separados.
- Si un resultado parece incorrecto, verifica que los parámetros correspondan al tipo de material y diseño.
- La aplicación no guarda datos; cada cálculo es independiente.

## Ejemplos de Uso

A continuación, se muestran ejemplos prácticos para algunas funciones. Estos valores son ilustrativos y deben adaptarse a tus necesidades reales.

### Ejemplo 1: Codo (codoWithJSLI)
- **Escenario**: Fabricar un codo de 90° en un tubo de 2 mm de grosor, con radio de rodillo de 50 mm.
- **Entradas**:
  - Ángulo: 90
  - Tubo: 2
  - Radio: 50
  - Factor K: 0.5
  - Eje: 1
- **Resultados esperados** (aproximados):
  - Descuento: ~78.5 mm
  - Desarrollo: ~157 mm
  - Tangente: ~25 mm
  - Biset: ~50 mm
- **Interpretación**: Corta 78.5 mm menos del tubo recto, dobla para obtener el ángulo, usando las tangentes para guiar.

### Ejemplo 2: Baranda (barandaWithJSLI)
- **Escenario**: Diseñar una baranda recta de 1000 mm de ancho y 900 mm de altura, con tubo de 2 mm.
- **Entradas**:
  - Ángulo: 0 (recta)
  - Tubo: [2, 1]
  - Rodillo: [25, 0]
  - Ancho: [1000, 0]
  - Altura: [900, 0]
  - Factor K: 0.5
- **Resultados esperados** (aproximados):
  - Desarrollo: ~2000 mm
  - Marca AL: ~450 mm
  - Marca CT: ~1000 mm
  - Descuento: ~50 mm
  - Altura EJE: ~900 mm
- **Interpretación**: La baranda requiere ~2000 mm de tubo desarrollado, con marcas para cortes y ensamblaje.

### Ejemplo 3: Dos Aguas (dosaguasWithJSLI)
- **Escenario**: Techo a dos aguas con ángulo de 30°, ancho de 6000 mm, tubo de 2 mm.
- **Entradas**:
  - Ángulo: 30
  - Tubo: [2, 1]
  - Rodillo: [25, 0]
  - Ancho: [6000, 0]
  - Factor K: 0.5
- **Resultados esperados** (aproximados):
  - Apice: ~1500 mm
  - Marca lado: ~2500 mm
  - Ángulo inferior: 150°
  - Lado: ~3464 mm
- **Interpretación**: El ápice está a 1500 mm, con lados de ~3464 mm cada uno para formar el techo.

Estos ejemplos muestran cómo los cálculos ayudan a planificar cortes y ensamblajes precisos en construcción metálica. Ajusta los valores según el material y las especificaciones del proyecto.

## Requisitos del Sistema

- Navegador web con soporte para JavaScript (Chrome, Firefox, Edge, Safari, etc.).
- No requiere conexión a internet ni servidor; funciona completamente offline.
- Compatible con dispositivos móviles y de escritorio.

## Estructura de Archivos

- `index.html`: Página principal con todas las calculadoras.
- `../javascrit/codo.js`: Archivo JavaScript con las funciones de cálculo.
- `../atribucion/`: Carpeta con imágenes CAD ilustrativas para cada tipo de cálculo.

## Origen y Créditos

Este proyecto está basado en el archivo `codo.js`, originalmente creado para ejemplos de WebVI en National Instruments LabVIEW. Las funciones implementan fórmulas estándar de geometría y metalurgia aplicadas a la construcción.

Las imágenes CAD son proporcionadas en la carpeta `atribucion/` y corresponden a diagramas técnicos de los cálculos.

## Notas Técnicas

- Todas las funciones devuelven arreglos `Float64Array` para precisión.
- Los ángulos se ingresan en grados y se convierten a radianes internamente.
- Algunos parámetros son arreglos [valor, factor] para representar propiedades compuestas.
- Las unidades típicas son milímetros para longitudes y grados para ángulos.

## Soporte

Si encuentras errores o necesitas ayuda, revisa los parámetros de entrada o consulta la documentación original de WebVI.