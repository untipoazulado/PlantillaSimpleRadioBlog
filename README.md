# 📻 Plantilla Simple Radio Blog para Blogger

Bienvenido a la **Plantilla Simple Radio Blog**, un tema moderno, ligero y optimizado diseñado especialmente para **emisoras de radio comunitarias, estaciones online, locutores y medios informativos locales** de América Latina.

Esta plantilla combina un **reproductor de radio en vivo permanente** con un **blog de noticias y páginas estáticas**, permitiendo a los oyentes navegar por todo el sitio web mediante **tecnología AJAX** sin que la transmisión de audio se corte en ningún momento.

> **Nota:** Todos los ajustes principales (logo, colores, enlaces de transmisión, páginas y redes sociales) pueden modificarse fácilmente desde el panel de control de Blogger (**Diseño** y **Personalizar tema**) sin necesidad de tocar código complejo.

---

## 🚀 Características Principales

- 🎵 **Reproductor en Vivo Ininterrumpido:** Audio persistente con controles de Play/Pausa, volumen deslizable e indicador animado de señal.
- ⚡ **Navegación AJAX Continua:** Los visitantes pueden leer noticias, cambiar de página o buscar información mientras la radio sigue sonando en vivo.
- 🎨 **Personalización Total de Colores:** Selector de colores para fondos y colores independientes de texto (evita que los textos se vuelvan invisibles al usar fondos claros o blancos).
- 📑 **Pestañas de Páginas Modernas:** Soporte para páginas estáticas en formato de pestañas tipo píldora con indicador activo.
- 🌐 **Barra Social Inteligente:** Detección automática de iconos vectoriales SVG y colores oficiales para Facebook, Instagram, WhatsApp, YouTube, X/Twitter, TikTok, Telegram y Spotify.
- 📱 **Diseño 100% Responsivo:** Adaptado para teléfonos móviles, tablets y computadoras de escritorio.
- 🔍 **Buscador de Noticias Integrado:** Búsqueda en tiempo real por palabras clave sin recargas completas.
- 🕒 **Fecha y Hora Dinámica:** Reloj en vivo sincronizado en la barra superior.
- 🖼️ **Logo por Defecto y Personalizable:** Carga tu propio logotipo o utiliza el gráfico predeterminado.
- 📡 **Metadatos Opcionales de Canción y Artista:** Soporte preparado para **AzuraCast**, **Centova Cast** y **SonicPanel** (deshabilitado por defecto para máxima ligereza y velocidad).

---

## 📦 Instalación Rápida en Blogger

1. Entra a tu panel de administración en [Blogger.com](https://www.blogger.com).
2. En el menú lateral izquierdo, haz clic en **Tema**.
3. Al lado del botón naranja *Personalizar*, haz clic en la **flecha hacia abajo** (icono de menú desplegable `▼`).
4. *(Recomendado)* Haz clic en **Copia de seguridad** y descarga una copia de tu tema actual por precaución.
5. Vuelve a desplegar el menú `▼` y selecciona **Restablecer**.
6. Haz clic en **Subir** y selecciona el archivo `SimpleRadioBlogger.xml`.
7. ¡Listo! Blogger aplicará el nuevo diseño a tu sitio web.

> **Método alternativo (Editar HTML):**  
> Si prefieres copiar y pegar directamente, en el mismo menú `▼` selecciona **Editar HTML**, borra todo el contenido anterior, pega el código de `SimpleRadioBlogger.xml` y haz clic en el icono de **Guardar** (disquete).

---

## 🎧 Configuración del Reproductor de Radio

El reproductor viene preconfigurado y listo para sonar, pero puedes adaptar fácilmente la transmisión y los mensajes a tu emisora:

1. Ve a **Blogger > Diseño**.
2. En la sección **Cabecera**, busca el bloque llamado **Reproductor de Radio** y haz clic en el icono de **Editar** (lápiz).
3. Verás una ventana con la siguiente configuración:

```html
<script>
  window.RADIO_SETTINGS = {
    // Enlace de transmisión de tu radio
    // ¡IMPORTANTE!: Debe comenzar obligatoriamente con https://
    streamUrl: "https://radio.labookostacion.com/listen/labookostacion/radio.mp3",

    // Texto cuando la emisora emite señal
    textLive: "Radio en vivo",

    // Texto cuando la emisora está apagada o sin señal
    textOffline: "Radio apagada",

    // Lema o subtítulo de tu radio
    tagline: "RADIO EN VIVO · NOTICIAS · MÚSICA",

    // Metadatos automáticos de canción y artista (deshabilitado por defecto)
    // Plataformas soportadas: "azuracast", "centova", "sonicpanel"
    metadata: {
      enabled: false,
      platform: "azuracast",
      endpointUrl: ""
    }
  };
</script>
```

### Parámetros Explicados:
- **`streamUrl`**: El enlace de tu servidor de radio (Icecast, Shoutcast, AzuraCast, Centova, SonicPanel, etc.).  
  > ⚠️ **Requisito indispensable:** El enlace de streaming **DEBE** comenzar con `https://`. Si usas un enlace `http://` normal, los navegadores (Chrome, Edge, Firefox, Safari) lo bloquearán por seguridad (error de contenido mixto).  
  > *Soporta múltiples tipos de puntos de montaje como `/stream`, `.mp3`, `/;`, etc.*
- **`textLive`**: El nombre o estado que se muestra cuando la radio está encendida (ejemplo: `"Emisión en directo"`, `"La Voz de la Comunidad"`).
- **`textOffline`**: Mensaje cuando el servidor de streaming esté caído o fuera del aire (ejemplo: `"Transmisión en pausa"`).
- **`tagline`**: Lema que aparece debajo del nombre de tu emisora.
- **`metadata` (Opcional)**: Muestra en vivo la canción y artista actual consultando tu panel de streaming cada 15 segundos:
  - **`enabled`**: Ponlo en `true` para activar los metadatos o `false` para solo mostrar el texto fijo (`textLive`).
  - **`platform`**: La plataforma que utiliza tu radio. Opciones:
    - `"azuracast"` *(Recomendada)*: Extrae título, artista o el nombre del locutor/DJ en vivo.
    - `"centova"`: Compatible con endpoints RPC o estadísticas JSON de Centova Cast.
    - `"sonicpanel"`: Compatible con la API JSON de SonicPanel.
  - **`endpointUrl`**: La dirección URL de la API de tu panel (debe ser `https://` y permitir CORS). Ejemplos:
    - *AzuraCast:* `https://tu-azuracast.com/api/nowplaying/1`
    - *Centova Cast:* `https://tu-centova.com:2199/external/rpc.php?m=streaminfo.get&username=tu_usuario`
    - *SonicPanel:* `https://tu-sonic.com:2083/api/...`

4. Haz clic en **Guardar**. Los cambios se reflejarán inmediatamente en tu web.

### 📋 Fragmento de Respaldo para el Editor de Bloques

> ⚠️ **¿Alguien borró o dañó por error el contenido del bloque?**  
> Si tú o alguien de tu equipo borró sin querer este código en **Blogger > Diseño > Reproductor de Radio**, no tienes que reinstalar la plantilla. Simplemente copia el siguiente bloque de código tal cual, pégalo dentro de la caja de contenido del bloque y haz clic en **Guardar**:

```html
<script>
  window.RADIO_SETTINGS = {
    // Enlace de streaming (Obligatorio https:// para funcionar en Blogger)
    streamUrl: "https://radio.labookostacion.com/listen/labookostacion/radio.mp3",

    // Texto cuando la emisora emite señal
    textLive: "Radio en vivo",

    // Texto cuando la emisora está apagada o sin señal
    textOffline: "Radio apagada",

    // Lema o subtítulo de tu radio (bajo el nombre en la cabecera)
    tagline: "RADIO EN VIVO · NOTICIAS · MÚSICA",

    // Metadatos automáticos de canción y artista (deshabilitado por defecto)
    // Plataformas soportadas: "azuracast", "centova", "sonicpanel"
    metadata: {
      enabled: false,
      platform: "azuracast",
      endpointUrl: ""
    }
  };
</script>
```

---

## 🎨 Personalización de Colores (Fondos y Textos)

Para cambiar la paleta de colores de tu emisora:

1. Ve a **Blogger > Tema**.
2. Haz clic en el botón naranja **Personalizar**.
3. En el menú lateral izquierdo, haz clic en **Avanzado**.
4. En **Colores del Tema**, encontrarás los siguientes controles:

| Opción de Color | Descripción | Valor por Defecto |
| :--- | :--- | :--- |
| **Fondo Cabecera y Barra Superior** | Color de fondo de la barra de fecha y de la cabecera principal. | `#071f3e` (Azul marino) |
| **Color de Acentos, Botón Play y Pestaña Activa** | Color del botón de reproducción, iconos y pestaña seleccionada. | `#39c0e8` (Celeste cian) |
| **Fondo Barra de Menú y Reproductor** | Color de fondo para la barra de navegación y el reproductor de radio. | `#102e52` (Azul profundo) |
| **Fondo General de la Web** | Color de fondo de toda la página detrás de la caja central. | `#f3f5f8` (Gris suave) |
| **Texto de Barra Superior (Fecha, Hora y Redes)** | Color de la fecha, hora dinámica y textos de redes sociales. | `#cbd5e1` (Gris claro) |
| **Texto de Cabecera (Nombre y Lema de Emisora)** | Color del título principal y del lema de tu radio. | `#ffffff` (Blanco) |
| **Texto de Enlaces del Menú** | Color de las opciones del menú de navegación. | `#dbeafe` (Azul pastel) |
| **Texto del Reproductor (Canción y Controles)** | Color del título de canción/estado y control de volumen. | `#ffffff` (Blanco) |
| **Texto Principal (Noticias, Títulos y Contenido)** | Color del texto de lectura, artículos y noticias del blog. | `#111827` (Gris oscuro) |

> 💡 **Consejo si prefieres un diseño claro o blanco:**  
> Si cambias el *Fondo de Cabecera* a blanco (`#ffffff`) o beige claro, simplemente cambia el *Texto de Barra Superior* y el *Texto de Cabecera* a un color oscuro (como `#111827`). De esta forma todos los textos se leerán con perfecta nitidez.

5. Haz clic en el botón de **Guardar** (icono de disquete en la esquina inferior derecha).

---

## 🖼️ Configuración del Logo y Título de la Emisora

1. Ve a **Blogger > Diseño**.
2. En la sección **Cabecera**, haz clic en el lápiz de edición de **Cabecera (Logo, Título y Lema/Descripción)**.
3. Puedes:
   - Escribir el **Título del blog** (nombre de tu radio).
   - Escribir la **Descripción del blog** (lema que aparecerá bajo el título).
   - En **Imagen**, subir el archivo de imagen con el logotipo de tu estación (formato PNG o JPG).
4. Si no subes ninguna imagen, la plantilla mostrará el logotipo predeterminado de Guille Locutor (`https://guillelocutor.com/wp-content/uploads/2024/03/dibujo-guille.png`).
5. Haz clic en **Guardar**.

---

## 📑 Pestañas de Páginas Estáticas (Navegación AJAX sin cortes)

La plantilla muestra las páginas estáticas de Blogger como **pestañas modernas tipo píldora** justo encima del buscador y de las noticias:

1. Primero crea tus páginas en **Blogger > Páginas** (por ejemplo: *Quiénes Somos*, *Programación*, *Locutores*, *Contacto*).
2. Ve a **Blogger > Diseño**.
3. En la sección central encontrarás el bloque **Pestañas de Páginas**.
4. Haz clic en **Editar**.
5. Marca las casillas de las páginas que desees mostrar como pestañas.
6. **Recomendación de diseño:** Para mantener una interfaz limpia y visualmente equilibrada tanto en computadoras como en móviles, se aconseja **no agregar más de 5 pestañas**.
7. Puedes arrastrar las páginas en la lista para decidir cuál aparece primero (por defecto, la pestaña de *Página principal / Blog* aparece al inicio).
8. Haz clic en **Guardar**.

> ✨ **Ventaja exclusiva de esta plantilla:**  
> Al hacer clic en cualquiera de las pestañas o regresar a *Página principal*, el contenido se carga instantáneamente mediante AJAX, permitiendo que la música y la locución continúen sonando sin cortes.

---

## 🌐 Redes Sociales en la Barra Superior

1. Ve a **Blogger > Diseño**.
2. En la parte superior, busca el bloque **Redes Sociales (Barra Superior)** y haz clic en **Editar**.
3. Agrega las redes que tenga tu emisora escribiendo el nombre y la dirección URL completa. Por ejemplo:
   - **Nombre:** Facebook | **URL:** `https://facebook.com/tu_radio`
   - **Nombre:** WhatsApp | **URL:** `https://wa.me/51999999999`
   - **Nombre:** Instagram | **URL:** `https://instagram.com/tu_radio`
   - **Nombre:** YouTube | **URL:** `https://youtube.com/@tu_radio`
   - **Nombre:** TikTok | **URL:** `https://tiktok.com/@tu_radio`
   - **Nombre:** Telegram | **URL:** `https://t.me/tu_radio`
   - **Nombre:** Spotify | **URL:** `https://open.spotify.com/...`
4. La plantilla **detecta automáticamente la plataforma por su enlace** y le asigna el icono SVG oficial y el color característico de la marca.
5. Puedes ordenar los enlaces y hacer clic en **Guardar**.

---

## 🧭 Menú de Navegación por Categorías

1. Ve a **Blogger > Diseño**.
2. Busca el widget **Menú de Navegación** (debajo del logo) y haz clic en **Editar**.
3. Añade los enlaces a las etiquetas o secciones de tu blog:
   - Ejemplo: `/search/label/Noticias`
   - Ejemplo: `/search/label/Deportes`
   - Ejemplo: `/search/label/Entrevistas`
4. Haz clic en **Guardar**. Al igual que las páginas, la navegación por categorías se realiza fluidamente.

---

## ❓ Preguntas Frecuentes y Solución de Problemas

### 1. ¿Por qué el reproductor no suena al presionar Play?
- Revisa que tu enlace de transmisión comience con **`https://`**. La inmensa mayoría de las transmisiones que no suenan se debe a enlaces `http://` bloqueados por el navegador web.
- Comprueba que tu servidor de streaming esté emitiendo señal en vivo. Si está apagado, el reproductor mostrará el indicador en gris con el texto *"Radio apagada"*.

### 2. ¿Cómo funciona la fecha y hora de la barra superior?
- La fecha y hora se toma dinámicamente del reloj del navegador del visitante y se actualiza segundo a segundo de forma automática en idioma español.

### 3. ¿Se muestran las fechas de publicación en las páginas estáticas?
- No. Por diseño editorial, las páginas estáticas (*Quiénes somos*, *Programación*, etc.) ocultan automáticamente la fecha, el autor y las etiquetas para brindar una presentación institucional limpia.

### 4. ¿Qué hago si alguien borró por accidente el contenido del bloque del reproductor?
- No te preocupes: ve a la sección [Fragmento de Respaldo para el Editor de Bloques](#-fragmento-de-respaldo-para-el-editor-de-bloques) de este manual, copia el bloque de código, pégalo en **Blogger > Diseño > Reproductor de Radio** y presiona **Guardar**. Con eso queda 100% restablecido.

---

## 📄 Licencia

Este proyecto es software libre y de código abierto, distribuido bajo los términos de la **Licencia Pública General de GNU Versión 3 (GPLv3)**. Puedes utilizarlo, modificarlo, compartirlo y adaptarlo con total libertad para tu emisora o comunidad, manteniendo siempre las libertades de software libre para todos los usuarios.

Consulta el archivo [LICENSE](LICENSE) para conocer todos los términos y condiciones de la licencia.

---

## 💙 Créditos y Comunidad

<p align="center">
  <img src="https://blogger.googleusercontent.com/img/a/AVvXsEgD0fqD0cXbcHa41xzfsSDzqRNiR0WP7yMSg1ErLB_NtyY-wEPEYn_47RhiB2Z49pD5WUoy1-j-9HF0OayBAQGVlPevmo6joPiJ0mM3tqCcSX37_JGmhFbNAwrFbdW4Yum55JgjzW3DVwoK_4RXPbnsYd7uNQViNx5zXqWdrmNusSDnJYYBt05d-9k-td4a=s1472" alt="Logo Un Tipo Azulado" width="130" style="border-radius: 50%; display: block; margin: 0 auto 16px auto;" />
</p>

Elaborado por **Un Tipo Azulado** con ayuda de IA para la comunidad radial de Latinoamérica.

Plantilla creada con dedicación para fortalecer la presencia digital de los medios radiales independientes, emisoras comunitarias y locutores de toda la región.

¡Éxitos con la transmisión de tu emisora! 📻🎙️

