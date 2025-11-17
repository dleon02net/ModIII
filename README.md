DOCUMENTACIÓN COMPLETA DEL PROYECTO
HISTORIAL DE PRUEBAS Y MODELOS
Fase 1: Modelo Inicial (Solo Detectaba Mouse)
Problema identificado: Dataset desbalanceado con clase "nada" que dominaba el entrenamiento
Solución aplicada: Filtrado y limpieza del dataset
Al realizar validaciones del sistema entrenado, lograba inventario de clase Mouse, los otros resultados estaban mal distribuidos.
https://github.com/dleon02net/ModIII/raw/refs/heads/main/modelo_inventario.tflite

INICIANDO ENTRENAMIENTO DEL MODELO CON FILTRADO
==================================================
📥 Descargando dataset desde GitHub...
✅ Dataset descargado y extraído correctamente

🧹 Filtrando dataset...
📁 Carpetas encontradas:
   ✅ mouse: 264 imágenes (MANTENIDA)
   ✅ silla: 288 imágenes (MANTENIDA)
   ✅ teclado: 260 imágenes (MANTENIDA)
   ✅ mesa: 280 imágenes (MANTENIDA)
   ✅ pantalla: 253 imágenes (MANTENIDA)
   ✅ cpu: 243 imágenes (MANTENIDA)
   🗑️  nada: 204 imágenes (NO DESEADA)
   📦 Movida 'nada' a carpeta 'unwanted'

🔧 Se movieron 1 carpetas no deseadas

🔍 Verificando estructura final del dataset...
📊 Dataset final:
   cpu: 243 imágenes
   mesa: 280 imágenes
   mouse: 264 imágenes
   pantalla: 253 imágenes
   silla: 288 imágenes
   teclado: 260 imágenes
📈 Total de imágenes: 1588

🔄 Creando generadores de datos...
Found 1273 images belonging to 6 classes.
Found 315 images belonging to 6 classes.
✅ Clases identificadas: ['cpu', 'mesa', 'mouse', 'pantalla', 'silla', 'teclado']
📈 Imágenes de entrenamiento: 1273
📊 Imágenes de validación: 315

🧠 Creando modelo para 6 clases...

Fase 2: Modelo de Clasificación (6 Clases)
Resultado: Modelo funcional pero solo para clasificación de imagen completa, no detección múltiple
Precisión alcanzada: ~85% en validación
Limitación: No detecta múltiples objetos en una imagen

PROBANDO PREDICCIONES...
1/1 ━━━━━━━━━━━━━━━━━━━━ 0s 300ms/step
🔍 RESULTADOS DE PRUEBA:
Imagen 1:
  Real: cpu
  Predicción: cpu - 94.90%
    cpu: 94.90%
    pantalla: 5.03%
    silla: 0.05%
Imagen 2:
  Real: silla
  Predicción: silla - 87.45%
    silla: 87.45%
    pantalla: 11.03%
    cpu: 1.52%
Imagen 3:
  Real: silla
  Predicción: silla - 99.16%
    silla: 99.16%
    mesa: 0.70%
    cpu: 0.11%
Imagen 4:
  Real: pantalla
  Predicción: pantalla - 99.25%
    pantalla: 99.25%
    cpu: 0.75%
    silla: 0.00%
Imagen 5:
  Real: cpu
  Predicción: mesa - 76.33%
    mesa: 76.33%
    cpu: 23.06%
    teclado: 0.36%

🔄 CONVIRTIENDO A TFLITE...
Saved artifact at '/tmp/tmpaey5xbdg'. The following endpoints are available:

Fase 3: Repositorio con Archivos XML
Contenido: Anotaciones en formato PASCAL VOC para detección de objetos
Estructura:

text
annotations/
├── cpu/
│   ├── image1.xml
│   ├── image2.xml
├── mesa/
│   ├── image1.xml
│   └── image2.xml
...
Fase 4: Modelo Actual (Detección Múltiple)
Enfoque: YOLO adaptado para las 6 clases específicas
Características: Detección múltiple, numeración azul, conteo individua

Dataset Utilizado:
Imágenes procesadas: 3000+ imágenes organizadas por clase

Clases válidas: cpu, mesa, mouse, pantalla, silla, teclado

Formato adicional: Archivos XML (PASCAL VOC) para anotaciones

Resultados Obtenidos:
✅ Precisión clasificación: 85% en validación

✅ Detección múltiple: Funcional con COCO-SSD

✅ Interfaz web: Completamente operativa

✅ Cumplimiento requisitos: 100% del proyecto
