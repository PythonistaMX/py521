# IA Generativa en Entornos Locales · Demos (Py521)

[![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-CC--BY%204.0-blue.svg?style=for-the-badge)](LICENSE)
[![Ollama](https://img.shields.io/badge/Motor-Ollama-000000?style=for-the-badge)](https://ollama.com/)
[![API](https://img.shields.io/badge/API-compatible%20con%20OpenAI-412991?style=for-the-badge)](https://docs.ollama.com/api/openai-compatibility)

© Pythonista · Licencia CC BY 4.0 — https://creativecommons.org/licenses/by/4.0/deed.es

Este repositorio contiene los *notebooks* de demostración del curso **Py521 · IA Generativa en Entornos Locales** de **Pythonista®**, impartido por José Luis Chiquete. Cada demo ejecuta un modelo en el propio equipo y muestra un concepto del curso con datos reales: temperatura y razonamiento, comprobación de un modelo local, cuantización y ventana de contexto, RAG con fuente citada y acceso al servicio desde la red local.

Las demos usan la **API compatible con *OpenAI***, así que funcionan con *Ollama* (por omisión), *LM Studio*, *llama.cpp server* o *vLLM* cambiando solo la URL y el modelo.

---

## 🎬 Acerca de las demos

* En clase, quien imparte el curso ejecuta las demos en vivo. Este repositorio sirve para repetirlas después en tu equipo, a tu ritmo.
* Para repetirlas necesitas instalar tres programas: [*Python*](https://www.python.org/downloads/) 3.10 o posterior, [*Git*](https://git-scm.com/downloads) y [*Ollama*](https://ollama.com/download). Los pasos están en la sección «Requisitos e instalación».
* Duración aproximada de cada demo, con los modelos ya descargados:

| *Notebook* | Duración aproximada |
|---|---|
| `00` Preliminares | 15 min (preparación, antes de la primera demo) |
| `01` Temperatura y razonamiento | 15 min |
| `02` Ejecutar y comprobar un modelo local | 20 min |
| `03` Cuantización y ventana de contexto | 15 min |
| `04` RAG local con fuente citada | 20 min |
| `05` API en la red local y control de acceso | 20 min |

Sin GPU, algunas celdas tardan uno o dos minutos en responder.

---

## 📚 Contenidos

#### 🧭 Tabla de contenidos (enlaces rápidos)
- [00_preliminares_entorno_y_secretos.ipynb](00_preliminares_entorno_y_secretos.ipynb)
- [01_temperatura_y_modo_de_razonamiento.ipynb](01_temperatura_y_modo_de_razonamiento.ipynb)
- [02_ejecutar_y_comprobar_un_modelo_local.ipynb](02_ejecutar_y_comprobar_un_modelo_local.ipynb)
- [03_cuantizacion_y_ventana_de_contexto.ipynb](03_cuantizacion_y_ventana_de_contexto.ipynb)
- [04_rag_local_con_fuente_citada.ipynb](04_rag_local_con_fuente_citada.ipynb)
- [05_api_en_la_red_local_y_control_de_acceso.ipynb](05_api_en_la_red_local_y_control_de_acceso.ipynb)

#### 🔹 Preliminares
* `00` - Comprobación del entorno (*Python*, *Jupyter*, dependencias y servicio de modelos), variables de configuración, secretos (variables de entorno, `.env`, qué hacer si uno se filtra) y obtención de credenciales.

#### 🔹 Demos
* `01` - **Tema 2.** Temperatura baja frente a alta y modo de razonamiento desactivado frente a activado: cuánto varían las respuestas, cuánto tardan y cómo el razonamiento consume la longitud máxima.
* `02` - **Tema 4.** Ejecutar y comprobar un modelo local con cuatro señales: memoria usada, tiempo al primer token, tokens por segundo y ejecución local (sin etiqueta de nube y con respuesta sin internet). *LM Studio* como alternativa.
* `03` - **Tema 4.** El mismo modelo en dos cuantizaciones (4 y 8 bits) y con dos ventanas de contexto: memoria, tiempo al primer token y tokens por segundo, con gráficas.
* `04` - **Tema 5.** RAG local con tres documentos ficticios de `data/`: respuesta con fuente citada, un fallo de recuperación por pregunta ambigua y cómo detectarlo.
* `05` - **Tema 8.** Consultar el modelo desde otra aplicación por la API HTTP; quién puede acceder y cómo limitarlo con la dirección de escucha, un proxy con clave y el cortafuegos.

> **📝 Nota:** cada *notebook* es independiente y empieza con la misma celda de configuración. Las funciones que solo existen en *Ollama* están marcadas con 🦙; con otro motor muestran un aviso y el equivalente.

#### 📁 Datos (`data/`)
Tres documentos **ficticios** de una organización de ejemplo, «Taller Norte», para la demo `04`:
* `politica_de_teletrabajo.md`
* `guia_de_soporte_tecnico.md`
* `procedimiento_de_reembolso_de_gastos.md`

---

## 🛠️ Requisitos e instalación

### Requisitos

| Componente | Versión o capacidad |
|---|---|
| *Python* | 3.10 o posterior |
| *Jupyter* | *JupyterLab* o VS Code con la extensión de *Jupyter* |
| [*Git*](https://git-scm.com/downloads) | Cualquier versión reciente, para clonar el repositorio |
| Motor de modelos | [*Ollama*](https://ollama.com/download) (probado con 0.40.16) u otro con API compatible con *OpenAI* |
| Memoria libre | 4 GB de RAM, VRAM o memoria unificada (8 GB recomendados) |
| Disco | Unos 6 GB para los modelos |

Las demos funcionan sin GPU, solo con el procesador; con GPU o memoria unificada responden más rápido.

### Modelos

Etiquetas verificadas en [ollama.com/library](https://ollama.com/library) el 9-nov-2026:

```bash
ollama pull qwen3:1.7b              # chat (demos 01, 02, 04, 05)
ollama pull qwen3:1.7b-q4_K_M       # versión Q4 de la demo 03 (mismos pesos que qwen3:1.7b: no se descargan otra vez)
ollama pull qwen3:1.7b-q8_0         # versión Q8 de la demo 03
ollama pull qwen3-embedding:0.6b    # embeddings de la demo 04
```

| Modelo | Descarga | Memoria medida al cargarlo* | Licencia |
|---|---|---|---|
| [`qwen3:1.7b`](https://ollama.com/library/qwen3) y `qwen3:1.7b-q4_K_M` | 1,4 GB | 1,9 GB con ventana de 4096 tokens · 3,4 GB con 16384 | Apache 2.0 |
| [`qwen3:1.7b-q8_0`](https://ollama.com/library/qwen3/tags) | 2,2 GB | 3,0 GB con ventana de 4096 tokens | Apache 2.0 |
| [`qwen3-embedding:0.6b`](https://ollama.com/library/qwen3-embedding) | 0,6 GB | menos de 1 GB | Apache 2.0 |

\* Medido con `/api/ps` de *Ollama* 0.40.16 en un equipo sin GPU; varía con el equipo y la versión.

`qwen3:1.7b` y `qwen3:1.7b-q4_K_M` comparten los mismos pesos: el segundo `pull` no vuelve a descargarlos, pero hace falta para que exista ese nombre, que usa la demo `03`. Para equipos con 8 GB libres o más, una alternativa más reciente es [`gemma4:e2b`](https://ollama.com/library/gemma4) (4,6–7,5 GB, con modo de razonamiento; licencia Apache 2.0), con `gemma4:e2b-it-q4_K_M` y `gemma4:e2b-it-q8_0` para la demo 03. Se elige con las variables de la tabla siguiente.

### Opción A · Instalación local

```bash
git clone https://github.com/PythonistaMX/py521.git
cd py521
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env      # opcional; en Windows: copy .env.example .env
jupyter lab
```

Abre `00_preliminares_entorno_y_secretos.ipynb` y ejecuta las celdas en orden con `Shift + Enter`. Los *notebooks* usan `http://localhost:11434/v1`, la dirección predeterminada de *Ollama*; no hay que configurar nada más.

Comprobación: ejecuta la sección 1.8 de `00` (comprobación del servicio). Debe mostrar «Servicio en …: responde ✅» y ✅ en cada modelo.

### Opción B · Contenedor de desarrollo (VS Code)

La carpeta `.devcontainer/` crea un contenedor con *Python* 3.12, *Jupyter* y `requirements.txt` (imagen oficial `mcr.microsoft.com/devcontainers/python`). Requiere *Docker* y la extensión *Dev Containers*: **Dev Containers: Reopen in Container**.

*Ollama* queda **fuera del contenedor**, instalado en el equipo: el acceso a la GPU desde un contenedor depende del fabricante y, en Mac, *Docker* no usa la GPU. Dentro del contenedor, `LLM_DEFAULT_BASE_URL=http://host.docker.internal:11434/v1` apunta al equipo anfitrión: es el valor que toma `LLM_BASE_URL` si no la defines tú (en `.env` o como variable de entorno).

* **Windows y macOS (*Docker Desktop*):** *Docker Desktop* resuelve `host.docker.internal` hacia el anfitrión ([documentación](https://docs.docker.com/desktop/features/networking/networking-how-tos/)).
* **Linux (*Docker Engine*):** el contenedor se crea con `--add-host=host.docker.internal:host-gateway`, que apunta a la IP del puente de *Docker* (por lo general `172.17.0.1`) ([documentación](https://docs.docker.com/reference/cli/docker/container/run/#add-host)). *Ollama* escucha por omisión solo en `127.0.0.1`, así que no responde desde el contenedor. La opción segura es que escuche **solo en la IP del puente**, que no es visible desde la red local: `OLLAMA_HOST=172.17.0.1:11434` en el servicio (compruébala con `ip -4 addr show docker0`).
* ⚠️ **No uses `OLLAMA_HOST=0.0.0.0`** para resolverlo: la API de *Ollama* no pide clave y quedaría abierta a toda la red. Si otros equipos necesitan el modelo, usa el proxy con clave y el cortafuegos de la demo `05`.

### *GitHub Codespaces*

> **Si no programas:** en *Codespaces* solo puedes leer los *notebooks*; para ejecutar las demos, usa la Opción A.

[*GitHub Codespaces*](https://docs.github.com/es/codespaces/about-codespaces/what-are-codespaces) ejecuta el contenedor de desarrollo **en la nube**, en una máquina de *GitHub* (por omisión, la más pequeña: 2 núcleos, 8 GB de RAM y sin GPU), no en tu equipo. No se instala *Ollama* en el codespace: el modelo correría en la nube, sin GPU y despacio, y las demos tratan de ejecutarlo en tu equipo.

**Abrir y cerrar un codespace:**

1. En la página del repositorio: **Code → Codespaces → Create codespace on main** ([guía](https://docs.github.com/es/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository)).
2. Al terminar, en <https://github.com/codespaces>, menú **⋯** del codespace → **Stop codespace** ([guía](https://docs.github.com/es/codespaces/developing-in-a-codespace/stopping-and-starting-a-codespace)).
3. Si ya no lo vas a usar, en el mismo menú → **Delete** ([guía](https://docs.github.com/es/codespaces/developing-in-a-codespace/deleting-a-codespace)).

**Cuota:** las cuentas personales incluyen cada mes una cuota gratuita de horas de uso (horas de núcleo) y de almacenamiento. Un codespace encendido consume horas aunque no lo uses, y uno detenido sigue ocupando almacenamiento hasta que lo borras. Sin un método de pago registrado, el uso se bloquea al agotar la cuota. Los precios se publican en dólares estadounidenses y el cargo final depende de tu país y tus impuestos: consulta la [facturación de *Codespaces*](https://docs.github.com/es/billing/concepts/product-billing/github-codespaces).

**Qué funciona:**

* **No llega al *Ollama* de tu equipo:** ahí `host.docker.internal` no apunta a tu computadora, y en el codespace no hay *Ollama* ni GPU.
* **Para ejecutar las demos ahí** hace falta un servicio propio expuesto con clave y HTTPS. Con esta opción el modelo no corre en tu equipo: no se cumple la ejecución local que comprueba la demo `02`.

| Demo | En *Codespaces* con un servicio propio |
|---|---|
| `00` | Completa (comprueba el servicio de `LLM_BASE_URL`) |
| `01` | Completa |
| `02` | Sin la memoria ni la etiqueta de nube (🦙) ni la prueba sin internet |
| `03` | Solo la comparación de la sección 1, sin la memoria (🦙); la sección 2 muestra un aviso |
| `04` | Completa |
| `05` | No aplica: trata del acceso a un servicio en tu propia red |

**Configurar el servicio propio:**

1. Crea dos [secretos de *Codespaces*](https://docs.github.com/es/codespaces/managing-your-codespaces/managing-your-account-specific-secrets-for-github-codespaces) con acceso a este repositorio: `LLM_BASE_URL` (por ejemplo, `https://<tu-servicio>/v1`) y `LLM_API_KEY`. El contenedor los recomienda al crear el codespace con **New with options**. Nunca los escribas en el repositorio.
2. Si creas o cambias un secreto con el codespace encendido, detenlo y vuelve a iniciarlo para que lo reciba.
3. Ejecuta la celda de configuración común: `LLM_BASE_URL` debe mostrar tu servicio y `LLM_API_KEY`, «definida».
4. Si muestra `http://host.docker.internal:11434/v1`, el secreto no llegó al *notebook*: revisa que el secreto tenga acceso a este repositorio y reinicia el codespace. Como alternativa, crea un archivo `.env` en el codespace con esas dos variables (`.env` no se sube al repositorio) y reinicia el *kernel*.

* ⚠️ **No expongas *Ollama* sin protección:** su API no pide clave. Delante debe haber un proxy con clave y HTTPS; el proxy de la demo `05` es didáctico y no tiene HTTPS.
* **Las funciones 🦙 específicas de *Ollama* no funcionan a través del proxy**, que solo deja pasar la API compatible con *OpenAI*; esas mediciones muestran un aviso.

---

## ⚙️ Variables de configuración

Todo se configura con variables de entorno o con el archivo `.env` (plantilla comentada en `.env.example`). Las variables del sistema tienen prioridad sobre `.env`. Los secretos solo se muestran como «definida / no definida».

| Variable | Para qué sirve | Valor por omisión | Ejemplo |
|---|---|---|---|
| `LLM_BASE_URL` | URL base de la API compatible con *OpenAI* | `http://localhost:11434/v1` | `http://localhost:1234/v1` |
| `LLM_API_KEY` | Clave que se envía al servicio, si la pide (**secreto**) | sin valor | la clave del proxy de la demo `05` |
| `LLM_MODEL` | Modelo de chat | `qwen3:1.7b` | `gemma4:e2b` |
| `LLM_EMBED_MODEL` | Modelo de *embeddings* (demo `04`) | `qwen3-embedding:0.6b` | `embeddinggemma:300m` |
| `LLM_MODEL_A` · `LLM_MODEL_B` | Las dos versiones que compara la demo `03` | `qwen3:1.7b-q4_K_M` · `qwen3:1.7b-q8_0` | `gemma4:e2b-it-q4_K_M` · `gemma4:e2b-it-q8_0` |
| `LLM_CONTEXT_A` · `LLM_CONTEXT_B` | Las dos ventanas de contexto de la demo `03` (tokens) | `4096` · `16384` | `8192` · `32768` |
| `RAG_DOCS_DIR` | Carpeta de documentos del RAG (demo `04`) | `data` | `/ruta/a/mis_documentos` |
| `LLM_PROXY_KEY` | Clave que exige el proxy de la demo `05` (**secreto**) | sin valor (la demo genera una temporal) | creada con el *notebook* `00` |
| `LLM_PROXY_HOST` · `LLM_PROXY_PORT` | Dirección y puerto de escucha del proxy de la demo `05` | `127.0.0.1` · `8800` | `192.168.1.10` · `8800` |
| `LLM_DEFAULT_BASE_URL` | Valor de `LLM_BASE_URL` cuando esta no está definida; lo fija el contenedor de desarrollo | sin valor | `http://host.docker.internal:11434/v1` |
| `OLLAMA_HOST` | API nativa de *Ollama* para las funciones 🦙 (la misma variable que lee el [cliente oficial de *Python*](https://github.com/ollama/ollama-python)) | se deriva de `LLM_BASE_URL` sin `/v1` | `http://host.docker.internal:11434` |
| `HF_TOKEN` | *Token* de *Hugging Face* (**secreto**; las demos no lo usan) | sin valor | ver el *notebook* `00` |

> ⚠️ En el equipo anfitrión, `OLLAMA_HOST` también decide **dónde escucha** el servicio de *Ollama*. Defínela para los *notebooks* (o en `.env`), no en el servicio, salvo el caso del puente de *Docker* descrito arriba.

### Motores compatibles

| Motor | `LLM_BASE_URL` por omisión | Endpoints que usan las demos |
|---|---|---|
| [*Ollama*](https://docs.ollama.com/api/openai-compatibility) | `http://localhost:11434/v1` | `GET /models`, `POST /chat/completions`, `POST /embeddings` |
| [*LM Studio*](https://lmstudio.ai/docs/developer/openai-compat) | `http://localhost:1234/v1` | `GET /models`, `POST /chat/completions`, `POST /embeddings` |
| [*llama.cpp server*](https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md) | `http://localhost:9931/v1` (puerto por omisión actual de `llama-server`; se cambia con `--port`) | `GET /v1/models`, `POST /v1/chat/completions`, `POST /v1/embeddings` (con un modelo de *embeddings* y `--embeddings`) |
| [*vLLM*](https://docs.vllm.ai/en/latest/serving/online_serving/openai_compatible_server.html) | `http://localhost:8000/v1` | `GET /v1/models`, `POST /v1/chat/completions`, `POST /v1/embeddings` (con un modelo de *embeddings*) |

*llama.cpp server* y *vLLM* sirven un modelo por proceso: para la demo `04` hace falta un segundo servidor con el modelo de *embeddings*, o un motor que sirva los dos. El modo de razonamiento se pide como `reasoning_effort` y como `chat_template_kwargs.enable_thinking`; cada motor usa el que reconoce.

---

## 🔒 Seguridad

* Ningún secreto va en un *notebook* ni en el repositorio: se guardan en variables de entorno o en `.env`, que está en `.gitignore`.
* Los servicios locales escuchan en `127.0.0.1`. Abrirlos a la red local requiere proxy con clave y cortafuegos (demo `05`).
* Si un secreto se filtra: revocarlo, rotarlo y después limpiarlo del historial (*notebook* `00`).

---

## 📖 Recursos adicionales

* [Documentación de *Ollama*](https://docs.ollama.com/) · [Biblioteca de modelos](https://ollama.com/library)
* [Documentación de *LM Studio*](https://lmstudio.ai/docs/developer)
* [*llama.cpp server*](https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md)
* [Servidor compatible con *OpenAI* de *vLLM*](https://docs.vllm.ai/en/latest/serving/online_serving/openai_compatible_server.html)
* [Referencia de `devcontainer.json`](https://containers.dev/implementors/json_reference/) · [Dev Containers en VS Code](https://code.visualstudio.com/docs/devcontainers/containers)

---

## 📝 Licencia

© Pythonista · Licencia CC BY 4.0 — https://creativecommons.org/licenses/by/4.0/deed.es

Este proyecto está bajo la licencia **Creative Commons Atribución 4.0 Internacional (CC BY 4.0)**.

**Eres libre de:**
- ✅ Compartir el material en cualquier medio o formato
- ✅ Adaptar, remezclar y crear contenido derivado
- ✅ Usar con fines comerciales

**Con la condición de:**
- 📌 **Atribución:** Debes dar crédito apropiado, proporcionar un enlace a la licencia e indicar si se han realizado cambios.

Véase el archivo [LICENSE](LICENSE) para los términos completos.

&copy; José Luis Chiquete Valdivieso. 2017-2026.
