# Frontend — Vue + Vite

Interfaz web para realizar búsquedas inmobiliarias usando lenguaje natural.

## Tecnologías

- Vue 3
- Vite

---

## Variables de entorno

Crear archivo `.env`

```env
VITE_API_URL=http://localhost:8000
```

---

## Ejecutar con Docker

Desde la raíz del proyecto:

```bash
docker compose up --build
```

Frontend disponible en:

```text
http://localhost:5173
```

---

## Ejecutar local (opcional)

Instalar dependencias:

```bash
npm install
```

Levantar:

```bash
npm run dev
```

---

## Funcionalidades

- Búsqueda por lenguaje natural
- Comunicación con API FastAPI
- Visualización de propiedades