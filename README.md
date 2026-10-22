# Docker + Nginx + Apache

Proyecto básico realizado con los conceptos de Docker y Nginx vistos en clase.

## Estructura

- `docker-compose.yml`: crea los dos contenedores.
- `nginx/default.conf`: Nginx actúa como proxy inverso.
- `apache/httpd.conf`: configuración básica de Apache.
- `apache/site/`: página web servida por Apache.

## Arrancar

```bash
docker compose up -d
```

## Probar

En el navegador:

- http://web1.localhost:8080
- http://web2.localhost:8080

También se puede comprobar con:

```bash
curl -I -H "Host: web1.localhost" http://localhost:8080
curl -I -H "Host: web2.localhost" http://localhost:8080
```

## Zona privada

La carpeta `/privado/` necesita la cabecera:

```text
X-Auth-Token: DAW2026
```

Ejemplo:

```bash
curl -H "Host: web1.localhost" -H "X-Auth-Token: DAW2026" http://localhost:8080/privado/
```

Sin esa cabecera, Apache rechaza el acceso.

## Arquitectura

Navegador -> Nginx -> Apache -> página HTML

Apache no publica ningún puerto directamente al host.
