# FORJA — Sitio web del gimnasio

Sitio estático (HTML, CSS y JavaScript) construido a partir de la base de datos
**`GYM.sql`** del proyecto *Sistema de Gestión para un Gimnasio*.

## Cómo abrirlo

1. Abrí la carpeta `GYM_Web`.
2. Hacé doble clic en `index.html`.

También podés levantarlo con un servidor local (recomendado para que el enlace de
descarga del `.sql` funcione siempre):

```bash
cd GYM_Web
python3 -m http.server 8000
```

Después entrá a <http://localhost:8000>.

## Estructura

```text
GYM_Web/
├── index.html          Página completa (una sola vista con secciones)
├── css/
│   └── styles.css      Diseño, grilla semanal, tablas, responsive y animaciones
├── js/
│   └── app.js          Menú móvil, filtros, buscador, contadores y formulario
└── data/
    └── GYM.sql         Copia descargable de la base de datos
```

## Qué muestra y de qué tabla sale

| Sección | Datos de `GYM.sql` |
| --- | --- |
| Hero / estadísticas | Conteos de `socio`, `clase`, `profesor` |
| Planes | 15 registros de `plan` (nombre, precio, duración) |
| Grilla semanal | `clase` + `profesor` + cupos calculados con `inscripcion_clase` |
| Equipo | 15 registros de `profesor` y cantidad de clases asignadas |
| Socios | 18 registros de `socio` + plan actual según el último `pago` |
| Pagos | 18 registros de `pago`, total recaudado y recaudación por mes |
| Modelo de datos | Estructura de las 6 tablas y sus claves |

## Funcionalidades

- Diseño responsive (celular, tablet y escritorio).
- Filtro de planes por duración.
- Buscador de socios por nombre, DNI o plan (sin distinguir acentos).
- Grilla semanal con cupos ocupados por clase.
- Gráfico de recaudación mensual hecho con CSS.
- Formulario de contacto de demostración (no envía datos a ningún servidor).
- Animaciones suaves y respeto por `prefers-reduced-motion`.

## Notas

- Los datos son los de ejemplo del archivo `GYM.sql` (18 socios, 15 planes,
  15 profesores, 15 clases, 18 inscripciones y 18 pagos).
- El “plan actual” de cada socio se deduce del pago más reciente registrado.
- El sitio no usa backend: toda la información está escrita en el HTML.
  Si actualizás la base de datos, hay que actualizar las secciones a mano.
- Las imágenes de fondo y las tipografías se cargan desde Unsplash y Google Fonts.
  Sin conexión, el sitio sigue funcionando con los degradados y las fuentes del sistema.
- Los precios y datos personales son ficticios y forman parte del trabajo práctico.

## Publicación

### GitHub

El proyecto ya está inicializado como repositorio Git en la rama `main`.
Para subirlo, creá un repositorio vacío en GitHub (sin README ni `.gitignore`)
y luego ejecutá:

```bash
cd GYM_Web
git remote add origin git@github.com:USUARIO/REPOSITORIO.git
git push -u origin main
```

### Netlify

**Opción rápida (sin repositorio):** entrá a <https://app.netlify.com/drop> y
arrastrá la carpeta `GYM_Web`. El sitio queda publicado al instante, pero no se
actualiza solo cuando cambiás archivos.

**Opción recomendada (con GitHub):** en Netlify elegí *Add new site → Import an
existing project → GitHub*, autorizá la cuenta y seleccioná el repositorio.
Dejá el comando de build vacío y usá `.` como directorio de publicación
(ya está definido en `netlify.toml`). Cada `git push` a `main` vuelve a publicar
el sitio automáticamente.

---

Proyecto académico · Base de Datos II · Merlín Ian Cumar Vinci · 2026
