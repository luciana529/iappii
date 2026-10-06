# iappii

Script en Python que se conecta a la API de **Google Gemini** para generar contenido a partir de un prompt de texto.

> Este repositorio es un fork de [HectorDeSosa/iappii](https://github.com/HectorDeSosa/iappii).

## Contenido del proyecto

| Archivo | Descripción |
|---|---|
| `gemini.py` | Script principal: envía un prompt a Gemini e imprime la respuesta |
| `requirements.txt` | Dependencias de Python |
| `referencias.txt` | Referencias del proyecto |
| `.env` | Tu clave de API (local, **no se sube a GitHub**) |

## Requisitos

- Python 3.9 o superior
- Una API key de Google Gemini (gratis en [Google AI Studio](https://aistudio.google.com/apikey))

## Instalación

1. Cloná el repositorio:

   ```bash
   git clone https://github.com/luciana529/iappii.git
   cd iappii
   ```

2. Creá y activá un entorno virtual:

   ```powershell
   # Windows (PowerShell)
   python -m venv venv
   venv\Scripts\activate
   ```

   ```bash
   # Mac / Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Instalá las dependencias:

   ```bash
   pip install -r requirements.txt
   ```

## Configuración de la API key

Creá un archivo `.env` en la raíz del proyecto, junto a `gemini.py`, con este contenido:

```
GOOGLE_API_KEY=tu_clave_aca
```

> **Importante:** el archivo `.env` está en el `.gitignore` y no debe subirse nunca al repositorio. Si por error se publica la clave, eliminala desde Google AI Studio y generá una nueva.

## Uso

```bash
python gemini.py
```

Para cambiar la pregunta, editá el parámetro `contents` en `gemini.py`:

```python
response = client.models.generate_content(
    model="gemini-3.6-flash",
    contents="Explicá qué es una computadora"
)
print(response.text)
```

Para ver qué modelos tiene disponibles tu clave:

```python
for m in client.models.list():
    print(m.name)
```

## Errores comunes

| Error | Causa probable | Solución |
|---|---|---|
| `ModuleNotFoundError` | Faltan dependencias | Ejecutá `pip install -r requirements.txt` con el entorno virtual activo |
| `No API key was provided` | El `.env` no existe, está en otra carpeta o está vacío | Revisá que esté junto a `gemini.py` y tenga la clave |
| `404` / model not found | El nombre del modelo no existe | Listá los modelos disponibles y elegí uno |
| `429` / quota exceeded | Se alcanzó el límite del nivel gratuito | Esperá unos minutos y reintentá |

## Mantener el fork actualizado

Para traer los cambios del repositorio original:

```bash
git remote add upstream https://github.com/HectorDeSosa/iappii.git
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

## Autoría

- Proyecto original: [HectorDeSosa](https://github.com/HectorDeSosa)
- Fork mantenido por: [luciana529](https://github.com/luciana529)