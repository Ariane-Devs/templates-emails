# Email Template - Welcome

Esta es una plantilla de correo electrónico profesional y responsiva convertida para uso en sistemas de envío de emails.

## Características

- **Responsiva**: Se adapta a diferentes tamaños de pantalla
- **Compatible**: Funciona en los principales clientes de email (Gmail, Outlook, Apple Mail, etc.)
- **Personalizable**: Variables de plantilla para contenido dinámico
- **Logo dinámico**: Soporte para logos personalizados con fallback automático
- **Espaciado optimizado**: Diseño más compacto y moderno
- **Accesible**: Estructura semántica con tablas para mejor compatibilidad

## Variables de Plantilla

La plantilla incluye las siguientes variables que puedes reemplazar:

| Variable           | Descripción                     | Ejemplo                           |
| ------------------ | ------------------------------- | --------------------------------- |
| `subject`          | Asunto del email                | "Bienvenido a ArianeStart"        |
| `company_name`     | Nombre de la empresa            | "ArianeStart"                     |
| `logo_url`         | URL del logo personalizado      | "https://mi-dominio.com/logo.png" |
| `main_title`       | Título principal del email      | "Bienvenido a nuestra plataforma" |
| `main_content`     | Contenido principal del mensaje | "Tu privacidad es importante..."  |
| `disclaimer_text`  | Texto de descargo               | "Si no te registraste..."         |
| `current_year`     | Año actual                      | "2025"                            |
| `app_name`         | Nombre de la aplicación         | "ArianeStart"                     |
| `unsubscribe_url`  | URL para darse de baja          | "https://example.com/unsubscribe" |
| `browser_view_url` | URL para ver en navegador       | "https://example.com/view"        |

## Logo Dinámico

{% raw %}
La plantilla soporta logos personalizados con fallback automático:

- **Con logo personalizado**: Proporciona la variable `{{logo_url}}` con la URL de tu logo
- **Sin logo personalizado**: Si no envías `logo_url` o está vacía, se usa automáticamente el logo por defecto de ArianeStart
- **Formato recomendado**: PNG o WebP, 40x40px para mejor visualización
- **URL absoluta**: Usa URLs completas (https://) para garantizar la visualización en todos los clientes de email

### Ejemplo de uso:

```javascript
// Con logo personalizado
const variables = {
  logo_url: "https://mi-empresa.com/assets/logo.png",
  company_name: "Mi Empresa",
  // ... otras variables
};

// Sin logo personalizado (usa el por defecto)
const variables = {
  // logo_url no se incluye o se deja vacío
  company_name: "Mi Empresa",
  // ... otras variables
};
```

{% endraw %}

## Archivos Incluidos

- **`welcome.html`**: Plantilla principal con variables `variable_name` para uso en producción
- **`welcome-preview.html`**: Versión con valores de ejemplo para visualización y testing
- **`template_config.json`**: Configuración con valores de ejemplo y documentación

## Uso

### Para Visualización/Testing

Abre `welcome-preview.html` directamente en tu navegador para ver cómo se verá el email con datos reales.

### Para Producción

1. **Reemplaza las variables**: En `welcome.html`, sustituye `variable_name` con los valores reales
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
  logo_url: "https://mi-empresa.com/logo.png", // Opcional
  main_title: "Bienvenido a nuestra plataforma",
  main_content: "Gracias por registrarte...",
  // ... más variables
};

// Reemplazar todas las variables (uso de expresiones RegExp escapadas para evitar Liquid en Jekyll)
Object.keys(variables).forEach((key) => {
  const regex = new RegExp("\\\\{\\\\{" + key + "\\\\}\\\\}", "g");
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

# Reemplazar variables (escapando dobles llaves en las cadenas)
for key, value in variables.items():
    template = template.replace('{{' + key + '}}', value)

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
- Espaciado optimizado entre logo y contenido (32px vs 240px anterior)

## Historial de Cambios

### v2.0 - Junio 2025

- ✨ **Nuevo**: Soporte para logos dinámicos con fallback automático
- 🎨 **Mejorado**: Espaciado optimizado entre logo y contenido principal
- 📝 **Actualizado**: Documentación completa con ejemplos de uso
- 🔧 **Corregido**: Error de sintaxis en welcome-preview.html

### v1.0 - Versión inicial

- 📧 Template básico de bienvenida
- 📱 Diseño responsivo
- 🔧 Variables de personalización
