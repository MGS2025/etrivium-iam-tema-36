# Tema 36 — Changelog

> **Título oficial**: Seguridad y protección en redes de comunicaciones. Seguridad perimetral. Acceso remoto seguro a redes. Redes privadas virtuales (VPN). Seguridad en el puesto del usuario.

---

## v1.0 — 2026-08-27 — Primera versión

Generación completa del tema desde el esqueleto oficial `Test_Prompting/temas agosto/36.md`, siguiendo el patrón de la serie técnica (plantilla de referencia: **T35**).

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | 5 secciones · 17 subsecciones · 15 epígrafes de tercer nivel · **≈ 24.200 palabras** |
| Diagramas SVG inline | **19** |
| Banco de test | **60 preguntas** A/B/C, balanceadas **20/20/20** |
| Casos prácticos | **3**, de 10 puntos cada uno |
| Fuentes | 63 Tier 1 · 6 Tier 2 · 3 Tier 3 · más un Tier 4 de fuentes descartadas |
| Pestañas del `index.html` | 8 (Inicio, Contenido, Índice, Diagramas, Test, Casos, Validación, Fuentes) |

### Decisiones de generación

1. **Estructura literal del esqueleto, sin ajustes.** Es el **segundo esqueleto de la serie de agosto que encaja sin retoques** en los tres niveles de numeración (`N`, `N.M`, `N.M.K`), tras el del T35: sus cinco bloques, sus diecisiete subapartados y sus quince epígrafes de tercer nivel se corresponden uno a uno con el contenido. No se repite el problema de mapeo de los Temas 27 y 30.

2. **Extensión: ≈ 24.200 palabras, el segundo tema más extenso de la serie**, solo por detrás del T32 (≈ 25.000) y por delante de T30 (≈ 21.400) y T29 (≈ 21.200). La causa es estructural, la misma que en aquellos: **el enunciado une cinco materias completas** que en la práctica pertenecen a equipos distintos —arquitectura de red, perímetro, identidad, comunicaciones cifradas y puesto de usuario—.

3. **La frontera con cuatro temas vecinos se declara desde las «Convenciones» y vertebra todo el tema.** Es el tema con más solapes de la serie. Criterio aplicado: **el T32 explica la criptografía y aquí se aplica a la red**; **el T34 explica los protocolos y aquí se da por sabido**; **el T35 desarrolla TLS y HTTPS y aquí TLS aparece solo como mecanismo de capa 4 y base de las VPN SSL/TLS**; **el T37 describe la red local y aquí solo se toma lo que es medida de seguridad** (VLAN, 802.1X, segmentación). Anotado como punto 2 de validación.

4. **Todo el ENS citado procede del PDF oficial del BOE**, texto consolidado (`BOE-A-2022-7191`), extraído con `pdftotext -layout`. De ahí salen **literales** los textos y las tablas de aplicación de `mp.com.1` a `mp.com.4`, `mp.eq.1` a `mp.eq.4`, `op.mon.1` a `op.mon.3`, `op.acc.1` a `op.acc.6`, `op.exp.2`, `op.exp.4`, `op.exp.6`, `op.pl.5`, `mp.per.3`, `mp.per.4`, `mp.s.1` a `mp.s.4` y `mp.info.6`, más los arts. 9, 10, 11, 20, 21, 22, 23 y 24. Esa lectura directa aportó cuatro precisiones que las fuentes secundarias suelen dar mal o no dar:

   - **`mp.com.2.1` exige literalmente VPN**: «se emplearán **redes privadas virtuales cifradas** cuando la comunicación discurra por redes fuera del propio dominio de seguridad». La VPN no es una recomendación técnica: es texto normativo.
   - **`mp.com.4.r2` implementa los segmentos mediante VPN**, y **`mp.com.4.r1.2`** obliga a segregar como mínimo en **usuarios, servicios y administración**, mientras que **`mp.com.4.2`** obliga a que las comunicaciones **inalámbricas** vayan en **segmento separado**.
   - **`op.exp.6.r4` nombra el EDR por su sigla**, en texto normativo, y lo hace exigible en **categoría ALTA**; y **`op.exp.6.r3`** es la **lista blanca de aplicaciones**.
   - **`mp.eq.2` (bloqueo del puesto) NO aplica en nivel BAJO**, y **`mp.com.4` NO aplica en categoría BÁSICA**, mientras que **`mp.com.1` (perímetro) sí aplica en las tres**. Estas tres asimetrías son la fuente número uno de errores en las preguntas del ENS y se han convertido en preguntas del test (P13, P14, P56).

5. **⚠️ Hallazgo normativo: la ITS de Interconexión a la que remite `mp.com.1` NO está publicada.** Verificado en el portal oficial del ENS del CCN: a agosto de 2026 solo hay **cuatro Instrucciones Técnicas de Seguridad** en el BOE —Conformidad e Informe del Estado de la Seguridad (2016), Auditoría y Notificación de Incidentes (2018)—, y tampoco están la de **Criptología** ni la de **Adquisición de productos de seguridad**. El propio `mp.com.1` anuncia que esa ITS «determinará los requisitos establecidos en el perímetro… en función de la categoría». Es un dato de alto valor examinable y un argumento profesional: en su ausencia, la referencia práctica del perímetro son las **guías CCN-STIC**, en particular la **408**.

6. **⚠️ Tres hallazgos de la verificación contra el índice oficial del RFC Editor** —descargado y grepeado, no consultado de memoria—, que prácticamente ningún material de oposición recoge todavía:

   - **RFC 9887 (diciembre de 2025): TACACS+ sobre TLS 1.3.** Actualiza el RFC 8907 y resuelve la debilidad histórica del protocolo, cuyo cifrado propio basado en MD5 nunca fue considerado sólido. Los temarios al uso siguen diciendo que TACACS+ «cifra todo el cuerpo» sin matizar con qué.
   - **RFC 9765 (abril de 2025): RADIUS/1.1**, que elimina el uso de **MD5** apoyándose en la negociación **ALPN**. Su estado es **Experimental**, matiz que se explica en el contenido porque no todo lo publicado como RFC es norma. Antes de él, la única protección de RADIUS eran **RadSec** (RFC 6614) y RADIUS sobre DTLS (RFC 7360), también experimentales.
   - **RFC 10024 (agosto de 2026): intercambio híbrido post-cuántico para TLS 1.3**, Proposed Standard, precedido del RFC 9954 en julio. Junto con los RFC 8784, 9370 y 9867 para IKEv2, permite responder con precisión a la amenaza de **«cosecha ahora, descifra después»**, que afecta especialmente a las VPN.

   Se confirmó además, de la misma verificación, que **el RFC 8446 (TLS 1.3) sigue obsoletado por el RFC 9846 de julio de 2026** —hallazgo original del T35, que este tema reutiliza— y que **IKEv1 está formalmente obsoleto desde el RFC 9395 (abril de 2023)**, mientras que **IKEv2 tiene la categoría de Internet Standard, STD 79**.

7. **Cifras de amenaza verificadas en la publicación oficial de ENISA**, no en resúmenes de terceros: **4.875 incidentes** entre el 1-7-2024 y el 30-6-2025; **DDoS 77 %** de los incidentes notificados pero solo **2 %** con interrupción real; **phishing 60 %** y **explotación de vulnerabilidades 21,3 %** como vectores de acceso inicial; y **más del 80 %** de la ingeniería social observada a principios de 2025 apoyada en **IA**. Ese último dato se ha convertido en un argumento del contenido: **enseñar a detectar phishing «por las faltas de ortografía» es hoy formación obsoleta**.

8. **Base legal del teletrabajo público incorporada como pieza central de §3**, y no como adorno: **art. 47 bis del TREBEP**, introducido por el **RDL 29/2020**, con su exigencia de que **«la Administración proporcionará los medios tecnológicos necesarios»** — que es el fundamento jurídico para rechazar el BYOD en el Caso 2, y no solo un argumento técnico.

9. **Sin fragmentos de código**, como en T26, T28, T29, T30, T31, T32 y T35. Lo memorizable aquí son **códigos de medida, puertos, números de protocolo IP, números de RFC y tablas de aplicación**. Sí se incluye una **tabla de reglas de cortafuegos** en el ejercicio resuelto de §2.2.1, por ser objeto directo de pregunta en los casos prácticos oficiales.

10. **Secuencia de letras del test fijada antes de redactar.** Aplicando la lección de T23, se definió de antemano la secuencia completa de 60 respuestas con 20 de cada letra. Resultado: **20/20/20 a la primera**, verificado por script.

11. **Corrección durante la redacción, anotada por transparencia**: en un primer borrador del test, el bloque P31-P60 se llenó con preguntas de §3 y §4 y **§5 (seguridad en el puesto del usuario) se quedó sin ninguna pregunta**. Se detectó antes de ensamblar el fichero y se reescribió el bloque completo respetando la secuencia de letras ya fijada, quedando §5 con nueve preguntas (P52-P60). La lección, que conviene incorporar al workflow: **con esqueletos de cinco materias, hay que comprobar la cobertura por sección antes de dar el test por bueno**, no solo la distribución A/B/C.

12. **Autocrítica declarada en la validación**: el reparto de preguntas no es equilibrado en número —33 para las dos primeras materias, 27 para las tres últimas—, porque §1 absorbe el marco normativo del ENS, que es transversal. Se propone mantenerlo, con la corrección mecánica descrita por si María o el IAM prefieren 12 por materia.

13. **Novedad de este tema: un Tier 4 de fuentes consultadas y NO utilizadas**, con el motivo del descarte —documentación comercial de fabricantes, términos de mercado sin norma, WireGuard y la documentación de la red SARA—. Permite que la validación compruebe el criterio en lugar de suponerlo, y deja explícita la decisión pendiente sobre **WireGuard**, que es hoy uno de los protocolos VPN más extendidos pero **no tiene RFC**.

14. **19 diagramas SVG**, uno más que el máximo anterior de la serie (18, en T32 y T35), justificado por las cinco materias del enunciado. Aplicadas todas las reglas de composición aprendidas: clases con sufijo único por diagrama; **nunca `class` y atributo `fill` en el mismo elemento**; atribución `[Fuente: …]` separada del último elemento dibujado; y tildes revisadas también en **mayúsculas** y en los `aria-label`.

15. **La frontera con el Tema 39 se declaró tarde y se corrigió.** El T39 es «Principios básicos del Esquema Nacional de Seguridad y el Esquema Nacional de Interoperabilidad», y §1.1 de este tema resume los principios de los arts. 5 a 11. El solape es real y estaba sin declarar. Criterio incorporado a las «Convenciones»: **en el T39 el ENS es la materia; aquí el ENS entra solo por las medidas aplicables a la red y al puesto**, y los principios se resumen como llave de lectura de esas medidas. Las **trece referencias cruzadas** del tema (T23, T27 a T35, T37 y T39) se han validado una a una contra el enunciado oficial del BOAM 10.032.

### ⚠️ Dos bugs del utillaje de QA corregidos en la copia canónica

Detectados al ejecutar el QA de este tema, y arreglados en `_tools-qa/qa_shots.py` para toda la serie:

1. **El número de diagramas a capturar estaba fijado a mano**: el bucle era `range(1,19)` y, con **19** diagramas, dejaba **el último sin capturar** — silenciosamente, porque el script no falla. Corregido para recorrer **todos** los SVG detectados.
2. **Falso resultado del headless, de la misma familia que los tres ya documentados**: el bucle de espera rompía en cuanto el DOM tenía **algún** SVG, y llegó a leer **4 de 19**, produciendo un juego de capturas incompleto con un mensaje de éxito. Corregido para esperar a que el recuento del DOM **coincida con el del fichero** y **abortar** si no llega a cuadrar. Además, el directorio de salida estaba fijado al *scratchpad* de una sesión antigua que ya no existía; ahora se deriva en tiempo de ejecución.

### QA ejecutado antes de publicar

- **Validación XML** de los 19 SVG y comprobación de que el número de SVG del DOM coincide con el del fichero (control del tercer falso OK documentado).
- **Medición con `getBBox`** sobre render real con la pestaña Diagramas **forzada a visible**: desbordes del `viewBox`, colisiones entre textos y **texto solapado con un `<rect>` que no lo contiene**.
- **Captura visual de los 19 diagramas** a PNG 2x y revisión una a una, porque el QA programático no ve ni los rótulos que no cuadran con lo que encabezan ni los colores ilegibles por la cascada CSS. **Volvió a demostrar su utilidad**: con el script ya en verde (0 desbordes, 0 colisiones), la revisión a ojo cazó seis defectos más — dos rótulos rozando el borde de su caja en D1, una denominación pegada a la columna contigua en D6, un texto desbordando un círculo en D7, una repetición fea («la red se queda sin red») y dos columnas que se tocaban en D10, un título mal partido en dos líneas en D13 y una celda invadiendo la columna vecina en D15.
- **Comprobación post-build de markdown crudo**: recuento de asteriscos y de `|---` en el `index.html` tras eliminar `<script>`, `<svg>`, `<style>` y `<pre><code>`.
- **Verificación del banco de test por script**: 60 preguntas, 3 opciones únicas, coincidencia exacta entre el texto de la opción correcta y el de la solución, y distribución A/B/C.
- **Prueba del motor de test sobre HTTP** (no sobre `file://`): render, penalización 1/3, corregir y reiniciar.
