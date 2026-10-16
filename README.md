# API de Inscripciones

API educativa desarrollada con FastAPI para validar y procesar inscripciones a cursos según reglas de negocio (validación de mayoría de edad y datos requeridos).

## Propósito

El backend recibe los datos de una solicitud de inscripción (nombre, edad, curso), valida la estructura y tipos de datos mediante modelos Pydantic, y responde indicando el estado de la inscripción:
- Si la persona tiene **18 años o más**, la inscripción es aceptada automáticamente.
- Si la persona tiene **menos de 18 años**, se indica que requiere autorización de una persona adulta.
- Si los datos son inconsistentes o fuera de rango (edad fuera de 0 a 120), se devuelve un error de validación HTTP 422.

---

## Requisitos previos

- Python 3.13 o superior instalado.
- Git.

---

## Creación y activación del entorno virtual

1. Clonar el repositorio y ubicarse en la raíz del proyecto:
   ```bash
   git clone https://github.com/eliann313/api-inscripciones-python.git
   cd api-inscripciones-python
   ```

2. Crear el entorno virtual:
   ```bash
   python -m venv .venv
   ```

3. Activar el entorno virtual:
   - **En Windows (PowerShell):**
     ```powershell
     .\.venv\Scripts\Activate.ps1
     ```
   - **En Linux / macOS:**
     ```bash
     source .venv/bin/activate
     ```

4. Instalar las dependencias:
   ```bash
   python -m pip install -r requirements.txt
   ```

---

## Ejecución del servidor con Uvicorn

Para iniciar el servidor de desarrollo en modo recarga automática:

```bash
python -m uvicorn app.main:app --reload
```

El servidor estará escuchando en `http://127.0.0.1:8000` (o `http://localhost:8000`).

---

## Documentación interactiva (Swagger UI)

Una vez iniciado el servidor, podés acceder a la interfaz interactiva de Swagger UI en:

👉 [http://localhost:8000/docs](http://localhost:8000/docs)

Desde Swagger UI podés explorar y probar los siguientes endpoints:
- `GET /`: Mensaje de bienvenida y verificación del servicio.
- `GET /status`: Chequeo del estado del servicio (`{"ok": true, "estado": "activo"}`).
- `POST /validar-inscripcion`: Recibe un cuerpo JSON con `nombre`, `edad` y `curso`, y devuelve el resultado de la validación.
