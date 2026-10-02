# Guía de Deployment: César Castillo Portfolio

## Estructura del Proyecto

```
cesar-castillo-portafolio/
├── index.html                          # Página de inicio
├── pages/
│   ├── sobre-mi.html                  # Sobre mí
│   ├── servicios.html                 # Servicios y aranceles
│   ├── experiencia.html                # Experiencia y publicaciones
│   └── contacto.html                   # Contacto y formulario
├── assets/
│   ├── css/
│   │   └── main.css                   # Estilos compartidos
│   ├── images/
│   │   └── foto-perfil.jpg            # Tu foto de perfil (agregar)
│   └── js/
│       └── (scripts adicionales si es necesario)
├── README.md                           # Documentación del proyecto
└── DEPLOYMENT.md                       # Este archivo
```

---

## 1. PREPARACIÓN LOCAL

### Requisitos
- Navegador web moderno (Chrome, Firefox, Safari, Edge)
- Editor de texto (VS Code, Sublime, etc.)
- Git (opcional, pero recomendado)

### Setup Inicial

1. **Descarga los archivos**:
   - Copia todos los archivos en una carpeta local llamada `cesar-castillo-portafolio`

2. **Añade tu foto de perfil**:
   - Coloca tu foto en `assets/images/foto-perfil.jpg`
   - Asegúrate que sea cuadrada o rectangularo (se adaptará con `object-fit: cover`)
   - Tamaño recomendado: 800x1000px mínimo

3. **Prueba localmente**:
   ```bash
   # Opción 1: Abre directamente
   open index.html  # macOS
   # o
   start index.html  # Windows
   # o navega a file:///tu/ruta/index.html en el navegador

   # Opción 2: Usa un servidor local (recomendado)
   python -m http.server 8000
   # Luego abre http://localhost:8000 en tu navegador
   ```

---

## 2. CONFIGURACIÓN DEL FORMULARIO DE CONTACTO

El formulario usa **Formspree** (servicio gratuito para contactos):

### Paso 1: Crear cuenta en Formspree
1. Visita https://formspree.io
2. Regístrate con tu email
3. Crea un nuevo form

### Paso 2: Obtener tu Form ID
- Formspree te dará un URL como: `https://formspree.io/f/YOUR_FORM_ID`
- Copia el `YOUR_FORM_ID`

### Paso 3: Actualizar el formulario en contacto.html
Busca esta línea en `pages/contacto.html`:
```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

Reemplaza `YOUR_FORM_ID` con tu ID real. Ejemplo:
```html
<form action="https://formspree.io/f/mzzpyebd" method="POST">
```

---

## 3. SUBIR A GITHUB PAGES

### Opción A: Usando Git (Recomendado)

1. **Crear repositorio en GitHub**:
   - Ve a https://github.com/new
   - Nombre: `cesar-castillo-portafolio`
   - Privado o Público (Público = visible en GitHub Pages)
   - Crea el repositorio

2. **Inicializar Git localmente**:
   ```bash
   cd cesar-castillo-portafolio
   git init
   git add .
   git commit -m "Initial commit: Portfolio setup"
   git branch -M main
   git remote add origin https://github.com/tu-usuario/cesar-castillo-portafolio.git
   git push -u origin main
   ```

3. **Habilitar GitHub Pages**:
   - Ve a Settings > Pages (en tu repo)
   - Source: Branch "main"
   - Guarda
   - Espera 1-2 minutos
   - Tu sitio estará en: `https://tu-usuario.github.io/cesar-castillo-portafolio`

### Opción B: Sin Git (Drag & Drop)

1. En GitHub, crea un repositorio (ver paso 1 anterior)
2. Usa la interfaz web para subir archivos
3. Mismo proceso de habilitación en Pages

---

## 4. DOMINIO PERSONALIZADO (Opcional)

Si quieres usar `midominio.com` en lugar de `github.io`:

### Opción A: Usar Namecheap, GoDaddy, etc.

1. Compra un dominio (ej: `cesarcastillo.cl`)
2. En GitHub Pages Settings, agrega tu dominio en "Custom Domain"
3. En tu registrador DNS, apunta los registros a GitHub (GitHub mostrará instrucciones)

### Opción B: Subdominio

Si ya tienes un dominio con hosting:
1. Agrega un registro CNAME: `portafolio.midominio.com` → `tu-usuario.github.io`
2. En GitHub Pages, coloca `portafolio.midominio.com` en Custom Domain

---

## 5. PERSONALIZACIONES ADICIONALES

### Agregar Analytics (Google Analytics)

1. Ve a https://analytics.google.com
2. Crea una propiedad para tu sitio
3. Obtén tu `TRACKING_ID`
4. Agrega esto en el `<head>` de todas las páginas:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-YOUR_TRACKING_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-YOUR_TRACKING_ID');
</script>
```

### Agregar Dark Mode

Reemplaza esto en `assets/css/main.css`:

```css
@media (prefers-color-scheme: dark) {
    body {
        background-color: #1a1a1a;
        color: #f0f0f0;
    }
    
    a {
        color: #a8a8a8;
    }
    
    .border-b-6, .border-t-6 {
        border-color: #333;
    }
}
```

### Agregar Favicon

1. Crea un favicon (16x16 o 32x32px) llamado `favicon.ico`
2. Colócalo en la raíz del proyecto
3. Agrega en el `<head>`:

```html
<link rel="icon" type="image/x-icon" href="favicon.ico">
```

---

## 6. MANTENIMIENTO Y ACTUALIZACIONES

### Editar Contenido

- **Sobre mí**: `pages/sobre-mi.html` (sección #bio)
- **Servicios**: `pages/servicios.html` (sección #servicios)
- **Experiencia**: `pages/experiencia.html` (sección #experiencia)
- **Contacto**: `pages/contacto.html` (información de contacto)

### Cambiar Colores

En `assets/css/main.css`, busca estas líneas y modifica:

```css
:root {
    --primary-color: #0a0a0a;  /* Negro actual */
    --text-light: #666666;     /* Texto gris */
}
```

O en las propias páginas, edita clases Tailwind como:
- `text-black` → cambiar a otro color
- `border-black` → cambiar a otro color
- `hover:bg-black` → cambiar a otro color

### Agregar Nuevas Páginas

1. Copia `pages/sobre-mi.html`
2. Renombra a `pages/nueva-pagina.html`
3. Edita el contenido
4. Agrega enlace en navegación (en header de todas las páginas)

---

## 7. TROUBLESHOOTING

### Problema: Formulario no funciona
- ✓ Verifica que hayas reemplazado `YOUR_FORM_ID` en contacto.html
- ✓ Asegúrate de haber confirmado el form en Formspree

### Problema: Imágenes no cargan
- ✓ Verifica ruta relativa: `assets/images/foto-perfil.jpg`
- ✓ Asegúrate que la imagen exista en esa carpeta
- ✓ En navegadores, abre inspector (F12) y ve errores

### Problema: Estilos no se aplican
- ✓ Limpia caché del navegador (Ctrl+Shift+R o Cmd+Shift+R)
- ✓ Verifica que `assets/css/main.css` esté en el directorio correcto
- ✓ Revisa que los links en HTML sean relativos correctos

### Problema: Navegación no funciona
- ✓ En `index.html`: links son `pages/sobre-mi.html`
- ✓ En `pages/*.html`: links son `../index.html` (volver a inicio)

---

## 8. CHECKLIST PRE-LAUNCH

- [ ] Foto de perfil cargada en `assets/images/foto-perfil.jpg`
- [ ] Teléfono y emails actualizados en todas las páginas
- [ ] Formulario de contacto configurado con Formspree ID
- [ ] Probado en navegador local (todos los links funcionan)
- [ ] Probado en móvil (responsivo se ve bien)
- [ ] Repositorio GitHub creado
- [ ] GitHub Pages habilitado
- [ ] Dominio personalizado configurado (si aplica)
- [ ] Analytics configurado (opcional)
- [ ] Dark mode probado (opcional)

---

## 9. URLs ÚTILES

- **GitHub Pages**: https://pages.github.com
- **Formspree**: https://formspree.io
- **Google Analytics**: https://analytics.google.com
- **Favicon Generator**: https://favicon-generator.org
- **Tailwind CSS**: https://tailwindcss.com/docs
- **Meta Tags (OpenGraph)**: https://metatags.io

---

## 10. PRÓXIMOS PASOS (Futuro)

Si necesitas escalabilidad futura:

1. **Blog**: Agregar carpeta `/blog` con posts en HTML o Markdown
2. **CMS**: Migrar a Hugo/Adritian (sin perder contenido)
3. **Funcionalidades avanzadas**: Búsqueda, filtros, etc.

Por ahora, este setup es perfecto para tu caso. ¡Adelante!

---

**Última actualización**: 2026-10-01
**Versión**: 1.0
**Autor**: César Castillo Portfolio Team
