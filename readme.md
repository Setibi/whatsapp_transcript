# 🧾 Sistema automático de pedidos por WhatsApp (Whisper + GPT)

Este proyecto permite **transcribir audios de WhatsApp**, limpiar el texto del pedido con **IA (GPT)** y generar automáticamente un **listado simple en Word**, listo para enviar a proveedores.

Funciona **100% en local en Windows**, sin móvil, sin virtualizar Android y sin apps externas tipo Luzia.

---

## 🎯 Objetivo

Automatizar este flujo:

```
Audio de WhatsApp (.ogg)
        ↓
Whisper (transcripción)
        ↓
Texto crudo del pedido
        ↓
GPT (limpieza y orden)
        ↓
Documento Word listo para enviar
```

---

## 🧰 Requisitos

### Sistema
- Windows 10 / 11
- Python **3.10 o superior** (probado con 3.14 64 bits)

### Software externo
- **FFmpeg** (imprescindible para audios `.ogg`)

---

## 📦 Librerías Python usadas

```bash
pip install openai-whisper torch watchdog python-docx openai
```

- `openai-whisper` → Transcripción de audio
- `torch` → Backend de Whisper
- `watchdog` → Vigilancia de carpetas (opcional)
- `python-docx` → Generación de documentos Word
- `openai` → Limpieza del texto con GPT

---

## 📂 Estructura del proyecto

```text
C:\WhatsApp_Audios\
│
├── audios\              # Audios de WhatsApp (.ogg)
├── procesados\          # Audios ya transcritos
├── pedidos_txt\         # Texto crudo generado por Whisper
├── pedidos_word\        # Pedidos limpios en Word (.docx)
│
└── whatsapp_pedidos_word.py
```

---

## ⚙️ Configuración inicial

1. Crear la carpeta principal:
```
C:\WhatsApp_Audios
```

2. Dentro, crear estas subcarpetas:
```
audios
procesados
pedidos_txt
pedidos_word
```

3. Copiar el script `whatsapp_pedidos_word.py` dentro de `C:\WhatsApp_Audios`

4. Colocar audios de WhatsApp (`.ogg`) en la carpeta `audios`

---

## 🔑 API Key de OpenAI

Es necesario disponer de una **API Key** de OpenAI.

Recomendado: definirla como variable de entorno:

```bat
setx OPENAI_API_KEY "tu_api_key_aqui"
```

El script la usará automáticamente.

---

## ▶️ Ejecución

Desde la carpeta del proyecto:

```bat
cd C:\WhatsApp_Audios
python whatsapp_pedidos_word.py
```

Salida esperada:

```
🔄 Cargando Whisper...
✅ Sistema de pedidos activo
🎧 Audio detectado: WhatsApp Ptt ....ogg
📝 Transcribiendo...
🤖 Limpiando pedido con GPT...
📄 Pedido guardado en Word
```

---

## 📄 Formato del resultado

El Word generado contiene:
- Un **listado simple**
- Una línea por producto
- Cantidad + producto
- Sin frases, sin saludos

Ejemplo:

```
2 cajas de aguacate
5 kg de cebolla blanca
3 manojos de albahaca
1 caja de champiñones
```

---

## ⚠️ Mensajes comunes (no son errores)

```
FP16 is not supported on CPU; using FP32 instead
```
✔ Normal si no hay GPU
✔ Whisper funciona correctamente

---

## 🛠️ Problemas habituales

### No detecta audios
- Verificar que estén en `audios`
- Verificar extensión `.ogg`
- Verificar que no estén ya en `procesados`

### Error FFmpeg
- Comprobar que `ffmpeg -version` funciona en consola
- Verificar rutas de archivo (sin borrar el audio mientras se procesa)

---

## 🔜 Mejoras posibles

- Vigilancia en tiempo real (estilo Luzia)
- Un solo Word diario con varios audios
- Clasificación por proveedor (fruta, pescado, varios)
- Envío automático por email o WhatsApp Web
- Corrección automática de productos frecuentes

---

## ✅ Estado del proyecto

✔ Funcional
✔ Estable
✔ Uso diario en entorno real de restaurante

---

## 📌 Resumen

Este proyecto convierte audios de WhatsApp en **pedidos profesionales limpios**, ahorrando tiempo, errores y trabajo manual.

Ideal para restaurantes, cocinas y negocios que reciben pedidos por voz.

---

**Autor:** Proyecto personalizado
**Uso:** Interno / Productivo

