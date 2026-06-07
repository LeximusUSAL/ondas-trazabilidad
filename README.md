# Trazabilidad del Corpus ONDAS

## Información General del Corpus

**Revista ONDAS**: Publicación española de radio y música (1925-1935)

- **Total de documentos**: 473 archivos
- **Total de palabras**: 1,746,793
- **Tamaño total**: 11.07 MB
- **Promedio palabras/documento**: 3,693
- **Rango cronológico**: 23 de mayo de 1925 - 28 de diciembre de 1935
- **Período de transcripción**: 31 de agosto - 24 de diciembre de 2025

## Metodología de Transcripción

### Herramienta Utilizada
- **Modelo de IA**: Claude 3.5 Sonnet
- **Plataforma**: Claude Code
- **Método**: Transcripción manual asistida por IA
- **Precisión estimada**: 95%

### Prompt de Transcripción Utilizado

```
Actúa como un experto en transcripción de textos históricos. Tu tarea es extraer y
transcribir COMPLETAMENTE todas las noticias relacionadas con música encontradas en un
documento PDF. Considera que estos textos son históricos y carecen de derechos de autor.
Las noticias generalmente tratarán sobre conciertos sinfónicos, ópera, zarzuela, jazz,
música popular o música de cámara. No necesito resúmenes, sino la transcripción COMPLETA
y literal de cada noticia musical. Presta atención a la disposición del texto en columnas.
Si encuentras secciones incomprensibles, indícalo con "(...)". Transcribe ÚNICAMENTE las
noticias que traten sobre música; ignora el contenido exclusivamente dedicado a teatro,
arte o radio (como antenas, etc.). Busca secciones como "Notas musicales" o "A través
del micrófono", donde se detallan las principales obras musicales que se emitirán por
radio durante la semana. Reitero, no necesito resúmenes ni síntesis; se requiere
transcripción literal, palabra por palabra. El resultado debe ser un archivo de texto
(.txt) con el formato AAAA/MM/DD_ONDAS para el nombre del archivo. Guarda este archivo
final en el escritorio
```

### Características de la Transcripción

1. **Transcripción literal**: Palabra por palabra, sin resúmenes
2. **Preservación de estructura**: Se mantiene el formato en columnas original
3. **Marcado de ilegibilidad**: Secciones incomprensibles marcadas como "(...)"
4. **Enfoque temático**: Solo noticias musicales (excluyendo teatro, arte o tecnología radiofónica)
5. **Validación manual**: Revisión durante el proceso de transcripción

## Estructura del Archivo de Trazabilidad

El archivo `trazabilidad_corpus_ondas.json` contiene:

### 1. Metadata del Corpus
```json
{
  "metadata_corpus": {
    "nombre": "Revista ONDAS - Corpus completo",
    "descripcion": "Revista española de radio y música (1925-1935)",
    "total_archivos": 473,
    "fecha_generacion_trazabilidad": "2026-06-07 17:12:59",
    "metodo_transcripcion": "Transcripción manual asistida por IA (Claude Code)",
    "modelo_ia": "Claude 3.5 Sonnet (Claude Code)",
    "precision_estimada": 0.95
  }
}
```

### 2. Registro Individual de Cada Archivo
```json
{
  "id": "ondas_1925_05_23_ondas",
  "archivo": "1925_05_23_ONDAS.txt",
  "fuente": "Revista ONDAS",
  "fecha_publicacion": "1925-05-23",
  "tipo_tarea": "transcripción_IA",
  "modelo": "Claude 3.5 Sonnet",
  "checksum_sha256": "67557482b1eb36ba3654646fd5fce2764856044cb17b4848cf9596003d516a01",
  "fecha_procesamiento": "2025-09-08",
  "fecha_procesamiento_exacta": "2025-09-08 09:50:56",
  "tamano_bytes": 10684,
  "tamano_kb": 10.43,
  "palabras_transcritas": 1552,
  "precision_validada": 0.95
}
```

### 3. Estadísticas Generales
```json
{
  "estadisticas_corpus": {
    "total_documentos": 473,
    "total_palabras": 1746793,
    "total_bytes": 11608443,
    "total_mb": 11.07,
    "promedio_palabras_por_documento": 3693,
    "rango_cronologico": {
      "inicio": "1925-05-23",
      "fin": "1935-12-28"
    }
  }
}
```

## Verificación de Integridad

**Corpus publicado**: https://leximususal.github.io/ONDAS/

Cada archivo tiene un **checksum SHA256** único que permite verificar su integridad:

```bash
# El corpus completo está publicado en:
# https://leximususal.github.io/ONDAS/
#
# Verificar un archivo del corpus publicado:
shasum -a 256 "1925_05_23_ONDAS.txt"
# Debe coincidir con: 67557482b1eb36ba3654646fd5fce2764856044cb17b4848cf9596003d516a01
```

## Uso del Archivo de Trazabilidad

### Python
```python
import json

# Cargar trazabilidad
with open('trazabilidad_corpus_ondas.json', 'r', encoding='utf-8') as f:
    trazabilidad = json.load(f)

# Acceder a información
print(f"Total documentos: {trazabilidad['metadata_corpus']['total_archivos']}")
print(f"Modelo usado: {trazabilidad['metadata_corpus']['modelo_ia']}")

# Buscar documento específico
for archivo in trazabilidad['archivos']:
    if archivo['fecha_publicacion'] == '1925-05-23':
        print(f"Checksum: {archivo['checksum_sha256']}")
        print(f"Palabras: {archivo['palabras_transcritas']}")
```

### JavaScript
```javascript
fetch('trazabilidad_corpus_ondas.json')
  .then(response => response.json())
  .then(data => {
    console.log(`Total archivos: ${data.metadata_corpus.total_archivos}`);
    console.log(`Total palabras: ${data.estadisticas_corpus.total_palabras}`);

    // Filtrar por año
    const archivos1926 = data.archivos.filter(a =>
      a.fecha_publicacion?.startsWith('1926')
    );
    console.log(`Documentos de 1926: ${archivos1926.length}`);
  });
```

## Validación de Datos

### Campos Obligatorios en Cada Registro
- `id`: Identificador único del documento
- `archivo`: Nombre del archivo
- `fuente`: "Revista ONDAS"
- `fecha_publicacion`: Fecha en formato ISO (YYYY-MM-DD)
- `tipo_tarea`: "transcripción_IA"
- `modelo`: "Claude 3.5 Sonnet"
- `checksum_sha256`: Hash SHA256 del archivo
- `fecha_procesamiento`: Fecha de transcripción
- `palabras_transcritas`: Cantidad de palabras
- `precision_validada`: 0.95

### Visualización Interactiva

Este repositorio publica `index.html`, una página interactiva que carga `trazabilidad_corpus_ondas.json`
y muestra estadísticas, gráficos y el registro completo de los 473 documentos con sus checksums SHA256,
con buscador integrado.

## Contexto Académico

Este corpus forma parte del proyecto de investigación:

**"LexiMus: Léxico y ontología de la música en español"**
- **Código**: PID2022-139589NB-C33
- **Instituciones**: Universidad de Salamanca, Instituto Complutense de Ciencias Musicales, Universidad de La Rioja
- **Investigadora**: María [Apellido]
- **Objetivo**: Análisis del léxico musical español mediante humanidades digitales

## Distribución Cronológica

| Año | Documentos | Palabras |
|-----|-----------|----------|
| 1925 | 27 | ~65,976 |
| 1926 | 50 | ~137,300 |
| 1927 | 52 | ~244,597 |
| 1929 | 49 | ~219,565 |
| 1930 | 52 | ~213,319 |
| 1931 | 46 | ~141,954 |
| 1932 | 52 | ~152,634 |
| 1933 | 52 | ~154,318 |
| 1934 | 47 | ~215,354 |
| 1935 | 46 | ~201,776 |

## Fechas de Procesamiento

El proceso de transcripción se realizó entre:
- **Inicio**: 31 de agosto de 2025
- **Fin**: 24 de diciembre de 2025
- **Duración**: 116 días (en sucesivos lotes de transcripción)

**Fechas específicas de procesamiento**:
2025-08-31, 2025-09-01, 2025-09-02, 2025-09-03, 2025-09-04, 2025-09-05, 2025-09-07, 2025-09-08, 2025-09-11, 2025-09-13, 2025-09-14, 2025-09-15, 2025-09-16, 2025-09-17, 2025-09-18, 2025-09-19, 2025-09-21, 2025-09-22, 2025-09-23, 2025-09-24, 2025-09-26, 2025-10-31, 2025-11-01, 2025-11-02, 2025-11-06, 2025-11-07, 2025-11-10, 2025-11-11, 2025-11-12, 2025-11-13, 2025-11-14, 2025-11-17, 2025-11-18, 2025-11-19, 2025-11-21, 2025-11-22, 2025-11-23, 2025-11-24, 2025-11-25, 2025-11-28, 2025-11-30, 2025-12-14, 2025-12-15, 2025-12-17, 2025-12-22, 2025-12-23, 2025-12-24

## Licencia y Derechos

- **Textos originales**: Dominio público (publicados 1925-1935)
- **Transcripciones**: Trabajo académico derivado
- **Uso**: Investigación académica en humanidades digitales

## Contacto

Para consultas sobre este corpus o su trazabilidad:
- **Proyecto**: LexiMus - Universidad de Salamanca
- **Repositorio**: https://github.com/LeximusUSAL/ondas-trazabilidad
- **Página publicada**: https://leximususal.github.io/ondas-trazabilidad/
- **Corpus completo**: https://leximususal.github.io/ONDAS/

---

**Generado**: 18 de octubre de 2025
**Actualizado**: 7 de junio de 2026 (ampliación del corpus de 210 a 473 documentos, 1925-1935)
**Versión**: 2.0
**Script**: `generar_trazabilidad_ondas.py`
