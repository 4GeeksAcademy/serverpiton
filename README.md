# Agent Loop Basico de Inventario con IA

Proyecto compuesto por:

- API REST con FastAPI.
- Persistencia del inventario en `products.csv`.
- Agente con LLM y tool calling manual.
- Registro append-only en `conversation_log.csv`.

## Estructura

```text
.
├── api/
│   ├── __init__.py
│   └── app.py
├── agent.py
├── products.csv
├── conversation_log.csv
├── .env
├── .gitignore
├── requirements.txt
└── README.md
```

## 1) Crear y activar entorno virtual

```bash
python -m venv myenv
source myenv/bin/activate
```

En Windows:

```bash
myenv\Scripts\activate
```

## 2) Instalar dependencias

```bash
pip install -r requirements.txt
```

## 3) Variables de entorno

Crear o editar `.env` con:

```env
GROQ_API_KEY=tu_clave_aqui
GROQ_MODEL=openai/gpt-oss-20b
```

## 4) Ejecutar la API (Terminal 1)

```bash
uvicorn api.app:app --reload
```

La API queda en `http://127.0.0.1:8000` y docs en `http://127.0.0.1:8000/docs`.

## 5) Ejecutar el agente (Terminal 2)

```bash
python agent.py
```

## Endpoints

- `GET /inventory`
- `POST /inventory`
- `PATCH /inventory/{product_id}`
- `GET /inventory/alerts?threshold=10`

## Ejemplos rapidos para probar el agente

- `Que productos tenemos?`
- `Acaban de llegar 30 unidades de leche de avena`
- `Vendimos 12 bolsas de cafe arabica`
- `Que productos estan por agotarse?`
- `Agrega jarabe de caramelo, tenemos 15 botellas`

## Notas

- `products.csv` guarda el inventario de forma persistente.
- `conversation_log.csv` se crea automaticamente si no existe.
- `.env` esta ignorado por git y no debe subirse al repositorio.