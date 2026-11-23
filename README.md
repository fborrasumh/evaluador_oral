# OralIA · Evaluador Oral

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21423283.svg)](https://doi.org/10.5281/zenodo.21423283)

**Aplicación:** https://fborrasumh.github.io/evaluador_oral/

**OralIA** prepara un examen oral a partir del **trabajo del estudiante**: un cuaderno, un informe, un código o unos apuntes. Varios agentes redactan preguntas ancladas en ese material, el estudiante responde de viva voz, la app repregunta si falta algo y al final hay un informe con rúbrica que **el docente revisa antes de poner la nota**. Es una aplicación de un solo fichero (`index.html`), sin servidor.

**Idiomas de la interfaz:** español (por defecto), inglés y portugués, con un selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL). El **idioma del examen** se elige aparte: español de España, de Latinoamérica o rioplatense, portugués de Brasil o de Portugal, catalán/valenciano o inglés.

## Novedades de la versión 3.0

- Reconstruida sobre el esqueleto **Forja**, con interfaz en **tres idiomas** (es/en/pt). El ejemplo existe en cada idioma.
- **Tres proveedores de IA** (OpenAI, Google Gemini y Anthropic Claude), cada uno con la clave de la persona y un desplegable con los modelos disponibles en esa clave.
- **Transcripción con tu proveedor**: OpenAI o Gemini (antes, solo OpenAI). La transcripción del navegador y las respuestas escritas se mantienen.
- **Privacidad**: antes de enviar nada se enmascaran el nombre del estudiante, los correos, los DNI/NIE y los teléfonos, y se muestra un **aviso previo con una muestra** de lo que va a salir.
- El **informe en Word se genera en el navegador, sin depender de ningún CDN**. Antes se cargaba una librería desde cdnjs y fallaba si había un bloqueador o no había red.
- El examen en curso y el informe se guardan en IndexedDB. Si había una sesión de la versión 2 en curso, se recupera.
- Si alguna pregunta no se pudo calificar (por ejemplo, porque se agotó el saldo), «Calificar de nuevo» recalifica **solo** esas preguntas y conserva las notas ya revisadas.
- Al preparar un examen nuevo se ponen a cero las notas y los tiempos del anterior.

## Qué hace

1. **Preparar.** Se indica el modo (*Practicar*, para el estudiante a solas, o *Evaluar*, con el docente), el nombre, la asignatura, el idioma del examen y el material. El material puede ser PDF, Word, PowerPoint, un cuaderno Jupyter, código, texto, CSV o JSON, y se lee en el navegador. Hay tres materiales de prueba.
2. **Preguntas.** Cinco agentes las preparan: Analizador, Diseñador, Evaluador de calidad, Retroalimentador y Verificador. Cada pregunta cita un fragmento literal del material, y **el código comprueba que esa cita existe**. Si no la encuentra, el Verificador intenta sustituirla y la cita se vuelve a comprobar; si sigue sin aparecer, la pregunta queda marcada como «cita no encontrada». Las preguntas se pueden editar, rehacer o quitar, y se pueden añadir preguntas propias.
3. **Examen.** El estudiante responde hablando o por escrito. La transcripción se puede corregir. Si falta un punto clave de la rúbrica, se hace **una repregunta**. Se puede fijar un tiempo máximo por respuesta y pausar el examen.
4. **Informe.** La IA propone una nota con la rúbrica, punto por punto. **El código contrasta esa nota con los puntos cumplidos** (sí = 1, en parte = 0,5): si se separan más de 2,5 puntos, las promedia y lo indica. El docente ajusta la nota de cada pregunta y añade comentarios. El informe se exporta a Word, CSV (con «;», compatible con Excel) y JSON.
5. **Indicadores de integridad** (opcionales, solo en el modo Evaluar): la velocidad al hablar y el tiempo que pasa hasta que el estudiante empieza a responder. Son medidas objetivas y **orientativas**. No se juzga si el texto «suena a IA».

## Privacidad

- **Se queda en el navegador:** la lectura de los archivos, el examen y el informe (en IndexedDB), la clave de IA (en `localStorage`; la de OpenAI, `ia_openai_key`, es compartida con el resto del catálogo), la comprobación de las citas y las descargas.
- **Sale hacia el proveedor de IA:** el texto del material y de las respuestas, con el nombre del estudiante y sus datos personales enmascarados. El audio solo sale si se elige la transcripción con el proveedor, y **la voz no se puede enmascarar**. Antes del primer envío de cada sesión se muestra una muestra de lo que va a salir y se pide confirmación.
- El JSON exportado no contiene claves.

## Límites

- La nota propuesta y los indicadores de integridad son **orientativos**: decide el docente.
- La comprobación de las citas acepta la coincidencia literal (sin distinguir mayúsculas, tildes ni puntuación) o la de la mayor parte de la cita en ventanas de 8 palabras. Comprueba que la cita existe, no que la pregunta sea buena.
- El enmascarado detecta el nombre escrito en el formulario, los correos, los DNI/NIE y los teléfonos españoles. No detecta otros nombres propios que aparezcan en el material. Para prácticas, mejor usar datos ficticios.
- La transcripción del navegador solo funciona en Chrome y Edge, y envía el audio al servicio de voz del propio navegador. Claude no transcribe audio.
- En los PDF escaneados no se lee el texto, porque no hay reconocimiento óptico de caracteres (OCR).
- Se ha probado con IA simulada de los tres proveedores (59 comprobaciones en `tests/oral_test.py`) y en el navegador Chromium. No se ha probado con claves reales ni con micrófono real.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) · ORCID [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. (2026). *Evaluador Oral (OralIA)* (versión 3.0.0) [Software]. Universidad Miguel Hernández de Elche. https://doi.org/10.5281/zenodo.21423283

El DOI es el de concepto y apunta siempre a la última versión. GitHub ofrece la cita en formato APA y BibTeX con el botón *Cite this repository*, que se genera a partir de `CITATION.cff`.

Forma parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT © 2026 Fernando Borrás Rocher · Universidad Miguel Hernández de Elche. Véase [LICENSE](LICENSE).
