# cdo-landing-app

Landing page estática de descarga de la app móvil **Colegas del Orden**.

Diseñada para servirse en `colegasdelorden.com/app`, fuera de WordPress.

## Estructura

```
cdo-landing-app/
├── index.html       # Página principal de descarga
├── css/
│   └── style.css    # Estilos
├── .htaccess        # Configuración Apache
└── README.md        # Este archivo
```

## Deploy

### Apache (WordPress usa Apache):

```bash
cd /var/www/html   # raíz de tu WordPress
git clone https://github.com/Colegas-del-Orden/cdo-landing-app.git app
```

El `.htaccess` incluido evita que WordPress intercepte las requests a `/app`.

### Nginx:

Agregar en el virtual host **antes** del bloque `location /`:

```nginx
location ^~ /app {
    alias /var/www/html/app;
    index index.html;
    try_files $uri $uri/ /app/index.html;
}
```

## Actualizar URLs de tiendas

Buscar los comentarios `TODO` en `index.html` y reemplazar:
- `idMOCK123456` → ID real de App Store
- `com.colegasdelorden.app` → package name real de la app Flutter
