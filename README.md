# CasoIA

Feedback formativo de supuestos prácticos de contabilidad, **sin nota**. Aplicación web de un solo fichero (`index.html`), pensada como referente para **Contabilidad de Sociedades**, **Planificación Contable** y **Normas Internacionales de Información Financiera (NIIF)**.

**Usar la app:** https://fborrasumh.github.io/casoia/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23335768.svg)](https://doi.org/10.5281/zenodo.23335768)

**Idiomas:** español (por defecto), inglés y portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

- **Actividad:** enunciado, solución orientativa (opcional) y rúbrica editable por asignatura (tres perfiles de partida y «otra materia»). Se pueden subir Word, PDF con texto, PowerPoint o texto. La rúbrica admite el formato `criterio | peso | grupo A1, A2; grupo B1, B2`; el peso solo ordena qué mejorar primero.
- **Solución generada con IA (opcional):** a partir del enunciado, la IA redacta la solución **dos veces de forma independiente**; el código comprueba que el asiento cuadre, compara ambas (cuentas, importes, normas), señala los importes que ha calculado la IA y muestra los supuestos que ha hecho. Es un borrador: **no se usa para contrastar entregas hasta que el profesorado la revisa y lo confirma**, y no entra en la ficha del alumnado mientras no esté revisada. El Word completo deja constancia de que se generó con IA y se revisó.
- **Entregas por lote:** un fichero por estudiante, con un código (E01, E02…). El nombre del fichero no se envía ni se exporta.
- **Revisión local, sin IA y sin coste:** por criterio indica si hay evidencia en el texto («Logrado», «En desarrollo», «No evidenciado»), con la frase literal. Extrae cuentas del plan, normas (NIC/NIIF) e importes y los contrasta con la solución. Suma lo que sigue a «Debe» y a «Haber» y avisa si el asiento no cuadra.
- **Análisis con IA (opcional):** evidencias literales por criterio, fortalezas, mejoras, una pista y una pregunta socrática. El código comprueba cada cita contra la entrega; si la IA dice «logrado» sin una cita verificada, el criterio pasa a «sin evidencia verificada». Avisa de cifras que la IA menciona y no están en el material.
- **Sin nota:** el prompt la prohíbe y el código la detecta (p. ej. «7/10», «aprobado»): reescribe una vez y, si persiste, elimina esas frases y lo indica.
- **No filtra la solución:** se eliminan de la pista, la pregunta y las mejoras las frases con importes, cuentas o normas de la solución que ni el enunciado ni la entrega mencionan.
- **Informes:** Word por estudiante en dos versiones (para el estudiante, sin solución; completa, para el profesorado), ZIP del lote, CSV de resumen y detalle (sin ninguna columna de nota) y JSON reproducible.
- **Resumen del grupo:** criterios por nivel de evidencia, cuentas, normas e importes que más faltan y asientos que no cuadran.
- **Modo alumnado:** ficha JSON o página HTML con la actividad incrustada. El estudiante trabaja un borrador con su propia clave y recibe feedback orientativo. Por defecto la ficha no incluye la solución ni los términos de evidencia de la rúbrica.
- **Ejemplo sin clave** (reparto del resultado de ALFA, S.A.) en los tres idiomas.

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude. La clave se guarda solo en el navegador. No hace falta servidor ni se usan modelos locales.

## Privacidad

- Todo se guarda en el navegador (IndexedDB); la clave, en `localStorage`.
- Solo si se pulsa «Analizar con IA» salen hacia el proveedor elegido: enunciado, solución, rúbrica y la entrega, con correos, DNI/NIE, teléfonos y el nombre indicado enmascarados. Se envía el código (E01…), nunca el nombre del fichero. Antes del primer envío de la sesión se muestra una muestra y se pide confirmación.
- Ningún fichero exportado incluye nombres ni la clave.

## Límites

- **No pone nota ni la propone.** «Logrado» significa que hay evidencia del criterio en el texto, no que el cálculo sea correcto: importes y asientos se contrastan aparte con la solución.
- El cuadre Debe/Haber es orientativo: depende de cómo esté escrito el texto.
- No lee imágenes ni PDF escaneados (no hace OCR) ni las imágenes incrustadas en Word o PowerPoint.
- Una solución generada con IA puede ser errónea aunque las dos generaciones coincidan: la revisión del profesorado es obligatoria y es lo que la valida.
- La IA puede equivocarse; el feedback es una primera revisión que valida el profesorado.
- Quien abra la ficha JSON puede leer su contenido: si los términos de evidencia o la solución contienen resultados, no se deben incluir.

## Pruebas

```bash
node tests/nucleo_test.js
NODE_MODULES=/ruta/node_modules python3 tests/casoia_test.py   # Playwright; requiere docx@8.5.0 jszip mammoth pdfjs-dist@3.11.174
```

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) y Mónica González Morales (Universidad Miguel Hernández de Elche).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. y González Morales, M. (2026). *CasoIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.23335768](https://doi.org/10.5281/zenodo.23335768)

## Licencia

MIT. Véase [LICENSE](LICENSE).
