---
layout: page
title: "00-intro-to-GoogleEarth"
permalink: /1-intro-to-GoogleEarth
has_children: true
nav_order: 2
---

# Introducción a Google Earth en la web

## Objetivo 
## Objetivo
Navegar en la interfaz de Google Earth en la web (GE) y aprender a almacenar, importar y organizar datos propios (KML, SHP, CSV), explorar imágenes históricas y conjuntos de datos del Catálogo de datos, y usar las herramientas de creación, medición y colaboración para analizar cambios en un paisaje de interés de su país.

## Set-up
1. [Ejecutar Earth](https://www.google.es/intl/es/earth/index.html) 
2. [Instrucciones para registrarse en Google Cloud Platform y GEE](https://docs.google.com/document/d/1n40y1vcDQVspXZODvGuCDtBnykudkURDvh-tPmvXLKs/edit?tab=t.si25om8ipoh9)


# Google Earth Web: Fundamentos

📑 Presentación completa:(https://docs.google.com/presentation/d/1w3-HQKTl1TTTIEQIfojF8Cv5hdC8F9hHIkwhl8n1Bto/edit?usp=sharing)  
📂 Datos del taller: [goo.gle/g4g26-data](http://goo.gle/g4g26-data)  
*Material original: Raleigh Seamster, Geo for Good Summit 2026*

---

## Almacenar

Puedes guardar tus datos en la **nube** o en tu **dispositivo**:

- **Proyectos (nube, Google Drive):** se sincronizan en vivo, se pueden compartir por enlace y coeditar con tu equipo.
- **Archivos KML locales (tu dispositivo):** ideales para información sensible. Solo se comparten enviando el archivo (por ejemplo, por email).

---

## Importar

| | Componentes de mapa | Capa de datos | KML local |
|---|---|---|---|
| **Mejor para** | Archivos pequeños de trabajo | Bases grandes con tabla de atributos | Datos sensibles o locales |
| **Formatos** | KML / KMZ | KML/KMZ, **SHP**, CSV, GeoJSON, Google Sheets | KML / KMZ |
| **Tamaño máximo** | 10.000 elementos por proyecto | Cientos de miles de elementos | Sin límite práctico |
| **Edición** | Editable | Solo lectura | Editable |
| **Carpetas** | Mantiene la estructura | Todo en una sola capa | Mantiene la estructura |
| **Estilo** | Conserva íconos y colores | Estilo según atributos | Conserva íconos y colores |

💡 Las **capas de datos** permiten ver la tabla de atributos, filtrar y aplicar estilos y etiquetas según sus valores.

📖 [Documentación oficial: importar datos](https://developers.google.com/maps/documentation/earth/import-data?platform=computer)

---

## Visibilidad

- **Ocultar o mostrar:** clic en el ícono junto al nombre de la capa.
- **Ordenar:** clic derecho sobre la capa → *Traer al frente* o *Enviar al fondo*.

---

## Imágenes

- **Fecha de la imagen:** aparece en pantalla; revísala siempre antes de interpretar.
- **Imágenes históricas:** permiten comparar el mismo lugar en distintos años (ideal para detectar cambios como deforestación).
- **Street View:** vista a nivel de calle donde esté disponible.
- **Solicitar actualizaciones:** puedes pedir imágenes más recientes de un área.

---

## Catálogo de datos

Capas listas para usar desde Google Earth, como modelos de elevación, curvas de nivel, límites administrativos, población, land cover (WorldCover). Se añaden directamente al mapa sin necesidad de descargar nada.

---

## Proyectos de referencia (reference layers)

Permiten ver otro proyecto como capa de fondo mientras trabajas en el tuyo, sin mezclarlos.

1. *Cambiar mapa base* → *Gestionar proyectos de referencia*.
2. Seleccionar el o los proyectos.
3. Aparecerán en tu mapa base y en el globo.

💡 Útil para combinar datos sensibles en un KML local con tu proyecto en la nube, sin subir la información sensible.

---

## Herramientas

- **Crear mapas:** marcadores, líneas y polígonos.
- **Medir:** distancias, áreas y círculos (por ejemplo, zonas de amortiguamiento de 2 km).
- **Compartir y colaborar:** con tu equipo y actores clave.
- **App móvil (iOS y Android):** marcadores con ubicación GPS y fotos en campo, sincronizados con la web.
- **Programa de Créditos de Google Earth:** acceso gratuito a herramientas avanzadas para ONG, investigadores, periodistas y equipos de respuesta a crisis.
- **Comentarios:** *Ayuda → Enviar comentarios* 

---
