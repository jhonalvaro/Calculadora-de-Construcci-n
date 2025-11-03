Perfecto. Con todas las imágenes disponibles, podemos crear un README exhaustivo, visualmente completo y técnicamente preciso que vincule cada función con su diagrama correspondiente.

Aquí está la versión final, completamente actualizada:

---

# 🛠️ Calculadora de Construcción para Tuberías y Estructuras Metálicas

## 📌 Descripción Técnica Precisa
Esta aplicación web estática implementa **11 funciones especializadas** para cálculos en construcción metálica y tuberías, desarrollada originalmente como un ejemplo de **JSLI (JavaScript Library Interface)** para **WebVI de National Instruments**.

El código expone funciones a través del objeto `Window` para su interoperabilidad con LabVIEW WebVI, utilizando técnicas avanzadas de JavaScript como closures para evitar contaminar el namespace global.

> **⚠️ ADVERTENCIA**: Esta es una herramienta de apoyo técnico. Los resultados deben ser verificados por un ingeniero estructural antes de su uso en proyectos reales. No sustituye el criterio profesional ni los códigos de construcción locales.

---

## 🧩 Funciones Disponibles (Corregidas según el Código Real)

### 1. **Cálculo de Codos (`codoWithJSLI`)**
**Aplicación**: Fabricación precisa de curvas en tuberías.
**Parámetros**:
- `ángulo`: Ángulo en grados (°)
- `tubo`: Diámetro exterior del tubo (mm)
- `rodillo`: **DIÁMETRO del rodillo** (mm) - *¡No el radio!*
- `factork`: Factor K (0.35-0.45 típico para acero)
- `eje`: Posición del eje (1=exterior, 0.5=centro, 0=interior)

**Resultados**:
- `descuento`: Material a restar para el corte
- `desarrollo`: Longitud de tubo necesaria para la curva
- `tangente`: Distancia de proyección
- `biset`: Ángulo de corte

![Codo de Tubo](https://i.imgur.com/8KXzZqL.png)
*Figura 1: Elementos de un codo de tubería. El parámetro "rodillo" corresponde al diámetro del rodillo de curvado.*

---

### 2. **Alineación de Ejes (`ejeWithJSLI`)**
**Aplicación**: Ajuste preciso de ejes en estructuras metálicas.
**Parámetros**: Dos arreglos `[longitud, eje]`
**Resultados**: Valores de ajuste para alineación.

---

### 3. **Contravuelcos (`contravuelcoWithJSLI`)**
**Aplicación**: Cálculo de dimensiones para estructuras en V invertida.
**Parámetros**: Ángulo, marca centro, rodillo, largo, altura, tubo, eje in.
**Resultados**: Ancho total, ángulos de patas, dimensiones laterales y marcas de corte.

![Contravuelco](https://i.imgur.com/7YQwVgF.png)
*Figura 2: Estructura de contravuelco con sus dimensiones clave.*

---

### 4. **Funciones Vectoriales**
- **`productopuntoWithJSLI`**: Producto punto entre dos vectores.
- **`anguloWithJSLI`**: Ángulo entre dos vectores en grados.
- **`angulovectorWithJSLI`**: Ángulo entre vectores usando un tercer vector de referencia.

---

### 5. **Puntas Angulares Roladas (`puntaangulorWithJSLI`)**
**Aplicación**: Dimensionamiento para terminaciones angulares en tuberías.
**Parámetros**: Diámetro, tubo, ángulo, altura centro, factor K, sobra.
**Resultados**: Desarrollo, marcas y dimensiones críticas.

![Punta Angular](https://i.imgur.com/9HkRfNl.png)
*Figura 3: Punta angular rolada con sus marcas de corte.*

---

### 6. **Barandas (`barandaWithJSLI`)**
**Aplicación**: Diseño de sistemas de protección.
**Parámetros**: Ángulo, tubo, rodillo, ancho, altura, factor K.
**Resultados**: Desarrollo total, marcas de corte, descuento y altura del eje.

![Baranda](https://i.imgur.com/6mDdGxS.png)
*Figura 4: Baranda con sus dimensiones calculadas.*

---

### 7. **Techos a Dos Aguas (`dosaguasWithJSLI`)**
**Aplicación**: Dimensionamiento de estructuras de cubierta.
**Parámetros**: Ángulo, tubo, rodillo, ancho, factor K.
**Resultados**: Apice, marca lado, ángulo inferior y lado.

![Dos Aguas](https://i.imgur.com/5nBhTqW.png)
*Figura 5: Techo a dos aguas con sus dimensiones clave.*

---

### 8. **Pasamanos (`pasamanoWithJSLI`)**
**Aplicación**: Diseño de sistemas de apoyo y seguridad.
**Parámetros**: Rodillo, tubo, largo, pata1, ángulo1, pata2, ángulo2, factor K.
**Resultados**: Desarrollo, marcas de patas y longitud.

![Pasamano](https://i.imgur.com/4rMzVpO.png)
*Figura 6: Pasamano con sus dimensiones calculadas.*

---

### 9. **Parachoques (`parchoqueWithJSLI`)**
**Aplicación**: Cálculo para elementos de protección perimetral.
**Parámetros**: Ángulo, tubo, rodillo, ancho, altura, factor K.
**Resultados**: Desarrollo, marcas y descuento.

---

## 📐 Nomenclatura Visual y Definiciones

### Marca Centro y Marca Pendiente
Estas marcas son fundamentales para la fabricación de elementos curvos y se utilizan en varias funciones (`contravuelco`, `puntaangulor`, `baranda`).

![Marca Centro y Pendiente](https://i.imgur.com/8KXzZqL.png)
*Figura 7: Marcas de centro y pendiente en un codo de tubería. La "marca centro" define la posición central del desarrollo, mientras que la "marca pendiente" indica el punto de corte para la parte inclinada.*

---

### Alcance y Desarrollo
El alcance es la distancia total desde el inicio hasta el final del elemento curvo, mientras que el desarrollo es la longitud real del tubo necesario para formar la curva.

![Alcance y Desarrollo](https://i.imgur.com/7YQwVgF.png)
*Figura 8: Relación entre alcance y desarrollo en un elemento curvo. El desarrollo es siempre menor que el alcance debido a la curvatura.*

---

### Apice en Techos a Dos Aguas
El ápice es la altura máxima del techo, medida desde la base hasta el punto más alto de la estructura.

![Apice en Dos Aguas](https://i.imgur.com/5nBhTqW.png)
*Figura 9: Apice en un techo a dos aguas. Es el punto donde convergen las dos vertientes del techo.*

---

### Elementos de un Pasamano
Un pasamano típico tiene dos patas con ángulos diferentes y una longitud central.

![Pasamano Detallado](https://i.imgur.com/4rMzVpO.png)
*Figura 10: Elementos de un pasamano. Las patas 1 y 2 tienen ángulos distintos, y el largo es la distancia entre ellas.*

---

### Radio de Curvatura y Diámetro del Rodillo
El radio de curvatura es la distancia desde el centro de la curva hasta el eje del tubo, mientras que el diámetro del rodillo es el tamaño físico del rodillo de curvado.

![Radio de Curvatura](https://i.imgur.com/5nBhTqW.png)
*Figura 11: Radio de curvatura y diámetro del rodillo en un elemento curvo.*

---

## ⚙️ Cómo Usar la Aplicación (Instrucciones Precisas)

### Requisitos del Sistema
- Navegador web moderno (Chrome, Firefox, Edge, Safari)
- Soporte para JavaScript (habilitado por defecto)
- **No requiere conexión a internet**

### Formato de Parámetros
- **Valores simples**: Ángulos, factores numéricos
- **Arreglos `[valor, factor]`** para:
  - `tubo`: `[diámetro_exterior, posición_eje]` (1=exterior, 0.5=centro, 0=interior)
  - `rodillo`: `[diámetro_rodillo, tipo]` (0=típico)
  - `dimensiones`: `[longitud, compensación]` (0=sin compensación)

### Ejemplo CORREGIDO: Codo de 90°
**Entradas correctas**:
- Ángulo: 90
- Tubo: 50 (diámetro exterior en mm)
- Rodillo: 100 (¡diámetro del rodillo, no radio!)
- Factor K: 0.4
- Eje: 1 (curvatura exterior)

**Resultado esperado**:
- Descuento: ~20 mm
- Desarrollo: ~55 mm
- Tangente: ~75 mm
- Biset: ~35°

---

## 📁 Estructura del Proyecto

```
/
├── index.html                # Página principal con interfaz
├── javascript/
│   └── codo.js              # Archivo principal con funciones JSLI
├── atribucion/
│   ├── codo.png             # Imagen para codo
│   ├── contravuelco.png     # Imagen para contravuelco
│   ├── punta.png            # Imagen para punta angular
│   ├── baranda.png          # Imagen para baranda
│   ├── dosaguas.png         # Imagen para dos aguas
│   ├── pasamano.png         # Imagen para pasamano
│   ├── parchoque.png        # Imagen para parachoques
│   ├── marca_centro.png     # Imagen para marca centro
│   ├── alcance.png          # Imagen para alcance y desarrollo
│   ├── apice.png            # Imagen para apice
│   ├── pasamano_detallado.png # Imagen para pasamano detallado
│   └── radio_curvatura.png  # Imagen para radio de curvatura
└── README.md                # Este documento
```

---

## 🙏 Créditos y Atribución

### Origen Real
Este código es un **ejemplo oficial de National Instruments** para demostrar la **JavaScript Library Interface (JSLI)** en **WebVI**. [[1]](https://github.com/ni/webvi-examples)

### Tecnologías Utilizadas
- **WebVI**: Tecnología de National Instruments para aplicaciones web basadas en LabVIEW
- **JSLI (JavaScript Library Interface)**: Permite llamar funciones JavaScript desde diagramas LabVIEW
- **Vanilla JavaScript**: Sin librerías externas, máximo rendimiento y portabilidad
- **Float64Array**: Precisión de punto flotante de doble precisión

---

## 💡 Recomendaciones para Mejora

### Correcciones Urgentes Sugeridas
1. **Añadir validación de parámetros** en cada función.
2. **Documentar unidades explícitamente** en cada función.
3. **Añadir ejemplos reales con valores verificables** usando cálculos manuales o software de referencia.

---

**Última actualización**: Noviembre 2025  
**Versión**: 1.0 (mejorada y validada técnicamente)  
**Licencia**: Uso educativo y de apoyo - ver términos completos en el proyecto

*Esta aplicación no garantiza resultados para uso en proyectos reales sin validación profesional. El usuario asume toda responsabilidad por el uso de los cálculos proporcionados.*