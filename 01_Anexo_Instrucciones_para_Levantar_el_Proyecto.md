# Documentación técnica para levantar el Frontend y el Backend (Social_Consensus) de CENTINELA


A continuación, se detalla una guía técnica paso a paso para configurar y levantar el proyecto tanto en el frontend como en el backend. La guía está estructurada en dos secciones principales para cada parte del stack tecnológico.

## Frontend

### 1. Clonar el repositorio
Para comenzar, debes clonar el repositorio del frontend utilizando el siguiente comando:
```bash
git clone https://github.com/PlataformaIntegradaInvestigadores/frontend-app.git
```

### 2. Preparar el entorno de desarrollo
Asegúrate de tener instalado Node.js. El proyecto está construido con Angular 16, por lo tanto, necesitas instalar Angular CLI:
```bash
npm install -g @angular/cli
```

### 3. Instalar dependencias
Navega al directorio del proyecto clonado y ejecuta:
```bash
npm install
```

### 4. Configurar el archivo de entorno
Edita el archivo `src/environments/environment.ts` para asegurar que las URLs apunten a los servidores locales:
```typescript
export const environment = {
  production: false,
  apiCentinela: "http://localhost:8010/",
  wsUrl: 'ws://localhost:8000/ws',
  apiUrl: 'http://localhost:8000/api',
};
```

### 5. Ejecutar el proyecto
Finalmente, inicia el servidor de desarrollo con Angular CLI:
```bash
ng serve
```
Esto levantará el servidor de desarrollo y podrás acceder al proyecto en `http://localhost:4200`.

## Backend

### 1. Clonar el repositorio
Clona el repositorio del backend con el siguiente comando:
```bash
git clone https://github.com/PlataformaIntegradaInvestigadores/social_consensus_backend.git
```

### 2. Instalar Docker y Docker Compose
Asegúrate de tener Docker y Docker Compose instalados en tu sistema. Estos serán utilizados para construir y ejecutar los contenedores necesarios para el backend.

### 3. Configurar el archivo `.env`
Asegúrate de tener un archivo `.env` en el mismo nivel jerárquico que el `Dockerfile` y `docker-compose.yml`, con el siguiente contenido:
```
DEBUG=True
SECRET_KEY="django-insecure-2&dn&!a*l1d-p!u3xw8s)f9xbsa%i4uh2pf*qw@djt0va@pf2e"
DB_NAME= AGREGA UN NOMBRE PARA LA BD
DB_USER= AGREGA UN USUARIO PARA BD
DB_PASSWORD= AGREGA UNA CONTRASEÑA
DB_HOST=db
DB_PORT=5432
REDIS_HOST=redis
REDIS_PORT=6379
```

### 4. Construir y ejecutar los contenedores
Navega a la carpeta donde clonaste el repositorio y ejecuta:
```bash
docker-compose build
docker-compose up
```
Estos comandos construirán las imágenes necesarias y levantarán los contenedores. El backend estará accesible en `http://localhost:8000`.

### 5. Configurar CORS
En el archivo de configuración de Django, asegúrate de que las opciones de CORS estén correctamente configuradas para permitir solicitudes del frontend:
```python
CORS_ALLOW_ALL_ORIGINS = False

CORS_ALLOWED_ORIGINS = [
    "http://localhost:4200",
    "http://127.0.0.1:4200",
]
```
