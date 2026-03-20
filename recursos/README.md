# Plantillas de Email - Gestión de Riesgos

## Compilar MJML a HTML

Requiere [Node.js](https://nodejs.org/) instalado.

```bash
npx mjml bienvenida.mjml -o bienvenida.html --config.minify=true --config.validationLevel=strict
```

### Flags

| Flag | Qué hace |
|------|----------|
| `-o bienvenida.html` | Archivo de salida |
| `--config.minify=true` | Minifica el HTML (evita bugs en iOS/Android y mantiene el email bajo 102KB para Gmail) |
| `--config.validationLevel=strict` | Falla si hay errores de sintaxis MJML |

### Antes de enviar a producción

Reemplazar las rutas relativas de imágenes (`./logo-blanco.png`, `./arrow-right-circle.png`, etc.) por las URLs del servidor/CDN donde se alojen los recursos.
