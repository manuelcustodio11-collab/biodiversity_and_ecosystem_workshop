# Taller práctico de Google Earth – Parte 2: Análisis de paisaje

**RedLAC Workshop 2026 · Ecosystem & Biodiversity Monitoring at Scale**
Facilitadoras: Tanya Birch y Paula Paz · Noviembre 2026

Este repositorio reúne las guías de los ejercicios prácticos del taller, en el que usamos las nuevas herramientas de **Detección de cambios** y **Clasificación** de Google Earth, basadas en los *embeddings* satelitales de **AlphaEarth Foundations (AEF)**.

## Contenido

1. [Requisitos y datos](#requisitos-y-datos)
2. [Ejercicio 1 – Detección de cambios](#ejercicio-1--detección-de-cambios)
3. [¿Qué es AlphaEarth Foundations?](#qué-es-alphaearth-foundations)
4. [Ejercicio 2 – Clasificación de coberturas](#ejercicio-2--clasificación-de-coberturas)
5. [Comentarios](#comentarios)

---

## Requisitos y datos

- Navegador web actualizado y cuenta de Google.
- Acceso a [Google Earth en la web](https://earth.google.com/web).
- Áreas de estudio en formato `.shp` / `.kml`: 👉 [Carpeta de datos en Google Drive](https://drive.google.com/drive/folders/1lnqEQvlJ2ETWOVK590MaZWmuWKMZDm5V?usp=sharing)

| Ejercicio | Área de estudio |
|-----------|-----------------|
| 1 – Detección de cambios | Pucallpa, Perú |
| 2 – Clasificación | Reserva Nacional Tambopata, Madre de Dios, Perú |

> **Nota:** el área de interés no debe superar ~20 200 ha (50 000 acres).

---

## Ejercicio 1 – Detección de cambios

**Área de estudio:** Pucallpa, Perú
**Temas:** deforestación, expansión urbana y cambios en cuerpos de agua

### Objetivos

1. Usar la herramienta **Detect Change** para identificar cambios desde 2017 en Pucallpa.
2. Explorar las nuevas funciones: barra de umbral y exportación a vectores.
3. Cargar un área de estudio en formato `.shp` / `.kml`.
4. Calcular el área de cambio (m²) relacionada con deforestación.

### Calentamiento (5 minutos)

Antes de usar la herramienta, intenta detectar cambios con **Imágenes históricas** de Google Earth. Elige una región (o usa Pucallpa) y responde: ¿qué cambió y cuándo?, ¿cómo lo identificaste? y ¿qué dificultades encontraste?

### Paso a paso

1. Abre **Detect Change** desde el menú principal de Google Earth.
2. Dibuja un área de interés o carga el polígono (máximo ~20 200 ha).
3. Selecciona los años a comparar (datos disponibles desde 2017).
4. Ajusta el **umbral de cambio** con el control deslizante (0 = sin cambio, 1 = cambio). Observa los resultados en tiempo real.
5. Crea la capa de salida:
   - **Ráster**, o
   - **Vector + tabla** con el área de cada polígono de cambio.

📂 [Ver proyecto de ejemplo en Google Earth](https://earth.google.com/earth/d/1dJgTcN98J-_5Wh4CYGa9VKcJIntDNR0s?usp=sharing)

### ¿Cómo funciona?

La herramienta calcula el **producto punto** entre las 64 bandas de los *embeddings* de cada año y normaliza el resultado. Así obtiene un puntaje de 0 (estable) a 1 (cambio).

📖 [Documentación oficial de Detect Change](https://developers.google.com/maps/documentation/earth/detect-change?hl=es-419)

### Aspectos a tener en cuenta

- Los *embeddings* combinan datos de distintos sensores, por lo que pueden detectar cambios que no se ven a simple vista: humedad del suelo, rotación de cultivos o degradación bajo el dosel.
- Un puntaje cercano a 1 no siempre corresponde a un cambio más *visible*.
- Cada *embedding* resume un año calendario completo; no equivale a una imagen de un día específico.
- Diferencias en fechas de cosecha entre años pueden marcarse como cambio aunque el uso siga siendo agrícola.

### Preguntas de reflexión

- ¿Qué cambios encontraste?
- ¿Tuviste alguna dificultad?
- ¿Probaste la herramienta en otra zona de estudio?

---

## ¿Qué es AlphaEarth Foundations?

AlphaEarth Foundations es un modelo que integra datos de muchas fuentes de observación de la Tierra en una sola representación por píxel: óptico (Sentinel-2, Landsat), térmico (Landsat), radar (Sentinel-1, ALOS PALSAR), LiDAR (GEDI), gravedad (GRACE), clima (ERA5-Land), elevación (Copernicus DEM), además de alineación con texto y datos semánticos.

El resultado es el **Satellite Embedding Dataset**: una capa anual, a 10 m de resolución, con 64 bandas por píxel. Estos *embeddings* permiten hacer búsqueda por similitud, clasificación y detección de cambios.

---

## Ejercicio 2 – Clasificación de coberturas

**Área de estudio:** Reserva Nacional Tambopata, Madre de Dios, Perú
**Tema:** minería y deforestación en un área natural protegida (ANP)

Realizaremos una clasificación de coberturas del suelo a partir de los *embeddings* satelitales de AlphaEarth Foundations (AEF), utilizando el clasificador supervisado Random Forest.

### Objetivos

1. Cargar el área de estudio en formato `.shp` / `.kml`.
2. Usar la herramienta **Classify** para clasificar los tipos de cobertura del área protegida.
3. Usar **Detect Change** para revisar si hubo cambios desde 2017.

### ¿Cómo funciona?

```
Puntos de entrenamiento por clase
            │
            ▼
Satellite Embedding Dataset (anual, 10 m, 64 bandas)
            │
            ▼
Random Forest (clasificador de Earth Engine)
            │
            ▼
        Mapa de coberturas
```

### Parte A – Clasificación

1. Abre la herramienta **Classify** desde el menú principal de Google Earth.
2. Define el área de interés: dibuja un polígono o carga el área de estudio (`.kml` / `.shp`).
3. Selecciona el año de clasificación.
4. Define las clases con el botón **+ Add custom class** (por ejemplo: bosque denso, minería, deforestación, agua).
5. Marca puntos de muestreo para cada clase.

   > **Tip:** Selecciona puntos balanceados por clase, distribuidos en toda el área y representativos de su variabilidad.

6. Genera el mapa (se necesitan **al menos 2 clases**).
7. Revisa el resultado e itera:
   - ¿No te convence? → agrega más puntos.
   - ¿Necesitas más clases? → crea una nueva y repite.
8. Compara tus resultados con los registros de minería del **SERNANP**.

### Parte B – Clasificación + Detección de cambios

1. Dentro del ANP, dibuja un polígono como área de estudio.
2. Abre **Detect Change** y selecciona los años de interés (desde 2017).
3. Modifica el umbral para detectar cambios asociados a minería y deforestación.
4. Exporta los resultados en ráster y vector.
5. Estima el área aproximada afectada en Tambopata.

📂 [Ver proyecto de ejemplo en Google Earth](https://earth.google.com/earth/d/18_ZX3kYWOcoB7FRS6zJ0g_RkDgYtIqV-?usp=sharing)

### Consejos para un buen mapa

- **El mapa es tan bueno como los puntos que proporcionas.**
- La clasificación es **iterativa**: revisa, corrige y vuelve a generar.
- Los resultados se basan en *embeddings* **anuales a 10 m**, así que los objetos muy pequeños pueden no distinguirse.

### Preguntas de reflexión

- ¿Qué tipo de clasificación realizaste (qué clases definiste)?
- ¿Qué cambios encontraste en la zona?
- ¿Cuál es el mejor umbral para identificar minería y deforestación?
- ¿Por qué la herramienta no detecta cambios en áreas que ya estaban identificadas como minería?
- ¿Tuviste alguna dificultad?

---

## Comentarios

¿Tienes sugerencias? En Google Earth web, ve a **Ayuda > Enviar comentarios** y escribe tu mensaje incluyendo **#RedLAC26**.
