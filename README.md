# OralIA · Evaluador Oral

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21423283.svg)](https://doi.org/10.5281/zenodo.21423283)

**Aplicación:** https://fborrasumh.github.io/evaluador_oral/

**OralIA** es la versión 2.0 del Evaluador Oral. Prepara un examen oral a partir del **trabajo del estudiante**: un cuaderno, un informe, un código o unos apuntes. Varios agentes redactan preguntas ancladas en ese material, el estudiante responde de viva voz, la app repregunta si falta algo y al final hay un informe con rúbrica que **el docente revisa antes de poner la nota**. Aplicación de un solo fichero (`index.html`), sin servidor.

## Novedades de la versión 2.0

- Recorrido guiado con el estilo de Forja (Preparar → Preguntas → Examen → Informe) y **dos modos**: *Practicar* (el estudiante prepara su defensa) y *Evaluar* (con el docente).
- **Ejemplos**: un informe completo que se ve sin clave y tres materiales de prueba (bioestadística, Python e historia).
- **Lectura real de PDF y Word.** Antes, el PDF se leía como texto plano y llegaba basura a los agentes. También admite cuadernos Jupyter, código, texto, CSV y JSON.
- **Citas comprobadas**: cada pregunta cita el fragmento del material en el que se apoya y la app comprueba que existe; si no, el verificador la sustituye.
- **Revisión de las preguntas** antes del examen: editar, cambiar por otra, quitar o añadir una propia.
- **Tres formas de responder**: transcripción del navegador (gratis, Chrome y Edge), transcripción de OpenAI (cualquier navegador) o respuesta escrita. El idioma del examen se elige entre variantes del español y del portugués, catalán e inglés.
- **Repreguntas**: si la respuesta deja fuera un punto clave de la rúbrica, se hace una pregunta breve para completarla.
- **Calificación coherente con la rúbrica**: si la nota del agente no cuadra con los puntos cumplidos, se corrige y se explica.
- **Informe revisable**: el docente ajusta la nota de cada pregunta y añade comentarios; se exporta a Word, CSV y JSON.
- **Integridad corregida.** La versión 1 asignaba una fluidez de 88 % (el umbral de sospecha máxima) cuando no la había podido medir, y juzgaba si el texto «sonaba a IA» sobre una transcripción automática que elimina las muletillas. Ahora solo se usan medidas objetivas, presentadas como orientativas.
- Tiempo máximo por respuesta, pausa y reanudación del examen.

## Privacidad

El material se lee en el navegador. El texto viaja a OpenAI con la clave del usuario, guardada en `localStorage` (`ia_openai_key`); el audio solo se envía si se elige la transcripción de OpenAI. La nota propuesta y los indicadores de integridad son orientativos: la decisión corresponde al docente.

## Cómo citar

Borrás Rocher, F. (2026). *Evaluador Oral (OralIA)* (versión 2.0.0) [Software]. Universidad Miguel Hernández de Elche. https://doi.org/10.5281/zenodo.21423283

El DOI es el de concepto: apunta siempre a la última versión. GitHub ofrece la cita en formato APA y BibTeX con el botón *Cite this repository*, a partir de `CITATION.cff`.

Forma parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT © 2026 Fernando Borrás Rocher · Universidad Miguel Hernández de Elche.
