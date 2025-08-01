# Guión: LLMs en Local con Ollama y LM Studio

## Contexto de la clase

Esta clase forma parte del contenido **obligatorio** del **Master Online de IA para Desarrolladores** de LIDR (https://www.lidr.co/ia-devs), un programa integral diseñado para profesionales del desarrollo que quieren dominar las tecnologías de Inteligencia Artificial.

### ¿Por qué esta clase es parte del master?

Aunque el master está diseñado para ser **accesible a cualquier desarrollador** sin requerir hardware especializado, consideramos fundamental que nuestros alumnos comprendan **el futuro de la IA local** y las oportunidades que presenta. Por este motivo, hemos incluido esta clase como contenido adicional que:

- **Es parte integral** del programa de estudios del master
- **Está disponible exclusivamente** para alumnos del master
- **Prepara a los estudiantes** para el futuro de la IA local y sus aplicaciones profesionales
- **Proporciona ventaja competitiva** en un mercado laboral en constante evolución

### Para quién es esta clase:

✅ **Alumnos del master** como parte de su formación integral  
✅ **Futuros profesionales de IA y entusiastas** que necesitan entender todas las opciones tecnológicas  
✅ **Desarrolladores** que quieren estar preparados para el siguiente nivel de la IA  
✅ **Estudiantes** que buscan una formación completa y actualizada  

### Importancia en tu formación profesional:

El **Master de IA para Desarrolladores** cubre todas las tecnologías de IA que necesitas como profesional, utilizando APIs y servicios en la nube que funcionan en cualquier ordenador. Esta clase te muestra **la evolución natural**: cómo la IA local se está convirtiendo en una opción cada vez más viable y qué oportunidades profesionales presenta.

**Comprender la IA local te permitirá**:
- Ofrecer soluciones más diversas a tus clientes
- Entender las ventajas y limitaciones de cada enfoque
- Estar preparado para proyectos que requieran máxima privacidad
- Anticiparte a las tendencias del mercado

---

## Introducción a la clase

Como alumno del **Master de IA para Desarrolladores**, esta clase te proporcionará conocimientos avanzados sobre **LLMs en local** que complementan perfectamente tu formación en tecnologías de IA en la nube. Te ayudará a valorar si merece la pena invertir en hardware local, qué configuración necesitas y cómo integrar estas herramientas en tu flujo profesional.

**Lo que veremos en esta clase:**

### **Herramientas principales para ejecutar LLMs localmente:**
- **Ollama**: Herramienta de línea de comandos, potente y flexible
- **LM Studio**: Interfaz gráfica amigable, ideal para principiantes

### **Interfaces gráficas para interactuar con LLMs:**
- **Open WebUI**: Interfaz de chat similar a ChatGPT (instalada con Pinokio)

### **Integraciones con editores de código:**
- **Cursor**: Editor con IA usando túneles Ngrok
- **VS Code**: Extensiones Continue, Cline y Roo Code para desarrollo asistido por IA

### **Casos de uso avanzados:**
- **DeerFlow**: Sistema experimental de investigación profunda de ByteDance con Qwen3

**Ventajas de ejecutar LLMs en local:**
- **Privacidad total**: Tus datos nunca salen de tu máquina
- **Sin conexión**: Funciona completamente offline
- **Sin límites**: No hay restricciones de uso
- **Personalización**: Control total sobre el comportamiento
- **Costes**: Sin suscripciones mensuales
- **Flexibilidad**: Desde chat casual hasta investigación profesional

## 1. Hardware Necesario

### Requisitos de hardware - Mi configuración actual:
- **GPU**: RTX 5090 (32 GB VRAM)
- **CPU**: AMD 7800X3D
- **RAM**: 64 GB DDR5

### ¿Necesitas tanto para empezar? ¡NO!

**El factor más limitante**: La **memoria de la tarjeta gráfica (VRAM)** es el cuello de botella principal.

#### Recomendaciones por VRAM:
- **16 GB VRAM**: Punto de entrada para modelos interesantes
  - Modelos 7B-13B con quantización
  - Llama 2/3 7B, Mistral 7B, CodeLlama 7B
- **24 GB VRAM**: Rango cómodo
  - Modelos 13B-20B sin problemas
  - Algunos modelos 30B quantizados
  - **Opción popular**: RTX 3090 de segunda mano (24 GB, 2 generaciones atrás pero muy demandada)
  - **Alternativa moderna**: RTX 4090 (24 GB, más rápida pero misma VRAM)
- **32 GB+ VRAM**: Opción más potente
  - Modelos 70B+ quantizados
  - Múltiples modelos simultáneos

#### Configuraciones multi-GPU:
Una estrategia popular es **combinar múltiples tarjetas gráficas** para sumar VRAM:
- **2x RTX 3090**: 48 GB VRAM total (24 GB + 24 GB)
- **2x RTX 4090**: 48 GB VRAM total (más velocidad)
- **Ventaja**: Acceso a modelos muy grandes sin invertir en hardware de gama ultra-alta
- **Consideraciones**: 
  - Requiere placa base con múltiples slots PCIe y fuente de alimentación potente
  - **Complejidad adicional**: Necesitas software especializado para distribución multi-GPU
  - Ollama soporta multi-GPU, pero otros frameworks requieren configuración avanzada

**Mensaje clave**: Puedes empezar con hardware modesto y obtener resultados útiles. La clave está en elegir los modelos adecuados para tu hardware.

## 2. Ollama - Herramienta de Línea de Comandos

### ¿Qué es Ollama?

Ollama es una herramienta que permite ejecutar modelos de lenguaje grandes (LLMs) localmente en tu máquina de manera sencilla. Es como tener ChatGPT, pero corriendo completamente en tu ordenador.

### Características principales:

- **Ejecución local**: No necesitas conexión a internet una vez descargado el modelo
- **Privacidad total**: Tus datos nunca salen de tu máquina
- **Múltiples modelos**: Soporta Llama, Mistral, CodeLlama, Gemma y muchos más
- **API REST**: Fácil integración con aplicaciones
- **Gestión automática**: Descarga, actualización y gestión de modelos automática

### ¿Qué se puede hacer con Ollama?

1. **Chatbots locales**: Crear asistentes personalizados
2. **Análisis de documentos**: Procesar archivos de forma privada
3. **Generación de código**: Asistente de programación offline
4. **Traducción**: Sin enviar datos a servicios externos
5. **Resúmenes y análisis**: De textos largos
6. **Integración en aplicaciones**: Via API REST o librerías

### Modelos disponibles

Ollama no se limita solo a los modelos oficiales de su biblioteca. Puedes usar modelos de múltiples fuentes:

#### 1. Biblioteca oficial de Ollama
- **URL**: https://ollama.com/library
- Modelos verificados y optimizados para Ollama
- Descarga directa con `ollama pull nombre:tag`

#### 2. Modelos de Hugging Face
- **Ventaja del código abierto**: La comunidad puede mejorar y modificar modelos existentes
- **Ejemplo**: [Devstral Small modificado](https://huggingface.co/unsloth/Devstral-Small-2505-GGUF)
  - Modelo Devstral original con encoder de visión añadido
  - Mejoras desarrolladas por la comunidad

**Formatos de modelos y compatibilidad:**

| Formato | Compatible con Ollama | Descripción |
|---------|----------------------|-------------|
| **GGUF** | ✅ Sí | Formato optimizado para inferencia local |
| **GGML** | ✅ Sí (formato anterior) | Predecesor de GGUF |
| **SafeTensors** | ❌ No directamente | Formato seguro de PyTorch/Transformers |
| **PyTorch (.bin)** | ❌ No directamente | Formato nativo de PyTorch |
| **TensorFlow** | ❌ No directamente | Formato de TensorFlow |

**Cómo identificar modelos compatibles:**
1. **Buscar "GGUF" en el nombre** del repositorio
2. **Verificar los archivos**: Deben contener archivos `.gguf`
3. **Buscar la etiqueta "gguf"** en las tags del modelo
4. **Ver si aparece el botón "Use with Ollama"** en la página del modelo

```bash
# Usar modelo de Hugging Face (solo si es GGUF)
ollama run hf.co/unsloth/Devstral-Small-2505-GGUF

# Si el modelo no es GGUF, necesitarás convertirlo (proceso avanzado)
```

**Nota importante**: Si un modelo no está en formato GGUF, no aparecerá la opción "Use with Ollama" en su página de Hugging Face.

**La gran ventaja del ecosistema opensource**: Grupos especializados pueden tomar modelos base y añadir capacidades (visión, audio, lenguajes específicos) que no tenía el modelo original.

### 2.1. Instalación y Primeros Pasos

### Instalación
```bash
# macOS/Linux
curl -fsSL https://ollama.ai/install.sh | sh

# Windows
# Descargar desde https://ollama.ai/download
```

### Comandos básicos
```bash
# Listar modelos disponibles
ollama list

# Ver modelos en ejecución
ollama ps

# Ejecutar un modelo (lo descarga si no existe)
ollama run llama2:7b

# Descargar un modelo sin ejecutarlo
ollama pull mistral:7b

# Ver información de un modelo
ollama show llama2:7b

# Eliminar un modelo
ollama rm llama2:7b
```

### 2.2. Personalización de Modelos

#### 2.2.1 Método 1: Comandos interactivos durante la ejecución

Una vez que ejecutas un modelo con `ollama run`, puedes usar comandos especiales para personalizar su comportamiento:

```bash
# Ejecutar el modelo
ollama run qwen3:32b

# Dentro del chat, usar comandos de configuración:
/set parameter num_ctx 30720          # Aumentar contexto a ~30k tokens
/set parameter temperature 0.3        # Hacer más determinista
/set parameter top_p 0.9             # Ajustar nucleus sampling
/set parameter repeat_penalty 1.2    # Reducir repeticiones

# Guardar la configuración personalizada como nuevo modelo
/save qwen3:32b-30k
```

#### Comandos disponibles en sesión:
- `/set parameter <nombre> <valor>` - Cambiar parámetros
- `/save <nombre>` - Guardar configuración actual como nuevo modelo
- `/show` - Ver configuración actual
- `/help` - Ver ayuda
- `/bye` - Salir

#### 2.2.2 Método 2: Modelfile (Configuración avanzada)

Para personalizaciones más complejas, crear un archivo `Modelfile`:

```dockerfile
# Modelfile
FROM qwen3:32b

# Parámetros del modelo
PARAMETER num_ctx 16384
PARAMETER temperature 0.7
PARAMETER top_p 0.9
PARAMETER repeat_penalty 1.1

# Prompt del sistema personalizado
SYSTEM """
Eres un asistente especializado en programación Python.
Siempre incluye ejemplos de código en tus respuestas.
Mantén un tono profesional pero amigable.
"""

# Plantilla de conversación
TEMPLATE """{{ if .System }}<|system|>
{{ .System }}<|end|>
{{ end }}{{ if .Prompt }}<|user|>
{{ .Prompt }}<|end|>
{{ end }}<|assistant|>
{{ .Response }}<|end|>
"""
```

Crear el modelo personalizado:
```bash
ollama create mi-asistente-python -f Modelfile
ollama run mi-asistente-python
```

### 2.3. Parámetros de Configuración Importantes

### Contexto y Memoria
- **num_ctx**: Tamaño del contexto (2048 por defecto)
  - 4096: Conversaciones cortas
  - 8192: Conversaciones medianas
  - 16384+: Conversaciones largas o documentos

### Creatividad y Determinismo
- **temperature**: Aleatoriedad (0.8 por defecto)
  - 0.0-0.3: Muy determinista
  - 0.4-0.7: Equilibrado
  - 0.8-1.0: Creativo
  
- **top_p**: Nucleus sampling (0.9 por defecto)
- **top_k**: Top-k sampling (40 por defecto)

### Control de Repeticiones
- **repeat_penalty**: Penalización por repetir (1.1 por defecto)
- **repeat_last_n**: Tokens a considerar para penalización

### Rendimiento
- **num_gpu**: GPUs a utilizar
- **num_thread**: Hilos de CPU
- **use_mlock**: Bloquear memoria en RAM

### 2.4. Ejemplos Prácticos

### Ejemplo 1: Modelo para análisis de código
```bash
ollama run hf.co/unsloth/Devstral-Small-2507-GGUF:Q4_K_M
/set parameter num_ctx 90000
/save devstral-90k
```

### Ejemplo 2: Modelo para escritura
```bash
ollama run qwen3:32b
/set parameter num_ctx 30000
/save qwen3:32b-30k
```

### 2.5. Consejos y Mejores Prácticas

1. **Empieza con modelos pequeños** (7B) para probar
2. **Ajusta gradualmente** los parámetros según necesidades
3. **Guarda configuraciones útiles** con `/save`
4. **Monitorea el uso de memoria** con modelos grandes
5. **Usa contextos grandes solo cuando necesario**
6. **Experimenta con diferentes temperaturas** según el uso

## 3. LM Studio - Interfaz Gráfica Amigable

### ¿Qué es LM Studio?

**LM Studio** es otra herramienta popular para ejecutar LLMs en local, pero con una **interfaz gráfica amigable**. Es ideal para usuarios que prefieren no depender de comandos y quieren una experiencia más visual.

### Ventajas de LM Studio:

- **Interfaz gráfica intuitiva**: No necesitas usar comandos
- **Gestión visual de modelos**: Descarga, instalación y gestión con clicks
- **Chat integrado**: Interfaz de chat similar a ChatGPT
- **Configuración visual**: Ajustar parámetros con sliders y controles
- **Compatibilidad GGUF**: Mismo formato que Ollama
- **API integrada**: Servidor OpenAI-compatible incluido

### Características principales:

#### 1. **Descarga de modelos**
- Explorar modelos desde Hugging Face directamente en la app
- Filtros por tamaño, tipo y popularidad
- Descarga con progress bar visual
- Gestión de espacio en disco

#### 2. **Chat interface**
- Interfaz similar a ChatGPT
- Historial de conversaciones
- Configuración de parámetros en tiempo real
- Exportar conversaciones

#### 3. **Configuración avanzada**
- **Temperature**: Control deslizante para creatividad
- **Context length**: Ajustar tamaño de contexto
- **GPU layers**: Decidir qué capas van a GPU vs CPU
- **Quantization**: Elegir nivel de quantización

#### 4. **API Server**
- Servidor OpenAI-compatible
- Integración fácil con aplicaciones existentes
- Documentación automática
- Monitoreo de uso

### Cuándo usar LM Studio vs Ollama:

| Aspecto | LM Studio | Ollama |
|---------|-----------|---------|
| **Facilidad de uso** | ✅ Interfaz gráfica | ⚠️ Requiere comandos |
| **Configuración** | ✅ Visual, intuitiva | ⚠️ Archivos de texto |
| **Automatización** | ⚠️ Limitada | ✅ Fácil scripting |
| **Recursos** | ⚠️ Más pesado | ✅ Más ligero |
| **Flexibilidad** | ⚠️ Limitada por UI | ✅ Total control |

### Instalación de LM Studio:
1. Descargar desde: https://lmstudio.ai/
2. Instalar el ejecutable según tu OS
3. Abrir la aplicación
4. Explorar y descargar modelos desde la interfaz

**Recomendación**: LM Studio es perfecto para **empezar** y **experimentar** rápidamente. Ollama es mejor para **automatización** y **integración** en workflows.

## 4. Open WebUI - Interfaz de Chat Similar a ChatGPT

### ¿Qué es Open WebUI?

**Open WebUI** es una interfaz web opensource que proporciona una experiencia de chat similar a ChatGPT, pero completamente local. Es perfecta para interacciones diarias con tus LLMs sin necesidad de usar la línea de comandos.

### Características principales:

- **Interfaz familiar**: Diseño similar a ChatGPT que ya conoces
- **Múltiples modelos**: Cambiar entre modelos con un click
- **Workspaces personalizados**: Crear espacios de trabajo especializados
- **System prompts customizados**: Personalizar el comportamiento de cada modelo
- **Historial de conversaciones**: Guardar y organizar tus chats
- **Compartir conversaciones**: Exportar e importar chats
- **Modo oscuro/claro**: Interfaz adaptable a tus preferencias

### Instalación con Pinokio:

**Pinokio** es una herramienta que simplifica enormemente la instalación de aplicaciones de IA. Es como una "tienda de apps" para herramientas de IA que se encarga de toda la configuración automáticamente.

#### Pasos para instalar Open WebUI con Pinokio:

1. **Descargar Pinokio**:
   - Ir a: https://pinokio.computer/
   - Descargar la versión para tu sistema operativo
   - Instalar y abrir Pinokio

2. **Instalar Open WebUI**:
   - En Pinokio, ir a la sección **"Discover"**
   - Buscar **"Open WebUI"**
   - Hacer clic en **"Download"** y luego **"Install"**
   - Pinokio descargará e instalará todo automáticamente

3. **Ejecutar Open WebUI**:
   - Una vez instalado, hacer clic en **"Start"**
   - Pinokio abrirá automáticamente tu navegador en la dirección correcta
   - Crear tu cuenta de administrador en la primera ejecución

#### Ventajas de usar Pinokio:
- ✅ **Instalación con un click**: No necesitas Docker ni comandos
- ✅ **Gestión automática**: Pinokio maneja actualizaciones y dependencias
- ✅ **Interfaz visual**: Todo se hace desde una aplicación gráfica
- ✅ **Múltiples herramientas**: Puedes instalar otras herramientas de IA fácilmente
- ✅ **Sin configuración manual**: Todo funciona "out of the box"

### Configuración con Ollama:

#### Paso 1: Asegurarse de que Ollama esté ejecutándose
```bash
# Verificar que Ollama está corriendo
ollama list

# Si no está ejecutándose, iniciarlo
ollama serve
```

#### Paso 2: Conectar Open WebUI
1. **Open WebUI detectará automáticamente Ollama** si está ejecutándose en el mismo equipo
2. Si necesitas configuración manual:
   - Ir a **Settings** → **Connections**
   - Configurar **Ollama API URL**: `http://localhost:11434`
   - Hacer clic en **Verify connection**
3. **Los modelos aparecerán automáticamente** en la interfaz

#### Ventaja de Pinokio + Ollama:
- **Detección automática**: Open WebUI encuentra Ollama sin configuración
- **Misma máquina**: No necesitas configurar direcciones IP ni puertos externos
- **Plug & Play**: Descargas un modelo en Ollama y aparece inmediatamente en Open WebUI

### Configuración con LM Studio:

#### **Paso 1: Iniciar LM Studio**
```bash
# Asegurarse de que LM Studio está ejecutándose
# 1. Abrir LM Studio
# 2. Cargar un modelo
# 3. Iniciar el servidor local (botón "Start Server")
# 4. El servidor normalmente se ejecuta en puerto 1234
```

#### **Paso 2: Conectar Open WebUI a LM Studio**
1. **Abrir Open WebUI** en tu navegador
2. **Ir a configuración de administrador**:
   - Hacer clic en tu avatar/perfil (esquina superior derecha)
   - Seleccionar **"Admin Settings"** o **"Configuración de Admin"**
3. **Configurar la conexión**:
   - Ir a la sección **"Connections"** o **"Conexiones"**
   - Hacer clic en **"Add Connection"** o **"Añadir Conexión"**
   - **URL del servidor**: `http://192.168.1.81:1234/v1`
     - ⚠️ **Importante**: Reemplaza `192.168.1.81` por la IP de tu máquina
     - ⚠️ **Importante**: Añadir `/v1` al final de la URL
   - **API Key**: Dejar vacío o poner cualquier texto (no se valida)
4. **Verificar la conexión**:
   - Hacer clic en **"Test Connection"** o **"Probar Conexión"**
   - Debería mostrar ✅ **"Connection successful"**

#### **Paso 3: Usar los modelos de LM Studio**
1. **Los modelos aparecerán automáticamente** en el selector de modelos de Open WebUI
2. **Crear un nuevo chat** y seleccionar el modelo de LM Studio
3. **¡Listo!** Ahora puedes usar Open WebUI con los modelos de LM Studio

#### **Ventajas de Open WebUI + LM Studio:**
- ✅ **Interfaz mejorada**: Open WebUI es más rica que la interfaz nativa de LM Studio
- ✅ **Workspaces**: Crear espacios especializados usando modelos de LM Studio
- ✅ **Historial avanzado**: Mejor gestión de conversaciones
- ✅ **Colaboración**: Compartir chats y configuraciones
- ✅ **Flexibilidad**: Cambiar entre modelos de LM Studio fácilmente

#### **Configuración dual (Ollama + LM Studio):**
**Puedes tener ambos conectados simultáneamente:**
1. **Ollama**: Detectado automáticamente en `http://localhost:11434`
2. **LM Studio**: Configurado manualmente en `http://192.168.1.81:1234/v1`
3. **Resultado**: Todos los modelos de ambas herramientas disponibles en un solo lugar

**Esto te permite**:
- Usar modelos específicos de cada herramienta según la tarea
- Comparar rendimiento entre las mismas configuraciones
- Tener un punto de acceso unificado para todos tus LLMs locales

### Ventajas vs otros métodos:

| Aspecto | Open WebUI | Ollama CLI | LM Studio |
|---------|------------|------------|-----------|
| **Facilidad de uso** | ✅ Interfaz web familiar | ⚠️ Requiere comandos | ✅ App nativa |
| **Workspaces** | ✅ Múltiples espacios | ❌ No disponible | ⚠️ Limitado |
| **Historial** | ✅ Persistente y organizado | ❌ No persistente | ✅ Básico |
| **Colaboración** | ✅ Compartir y exportar | ❌ Solo local | ⚠️ Limitado |
| **Personalización** | ✅ System prompts por workspace | ✅ Modelfiles | ⚠️ Básica |
| **Acceso remoto** | ✅ Desde cualquier dispositivo | ❌ Solo local | ❌ Solo local |

### Casos de uso ideales:

1. **Trabajo diario**: Asistente personal para tareas cotidianas
2. **Investigación**: Analizar documentos y extraer información
3. **Brainstorming**: Sesiones creativas con diferentes personalidades
4. **Soporte técnico**: Resolver dudas técnicas de forma conversacional
5. **Educación**: Tutor personalizado para aprender nuevos temas

### Tips y mejores prácticas:

1. **Usa workspaces específicos** para diferentes tipos de trabajo
2. **Personaliza system prompts** según tus necesidades exactas
3. **Organiza conversaciones** con carpetas y etiquetas
4. **Experimenta con diferentes modelos** para cada tipo de tarea
5. **Exporta conversaciones importantes** como referencia futura

**Open WebUI transforma la experiencia de usar LLMs locales**, pasando de comandos técnicos a una interfaz intuitiva que puedes usar durante todo el día para cualquier tarea que requiera asistencia de IA.

## 5. Casos de Uso Prácticos

### 5.1. Usar LLMs locales con Cursor

Una de las preguntas más frecuentes es cómo integrar un LLM local con **Cursor**, el editor de código con IA.

#### El problema:
Cursor no permite conexiones directas a servicios en tu red local por razones de seguridad.

#### La solución: Ngrok
**Ngrok** es un servicio que crea túneles seguros desde internet hacia tu máquina local. Es **gratuito** para uso básico.

#### Pasos para configurar Cursor con LM Studio:

##### 1. **Instalar Ngrok**
- Descargar desde: https://ngrok.com/
- Crear cuenta gratuita
- Instalar según tu sistema operativo

##### 2. **Iniciar LM Studio**
- Abrir LM Studio
- Cargar el modelo que quieres usar
- Iniciar el servidor local (normalmente en puerto 1234)

##### 3. **Crear el túnel con Ngrok**
```bash
# Reemplaza la IP por la de tu máquina local
ngrok http http://192.168.1.81:1234
```

Esto te dará una URL pública, por ejemplo:
```
https://371391b6cf3a.ngrok-free.app
```

##### 4. **Configurar Cursor**
1. Abrir **Cursor Settings** → **Models**
2. Abajo, en la sección OpenAI, **sobreescribir la URL base**:
   ```
   https://371391b6cf3a.ngrok-free.app/v1
   ```
   ⚠️ **Importante**: Añadir `/v1` al final

3. En **API Key**: Poner cualquier texto (requerido pero no se valida)
4. Hacer clic en **Verify** para comprobar la conexión

##### 5. **Añadir el modelo**
1. En la sección **Models**, añadir el nombre exacto del modelo:
   ```
   Devstral-Small-2507-GGUF/Devstral-Small-2507-Q6_K.gguf
   ```
2. Guardar la configuración

##### 6. **Usar el modelo**
- Abrir el chat de Cursor
- Seleccionar tu modelo local de la lista
- ¡Empezar a programar con tu LLM local!

#### Ventajas de esta configuración:
- **Privacidad**: Aunque uses Ngrok, el procesamiento sigue siendo local
- **Sin límites**: No hay restricciones de uso
- **Personalización**: Usar modelos específicos para programación
- **Sin costes**: No pagas por tokens

#### Consideraciones:
- **Ngrok gratuito**: Tiene límites de sesiones simultáneas
- **Velocidad**: Depende de tu hardware local
- **Estabilidad**: El túnel puede desconectarse ocasionalmente

### 5.2. Extensiones de VS Code para Desarrollo con LLMs Locales

Además de Cursor, existen **varias extensiones populares** de Visual Studio Code que permiten integrar LLMs locales directamente en tu flujo de desarrollo. Vamos a ver tres de ellas:

#### **Continue** - Asistente AI Personalizable

**Continue** es una extensión open-source altamente personalizable que te permite crear asistentes de código AI completamente customizados.

**Características principales:**
- **4 modos de funcionamiento**:
  - **Agent**: Para cambios sustanciales en la base de código
  - **Chat**: Conversación con el LLM sin salir del IDE
  - **Autocomplete**: Sugerencias inline mientras escribes
  - **Edit**: Modificar código sin cambiar de archivo

- **Compatible con LLMs locales**: Ollama, LM Studio y cualquier API OpenAI-compatible
- **Hub de componentes**: Modelos, reglas, prompts y herramientas reutilizables
- **Integración profunda**: Acceso al codebase, documentación y contexto

**Instalación**: 
```bash
# Desde VS Code Marketplace
ext install Continue.continue
```

#### **Cline** - Agente Autónomo de Desarrollo

**Cline** (pronunciado "Klein") es un agente de desarrollo autónomo que puede realizar tareas complejas paso a paso con tu supervisión.

**Capacidades avanzadas:**
- **Ejecución de comandos**: Ejecuta comandos en terminal y lee la salida
- **Navegador integrado**: Puede abrir páginas web, hacer clicks y capturas
- **Edición de archivos**: Crea y modifica archivos con vista diff
- **Herramientas extensibles**: Protocolo MCP para crear herramientas personalizadas
- **Control total**: Apruebas cada acción antes de ejecutarse

**Casos de uso especiales:**
- Testing end-to-end automatizado
- Debugging visual de aplicaciones web
- Instalación y configuración de dependencias
- Deploy y gestión de aplicaciones

**Instalación**:
```bash
# Desde VS Code Marketplace  
ext install saoudrizwan.claude-dev
```

#### **Roo Code** - Equipo Completo de Agentes AI

**Roo Code** (anteriormente Roo Cline) es un fork especializado de Cline que ofrece múltiples "personalidades" de desarrollo.

**Modos especializados:**
- **Code Mode**: Desarrollo general
- **Architect Mode**: Planificación y arquitectura técnica  
- **Ask Mode**: Responder preguntas sobre el código
- **Debug Mode**: Diagnóstico sistemático de problemas
- **Modos personalizados**: Security auditing, performance optimization, documentación

**Funcionalidades únicas:**
- **Indexación de codebase**: Comprensión completa del proyecto
- **Lista de TODO integrada**: Gestión de tareas
- **Auto-approval**: Flujos de trabajo más rápidos
- **Instrucciones personalizadas**: Comportamiento adaptado a tu estilo

**Instalación**:
```bash
# Desde VS Code Marketplace
ext install RooVeterinaryInc.roo-cline
```

#### Comparación rápida:

| Extensión | Enfoque | Mejor para | Complejidad |
|-----------|---------|------------|-------------|
| **Continue** | Personalización | Crear asistentes únicos | Media |
| **Cline** | Autonomía supervisada | Tareas complejas paso a paso | Alta |
| **Roo Code** | Especialización por roles | Equipos y workflows específicos | Alta |

#### Configuración para LLMs locales:

**Todas las extensiones soportan**:
- **Ollama**: Conexión directa a `http://localhost:11434`
- **LM Studio**: Conexión al servidor local (puerto 1234)
- **APIs personalizadas**: Cualquier endpoint compatible con OpenAI

**Ejemplo de configuración básica**:
```json
{
  "model": "Devstral-Small-2507-GGUF/Devstral-Small-2507-Q6_K.gguf",
  "apiBase": "http://localhost:11434/v1",
  "apiKey": "placeholder"
}
```

**Ventajas vs Cursor + Ngrok**:
- ✅ **Sin túneles**: Conexión directa local
- ✅ **Sin dependencias externas**: No necesitas Ngrok
- ✅ **Más integrado**: Funcionalidades nativas de VS Code
- ✅ **Gratuito**: Sin limitaciones de sesiones

Estas extensiones transforman VS Code en un potente entorno de desarrollo asistido por IA, manteniendo todo el procesamiento completamente local.

### Recomendación personal: Roo Code

**Personalmente, mi favorita es Roo Code** por varias razones que la hacen especialmente potente:

#### **Marketplace de Modos y MCPs**
- **Marketplace integrado**: Acceso a modos y herramientas MCP creados por la comunidad
- **Modos personalizados**: Puedes crear tus propios modos especializados para cualquier tarea
- **Extensibilidad**: Fácil distribución e instalación de nuevas capacidades

#### **Indexación Avanzada de Código**
Una de las características más impresionantes es la **indexación semántica del codebase**:

**Configuración con Ollama + Qdrant:**
```bash
# 1. Instalar Qdrant (base de datos vectorial)
docker run -p 6333:6333 qdrant/qdrant

# 2. Configurar modelo de embeddings en Ollama
ollama pull nomic-embed-text
```

**Configuración en Roo Code:**
```json
{
  "codebaseIndexing": {
    "enabled": true,
    "embeddingModel": "nomic-embed-text",
    "vectorDatabase": {
      "type": "qdrant",
      "url": "http://localhost:6333"
    },
    "chunkSize": 512,
    "overlapSize": 50
  }
}
```

**Ventajas de la indexación:**
- **Comprensión contextual**: El modelo entiende mejor la arquitectura del proyecto
- **Búsqueda semántica**: Encuentra código relacionado conceptualmente
- **Respuestas más precisas**: Mejores sugerencias basadas en el contexto completo
- **Proyectos grandes**: Funciona bien con codebases de cientos de archivos

#### **Configuración paso a paso de indexación:**

1. **Preparar la infraestructura**:
   ```bash
   # Iniciar Qdrant
   docker run -d -p 6333:6333 --name qdrant qdrant/qdrant
   
   # Descargar modelo de embeddings
   ollama pull nomic-embed-text
   ```

2. **Configurar Roo Code**:
   - Abrir configuración de la extensión
   - Habilitar "Codebase Indexing"
   - Configurar endpoint de Qdrant y modelo de embeddings

3. **Indexar el proyecto**:
   - Roo Code escaneará automáticamente tu workspace
   - Creará embeddings de funciones, clases y módulos
   - Almacenará los vectores en Qdrant

4. **Beneficios inmediatos**:
   - Respuestas más contextuales
   - Mejor comprensión de dependencias
   - Sugerencias de refactoring más inteligentes

#### **¿Por qué Roo Code es mi favorita?**
- **Ecosistema completo**: Modos + MCPs + indexación
- **Configuración avanzada**: Máximo control sobre el comportamiento
- **Rendimiento superior**: La indexación marca una diferencia notable
- **Comunidad activa**: Constante desarrollo de nuevos modos y herramientas

**Nota**: La configuración de indexación requiere algo más de setup inicial, pero el **rendimiento extra que proporciona** vale completamente la pena, especialmente en proyectos grandes y complejos.

## 6. DeerFlow - Sistema de Investigación Avanzada de ByteDance

### ¿Qué es DeerFlow?

**DeerFlow** es un sistema experimental de investigación desarrollado por **ByteDance** para análisis profundo y razonamiento avanzado. Aunque no es una herramienta pública como Ollama o LM Studio, representa el tipo de innovación que están desarrollando las grandes empresas tecnológicas para casos de uso especializados.

### Características principales:

- **Investigación profunda**: Especializado en análisis exhaustivos y razonamiento complejo
- **Integración con Qwen**: Funciona especialmente bien con los modelos Qwen3 de Alibaba Cloud
- **Sistema experimental**: Representa tecnología de vanguardia en desarrollo
- **Compatibilidad con Ollama**: Se puede configurar para trabajar con tu stack local

### ¿Por qué Qwen3 con DeerFlow?

**Qwen3** es uno de los modelos más avanzados disponibles actualmente:

#### **Capacidades de Qwen3:**
- **Modelo base robusto**: Hasta 235B parámetros en las versiones más grandes
- **Multilingüe**: Excelente rendimiento en español, inglés, chino y otros idiomas
- **Razonamiento avanzado**: Especialmente fuerte en tareas de análisis y lógica
- **Código especializado**: Qwen3-Coder para programación
- **Modelos de embeddings**: Qwen3-Embedding para búsqueda semántica

#### **Beneficios del stack local:**
- **Privacidad total**: Investigación sensible permanece local
- **Sin límites**: Análisis extensos sin restricciones de tokens
- **Personalización**: Control total sobre el comportamiento del modelo
- **Disponibilidad**: 24/7 sin depender de servicios externos

**La lección clave**: No necesitas esperar a las herramientas comerciales. Con las herramientas opensource disponibles hoy (Ollama, Qwen3, Open WebUI, etc.), puedes crear sistemas de investigación potentes y personalizados que rivalizan con soluciones corporativas.

**Para el futuro**: Este tipo de sistemas experimentales eventualmente se convertirán en productos disponibles. Mientras tanto, dominar el stack local te da ventaja competitiva y te prepara para integrar estas tecnologías cuando estén disponibles.

## 7. Recursos Adicionales

### Herramientas principales:
- [Documentación oficial de Ollama](https://ollama.ai/docs)
- [Lista de modelos disponibles en Ollama](https://ollama.ai/library)
- [LM Studio oficial](https://lmstudio.ai/)
- [Pinokio - App store para herramientas de IA](https://pinokio.computer/)

### Modelos y ecosistema:
- [Hugging Face - Modelos GGUF](https://huggingface.co/models?library=gguf)
- [Qwen - Página oficial](https://qwenlm.github.io/)
- [Qwen en Hugging Face](https://huggingface.co/Qwen)
- [Qwen en GitHub](https://github.com/QwenLM)
- [Chat oficial de Qwen](https://chat.qwen.ai/)

### Extensiones de desarrollo:
- [Continue - VS Code Extension](https://marketplace.visualstudio.com/items?itemName=Continue.continue)
- [Cline - VS Code Extension](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev)
- [Roo Code - VS Code Extension](https://marketplace.visualstudio.com/items?itemName=RooVeterinaryInc.roo-cline)

### Herramientas adicionales:
- [Ngrok - Túneles seguros](https://ngrok.com/)
- [Cursor - Editor con IA](https://cursor.sh/)
- [Open WebUI - Interfaz de chat](https://github.com/open-webui/open-webui)

---

*Clase: LLMs en Local - Fecha: 23 de julio de 2025*
