# Balanceador de Carga con Nginx y Docker

## Descripción
Este proyecto implementa un balanceador de carga utilizando Nginx con el algoritmo Round Robin para distribuir las peticiones entre dos servidores web.

## Diagrama de Infraestructura
```
                    ┌─────────────────────┐
                    │                     │
                    │   Cliente (Browser) │
                    │                     │
                    └──────────┬──────────┘
                               │
                               │ HTTP Request
                               │ (localhost:8080)
                               ▼
                    ┌─────────────────────┐
                    │                     │
                    │  Load Balancer      │
                    │  (Nginx)            │
                    │  Port: 8080         │
                    │                     │
                    └──────────┬──────────┘
                               │
                ┌──────────────┴──────────────┐
                │                             │
                │ Round Robin Distribution    │
                │                             │
        ┌───────▼────────┐          ┌────────▼───────┐
        │                │          │                │
        │  Server 1      │          │  Server 2      │
        │  (Nginx)       │          │  (Nginx)       │
        │  Port: 80      │          │  Port: 80      │
        │                │          │                │
        └────────────────┘          └────────────────┘
```

## Requisitos Previos
- Docker Desktop instalado y en ejecución
- Docker Compose
- Git

## Comandos para Ejecutar la Infraestructura

### Levantar la infraestructura
```bash
docker compose up --build
```

### Levantar en segundo plano (modo detached)
```bash
docker compose up -d --build
```

### Detener la infraestructura
```bash
docker compose down
```

### Ver logs
```bash
docker compose logs -f
```

## URL del Balanceador de Carga

**URL:** http://localhost:8080

## Prueba de Funcionamiento

1. Abre tu navegador y visita http://localhost:8080
2. Recarga la página varias veces (F5)
3. Deberías ver alternadamente:
   - "Hola mundo desde Server 1" (fondo morado)
   - "Hola mundo desde Server 2" (fondo rosado)

## Estructura del Proyecto
```
load-balancer-project/
├── docker-compose.yml
├── nginx/
│   └── nginx.conf
├── server1/
│   ├── Dockerfile
│   └── index.html
├── server2/
│   ├── Dockerfile
│   └── index.html
└── README.md
```

## Tecnologías Utilizadas
- **Docker & Docker Compose**: Contenedorización y orquestación
- **Nginx**: Servidor web y balanceador de carga
- **HTML/CSS**: Interfaz web simple
- **Algoritmo Round Robin**: Distribución equitativa de carga
```

---

### 📁 **.gitignore**

Haz clic derecho en la carpeta raíz → New File → `.gitignore`
```
# Docker
.dockerignore

# Sistema
.DS_Store
Thumbs.db

# Editores
.vscode/
.idea/
*.swp
*.swo
*~