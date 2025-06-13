# Email Template - Welcome

Esta es una plantilla de correo electrónico profesional y responsiva convertida para uso en sistemas de envío de emails.

## Características

- **Responsiva**: Se adapta a diferentes tamaños de pantalla
- **Compatible**: Funciona en los principales clientes de email (Gmail, Outlook, Apple Mail, etc.)
- **Personalizable**: Variables de plantilla para contenido dinámico
- **Accesible**: Estructura semántica con tablas para mejor compatibilidad

## Variables de Plantilla

La plantilla incluye las siguientes variables que puedes reemplazar:

| Variable               | Descripción                     | Ejemplo                           |
| ---------------------- | ------------------------------- | --------------------------------- |
| `{{subject}}`          | Asunto del email                | "Bienvenido a ArianeStart"        |
| `{{company_name}}`     | Nombre de la empresa            | "ArianeStart"                     |
| `{{main_title}}`       | Título principal del email      | "Bienvenido a nuestra plataforma" |
| `{{main_content}}`     | Contenido principal del mensaje | "Tu privacidad es importante..."  |
| `{{disclaimer_text}}`  | Texto de descargo               | "Si no te registraste..."         |
| `{{current_year}}`     | Año actual                      | "2025"                            |
| `{{app_name}}`         | Nombre de la aplicación         | "ArianeStart"                     |
| `{{unsubscribe_url}}`  | URL para darse de baja          | "https://example.com/unsubscribe" |
| `{{browser_view_url}}` | URL para ver en navegador       | "https://example.com/view"        |

## Uso

1. **Reemplaza las variables**: Sustituye `{{variable_name}}` con los valores reales
2. **Personaliza el estilo**: Modifica los colores y fuentes en los estilos CSS inline
3. **Prueba en diferentes clientes**: Verifica que se vea correctamente en Gmail, Outlook, etc.

## Ejemplo de Uso en Código

### JavaScript/Node.js

```javascript
const fs = require("fs");

// Leer la plantilla
let template = fs.readFileSync("welcome.html", "utf8");

// Reemplazar variables
const variables = {
  subject: "Bienvenido a ArianeStart",
  company_name: "ArianeStart",
  main_title: "Bienvenido a nuestra plataforma",
  main_content: "Gracias por registrarte...",
  // ... más variables
};

// Reemplazar todas las variables
Object.keys(variables).forEach((key) => {
  const regex = new RegExp(`{{${key}}}`, "g");
  template = template.replace(regex, variables[key]);
});

// Ahora 'template' contiene el HTML final listo para enviar
```

### Python

```python
import json

# Leer la plantilla
with open('welcome.html', 'r', encoding='utf-8') as file:
    template = file.read()

# Leer variables desde config
with open('template_config.json', 'r', encoding='utf-8') as file:
    config = json.load(file)
    variables = config['template_variables']

# Reemplazar variables
for key, value in variables.items():
    template = template.replace(f'{{{{{key}}}}}', value)

# template ahora contiene el HTML final
```

## Personalización

### Colores

- **Primario**: `#4f5a68` (texto principal)
- **Secundario**: `rgba(79, 90, 104, 0.6)` (texto secundario)
- **Enlaces**: `#5266ee` (azul)
- **Fondo**: `#f2f2f7` (gris claro)

### Tipografía

- **Principal**: Arial, sans-serif
- **Logo**: 'Inter', Arial, sans-serif

## Compatibilidad

✅ Gmail  
✅ Outlook (2016+)  
✅ Apple Mail  
✅ Yahoo Mail  
✅ Thunderbird  
✅ Dispositivos móviles

## Notas Técnicas

- Usa tablas para layout (requerido para compatibilidad con email)
- CSS inline para máxima compatibilidad
- Ancho máximo de 600px para desktop
- Responsive usando media queries para móvil
