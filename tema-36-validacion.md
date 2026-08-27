# Tema 36 — Validación

> **Título oficial**: Seguridad y protección en redes de comunicaciones. Seguridad perimetral. Acceso remoto seguro a redes. Redes privadas virtuales (VPN). Seguridad en el puesto del usuario.
>
> **Versión**: v1.0 — **Pendiente de validación por María, Ana y el IAM**
> **Fecha**: 2026-08-27

---

## 1. Cobertura del temario oficial

El enunciado oficial (BOAM 10.032, tema 36) enumera **cinco materias**. Correspondencia con las secciones del contenido:

| Enunciado oficial | Sección | Estado |
|---|---|---|
| **Seguridad y protección en redes de comunicaciones** | §1 | ✅ Completo |
| **Seguridad perimetral** | §2 | ✅ Completo |
| **Acceso remoto seguro a redes** | §3 | ✅ Completo |
| **Redes privadas virtuales (VPN)** | §4 | ✅ Completo |
| **Seguridad en el puesto del usuario** | §5 | ✅ Completo |

El **esqueleto de partida** (`Test_Prompting/temas agosto/36.md`) se ha seguido **literalmente**: sus **cinco bloques de primer nivel**, sus **diecisiete subapartados** y sus **quince epígrafes de tercer nivel** se corresponden uno a uno con la numeración `N`, `N.M` y `N.M.K` del contenido. **Es el segundo esqueleto de la serie de agosto que encaja sin ajustes en los tres niveles**, tras el del Tema 35, y a diferencia de lo ocurrido en los Temas 27 y 30 — donde el mapeo sigue pendiente de una decisión de criterio que conviene unificar.

## 2. Contenido teórico

- **5 secciones · 17 subsecciones · 15 epígrafes de tercer nivel** (numeración de tres niveles, coherente con el resto de la serie técnica).
- **≈ 24.200 palabras** medidas con `wc -w`. Es **el segundo tema más extenso de toda la serie**, solo por detrás del **T32 (≈ 25.000)** y por delante del **T29 (≈ 21.200)** y el **T30 (≈ 21.400)**. La causa es estructural y la misma que en aquellos: el enunciado une **cinco materias completas** que en la práctica profesional pertenecen a equipos distintos.
- **4 tipos de callout**: `[DATO CLAVE EXAMEN]`, `[EJERCICIO RESUELTO]`, `[EJEMPLO AYTO MADRID]` y `[REFERENCIA CRUZADA]`.
- **Caso de referencia transversal**: la red corporativa municipal del IAM, con tres piezas que reaparecen en cada sección —el CPD, una oficina de atención a la ciudadanía de distrito y el portátil de un empleado que teletrabaja—. Las cinco secciones se presentan explícitamente como **cinco preguntas sobre el mismo escenario**.
- **Sin fragmentos de código**, como en T26, T28, T29, T30, T31, T32 y T35. Decisión deliberada: el enunciado no menciona ningún lenguaje y lo memorizable son **códigos de medida del ENS, puertos, números de protocolo IP, números de RFC y tablas de aplicación**, que se concentran en tablas y en los diagramas D5, D6, D16 y D17. Sí se incluye **una tabla de reglas de cortafuegos** en el ejercicio resuelto de §2.2.1, por ser objeto directo de pregunta en los casos prácticos oficiales.
- Cierre con un bloque de **«los ocho datos que no se pueden fallar»**, no numerado, a modo de resumen memorístico.

## 3. Fuentes

- **Tier 1**: 63 referencias (normativa española y europea, seis guías CCN-STIC, y especificaciones del IETF, IEEE, ISO/IEC y NIST).
- **Tier 2**: 6 referencias de informes, hojas de ruta institucionales y documentación de soporte, todas fechadas.
- **Tier 3**: 3 referencias de contexto municipal.
- **Tier 4**: se ha añadido, como novedad de este tema, un apartado de **fuentes consultadas y NO utilizadas** con el motivo del descarte, para que la validación pueda comprobar el criterio.
- **Verificación contra fuente primaria** (no de memoria ni de fuentes secundarias):
  - **ENS**: se descargó el **PDF oficial del BOE** del texto consolidado (`BOE-A-2022-7191`) y se extrajo con `pdftotext -layout`. De él proceden **literales** los textos y las tablas de aplicación de `mp.com.1` a `mp.com.4`, `mp.eq.1` a `mp.eq.4`, `op.mon.1` a `op.mon.3`, `op.acc.1` a `op.acc.6`, `op.exp.2`, `op.exp.4`, `op.exp.6`, `op.pl.5`, `mp.per.3`, `mp.per.4`, `mp.s.1` a `mp.s.4` y `mp.info.6`, así como los artículos 9, 10, 11, 20, 21, 22, 23 y 24.
  - **RFC**: se descargó el **índice oficial del RFC Editor** (`rfc-index.txt`) y se comprobaron uno a uno **número, título, fecha, estado y relaciones de obsolescencia** de los RFC citados. De ahí salieron los tres hallazgos del punto 8.
  - **Instrucciones Técnicas de Seguridad**: comprobado en el **portal oficial del ENS del CCN** que solo hay **cuatro publicadas** y que **no** está la de Interconexión, a la que remite `mp.com.1`.
  - **Cifras de amenaza**: verificadas en la publicación oficial de **ENISA** (ETL 2025), y no en resúmenes de terceros.
  - **Fin de soporte de Windows 10 y programa ESU**: verificado en la documentación oficial del fabricante.

## 4. Test (60 preguntas)

- **60 preguntas** de 3 opciones (A/B/C), formato oficial de la oposición, con penalización de **1/3** en el motor de corrección.
- **Distribución de la respuesta correcta: 20 A / 20 B / 20 C**, conseguida **a la primera** por haber fijado la secuencia completa de letras **antes** de redactar (lección aprendida en T23) y verificada por script.
- Reparto por materia: **P1-P16** fundamentos, amenazas, mecanismos por capa y ENS en la red · **P17-P33** seguridad perimetral, incluida la confianza cero · **P34-P41** acceso remoto seguro · **P42-P51** redes privadas virtuales · **P52-P60** seguridad en el puesto del usuario.
- **Nota de autocrítica para la validación**: el reparto no es equilibrado en número. Las dos primeras materias suman **33** preguntas y las tres últimas **27**, cuando en el enunciado oficial pesan lo mismo. La razón es que §1 absorbe el marco normativo del ENS, que es **transversal a las otras cuatro secciones** y del que se pregunta mucho. **Si María o el IAM prefieren un reparto de 12 por materia, la corrección es mecánica** y no exige rehacer el banco: bastaría convertir cuatro preguntas de §1.4 (marco ENS) en preguntas de §4 y §5, conservando su letra correcta para no romper el 20/20/20.
- Verificación automática: 60 preguntas, 3 opciones únicas por pregunta, **coincidencia exacta** entre el texto de la opción correcta y el de la solución, y referencia a epígrafe y fuente en las 60.

## 5. Casos prácticos (3)

Los tres se sitúan en el Ayuntamiento de Madrid y comparten el escenario de referencia del tema:

1. **Rediseño del perímetro y la red de una oficina de distrito** (§1.4, §2, §4.2.3): segmentación de un armario con puestos, impresoras, cámaras IP y Wi-Fi público; un encaminador 4G contratado al margen del IAM como salida no controlada; la trampa de la «VPN MPLS» del operador, que **no cifra**; y la publicación de un servicio de cita previa en DMZ.
2. **Acceso remoto y VPN para 900 empleados en teletrabajo** (§3, §4, §5): autenticación sin segundo factor en categoría MEDIA; cuentas compartidas de proveedor; pasarela en la red interna; túnel dividido; equipo personal frente al art. 47 bis del TREBEP; y elección de tecnología para teletrabajo y para el enlace con el centro de respaldo.
3. **Incidente de ransomware entrado por un portátil municipal** (§1.2, §2.3, §5): reconstrucción de la cadena en ocho eslabones con la medida del ENS que habría detenido cada uno, contención ordenada de las dos primeras horas, la **doble obligación de notificación** (CCN-CERT por el ENS y AEPD en 72 horas por el RGPD) y plan de mejora priorizado.

Cada caso suma **10 puntos** repartidos en cuatro cuestiones, con solución orientativa y tabla de criterios de evaluación.

## 6. Diagramas (19 SVG)

- **19 diagramas** SVG inline, sin dependencias externas, con `viewBox`, `role="img"` y `aria-label` descriptivo en castellano.
- Clases CSS con **sufijo numérico único por diagrama** (`.t1`, `.h1`… `.t19`, `.h19`), para evitar la colisión de estilos entre los 19 SVG embebidos en la misma página — el bug sistémico detectado en el T5.
- **Regla aplicada desde el T33 y T34**: dentro de un mismo elemento **nunca se mezclan `class` y atributo `fill`**, porque en la cascada CSS la clase gana al atributo de presentación y el texto sale del color equivocado. Cuando hacía falta un color distinto se declaró una clase propia. **Comprobado por script**: `grep 'class="[a-z]*[0-9]*" fill='` devuelve vacío.
- Diagramas de mayor valor para el estudio: **D6** (matriz de medidas del ENS por categoría, el más rentable del tema), **D5** (tabla de protocolos y puertos), **D10** (IDS frente a IPS con la matriz de los cuatro resultados), **D16** (taxonomía de VPN con qué cifra cada protocolo) y **D17** (estructura del paquete IPsec en los dos modos).

## 7. Fronteras con otros temas

Declaradas expresamente en las «Convenciones» del contenido, porque es el tema con más solapes de la serie:

| Tema | Qué le corresponde | Qué se toma de él aquí |
|---|---|---|
| **T32** | Criptografía, firma digital, PKI, seguridad física y lógica | Se **aplica** a la red, no se reexplica |
| **T34** | Protocolos TCP/IP y modelo OSI: cabeceras, saludo, ARP, ICMP | Se da por sabido; solo se usa para situar cada defensa en su capa |
| **T35** | Internet, HTTP, HTTPS y el saludo TLS | TLS aparece solo como mecanismo de capa 4 y como base de las VPN SSL/TLS |
| **T37** | Redes locales, tipología, dispositivos de interconexión | Se toma únicamente lo que es medida de seguridad: VLAN, 802.1X, segmentación |
| **T39** | El **ENS como marco**: ámbito, gobernanza, principios, categorización, auditoría y conformidad, junto con el ENI | Aquí el ENS entra **solo por las medidas** aplicables a la red y al puesto; los principios de los arts. 5 a 11 se resumen en §1.1 como llave de lectura, no como materia propia |
| **T23** | Desarrollo web y OWASP | Solo se cita como catálogo de lo que mitiga un WAF |
| **T27, T28, T29, T30, T31** | Administración del SO, virtualización, CAU, administración de la LAN, nube | Referencias cruzadas explícitas en §5 y §2.4.2 |

**Punto de validación**: conviene que el IAM confirme que el criterio de frontera con el **T32** es el correcto, es decir, que en el examen del T36 **no** se espera que el opositor explique cómo funciona AES o una firma digital, sino qué protocolo de red usa qué mecanismo y en qué capa.

## 8. Hallazgos de la verificación de fuentes

Tres datos que **prácticamente ningún material de oposición recoge todavía**, todos verificados contra fuente primaria:

1. **TACACS+ tiene desde diciembre de 2025 una norma que lo lleva sobre TLS 1.3**: el **RFC 9887**, que actualiza el RFC 8907 y resuelve la debilidad histórica del protocolo, cuyo cifrado propio basado en MD5 nunca fue sólido. La mayoría de los temarios siguen describiendo TACACS+ como «cifra todo el cuerpo del mensaje» sin matizar **con qué**.
2. **RADIUS ha recibido una revisión que elimina MD5**: el **RFC 9765**, de abril de 2025, define **RADIUS/1.1** apoyándose en la negociación **ALPN** de TLS. Su estado es **Experimental**, matiz que conviene explicar porque no todo lo publicado como RFC es norma.
3. **El intercambio de claves híbrido post-cuántico para TLS 1.3 se normalizó el mes pasado**: el **RFC 10024**, de **agosto de 2026**, con estado Proposed Standard, precedido del RFC 9954 en julio. Junto con los RFC 8784, 9370 y 9867 para IKEv2, permite responder con precisión a la pregunta de cómo se protege una VPN frente a la amenaza de «cosecha ahora, descifra después».

A ellos se añade un **cuarto hallazgo, de fuente normativa**: **la Instrucción Técnica de Seguridad de Interconexión de Sistemas de Información, a la que remite expresamente `mp.com.1`, no ha sido publicada**. Solo hay **cuatro ITS** en el BOE, y tampoco están la de Criptología ni la de Adquisición de productos de seguridad. Es un dato de alto valor para una pregunta de examen y un argumento profesional: en su ausencia, la referencia práctica del perímetro son las **guías CCN-STIC**, en particular la **408**.

## 9. Puntos que requieren decisión de María, Ana o el IAM

1. **Reparto de preguntas por materia** (ver el punto 4): 33 preguntas para las dos primeras materias frente a 27 para las tres últimas. Se propone mantenerlo, por el peso transversal del marco ENS, pero la corrección a 12 por materia es mecánica si se prefiere.
2. **Frontera con el T32** (ver el punto 7): confirmar que la criptografía no se reexplica aquí.
3. **WireGuard**: es hoy uno de los protocolos VPN más extendidos en la práctica, pero **no tiene RFC** —su especificación es un artículo académico— y por eso se ha dejado fuera del contenido examinable, dejándolo anotado en el Tier 4 de fuentes. **Decisión pendiente**: si el IAM considera que debe mencionarse por su presencia real en el mercado, la incorporación es de media página en §4.2.2.
4. **Términos de mercado (SASE, SSE, ZTNA, NGFW)**: se mencionan advirtiendo expresamente de que **no son estándares**. Confirmar que ese tratamiento es el deseado, o si se prefiere ampliarlos por aparecer en pliegos.
5. **Profundidad de la parte de confianza cero**: se ha desarrollado con los siete principios literales de la NIST SP 800-207 porque son preguntables casi textualmente. Confirmar que ese nivel de detalle es proporcionado para un C1.

## 10. Estado

**v1.0 — pendiente de validación.** El tema está completo en sus ocho entregables (índice, contenido, diagramas, test, casos prácticos, fuentes, validación y changelog) y su `index.html` se genera desde los `.md` mediante `build_t36.py`, de modo que documento y web quedan **sincronizados**.
