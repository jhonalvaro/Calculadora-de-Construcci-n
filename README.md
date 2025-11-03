# 📐 Análisis Técnico de las Imágenes y Enriquecimiento de Definiciones de Cálculos

## 1. Cálculo de Codos (codoWithJSLI)

![Proceso de curvado de tubo](https://i.imgur.com/8KXzZqL.png)
*Figura 1: Proceso de curvado de tubo con rodillos*

**Análisis técnico de la imagen**:
- El diagrama muestra el proceso de formación de un codo mediante rodillos
- El "diametro" se refiere al diámetro exterior del tubo
- El "rodillo" es el diámetro del rodillo de curvado (¡no el radio!)
- El "ancho" representa la distancia entre los centros de los rodillos

**Cálculos técnicos enriquecidos**:
- **Descuento**: Material que debe restarse para obtener el corte preciso. Es la diferencia entre la tangente y el desarrollo. 
  - Fórmula: `tangente - desarrollo`
  - Importancia: Determina cuánto tubo debe cortarse para que el codo quede con las dimensiones correctas

- **Desarrollo**: Longitud de tubo necesaria para formar la curva deseada
  - Fórmula: `(radio + (tubo*factork)) * (90-angulo/2) * π/180`
  - Importancia: Permite calcular la longitud de material a utilizar antes del curvado

- **Tangente**: Distancia de proyección desde el inicio hasta el final del codo
  - Fórmula: `(radio + eje*tubo/2) / tan(ángulo * π / 360)`
  - Importancia: Determina la proyección del codo para su integración en estructuras

- **Biset**: Ángulo de corte necesario para la unión del codo
  - Fórmula: `((radio + eje*tubo/2) / sin(ángulo * π / 360)) - (radio + eje*tubo/2)`
  - Importancia: Define el ángulo de bisel para soldaduras perfectas

**Parámetros críticos**:
- `ángulo`: Ángulo del codo (0-180°)
- `tubo`: Diámetro exterior del tubo (mm)
- `rodillo`: Diámetro del rodillo de curvado (mm) - ¡no el radio!
- `factork`: Factor K (0.35-0.45 para acero suave)
- `eje`: Posición del eje (1=exterior, 0.5=centro, 0=interior)

## 2. Contravuelco (contravuelcoWithJSLI)

![Contravuelco](https://i.imgur.com/7YQwVgF.png)
*Figura 2: Estructura de contravuelco con dimensiones clave*

**Análisis técnico de la imagen**:
- Muestra una estructura en V invertida (contravuelco)
- "marca centro" indica el punto central del desarrollo
- "marca pendiente" muestra la posición de corte para la parte inclinada
- "ancho" representa la distancia total entre extremos
- "altura" es la distancia vertical desde base a punto más alto

**Cálculos técnicos enriquecidos**:
- **Ancho total**: Ancho final de la estructura
  - Fórmula: `(ejein-1)*tubo + centro + 2*lado*Math.tan((angulo-90) * π / 180)`
  - Importancia: Determina el ancho total de la estructura para su integración

- **Ángulo de patas**: Ángulo de las patas respecto a la vertical
  - Fórmula: `90 + Math.asin(altura/ladopendiente)*180/π`
  - Importancia: Define la inclinación de las patas para el diseño estructural

- **Lado pendiente**: Longitud de la parte inclinada
  - Fórmula: `lado / Math.cos((angulo-90) * π / 180)`
  - Importancia: Determina la longitud real del tubo para la parte inclinada

- **Lado centro**: Distancia desde el centro al punto de curvatura
  - Fórmula: `lado * Math.tan((angulo-90) * π / 180)`
  - Importancia: Ayuda a localizar el punto de curvatura central

**Parámetros críticos**:
- `ángulo`: Ángulo principal de la estructura
- `marca centro`: Punto de referencia central
- `rodillo`: Diámetro del rodillo de curvado
- `largo`: Longitud horizontal del segmento
- `altura`: Altura vertical total
- `tubo`: Diámetro del tubo
- `ejein`: Posición del eje de curvatura

## 3. Punta Angular Rolada (puntaangulorWithJSLI)

![Punta angular](https://i.imgur.com/9HkRfNl.png)
*Figura 3: Punta angular rolada con marcas de corte*

**Análisis técnico de la imagen**:
- Muestra una punta angular con forma de techo
- "apice" indica la altura máxima desde la base
- "rodillo" muestra el diámetro del rodillo de curvado
- "ancho" representa la distancia horizontal total

**Cálculos técnicos enriquecidos**:
- **Marca centro**: Posición central del desarrollo
  - Fórmula: `(diametro[0]+tubo[0]*(0-diametro[1])+factork*2*tubo[0])*(180-angulo)*π/360`
  - Importancia: Define el punto central para el corte y alineación

- **Altura restante**: Altura efectiva después de curvado
  - Fórmula: `alturaCentro[0] - (diametro[0]+tubo[0]*(alturaCentro[1]-diametro[1]))*Math.pow(Math.sin((180-angulo)*π/(4*180)),2)`
  - Importancia: Determina la altura real de la estructura terminada

- **Ancho restante**: Ancho final de la estructura
  - Fórmula: `2*alturest*(Math.tan((angulo)*π/(2*180))) + 2*(diametro[0]+tubo[0]*(tubo[1]-diametro[1]))*Math.sin((180-angulo)*π/(4*180))*Math.cos((180-angulo)*π/(4*180))`
  - Importancia: Calcula el ancho final para la fabricación precisa

- **Desarrollo**: Longitud total de tubo necesaria
  - Fórmula: `sobra + (diametro[0]+tubo[0]*(1-diametro[1]))*(180-angulo)*π/360 + 2*alturest/Math.cos((angulo)*π/(2*180))`
  - Importancia: Determina la cantidad exacta de material requerido

**Parámetros críticos**:
- `diametro`: [diámetro, factor]
- `tubo`: [diámetro, factor]
- `angulo`: Ángulo principal
- `alturaCentro`: [altura, factor]
- `factork`: Factor K de compensación
- `sobra`: Material adicional para ajustes

## 4. Baranda (barandaWithJSLI)

![Baranda](https://i.imgur.com/6mDdGxS.png)
*Figura 4: Baranda con dimensiones calculadas*

**Análisis técnico de la imagen**:
- Muestra una baranda con curvas y segmentos rectos
- "flecha" representa la desviación máxima desde la cuerda
- "cuerda" es la distancia recta entre extremos
- "dia_rodillo" indica el diámetro del rodillo de curvado

**Cálculos técnicos enriquecidos**:
- **TuboH**: Componente horizontal del tubo
  - Fórmula: `tubo[0]*Math.cos((angulo-90)*π/180)`
  - Importancia: Determina la proyección horizontal para el alineamiento

- **TuboAL**: Componente vertical del tubo
  - Fórmula: `tubo[0]*Math.sin((angulo-90)*π/180)`
  - Importancia: Determina la proyección vertical para el alineamiento

- **TuboV**: Distancia vertical del tubo
  - Fórmula: `tubo[0]/Math.tan((angulo/2)*π/180)`
  - Importancia: Calcula la distancia vertical para el diseño estructural

- **Alineado**: Distancia de alineación
  - Fórmula: `altura[0]/Math.cos((angulo-90)*π/180)`
  - Importancia: Determina la longitud necesaria para el alineamiento correcto

- **MarcaAL**: Marca de alineación lateral
  - Fórmula: `(alineado+tuboV*(tubo[1]-altura[1])/2)-descuento[0]`
  - Importancia: Define el punto de corte para la alineación lateral

- **AlturaEJE**: Altura del eje de curvatura
  - Fórmula: `altura[0]-tuboAL*(tubo[1]-altura[1])/2+tubo[0]*(tubo[1]-altura[1])/2`
  - Importancia: Determina la altura del eje para el cálculo preciso

- **MarcaCT**: Marca de centro total
  - Fórmula: `(ancho[0]+tuboH*(tubo[1]-ancho[1]))-2*alturaEJE*Math.tan((angulo-90)*π/180)-2*descuento[0]`
  - Importancia: Define el punto de corte central para la estructura

- **Desarrollo**: Longitud total de tubo necesaria
  - Fórmula: `2*marcaAL + marcaCT`
  - Importancia: Determina la cantidad exacta de material requerido

**Parámetros críticos**:
- `ángulo`: Ángulo de curvatura
- `tubo`: [diámetro, factor]
- `rodillo`: [diámetro, factor]
- `ancho`: [ancho total, factor]
- `altura`: [altura total, factor]
- `factork`: Factor K de compensación

## 5. Techo a Dos Aguas (dosaguasWithJSLI)

![Techo a dos aguas](https://i.imgur.com/5nBhTqW.png)
*Figura 5: Techo a dos aguas con dimensiones clave*

**Análisis técnico de la imagen**:
- Muestra una estructura de techo con forma de A
- "apice" indica la altura máxima del techo
- "rodillo" representa el diámetro del rodillo de curvado
- "ancho" es la distancia horizontal total del techo

**Cálculos técnicos enriquecidos**:
- **Ángulo inferior**: Ángulo en la base de la estructura
  - Fórmula: `180-(angulo/2)`
  - Importancia: Define el ángulo de las patas inferiores para la estabilidad

- **Apice**: Altura máxima del techo
  - Fórmula: `ancho[0]/(2*Math.tan((angulo/2)*π/180))-codo1[3]`
  - Importancia: Determina la altura del punto más alto para el diseño

- **Lado**: Longitud de cada lado del techo
  - Fórmula: `ancho[0]/(2*Math.sin((angulo/2)*π/180))`
  - Importancia: Calcula la longitud de tubo necesaria para cada lado

- **MarcaLado**: Marca de corte para el lado
  - Fórmula: `lado-(codo1[0]+codo2[0])`
  - Importancia: Define el punto de corte para la fabricación precisa

**Parámetros críticos**:
- `ángulo`: Ángulo principal del techo
- `tubo`: [diámetro, factor]
- `rodillo`: [diámetro, factor]
- `ancho`: [ancho total, factor]
- `factork`: Factor K de compensación

## 6. Pasamano (pasamanoWithJSLI)

![Pasamano](https://i.imgur.com/4rMzVpO.png)
*Figura 6: Pasamano con dimensiones calculadas*

**Análisis técnico de la imagen**:
- Muestra un pasamano con dos patas inclinadas
- "pata 1" y "pata 2" representan los segmentos verticales
- "angulo 1" y "angulo 2" indican los ángulos de inclinación
- "largo" es la distancia horizontal entre patas
- "rodillo" representa el diámetro del rodillo de curvado

**Cálculos técnicos enriquecidos**:
- **TuboV1/V2**: Distancia vertical de las patas
  - Fórmula: `tubo[0]/Math.tan((angulo1/2)*π/180)`
  - Importancia: Determina la altura vertical para cada pata

- **Codo1/2**: Cálculos de codos para cada curva
  - Fórmula: `window.codoWithJSLI(angulo1, tubo[0], (rodillo[0]+tubo[0]*(0-rodillo[1])), factork, tubo[1])`
  - Importancia: Calcula los parámetros de curvado para cada esquina

- **MarcaPata1/2**: Marcas de corte para las patas
  - Fórmula: `(pata1[0]+tuboV1*(tubo[1]-pata1[1])/2)-codo1[0]`
  - Importancia: Define los puntos de corte para la alineación correcta

- **MarcaLargo**: Marca de longitud para el segmento horizontal
  - Fórmula: `(largo[0]+tuboV1*(tubo[1]-largo[1])/2+tuboV2*(tubo[1]-largo[1])/2)-codo1[0]-codo2[0]`
  - Importancia: Determina la longitud del segmento horizontal entre patas

- **Desarrollo**: Longitud total de tubo necesaria
  - Fórmula: `marcalargo + marcapata1+marcapata2`
  - Importancia: Calcula la cantidad total de material requerido

**Parámetros críticos**:
- `rodillo`: [diámetro, factor]
- `tubo`: [diámetro, factor]
- `largo`: [largo total, factor]
- `pata1/2`: [longitud pata, factor]
- `angulo1/2`: Ángulos de las patas
- `factork`: Factor K de compensación

## 7. Parachoques (parchoqueWithJSLI)

![Parachoques](https://i.imgur.com/4rMzVpO.png)
*Figura 7: Parachoques con dimensiones calculadas*

**Análisis técnico de la imagen**:
- Similar a las barandas pero con aplicaciones en protección
- Muestra una estructura curva con segmentos rectos
- "marca centro" y "marca pendiente" indican puntos de corte

**Cálculos técnicos enriquecidos**:
- **TuboH**: Componente horizontal del tubo
  - Fórmula: `tubo[0]*Math.cos((angulo-90)*π/180)`
  - Importancia: Determina la proyección horizontal para el alineamiento

- **TuboV**: Distancia vertical del tubo
  - Fórmula: `tubo[0]/Math.tan((angulo/2)*π/180)`
  - Importancia: Calcula la distancia vertical para el diseño estructural

- **Alineado**: Distancia de alineación
  - Fórmula: `altura[0]/Math.cos((angulo-90)*π/180)`
  - Importancia: Determina la longitud necesaria para el alineamiento correcto

- **Descuento**: Material a restar para el corte preciso
  - Fórmula: Llamada a `codoWithJSLI`
  - Importancia: Determina cuánto material debe restarse para obtener la curva deseada

- **MarcaAL**: Marca de alineación lateral
  - Fórmula: `(alineado+tuboV*(tubo[1]-altura[1])/2)-descuento[0]`
  - Importancia: Define el punto de corte para la alineación lateral

- **MarcaCT**: Marca de centro total
  - Fórmula: `(ancho[0]+tuboH*(tubo[1]-ancho[1]))-2*altura[0]*Math.tan((angulo-90)*π/180)-2*descuento[0]`
  - Importancia: Define el punto de corte central para la estructura

- **Desarrollo**: Longitud total de tubo necesaria
  - Fórmula: `2*marcaAL + marcaCT`
  - Importancia: Determina la cantidad exacta de material requerido

**Parámetros críticos**:
- `ángulo`: Ángulo de curvatura
- `tubo`: [diámetro, factor]
- `rodillo`: [diámetro, factor]
- `ancho`: [ancho total, factor]
- `altura`: [altura total, factor]
- `factork`: Factor K de compensación

## 🔍 Conclusión Técnica

Estas funciones implementan algoritmos especializados para la fabricación de estructuras metálicas, con enfoque en:
- **Precisión dimensional**: Cálculos trigonométricos para dimensiones exactas
- **Compensación de material**: Uso del factor K para compensar deformaciones
- **Posicionamiento del eje**: Parámetros que determinan si el cálculo se basa en el eje exterior, interior o central
- **Estructuras complejas**: Capacidad para manejar geometrías complejas como contravuelcos y techos a dos aguas

> **Nota técnica crítica**: El parámetro "rodillo" siempre representa el **DIÁMETRO del rodillo**, no el radio. Esto es fundamental para obtener resultados correctos, ya que el código internamente divide este valor entre 2 para obtener el radio real. Un error común es usar el radio del rodillo en lugar de su diámetro, lo que produciría errores significativos en los cálculos.

Estos cálculos son esenciales para la fabricación precisa de estructuras metálicas, permitiendo a los fabricantes determinar exactamente:
- Cuánto material cortar
- Dónde hacer los cortes
- Cómo alinear las piezas para ensamblaje
- La cantidad total de material requerido

*Esta aplicación es una herramienta de apoyo técnico. Los resultados deben ser verificados por un ingeniero estructural antes de su uso en proyectos reales. No sustituye el criterio profesional ni los códigos de construcción locales.*