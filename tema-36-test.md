# Tema 36 — Test de Autoevaluación

> **Título**: Seguridad y protección en redes de comunicaciones. Seguridad perimetral. Acceso remoto seguro a redes. Redes privadas virtuales (VPN). Seguridad en el puesto del usuario.
> **Formato**: 60 preguntas tipo test A/B/C (formato oficial oposición)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-08-27
> **Fuentes**: ver tema-36-fuentes.md

---

## Instrucciones

- Cada pregunta tiene **3 opciones** (A, B, C). Solo una es correcta.
- Penalización en examen real: respuesta incorrecta descuenta **1/3** del valor de una correcta.
- Tiempo orientativo: 1 minuto por pregunta.
- Distribución: Fundamentos, amenazas, mecanismos por capa y ENS en la red (P1-P16), Seguridad perimetral, incluida la confianza cero (P17-P33), Acceso remoto seguro (P34-P41), Redes privadas virtuales (P42-P51), Seguridad en el puesto del usuario (P52-P60).

---

### Pregunta 1

**¿Cuántas dimensiones de seguridad contempla el Esquema Nacional de Seguridad y cuáles son?**

A) Tres: confidencialidad, integridad y disponibilidad
B) Cinco: confidencialidad, integridad, trazabilidad, autenticidad y disponibilidad
C) Cuatro: confidencialidad, integridad, disponibilidad y no repudio

<details><summary>Respuesta</summary>

**Correcta: B) Cinco: confidencialidad, integridad, trazabilidad, autenticidad y disponibilidad** La nemotécnica es **CITAD**. La opción A recoge la tríada clásica CIA, que es la formulación teórica internacional, pero el marco español añade **trazabilidad** y **autenticidad**, y de cada dimensión se predica un **nivel** que determina qué medidas son exigibles.

*Referencia: §1.1 [ENS]*
</details>

---

### Pregunta 2

**Un sistema tiene confidencialidad MEDIA, integridad MEDIA, trazabilidad BAJA, autenticidad MEDIA y disponibilidad ALTA. ¿Cuál es su categoría?**

A) MEDIA, porque es el nivel que más se repite
B) BÁSICA, porque hay una dimensión en nivel BAJO
C) ALTA, porque basta con que una dimensión sea de nivel ALTO

<details><summary>Respuesta</summary>

**Correcta: C) ALTA, porque basta con que una dimensión sea de nivel ALTO** La categoría se deriva de la **dimensión más exigente**: si alguna es ALTO, el sistema es de categoría ALTA; si ninguna es ALTO pero alguna es MEDIO, es MEDIA; y en el resto de casos, BÁSICA. No se calcula por promedio ni por moda.

*Referencia: §1.1 [ENS]*
</details>

---

### Pregunta 3

**El artículo 9 del ENS, «existencia de líneas de defensa», es el fundamento normativo de:**

A) La defensa en profundidad: varias capas independientes, de modo que el compromiso de una no comprometa el sistema entero
B) La obligación de cifrar toda la información en tránsito por redes públicas
C) La diferenciación entre el responsable de la seguridad y el responsable del sistema

<details><summary>Respuesta</summary>

**Correcta: A) La defensa en profundidad: varias capas independientes, de modo que el compromiso de una no comprometa el sistema entero** El artículo 9 exige «múltiples capas de seguridad» de naturaleza **organizativa, física y lógica**. La opción B corresponde al art. 22 y a `mp.com.2`; la opción C, al art. 11.

*Referencia: §1.1 [ENS]*
</details>

---

### Pregunta 4

**Sobre los conceptos de amenaza, vulnerabilidad y riesgo, señale la afirmación correcta.**

A) La amenaza es una debilidad del propio sistema que se puede corregir aplicando parches
B) El riesgo se elimina por completo si se implantan todas las medidas del anexo II del ENS
C) Sobre la amenaza no se puede actuar: el riesgo solo se reduce actuando sobre la vulnerabilidad o sobre el impacto

<details><summary>Respuesta</summary>

**Correcta: C) Sobre la amenaza no se puede actuar: el riesgo solo se reduce actuando sobre la vulnerabilidad o sobre el impacto** La amenaza existe con independencia de la organización. La debilidad propia es la **vulnerabilidad** (opción A, que invierte los términos), y siempre queda un **riesgo residual** que la dirección debe aceptar formalmente (opción B).

*Referencia: §1.2 [MAGERIT]*
</details>

---

### Pregunta 5

**Según el informe ENISA Threat Landscape 2025, ¿cuál es el vector de acceso inicial dominante en los incidentes analizados?**

A) El phishing, con aproximadamente el 60 % de los accesos iniciales
B) La explotación de vulnerabilidades, con aproximadamente el 60 %
C) El acceso mediante credenciales robadas en la red oscura, con el 45 %

<details><summary>Respuesta</summary>

**Correcta: A) El phishing, con aproximadamente el 60 % de los accesos iniciales** Le sigue la **explotación de vulnerabilidades con el 21,3 %**. Entre las dos explican más de ocho de cada diez intrusiones, lo que justifica que las dos medidas más rentables sean la **formación** y el **parcheado**.

*Referencia: §1.2 [ENISA-ETL]*
</details>

---

### Pregunta 6

**Sobre los ataques de denegación de servicio distribuida, el ETL 2025 concluye que:**

A) Son minoritarios en número pero provocan la mayor parte de las interrupciones de servicio
B) Representan el 77 % de los incidentes notificados, pero solo el 2 % provocó una interrupción real del servicio
C) Han desaparecido prácticamente como amenaza gracias a los servicios de mitigación en la nube

<details><summary>Respuesta</summary>

**Correcta: B) Representan el 77 % de los incidentes notificados, pero solo el 2 % provocó una interrupción real del servicio** Es el ataque **más frecuente y menos dañino**: la mayoría son acciones hacktivistas de bajo nivel. El ransomware, en cambio, es la amenaza de **mayor impacto** en la Unión Europea.

*Referencia: §1.2 [ENISA-ETL]*
</details>

---

### Pregunta 7

**Un ataque pasivo se caracteriza porque:**

A) Solo escucha, no altera nada y por ello es muy difícil de detectar: se combate previniéndolo con cifrado
B) Interrumpe el servicio y se detecta de inmediato por la caída de disponibilidad
C) Inyecta información espuria en la comunicación para suplantar al origen legítimo

<details><summary>Respuesta</summary>

**Correcta: A) Solo escucha, no altera nada y por ello es muy difícil de detectar: se combate previniéndolo con cifrado** Las opciones B y C describen ataques **activos**. El propio ENS enumera como ataques activos, en `mp.com.3.2`, la alteración de la información en tránsito, la inyección de información espuria y el secuestro de la sesión.

*Referencia: §1.2 [ENS]*
</details>

---

### Pregunta 8

**El envenenamiento de la caché ARP es un ataque que actúa en la capa de enlace. ¿Cuál es la contramedida adecuada?**

A) Una regla de denegación en el cortafuegos perimetral que bloquee el tráfico ARP saliente
B) Cifrar el tráfico con TLS extremo a extremo, que impide la asociación falsa de direcciones
C) Inspección dinámica de ARP y seguridad de puerto en el conmutador, más 802.1X y segmentación

<details><summary>Respuesta</summary>

**Correcta: C) Inspección dinámica de ARP y seguridad de puerto en el conmutador, más 802.1X y segmentación** El cortafuegos perimetral **no ve** este tráfico, porque nunca sale del segmento (opción A). TLS protegería el contenido, pero no impediría el ataque ni sus efectos sobre el tráfico no cifrado (opción B). La regla general: **un ataque de capa 2 no lo para un dispositivo de capa 3**.

*Referencia: §1.2 y §1.3.1 [ENS]*
</details>

---

### Pregunta 9

**¿Qué mecanismo proporciona cifrado e integridad salto a salto en la propia trama Ethernet?**

A) IPsec en modo transporte
B) MACsec, normalizado como IEEE 802.1AE
C) DTLS sobre UDP

<details><summary>Respuesta</summary>

**Correcta: B) MACsec, normalizado como IEEE 802.1AE** Protege el enlace entre dos equipos contiguos —entre conmutadores, o entre el puesto y el conmutador—. IPsec actúa en la capa de red y DTLS en la de transporte: ninguno de los dos protege la trama.

*Referencia: §1.3.1 [IEEE8021AE]*
</details>

---

### Pregunta 10

**Sobre el estado de TLS en 2026, señale la afirmación correcta.**

A) TLS 1.0 y 1.1 están prohibidos por el RFC 8996, y la especificación vigente de TLS 1.3 es el RFC 9846, que obsoleta el RFC 8446
B) TLS 1.1 sigue siendo admisible si se configura con suites de cifrado modernas
C) El RFC 8446 continúa siendo la especificación vigente de TLS 1.3 y no ha sido sustituido

<details><summary>Respuesta</summary>

**Correcta: A) TLS 1.0 y 1.1 están prohibidos por el RFC 8996, y la especificación vigente de TLS 1.3 es el RFC 9846, que obsoleta el RFC 8446** El RFC 9846, de **julio de 2026**, reedita TLS 1.3 y obsoleta también el RFC 5246 (TLS 1.2). SSL 3.0 quedó deprecado por el RFC 7568. Hoy solo son admisibles **TLS 1.2 bien configurado y TLS 1.3**.

*Referencia: §1.3.2 [RFC9846]*
</details>

---

### Pregunta 11

**¿Cuál de estas afirmaciones sobre seguridad del DNS es correcta?**

A) DNSSEC cifra las consultas y por tanto aporta confidencialidad
B) DoH y DoT firman las respuestas y garantizan la autenticidad de la zona
C) DNSSEC firma las respuestas y aporta autenticidad e integridad, mientras que DoT y DoH cifran y aportan confidencialidad

<details><summary>Respuesta</summary>

**Correcta: C) DNSSEC firma las respuestas y aporta autenticidad e integridad, mientras que DoT y DoH cifran y aportan confidencialidad** Son mecanismos **complementarios**, no alternativos. Las opciones A y B intercambian exactamente las funciones de uno y otro.

*Referencia: §1.3.2 [RFC9846]*
</details>

---

### Pregunta 12

**En agosto de 2026, ¿cuál es la situación de la Directiva (UE) 2022/2555 (NIS2) en España?**

A) Está plenamente en vigor y es directamente aplicable a todas las entidades locales
B) Sigue pendiente de transposición: el anteproyecto de Ley de Coordinación y Gobernanza de la Ciberseguridad continúa en tramitación y no se ha publicado en el BOE
C) Fue transpuesta mediante el Real Decreto 311/2022, que aprueba el Esquema Nacional de Seguridad

<details><summary>Respuesta</summary>

**Correcta: B) Sigue pendiente de transposición: el anteproyecto de Ley de Coordinación y Gobernanza de la Ciberseguridad continúa en tramitación y no se ha publicado en el BOE** El anteproyecto se aprobó en Consejo de Ministros el **14 de enero de 2025**; España incumplió el plazo del 17 de octubre de 2024 y recibió dictamen motivado de la Comisión. La norma exigible hoy a las Administraciones sigue siendo el **ENS**, que es anterior a NIS2 y no la transpone.

*Referencia: §1.4 [NIS2]*
</details>

---

### Pregunta 13

**¿Qué exige literalmente la medida `mp.com.1` del ENS?**

A) Un sistema de protección perimetral que separe la red interna del exterior, por el que todo el tráfico debe pasar, con todos los flujos autorizados previamente
B) El cifrado de todas las comunicaciones que discurran por redes fuera del dominio de seguridad propio
C) La segregación del tráfico en, al menos, tres subredes: usuarios, servicios y administración

<details><summary>Respuesta</summary>

**Correcta: A) Un sistema de protección perimetral que separe la red interna del exterior, por el que todo el tráfico debe pasar, con todos los flujos autorizados previamente** La opción B es `mp.com.2.1` y la opción C es el refuerzo `mp.com.4.r1.2`. `mp.com.1` **aplica en las tres categorías**, incluida la BÁSICA.

*Referencia: §1.4 y §2.1 [ENS]*
</details>

---

### Pregunta 14

**La medida `mp.com.4`, separación de flujos de información en la red, tiene una particularidad en su tabla de aplicación:**

A) Aplica en las tres categorías con el mismo contenido
B) No aplica en categoría BÁSICA; en MEDIA exige `+ [R1 o R2 o R3]` y en ALTA `+ [R2 o R3] + R4`
C) Solo aplica en categoría ALTA, y exige separación física de los medios

<details><summary>Respuesta</summary>

**Correcta: B) No aplica en categoría BÁSICA; en MEDIA exige `+ [R1 o R2 o R3]` y en ALTA `+ [R2 o R3] + R4`** Obsérvese que en categoría **ALTA la VLAN sola (R1) ya no basta**: hay que llegar a VPN (R2) o separación física (R3), y añadir el control de los puntos de interconexión (R4).

*Referencia: §1.4 y §2.4.1 [ENS]*
</details>

---

### Pregunta 15

**La medida `mp.com.1` remite a una Instrucción Técnica de Seguridad de Interconexión de Sistemas de Información. ¿Cuál es su situación?**

A) Fue publicada en el BOE en 2018, junto con la ITS de Auditoría
B) Fue publicada en 2016, junto con la ITS de Conformidad
C) No está publicada: a agosto de 2026 solo hay cuatro ITS en el BOE — Conformidad e Informe del Estado de la Seguridad, de 2016, y Auditoría y Notificación de Incidentes, de 2018

<details><summary>Respuesta</summary>

**Correcta: C) No está publicada: a agosto de 2026 solo hay cuatro ITS en el BOE — Conformidad e Informe del Estado de la Seguridad, de 2016, y Auditoría y Notificación de Incidentes, de 2018** Tampoco están publicadas la ITS de **Criptología** ni la de **Adquisición de productos de seguridad**, aunque el ENS también las anuncia. En su ausencia, la referencia práctica son las **guías CCN-STIC**.

*Referencia: §1.4 [ITS]*
</details>

---

### Pregunta 16

**¿Qué artículo del ENS constituye la base legal específica de la seguridad perimetral?**

A) El artículo 20, mínimo privilegio
B) El artículo 22, protección de información almacenada y en tránsito
C) El artículo 23, prevención ante otros sistemas de información interconectados

<details><summary>Respuesta</summary>

**Correcta: C) El artículo 23, prevención ante otros sistemas de información interconectados** Dispone que «se protegerá el **perímetro** del sistema de información, especialmente, si se conecta a redes públicas», y exige analizar los riesgos de la **interconexión** y controlar su **punto de unión**. No debe confundirse con `mp.com.1`, que es la **medida** del anexo II que lo desarrolla.

*Referencia: §1.4 [ENS]*
</details>

---

### Pregunta 17

**La política de denegación por defecto en un cortafuegos consiste en:**

A) Prohibir todo el tráfico y autorizar únicamente lo imprescindible, mediante una regla final que deniega y registra
B) Permitir todo el tráfico y bloquear las amenazas conocidas mediante listas negras actualizadas
C) Denegar el tráfico entrante y permitir sin restricciones todo el tráfico saliente

<details><summary>Respuesta</summary>

**Correcta: A) Prohibir todo el tráfico y autorizar únicamente lo imprescindible, mediante una regla final que deniega y registra** Es la traducción operativa de `mp.com.1.2`. La opción B describe la política contraria —lista negra—, que obliga a enumerar amenazas, que son infinitas, en lugar de necesidades, que son finitas. La opción C es el error más habitual en la vida real: permite que un equipo comprometido exfiltre por cualquier puerto.

*Referencia: §2.1 y §2.2.1 [ENS]*
</details>

---

### Pregunta 18

**¿Cuál es la diferencia esencial entre un filtro de paquetes sin estado y un cortafuegos con estado?**

A) El filtro de paquetes actúa en capa 7 y el cortafuegos con estado en capas 3 y 4
B) El cortafuegos con estado mantiene una tabla de conexiones, de modo que acepta el tráfico de vuelta sin necesidad de una regla explícita en sentido contrario
C) El cortafuegos con estado identifica la aplicación y el usuario, mientras que el filtro de paquetes solo ve puertos

<details><summary>Respuesta</summary>

**Correcta: B) El cortafuegos con estado mantiene una tabla de conexiones, de modo que acepta el tráfico de vuelta sin necesidad de una regla explícita en sentido contrario** La opción C describe el **NGFW**. La consecuencia de seguridad de esa tabla: es un recurso finito, y agotarla es exactamente el objetivo de un **SYN flood**.

*Referencia: §2.2.1 [CCN-408]*
</details>

---

### Pregunta 19

**En el perímetro externo, ante un paquete no autorizado, ¿qué es preferible y por qué?**

A) Descartarlo silenciosamente, porque no responder no confirma al atacante que hay un sistema y ralentiza los escaneos
B) Rechazarlo con un mensaje de error, porque es más rápido para el usuario legítimo y facilita el diagnóstico
C) Es indiferente: ambas acciones producen exactamente el mismo efecto de seguridad

<details><summary>Respuesta</summary>

**Correcta: A) Descartarlo silenciosamente, porque no responder no confirma al atacante que hay un sistema y ralentiza los escaneos** El **rechazo** con mensaje de error es más cortés y útil en redes internas, pero en el perímetro externo revela información. En ambos casos, la regla de cierre debe **registrar**, porque sin registro no hay trazabilidad (`op.exp.8`).

*Referencia: §2.2.1 [CCN-408]*
</details>

---

### Pregunta 20

**El cortafuegos de aplicaciones web (WAF):**

A) Sustituye al cortafuegos perimetral en las arquitecturas de nueva generación
B) Es la denominación moderna del cortafuegos con estado
C) Protege una aplicación web concreta frente a ataques como la inyección SQL o el XSS, y no sustituye al desarrollo seguro

<details><summary>Respuesta</summary>

**Correcta: C) Protege una aplicación web concreta frente a ataques como la inyección SQL o el XSS, y no sustituye al desarrollo seguro** Protege **la aplicación**, no la red, y es una mitigación, no una corrección. La medida del ENS que lo ampara es **`mp.s.2`**, que ya en categoría **BÁSICA** exige `+ [R1 o R2]`.

*Referencia: §2.2.1 [ENS]*
</details>

---

### Pregunta 21

**¿Qué elemento se sitúa delante de los servidores publicados, termina el TLS, equilibra la carga y oculta la topología interna?**

A) Un proxy inverso
B) Un proxy directo
C) Un cortafuegos con estado en modo transparente

<details><summary>Respuesta</summary>

**Correcta: A) Un proxy inverso** El **proxy directo** (opción B) hace lo contrario: se sitúa delante de los **clientes internos** que salen a internet y aplica `mp.s.3`. La medida del ENS asociada al proxy inverso es `mp.s.2`.

*Referencia: §2.2.2 [ENS]*
</details>

---

### Pregunta 22

**Sobre la inspección del tráfico cifrado en el proxy corporativo, el ENS establece que:**

A) Está prohibida en todo caso por afectar al secreto de las comunicaciones
B) Puede realizarse libremente, sin más requisitos, siempre que el equipo sea corporativo
C) El refuerzo `mp.s.3.r1.2`, exigible en categoría ALTA, la permite indicando qué se analiza, qué se registra, cuánto tiempo se retienen los registros y qué uso se prevé hacer de ellos

<details><summary>Respuesta</summary>

**Correcta: C) El refuerzo `mp.s.3.r1.2`, exigible en categoría ALTA, la permite indicando qué se analiza, qué se registra, cuánto tiempo se retienen los registros y qué uso se prevé hacer de ellos** El propio refuerzo admite excepciones para «destinos de confianza». En cualquier caso hay que **informar previamente** y respetar los límites de protección de datos.

*Referencia: §2.2.2 [ENS]*
</details>

---

### Pregunta 23

**¿Cuál es la diferencia fundamental entre un IDS y un IPS?**

A) El IDS detecta ataques conocidos por firmas y el IPS solo detecta anomalías de comportamiento
B) El IDS se sitúa fuera de línea y solo alerta; el IPS se sitúa en línea y además bloquea
C) El IDS protege una máquina concreta y el IPS protege un segmento de red completo

<details><summary>Respuesta</summary>

**Correcta: B) El IDS se sitúa fuera de línea y solo alerta; el IPS se sitúa en línea y además bloquea** Los métodos de detección —firmas y anomalías— son independientes del tipo de dispositivo (opción A), y la distinción entre máquina y red corresponde a la pareja **HIDS/NIDS** (opción C).

*Referencia: §2.3 [ENS]*
</details>

---

### Pregunta 24

**¿Cuál es la consecuencia más grave de un falso positivo en un IPS que protege una sede electrónica?**

A) Que se corta tráfico legítimo y ciudadanos no pueden completar sus trámites, con impacto en la disponibilidad
B) Que se genera una alerta innecesaria que consume tiempo del equipo de análisis
C) Que el ataque real pasa desapercibido al quedar oculto entre las alertas

<details><summary>Respuesta</summary>

**Correcta: A) Que se corta tráfico legítimo y ciudadanos no pueden completar sus trámites, con impacto en la disponibilidad** Como el IPS está **en línea**, su falso positivo no es ruido, es un corte. La opción B describe la consecuencia en un **IDS**, y la opción C describe el efecto de la **fatiga de alertas**, que es real pero indirecto.

*Referencia: §2.3 [ENS]*
</details>

---

### Pregunta 25

**Sobre la detección por firmas y la detección por anomalías, señale la afirmación correcta.**

A) La detección por anomalías es más precisa y genera menos falsos positivos que la detección por firmas
B) La detección por firmas es precisa pero no ve el ataque de día cero; la detección por anomalías puede verlo, a costa de más falsos positivos
C) Ambas detectan igual de bien los ataques desconocidos, y la diferencia está solo en el rendimiento

<details><summary>Respuesta</summary>

**Correcta: B) La detección por firmas es precisa pero no ve el ataque de día cero; la detección por anomalías puede verlo, a costa de más falsos positivos** La detección por anomalías necesita además un periodo de aprendizaje, y si aprende con la red ya comprometida, **aprende que el ataque es normal**.

*Referencia: §2.3 [ENS]*
</details>

---

### Pregunta 26

**La medida `op.mon.1`, detección de intrusión, del ENS:**

A) No aplica en categoría BÁSICA, y en MEDIA exige un IPS en línea
B) Solo es exigible en categoría ALTA, con procedimientos de respuesta automática
C) Aplica ya en categoría BÁSICA; en MEDIA añade el refuerzo R1, detección basada en reglas; y en ALTA el R2, procedimientos de respuesta a las alertas

<details><summary>Respuesta</summary>

**Correcta: C) Aplica ya en categoría BÁSICA; en MEDIA añade el refuerzo R1, detección basada en reglas; y en ALTA el R2, procedimientos de respuesta a las alertas** La medida habla de «herramientas de detección **o prevención** de intrusiones», sin imponer cuál. Existe además un R3 de acciones automáticas de respuesta que la tabla **no exige ni siquiera en ALTA**.

*Referencia: §2.3 [ENS]*
</details>

---

### Pregunta 27

**¿Qué medida del ENS constituye el fundamento de un SIEM?**

A) `op.exp.8`, registro de la actividad, en su redacción base
B) `op.mon.3`, vigilancia, en su refuerzo R1, que exige un sistema automático de recolección de eventos que permita la correlación
C) `op.mon.2`, sistema de métricas, en su refuerzo R2

<details><summary>Respuesta</summary>

**Correcta: B) `op.mon.3`, vigilancia, en su refuerzo R1, que exige un sistema automático de recolección de eventos que permita la correlación** La recolección automática sin correlación es la redacción base de `op.mon.3`, exigible en BÁSICA; la **correlación** —el SIEM— llega con el R1, exigible desde MEDIA. `op.exp.8` genera los registros, pero no los correlaciona.

*Referencia: §2.3 [ENS]*
</details>

---

### Pregunta 28

**La regla direccional que define una DMZ establece que:**

A) Desde la DMZ no se puede iniciar ninguna conexión hacia la red interna; desde la red interna sí se puede iniciar hacia la DMZ
B) Desde la red interna no se puede iniciar ninguna conexión hacia la DMZ, para evitar la fuga de información
C) La DMZ solo admite conexiones entrantes desde internet, y ninguna otra en ningún sentido

<details><summary>Respuesta</summary>

**Correcta: A) Desde la DMZ no se puede iniciar ninguna conexión hacia la red interna; desde la red interna sí se puede iniciar hacia la DMZ** Si un servidor de la DMZ puede abrir sesiones contra la base de datos interna, **eso no es una DMZ**: es red interna con otro nombre. Cuando la DMZ necesita un dato de dentro, la conexión debe originarse en la red interna o resolverse con un elemento intermedio en la propia DMZ.

*Referencia: §2.4.1 [ENS]*
</details>

---

### Pregunta 29

**¿Cuál es la ventaja principal de la arquitectura de doble cortafuegos frente a la de tres patas?**

A) Reduce el coste y simplifica la gestión al concentrar una única política
B) Permite prescindir de la DMZ, porque los dos cortafuegos ya la sustituyen
C) Aporta defensa en profundidad real, sobre todo si los dos equipos son de fabricantes distintos, de modo que una vulnerabilidad del primero no afecta al segundo

<details><summary>Respuesta</summary>

**Correcta: C) Aporta defensa en profundidad real, sobre todo si los dos equipos son de fabricantes distintos, de modo que una vulnerabilidad del primero no afecta al segundo** La opción A describe la ventaja de la arquitectura **de tres patas**, cuyo inconveniente es que un solo dispositivo separa internet de la red interna.

*Referencia: §2.4.1 [ENS]*
</details>

---

### Pregunta 30

**¿Qué segmentación mínima exige el refuerzo `mp.com.4.r1.2` del ENS?**

A) Dos subredes: interna y DMZ
B) Al menos tres subredes: usuarios, servicios y administración
C) Una subred por cada unidad organizativa del organismo

<details><summary>Respuesta</summary>

**Correcta: B) Al menos tres subredes: usuarios, servicios y administración** Y `mp.com.4.2` añade una obligación independiente: si se emplean **comunicaciones inalámbricas**, será **en un segmento separado**. Ambas son texto literal del anexo II.

*Referencia: §2.4.1 [ENS]*
</details>

---
### Pregunta 31

**Según la publicación NIST SP 800-207, uno de los siete principios de la confianza cero establece que:**

A) La red interna se considera de confianza siempre que esté segmentada mediante VLAN
B) El acceso se concede de forma permanente una vez validada la identidad del usuario
C) El acceso a los recursos se concede por sesión y se determina mediante política dinámica, que valora identidad, aplicación, estado del dispositivo y contexto

<details><summary>Respuesta</summary>

**Correcta: C) El acceso a los recursos se concede por sesión y se determina mediante política dinámica, que valora identidad, aplicación, estado del dispositivo y contexto** Las opciones A y B contradicen frontalmente el modelo: desaparece la confianza implícita por ubicación y **no existe la sesión indefinidamente confiable**.

*Referencia: §2.4.2 [NIST-ZT]*
</details>

---

### Pregunta 32

**En una arquitectura de confianza cero, ¿qué componente está en el camino del tráfico y deja pasar o no?**

A) El Punto de Aplicación de Políticas (PEP)
B) El Motor de Políticas (PE)
C) El Administrador de Políticas (PA)

<details><summary>Respuesta</summary>

**Correcta: A) El Punto de Aplicación de Políticas (PEP)** El **Motor (PE)** decide y el **Administrador (PA)** ejecuta la decisión; ambos forman el **punto de decisión (PDP)**, que no está en el camino del tráfico. Esa separación entre quien decide y quien ejecuta es lo que permite que la decisión sea dinámica.

*Referencia: §2.4.2 [NIST-ZT]*
</details>

---

### Pregunta 33

**Señale la afirmación correcta sobre la relación entre confianza cero y el modelo perimetral en España.**

A) La confianza cero deroga la obligación de disponer de perímetro, por ser un modelo superado
B) La confianza cero complementa al modelo perimetral, que sigue siendo obligatorio por `mp.com.1` en las tres categorías
C) Ambos modelos son incompatibles, y el ENS obliga a elegir uno de los dos en la política de seguridad

<details><summary>Respuesta</summary>

**Correcta: B) La confianza cero complementa al modelo perimetral, que sigue siendo obligatorio por `mp.com.1` en las tres categorías** Lo que la confianza cero sustituye es la idea de **red interna de confianza**, no el perímetro. Además, `op.acc.4` y `mp.com.4` son, leídos hoy, principios de confianza cero escritos en 2022.

*Referencia: §2.4.2 [NIST-ZT]*
</details>

---

### Pregunta 34

**¿Qué requisito del ENS hay que citar necesariamente en una pregunta sobre acceso remoto?**

A) `mp.com.1.1`, que obliga a que todo el tráfico atraviese el sistema de protección perimetral
B) `op.exp.8`, que obliga a registrar la actividad de los usuarios
C) `op.acc.4.5`, que obliga a establecer una política específica de acceso remoto requiriendo autorización expresa

<details><summary>Respuesta</summary>

**Correcta: C) `op.acc.4.5`, que obliga a establecer una política específica de acceso remoto requiriendo autorización expresa** Está dentro de `op.acc.4`, que **aplica en las tres categorías**. Las otras dos medidas son también aplicables, pero no son específicas de acceso remoto.

*Referencia: §3.1 [ENS]*
</details>

---

### Pregunta 35

**¿Qué establece `mp.eq.3.3` del ENS respecto a un portátil que se conecta desde una red no controlada por la organización?**

A) Que el ámbito de operación del servidor limitará la información y los servicios accesibles a los mínimos imprescindibles, con autorización previa de los responsables
B) Que el portátil deberá llevar necesariamente el disco cifrado, con independencia del nivel de confidencialidad
C) Que solo se permitirá la conexión desde redes previamente registradas por su dirección IP pública

<details><summary>Respuesta</summary>

**Correcta: A) Que el ámbito de operación del servidor limitará la información y los servicios accesibles a los mínimos imprescindibles, con autorización previa de los responsables** Es decir: **el teletrabajador no debe ver la misma red que si estuviera en la oficina**. La opción B corresponde al refuerzo `mp.eq.3.r1`, que se activa cuando la confidencialidad es de nivel MEDIO.

*Referencia: §3.1 [ENS]*
</details>

---

### Pregunta 36

**¿Cuál es la base legal del teletrabajo en las Administraciones Públicas españolas?**

A) El Real Decreto 311/2022, que aprueba el Esquema Nacional de Seguridad
B) El artículo 14 de la Ley 39/2015, sobre el derecho a relacionarse electrónicamente
C) El artículo 47 bis del TREBEP, introducido por el Real Decreto-ley 29/2020, de 29 de septiembre

<details><summary>Respuesta</summary>

**Correcta: C) El artículo 47 bis del TREBEP, introducido por el Real Decreto-ley 29/2020, de 29 de septiembre** Configura el teletrabajo como **expresamente autorizado**, **voluntario y reversible** y compatible con la modalidad presencial, y obliga a la Administración a **proporcionar los medios tecnológicos** necesarios — que es el fundamento de que el equipo sea corporativo y gestionado.

*Referencia: §3.1 [TREBEP]*
</details>

---

### Pregunta 37

**En una autenticación 802.1X, ¿qué papel desempeña el conmutador de red?**

A) El de suplicante, porque solicita la autenticación en nombre del equipo conectado
B) El de autenticador: no decide nada, transporta el diálogo EAP y aplica el resultado
C) El de servidor de autenticación, porque valida las credenciales contra el directorio

<details><summary>Respuesta</summary>

**Correcta: B) El de autenticador: no decide nada, transporta el diálogo EAP y aplica el resultado** El **suplicante** es el software del equipo que se conecta, y el **servidor de autenticación** —normalmente RADIUS— es quien decide. Hasta que la autenticación tiene éxito, el puerto solo deja pasar **EAPOL**: ni siquiera se obtiene dirección IP.

*Referencia: §3.2.2 [RFC3748]*
</details>

---

### Pregunta 38

**¿Cuál de estas combinaciones constituye autenticación multifactor en sentido estricto?**

A) Certificado en tarjeta criptográfica más el PIN que la desbloquea
B) Contraseña de acceso al sistema más PIN de acceso a la aplicación
C) Contraseña más respuesta a una pregunta de seguridad

<details><summary>Respuesta</summary>

**Correcta: A) Certificado en tarjeta criptográfica más el PIN que la desbloquea** Combina «algo que se tiene» con «algo que se sabe». Las opciones B y C combinan **dos factores de la misma categoría** —ambos «algo que se sabe»—, y por tanto **no son MFA**.

*Referencia: §3.2.1 [ENS]*
</details>

---

### Pregunta 39

**Un organismo categorizado MEDIA autoriza el teletrabajo con VPN cifrada y contraseña robusta de doce caracteres. ¿Cumple `op.acc.5`?**

A) Sí, porque la longitud y la complejidad de la contraseña compensan la ausencia de segundo factor
B) No: en nivel MEDIO la tabla exige `+ [R2 o R3 o R4] + R5`, de modo que la contraseña sola (R1) deja de estar disponible y es obligatorio registrar accesos con éxito y fallidos
C) Sí, siempre que la contraseña se cambie cada noventa días y se registren los accesos correctos

<details><summary>Respuesta</summary>

**Correcta: B) No: en nivel MEDIO la tabla exige `+ [R2 o R3 o R4] + R5`, de modo que la contraseña sola (R1) deja de estar disponible y es obligatorio registrar accesos con éxito y fallidos** El matiz que se pregunta: **la longitud de la contraseña es irrelevante para la conformidad**; lo que la norma exige es un **segundo factor**. En nivel BAJO sí bastaría `+ [R1 o R2 o R3 o R4]`.

*Referencia: §3.2.1 [ENS]*
</details>

---

### Pregunta 40

**Señale la afirmación correcta sobre los protocolos de gestión remota.**

A) Telnet puede utilizarse siempre que la conexión se limite a la red interna, porque el tráfico no sale del perímetro
B) SFTP y FTPS son dos nombres del mismo protocolo, y ambos emplean el puerto 990
C) SSH sustituye a Telnet y a rlogin en el puerto TCP 22, y sobre él viajan SFTP y SCP; SNMPv1 y v2c no ofrecen seguridad real y solo SNMPv3 autentica y cifra

<details><summary>Respuesta</summary>

**Correcta: C) SSH sustituye a Telnet y a rlogin en el puerto TCP 22, y sobre él viajan SFTP y SCP; SNMPv1 y v2c no ofrecen seguridad real y solo SNMPv3 autentica y cifra** Telnet transmite las credenciales **en claro** y no se usa jamás, tampoco en la red interna (opción A). **SFTP** es un subsistema de SSH y **FTPS** es FTP envuelto en TLS: no son lo mismo (opción B). Y las interfaces de gestión fuera de banda deben vivir en una **red de administración separada**, que es una de las tres subredes mínimas de `mp.com.4.r1.2`.

*Referencia: §3.3 [RFC4251]*
</details>

---

### Pregunta 41

**Señale tres diferencias correctas entre RADIUS y TACACS+.**

A) RADIUS usa UDP 1812 y 1813, cifra solo la contraseña y junta autenticación y autorización; TACACS+ usa TCP 49, cifra todo el cuerpo del mensaje y separa las tres funciones
B) RADIUS usa TCP 49 y cifra todo el mensaje; TACACS+ usa UDP y solo cifra la contraseña
C) Ambos usan UDP, pero RADIUS separa las tres funciones y TACACS+ las combina

<details><summary>Respuesta</summary>

**Correcta: A) RADIUS usa UDP 1812 y 1813, cifra solo la contraseña y junta autenticación y autorización; TACACS+ usa TCP 49, cifra todo el cuerpo del mensaje y separa las tres funciones** De ahí el reparto práctico: **RADIUS** para el acceso de usuarios a la red (Wi-Fi, 802.1X, VPN) y **TACACS+** para la administración de equipos de red, donde interesa autorizar comando a comando. Dos novedades recientes: el **RFC 9887** (diciembre de 2025) lleva TACACS+ sobre **TLS 1.3**, y el **RFC 9765** (abril de 2025) define **RADIUS/1.1**, que elimina MD5 mediante ALPN.

*Referencia: §3.2.2 [RFC2865]*
</details>

---

### Pregunta 42

**En un entorno sujeto al ENS, ¿qué configuración de túnel es la correcta por defecto en una VPN de acceso remoto y por qué?**

A) Túnel dividido, porque mejora el rendimiento y descarga el enlace de la sede central
B) Túnel completo, porque hace que toda la navegación pase por la organización y quede sujeta a `mp.s.3`, y evita que el equipo quede con un pie en cada red
C) Es indiferente, porque en ambos casos el tráfico corporativo viaja cifrado

<details><summary>Respuesta</summary>

**Correcta: B) Túnel completo, porque hace que toda la navegación pase por la organización y quede sujeta a `mp.s.3`, y evita que el equipo quede con un pie en cada red** El **túnel dividido** es una excepción que hay que justificar y acotar. Además de romper el control de la navegación, compromete el art. 9 al convertir el equipo en puente potencial entre dos redes.

*Referencia: §4.1.2 [ENS]*
</details>

---

### Pregunta 43

**¿Qué convierte un túnel en una red privada virtual?**

A) La encapsulación: cualquier protocolo que meta un paquete dentro de otro crea ya una VPN
B) El uso de direccionamiento privado conforme al RFC 1918 en ambos extremos del túnel
C) El cifrado: GRE encapsula pero no cifra, y MPLS aísla el tráfico entre clientes del operador pero tampoco lo cifra

<details><summary>Respuesta</summary>

**Correcta: C) El cifrado: GRE encapsula pero no cifra, y MPLS aísla el tráfico entre clientes del operador pero tampoco lo cifra** La MPLS del operador ofrece privacidad **administrativa**, no criptográfica, y por sí sola **no cumple `mp.com.2.1`**, que exige redes privadas virtuales **cifradas** cuando el tráfico sale del dominio de seguridad propio. La solución conforme es cifrar por encima con IPsec.

*Referencia: §4.1 [RFC2784]*
</details>

---

### Pregunta 44

**¿Qué diferencia el modo túnel del modo transporte de IPsec?**

A) El modo transporte cifra el paquete IP completo y el modo túnel solo la carga útil
B) El modo transporte conserva la cabecera IP original y protege solo la carga; el modo túnel cifra el paquete IP completo y añade una cabecera IP nueva, ocultando el direccionamiento interno
C) El modo túnel solo se puede usar con AH, y el modo transporte solo con ESP

<details><summary>Respuesta</summary>

**Correcta: B) El modo transporte conserva la cabecera IP original y protege solo la carga; el modo túnel cifra el paquete IP completo y añade una cabecera IP nueva, ocultando el direccionamiento interno** Regla de examen: **VPN de sitio a sitio implica ESP en modo túnel**. En ese modo, un observador en internet solo ve las direcciones de las dos **pasarelas**, no las de los equipos internos.

*Referencia: §4.2.1 [RFC4301]*
</details>

---

### Pregunta 45

**Sobre AH y ESP, los dos protocolos de seguridad de IPsec, señale la afirmación correcta.**

A) AH proporciona integridad y autenticación del origen pero NO cifra, y usa el protocolo IP 51; ESP cifra y además autentica, y usa el protocolo IP 50
B) AH cifra la carga útil y ESP solo comprueba la integridad; AH usa el protocolo IP 50 y ESP el 51
C) Ambos cifran, y la diferencia está en que AH trabaja en modo túnel y ESP en modo transporte

<details><summary>Respuesta</summary>

**Correcta: A) AH proporciona integridad y autenticación del origen pero NO cifra, y usa el protocolo IP 51; ESP cifra y además autentica, y usa el protocolo IP 50** Como ESP hace casi todo lo que hace AH, en la práctica **se usa ESP y AH está en desuso**. Son **números de protocolo IP**, no puertos: AH y ESP van directamente sobre IP y no tienen puertos, y eso es lo que les da problemas con NAT.

*Referencia: §4.2.1 [RFC4303]*
</details>

---

### Pregunta 46

**Sobre las asociaciones de seguridad (SA) de IPsec, señale la afirmación correcta.**

A) Una SA es bidireccional y basta con una por cada conexión establecida
B) Una SA se identifica únicamente por el SPI, que es un valor globalmente único
C) Una SA es unidireccional, de modo que una comunicación bidireccional requiere dos, y se identifica por el trío SPI, dirección IP de destino y protocolo de seguridad

<details><summary>Respuesta</summary>

**Correcta: C) Una SA es unidireccional, de modo que una comunicación bidireccional requiere dos, y se identifica por el trío SPI, dirección IP de destino y protocolo de seguridad** Las SA vivas se guardan en la **SAD**, y la política que decide qué tráfico se protege, en la **SPD**, cuyas tres acciones posibles son descartar, omitir IPsec o aplicar IPsec.

*Referencia: §4.2.1 [RFC4301]*
</details>

---

### Pregunta 47

**Un túnel IPsec se negocia correctamente pero no cursa tráfico. El extremo remoto está detrás de un dispositivo que hace NAT y el cortafuegos solo permite UDP 500. ¿Cuál es la causa más probable?**

A) Que falta abrir UDP 4500: con NAT en medio, IKEv2 conmuta a la travesía de NAT y encapsula ESP en UDP 4500 conforme al RFC 3948
B) Que el modo túnel no es compatible con la traducción de direcciones y hay que cambiar a modo transporte
C) Que el tiempo de vida de la asociación de seguridad es demasiado corto y expira antes de cursar datos

<details><summary>Respuesta</summary>

**Correcta: A) Que falta abrir UDP 4500: con NAT en medio, IKEv2 conmuta a la travesía de NAT y encapsula ESP en UDP 4500 conforme al RFC 3948** Es exactamente el síntoma descrito: la negociación inicial funciona por el 500 —el túnel «se levanta»— pero los datos no pasan. Si además se estuviera usando **AH**, habría un segundo problema: AH es **incompatible con NAT** porque autentica campos de la cabecera IP.

*Referencia: §4.2.1 [RFC3948]*
</details>

---

### Pregunta 48

**¿Cuál es la razón principal del éxito de las VPN basadas en SSL/TLS en escenarios de movilidad?**

A) Que ofrecen mejor rendimiento bruto por encapsular TCP dentro de TCP
B) Que no requieren autenticar al usuario, lo que simplifica el despliegue
C) Que usan TCP 443, indistinguible del tráfico HTTPS ordinario, y por tanto atraviesan cortafuegos ajenos que bloquean IPsec

<details><summary>Respuesta</summary>

**Correcta: C) Que usan TCP 443, indistinguible del tráfico HTTPS ordinario, y por tanto atraviesan cortafuegos ajenos que bloquean IPsec** Su contrapartida es precisamente el **rendimiento**: encapsular TCP dentro de TCP provoca el llamado derretimiento de TCP, con dos controles de congestión superpuestos. Por eso los productos modernos prefieren transportar el túnel sobre DTLS o QUIC y dejar el 443 como respaldo.

*Referencia: §4.2.2 [RFC9846]*
</details>

---

### Pregunta 49

**¿Cuál es la situación normativa de IKEv1 e IKEv2?**

A) IKEv1 sigue siendo la versión recomendada por su mayor compatibilidad entre fabricantes
B) IKEv1 fue declarado obsoleto por el RFC 9395, de abril de 2023; IKEv2 es la versión vigente y tiene la categoría de Internet Standard (STD 79)
C) Ambas versiones están obsoletas y han sido sustituidas por el protocolo IKEv3

<details><summary>Respuesta</summary>

**Correcta: B) IKEv1 fue declarado obsoleto por el RFC 9395, de abril de 2023; IKEv2 es la versión vigente y tiene la categoría de Internet Standard (STD 79)** Ventajas de IKEv2 que se preguntan: menos mensajes para establecer el túnel, detección de par muerto integrada, soporte nativo de **EAP** —y por tanto de MFA—, travesía de NAT normalizada y **MOBIKE**, que permite cambiar de red sin que se caiga el túnel.

*Referencia: §4.2.1 [RFC7296]*
</details>

---

### Pregunta 50

**Sobre los protocolos de tunelización de nivel de enlace, señale la afirmación correcta.**

A) L2TP no cifra por sí solo, y por eso se despliega como L2TP/IPsec, con IPsec en modo transporte; PPTP está criptográficamente roto y no debe usarse
B) L2TP incorpora cifrado propio equivalente a ESP y puede usarse de forma autónoma
C) PPTP es la opción recomendada por su integración nativa en los sistemas operativos de escritorio

<details><summary>Respuesta</summary>

**Correcta: A) L2TP no cifra por sí solo, y por eso se despliega como L2TP/IPsec, con IPsec en modo transporte; PPTP está criptográficamente roto y no debe usarse** L2TP usa **UDP 1701**. En la combinación L2TP/IPsec, IPsec trabaja en **modo transporte** porque el túnel ya lo aporta L2TP. PPTP se descifra en horas: su autenticación MS-CHAPv2 y su cifrado MPPE están rotos.

*Referencia: §4.2.3 [RFC2661]*
</details>

---

### Pregunta 51

**¿Qué es la amenaza de «cosecha ahora, descifra después» y por qué afecta especialmente a las VPN?**

A) Es la captura de credenciales en redes públicas para reutilizarlas más adelante, y afecta a las VPN porque muchas siguen usando contraseña
B) Es el almacenamiento de copias de seguridad sin cifrar por parte del proveedor de nube, y se combate exigiendo productos del CPSTIC
C) Es la grabación hoy del tráfico cifrado para descifrarlo cuando existan ordenadores cuánticos, y afecta a las VPN porque protegen información de vida útil larga

<details><summary>Respuesta</summary>

**Correcta: C) Es la grabación hoy del tráfico cifrado para descifrarlo cuando existan ordenadores cuánticos, y afecta a las VPN porque protegen información de vida útil larga** Respuestas normalizadas: en IKEv2, los **RFC 8784 y 9370**; en TLS 1.3, el **RFC 10024**, de agosto de 2026. Calendario de la **hoja de ruta coordinada de la UE** (Grupo de Cooperación NIS, 23-6-2025): **31-12-2026** planes nacionales, **31-12-2030** casos de alto riesgo y **31-12-2035** transición completa.

*Referencia: §4.2.1 [PQC-EU]*
</details>

---

### Pregunta 52

**¿Qué exige literalmente la medida `op.exp.6` del ENS respecto al software de protección frente a código dañino?**

A) Que se instale exclusivamente en los puestos de usuario, por ser el punto de entrada habitual
B) Que se instale en todos los equipos: puestos de usuario, servidores y elementos perimetrales, con las bases de detección permanentemente actualizadas y protección en tiempo real
C) Que se instale en los servidores y en el perímetro, quedando los puestos cubiertos por el cortafuegos personal

<details><summary>Respuesta</summary>

**Correcta: B) Que se instale en todos los equipos: puestos de usuario, servidores y elementos perimetrales, con las bases de detección permanentemente actualizadas y protección en tiempo real** Es texto literal de `op.exp.6.2`, `op.exp.6.4` y `op.exp.6.5`. Añade además `op.exp.6.3`: **todo fichero procedente de fuentes externas será analizado antes de trabajar con él**.

*Referencia: §5.2.1 [ENS]*
</details>

---

### Pregunta 53

**¿Cuál es la diferencia esencial entre una plataforma de protección del punto final (EPP) y una solución de detección y respuesta (EDR)?**

A) El EPP previene bloqueando lo que reconoce como malo; el EDR asume que algo entrará y aporta telemetría de comportamiento para investigar, además de permitir aislar el equipo en red desde la consola
B) El EPP actúa en el servidor y el EDR en el puesto de usuario
C) El EPP usa detección por anomalías y el EDR se limita a las firmas del fabricante

<details><summary>Respuesta</summary>

**Correcta: A) El EPP previene bloqueando lo que reconoce como malo; el EDR asume que algo entrará y aporta telemetría de comportamiento para investigar, además de permitir aislar el equipo en red desde la consola** El **aislamiento remoto** —dejar el equipo sin comunicación salvo con la consola— es la capacidad más característica del EDR y la que un antivirus no puede ofrecer. El **XDR** amplía la correlación a red, correo, identidad y nube; el **MDR** es el mismo servicio operado por un tercero.

*Referencia: §5.2.1 [ENS]*
</details>

---

### Pregunta 54

**En categoría ALTA, ¿qué añade la tabla de aplicación de `op.exp.6` respecto a la categoría MEDIA?**

A) Nada: la medida se aplica igual en MEDIA y en ALTA
B) Los refuerzos R3 y R4: lista blanca de aplicaciones —solo se ejecuta lo previamente autorizado— y herramientas EDR, que el ENS nombra expresamente por su sigla
C) Únicamente el refuerzo R1, escaneo periódico de todo el sistema

<details><summary>Respuesta</summary>

**Correcta: B) Los refuerzos R3 y R4: lista blanca de aplicaciones —solo se ejecuta lo previamente autorizado— y herramientas EDR, que el ENS nombra expresamente por su sigla** La tabla completa es: **BÁSICA** la medida; **MEDIA** `+ R1 + R2` (escaneo periódico y revisión de funciones críticas al arranque); **ALTA** `+ R1 + R2 + R3 + R4`. Es uno de los pocos lugares donde el ENS cita una tecnología concreta con su nombre comercial habitual.

*Referencia: §5.2.1 [ENS]*
</details>

---

### Pregunta 55

**Sobre el cifrado de disco completo del portátil corporativo, señale la afirmación correcta.**

A) Impide que el ransomware cifre los ficheros, porque estos ya están cifrados por el sistema
B) Solo es exigible en categoría ALTA y en ningún otro caso
C) Protege exclusivamente frente al acceso físico al equipo apagado; con la sesión iniciada el disco está descifrado para el sistema y también para cualquier proceso malicioso

<details><summary>Respuesta</summary>

**Correcta: C) Protege exclusivamente frente al acceso físico al equipo apagado; con la sesión iniciada el disco está descifrado para el sistema y también para cualquier proceso malicioso** La medida que lo exige es **`mp.eq.3.r1`**, cuando el nivel de **confidencialidad** de la información almacenada es **MEDIO** (opción B, incorrecta). Y hay que custodiar centralmente las **claves de recuperación**, o una medida de confidencialidad acaba dañando la disponibilidad.

*Referencia: §5.2.2 [ENS]*
</details>

---

### Pregunta 56

**¿Cuál de estas medidas de protección del puesto NO es exigible en un sistema cuyo nivel de autenticidad es BAJO?**

A) `mp.eq.2`, bloqueo del puesto de trabajo, que no aplica en nivel BAJO y empieza a exigirse en MEDIO
B) `mp.eq.1`, puesto de trabajo despejado, que solo se exige desde categoría MEDIA
C) `mp.eq.3`, protección de dispositivos portátiles, que solo se exige en categoría ALTA

<details><summary>Respuesta</summary>

**Correcta: A) `mp.eq.2`, bloqueo del puesto de trabajo, que no aplica en nivel BAJO y empieza a exigirse en MEDIO** En nivel ALTO añade el refuerzo **R1**, que obliga a **cancelar las sesiones abiertas** pasado un tiempo mayor. `mp.eq.1` y `mp.eq.3` sí aplican desde categoría **BÁSICA**, por lo que las opciones B y C son falsas.

*Referencia: §5.1 [ENS]*
</details>

---

### Pregunta 57

**¿Qué obligaciones establece `mp.eq.3`, protección de dispositivos portátiles?**

A) Únicamente el cifrado del disco duro y el bloqueo automático por inactividad
B) Inventario de portátiles con persona responsable y control regular, procedimiento para informar de pérdidas o sustracciones, limitación a los mínimos imprescindibles desde redes no controladas y evitar que el equipo contenga claves de acceso remoto no imprescindibles
C) La prohibición de sacar equipos de las instalaciones sin autorización del responsable de seguridad

<details><summary>Respuesta</summary>

**Correcta: B) Inventario de portátiles con persona responsable y control regular, procedimiento para informar de pérdidas o sustracciones, limitación a los mínimos imprescindibles desde redes no controladas y evitar que el equipo contenga claves de acceso remoto no imprescindibles** Son los cuatro requisitos base, `mp.eq.3.1` a `mp.eq.3.4`. Los refuerzos, exigibles en categoría **ALTA**, son **R1** (cifrado del disco) y **R2** (entornos protegidos, «a salvo de hurtos y miradas indiscretas»).

*Referencia: §5.1 [ENS]*
</details>

---

### Pregunta 58

**Un organismo mantiene en producción puestos con un sistema operativo cuyo soporte terminó el 14 de octubre de 2025. ¿Cómo se valora?**

A) Es aceptable si el antivirus está actualizado, porque compensa la ausencia de parches
B) Es aceptable si los equipos están segmentados en una VLAN propia sin salida a internet
C) Es un incumplimiento directo de `op.exp.4`: un sistema fuera de soporte no recibe parches y ninguna otra medida lo compensa; el programa de pago ESU solo prolonga las actualizaciones críticas e importantes hasta el 12 de octubre de 2027

<details><summary>Respuesta</summary>

**Correcta: C) Es un incumplimiento directo de `op.exp.4`: un sistema fuera de soporte no recibe parches y ninguna otra medida lo compensa; el programa de pago ESU solo prolonga las actualizaciones críticas e importantes hasta el 12 de octubre de 2027** El antivirus no tapa una vulnerabilidad del núcleo (opción A) y la segmentación reduce el impacto pero no la vulnerabilidad (opción B). Es un hallazgo sistemático en las auditorías del ENS, en relación también con el **art. 21**.

*Referencia: §5.3 [ENS]*
</details>

---

### Pregunta 59

**¿Cuál es la justificación técnica del cortafuegos personal en un puesto que ya está detrás de un cortafuegos perimetral?**

A) Que el cortafuegos perimetral no ve el tráfico entre dos puestos de la misma VLAN, de modo que el personal es la única defensa frente al movimiento lateral y la única existente cuando el portátil está fuera de la organización
B) Que duplica las reglas del perimetral y así se dispone de una copia de seguridad de la política
C) Que sustituye al antimalware en los equipos que no pueden ejecutar un agente EDR

<details><summary>Respuesta</summary>

**Correcta: A) Que el cortafuegos perimetral no ve el tráfico entre dos puestos de la misma VLAN, de modo que el personal es la única defensa frente al movimiento lateral y la única existente cuando el portátil está fuera de la organización** Es por tanto una **capa independiente** en el sentido del art. 9 del ENS, no una redundancia. Además permite reglas **por aplicación** y perfiles distintos para «en la oficina» y «fuera».

*Referencia: §5.2.2 [ENS]*
</details>

---

### Pregunta 60

**¿Qué obliga a recordar periódicamente la medida `mp.per.3`, concienciación, del ENS?**

A) Únicamente la política de contraseñas y el procedimiento de bloqueo del puesto, y solo en categoría ALTA
B) La normativa de buen uso de los equipos y las técnicas de ingeniería social más habituales, la identificación de incidentes o comportamientos sospechosos, y el procedimiento para informar sobre incidentes de seguridad, sean reales o falsas alarmas
C) El contenido íntegro del anexo II del ENS, mediante una acción formativa anual obligatoria

<details><summary>Respuesta</summary>

**Correcta: B) La normativa de buen uso de los equipos y las técnicas de ingeniería social más habituales, la identificación de incidentes o comportamientos sospechosos, y el procedimiento para informar sobre incidentes de seguridad, sean reales o falsas alarmas** Son los tres apartados literales de `mp.per.3`, y la medida **aplica en las tres categorías**, incluida la BÁSICA. El inciso **«sean reales o falsas alarmas»** es el más importante: si notificar conlleva reproche, el empleado deja de notificar y se pierde el sensor más rápido de la organización. `mp.per.4` añade la **formación** y exige **evaluar su eficacia**.

*Referencia: §5.4 [ENS]*
</details>
