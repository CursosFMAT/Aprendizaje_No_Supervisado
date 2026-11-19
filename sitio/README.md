# Página web del curso

Página publicada en https://cursosfmat.github.io/Aprendizaje_No_Supervisado/

## Archivos

| Archivo | Para qué sirve |
| --- | --- |
| `contenido.toml` | Texto de la página: datos del curso, evaluación, unidades, temas de cada sesión, recursos. |
| `estilo.css` | Diseño de la página. |
| `construir.py` | Genera la página en `_site/` a partir de `contenido.toml` y de los materiales del repositorio. |
| `../.github/workflows/pagina.yml` | Publica la página en GitHub Pages en cada push a `main`. |

La carpeta `_site/` se genera y no se guarda en git.

## Cómo se detectan los materiales

No hay que anotar las presentaciones en ningún lado. El script las busca:

- **Presentación de la sesión N**: `Sesion_N/SesionN-*.pdf`, por ejemplo `Sesion_3/Sesion3-Jerarquico.pdf`.
  Si existe, el botón «Presentación (PDF)» se activa; si no, aparece «Presentación: próximamente».
- **Notebooks de la sesión N**: cualquier `Sesion_N/*.ipynb`. Cada uno agrega los botones
  «Notebook» y «Abrir en Colab».

Si un PDF tiene otro nombre, se indica en la sesión con `presentacion = "ruta/al/archivo.pdf"`.

## Publicar materiales nuevos

1. Compilar la presentación y dejar el PDF como `Sesion_N/SesionN-Tema.pdf`.
2. Si cambiaron temas, títulos o la evaluación, editar `sitio/contenido.toml`.
3. (Opcional) Revisar la página en local:
   ```
   python3 sitio/construir.py
   ```
   y abrir `_site/index.html` en el navegador. El script lista qué sesiones tienen
   presentación y avisa si algún archivo todavía no está en git.
4. Hacer commit y push a `main`. En uno o dos minutos la página se actualiza sola.

Para ver el avance de la publicación: pestaña **Actions** del repositorio, o
`gh run list --workflow pagina.yml`. Para volver a publicar sin cambios: `gh workflow run pagina.yml`.

## Configuración (una sola vez)

En GitHub: **Settings → Pages → Source: GitHub Actions**.
