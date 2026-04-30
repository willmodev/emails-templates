# Plantillas de Email - Gestión de Riesgos

## Compilar MJML a HTML

Requiere [Node.js](https://nodejs.org/) instalado.

```bash
npx mjml bienvenida.mjml -o bienvenida.html --config.minify=true --config.validationLevel=strict
npx mjml codigo-otp.mjml -o codigo-otp.html --config.minify=true --config.validationLevel=strict
npx mjml reactivacion-cuenta.mjml -o reactivacion-cuenta.html --config.minify=true --config.validationLevel=strict
```

### Flags

| Flag | Qué hace |
|------|----------|
| `-o bienvenida.html` | Archivo de salida |
| `--config.minify=true` | Minifica el HTML (evita bugs en iOS/Android y mantiene el email bajo 102KB para Gmail) |
| `--config.validationLevel=strict` | Falla si hay errores de sintaxis MJML |

## Convertir HTML a Base64

Para almacenar las plantillas en base64 (por ejemplo, en la DB):

```bash
base64 -w 0 bienvenida.html > bienvenida.base64.txt; base64 -w 0 codigo-otp.html > codigo-otp.base64.txt; base64 -w 0 reactivacion-cuenta.html > reactivacion-cuenta.base64.txt; base64 -w 0 correo-prueba-smtp.html > correo-prueba-smtp.base64.txt; ls -lh *.base64.txt
```

> Los estilos no se alteran porque están inline en el HTML. Al decodificar el base64 se obtiene el HTML original intacto.

### Antes de enviar a producción

Reemplazar las rutas relativas de imágenes (`./logo-blanco.png`, `./arrow-right-circle.png`, etc.) por las URLs del servidor/CDN donde se alojen los recursos.
