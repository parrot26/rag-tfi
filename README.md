# rag-tfi (README en modo borrador inicial)
Este README luego se va a modificar, ampliar y detallar sobre todos los puntos. 

## Pasos para correr el sistema RAG local sobre Docker 
Para esto es necesario contar con un servidor en lo posible linux con buena capacidad de RAM para poder acelerar los tiempos de respuesta con el Chat.

### 1. Clonar el repositorio

```bash
git clone https://github.com/parrot26/rag-tfi.git
```

### 2. Crear archivo .env

Crear el archivo .env donde se encuentran los archivos del repositorio clonado y generar las claves solicitadas.

```bash
# PostgreSQL
POSTGRES_USER=postgres
POSTGRES_PASSWORD=generar_pass_postgres
POSTGRES_DB=pgdb

# N8N (IMPORTANTE: generar estas claves)
N8N_ENCRYPTION_KEY=generar_key_64caracteres # openssl rand -hex 32
N8N_JWT_SECRET=generar_pass_secret
N8N_URL=http://localhost:5678/
```

### 3. Deploy del RAG
Correr el deploy del docker compose.

```bash
docker compose up -d
```
Revisar los servicios.

```bash
docker compose ps
```

Se tienen que visualizar los servicios de:
- n8n-rag
- postgres-rag
- qdrant-rag
- ollama-rag


### 4. Acceder a n8n

Entrar al navegador web donde se instaló el sistema RAG y acceder a:

http://localhost:5678/

Nota: Si el servidor es Linux sin entorno gráfico se puede realizar un túnel ssh al servidor y acceder desde tu computadora utilizando tu navegador a través del puerto elegido para el túnel.

### 5. Configuración N8N
Una vez dentro de n8n importar el archivo **rag-stack-tfi-v4.json** ubicado en la carpeta **archivo-n8n**.

- Luego aparecerá el flujo que hace funcionar el sistema RAG.
- Se deberá configurar las credenciales solicitadas en el flujo.
- Alimentar el sistema con el pdf de la guía.
- Correr el primer flujo para crear la estructura de la base de datos.
- Chatear con el sistema para recibir respuestas sobre la guía.






