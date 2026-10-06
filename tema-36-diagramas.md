# Tema 36 — Catálogo de Diagramas

> **Título oficial**: Seguridad y protección en redes de comunicaciones. Seguridad perimetral. Acceso remoto seguro a redes. Redes privadas virtuales (VPN). Seguridad en el puesto del usuario.
>
> **Versión**: v1.0
> **Fecha**: 2026-08-27
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (zero-dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)
> **Nota técnica**: las clases CSS de cada SVG llevan sufijo numérico único (`.t1`, `.h1`…) para evitar colisiones de estilos entre los 19 diagramas embebidos en la misma página. Dentro de un mismo elemento **nunca** se mezclan `class` y atributo `fill`: cuando hace falta un color distinto se declara una clase propia, porque la clase CSS gana al atributo de presentación.

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | Mapa del tema: las cinco capas de defensa | § intro | Mapa de secciones | 680×372 |
| D2 | Las cinco dimensiones de seguridad y los principios del ENS | §1.1 | Comparativa + principios | 680×352 |
| D3 | Amenazas y vectores de ataque: qué dice el ETL 2025 | §1.2 | Taxonomía + cifras | 680×364 |
| D4 | Ataque por capa de la pila TCP/IP y su contramedida | §1.3 | Capas + tabla | 680×356 |
| D5 | Protocolos en claro y su versión segura: tabla de puertos | §1.3.2 | Tabla de equivalencias | 680×372 |
| D6 | El ENS en la red: qué medida aplica en qué categoría | §1.4 | Matriz normativa | 680×380 |
| D7 | Del perímetro-muralla al perímetro distribuido | §2.1 | Evolución en tres etapas | 680×340 |
| D8 | Las cinco generaciones de cortafuegos | §2.2.1 | Escala evolutiva | 680×364 |
| D9 | Proxy directo, proxy inverso y pasarela de aplicación | §2.2.2 | Topología comparada | 680×348 |
| D10 | IDS frente a IPS: ubicación y matriz de decisión | §2.3 | Comparativa + matriz | 680×372 |
| D11 | DMZ: tres patas, doble cortafuegos y segmentación interna | §2.4.1 | Arquitecturas | 680×372 |
| D12 | Confianza cero: los siete principios y los componentes | §2.4.2 | Principios + PDP/PEP | 680×372 |
| D13 | Acceso remoto del empleado municipal, paso a paso | §3.1 | Flujo numerado | 680×372 |
| D14 | Los tres factores de autenticación y qué exige el ENS | §3.2.1 | Factores + tabla `op.acc.5` | 680×364 |
| D15 | AAA y 802.1X: RADIUS, TACACS+ y el flujo de autenticación | §3.2.2 | Comparativa + flujo | 680×372 |
| D16 | Taxonomía de VPN: tipo, nivel y protocolo | §4.1 | Doble clasificación | 680×364 |
| D17 | IPsec: AH y ESP, modo transporte y modo túnel | §4.2.1 | Estructura de paquete | 680×372 |
| D18 | IPsec frente a SSL/TLS: tabla de decisión | §4.2.2 | Comparativa | 680×356 |
| D19 | El puesto blindado: de antivirus a EDR y capas de defensa | §5.1 · §5.2 | Escalera + capas | 680×372 |

---
## D1 · Mapa del tema: las cinco capas de defensa

**Sección**: § Convenciones — visión de conjunto de las cinco secciones
**Propósito**: Ordenar el tema entero como **cinco capas concéntricas** sobre un mismo escenario municipal, mostrando qué protege cada sección y con qué medida del ENS se respalda. Es el diagrama de orientación: conviene volver a él al terminar cada sección.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Mapa del tema en cinco capas de defensa: sección uno fundamentos y amenazas con las cinco dimensiones del Esquema Nacional de Seguridad; sección dos seguridad perimetral con cortafuegos, proxy, sistemas de detección y zona desmilitarizada, respaldada por la medida mp punto com punto uno; sección tres acceso remoto seguro con autenticación multifactor y servidores AAA, respaldada por op punto acc punto cuatro punto cinco; sección cuatro redes privadas virtuales con IPsec y TLS, respaldada por mp punto com punto dos; y sección cinco seguridad del puesto de usuario con cifrado, EDR y concienciación, respaldada por mp punto eq y op punto exp punto seis">
  <style>.h1{font:700 13px system-ui,sans-serif;fill:#0055a0}.k1{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t1{font:700 8.5px system-ui,sans-serif;fill:#fff}.s1{font:8.5px system-ui,sans-serif;fill:#fff}.d1{font:8.5px system-ui,sans-serif;fill:#333}.b1{font:700 9px system-ui,sans-serif;fill:#0055a0}.n1{font:8px system-ui,sans-serif;fill:#666}.w1{font:700 9px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="h1">Cinco secciones, cinco capas sobre el mismo escenario municipal</text>
  <text x="20" y="40" class="k1">QUÉ PROTEGE CADA SECCIÓN</text>

  <rect x="20" y="48" width="98" height="52" rx="5" fill="#0055a0"/><text x="69" y="68" text-anchor="middle" class="t1">§1 FUNDAMENTOS</text><text x="69" y="82" text-anchor="middle" class="s1">Principios, amenazas</text><text x="69" y="94" text-anchor="middle" class="s1">y mecanismos</text>
  <rect x="126" y="48" width="98" height="52" rx="5" fill="#0055a0"/><text x="175" y="68" text-anchor="middle" class="t1">§2 PERÍMETRO</text><text x="175" y="82" text-anchor="middle" class="s1">Cortafuegos, proxy,</text><text x="175" y="94" text-anchor="middle" class="s1">IDS/IPS, DMZ</text>
  <rect x="232" y="48" width="98" height="52" rx="5" fill="#0055a0"/><text x="281" y="68" text-anchor="middle" class="t1">§3 ACCESO REMOTO</text><text x="281" y="82" text-anchor="middle" class="s1">Identidad, MFA,</text><text x="281" y="94" text-anchor="middle" class="s1">AAA y 802.1X</text>
  <rect x="338" y="48" width="98" height="52" rx="5" fill="#0055a0"/><text x="387" y="68" text-anchor="middle" class="t1">§4 VPN</text><text x="387" y="82" text-anchor="middle" class="s1">IPsec, SSL/TLS y</text><text x="387" y="94" text-anchor="middle" class="s1">túneles de nivel 2</text>
  <rect x="444" y="48" width="98" height="52" rx="5" fill="#0055a0"/><text x="493" y="68" text-anchor="middle" class="t1">§5 PUESTO</text><text x="493" y="82" text-anchor="middle" class="s1">Bastionado, EDR,</text><text x="493" y="94" text-anchor="middle" class="s1">cifrado y personas</text>
  <rect x="550" y="48" width="110" height="52" rx="5" fill="#e89822"/><text x="605" y="68" text-anchor="middle" class="t1">EL ESCENARIO</text><text x="605" y="82" text-anchor="middle" class="s1">CPD + oficina de</text><text x="605" y="94" text-anchor="middle" class="s1">distrito + teletrabajo</text>

  <text x="20" y="124" class="k1">LA MEDIDA DEL ENS QUE RESPALDA CADA UNA</text>
  <rect x="20" y="132" width="204" height="46" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="122" y="150" text-anchor="middle" class="b1">§1 y §2 · mp.com.1 · art. 23</text><text x="122" y="164" text-anchor="middle" class="d1">Perímetro seguro: aplica en BÁSICA,</text><text x="122" y="175" text-anchor="middle" class="d1">MEDIA y ALTA. Todo el tráfico pasa por él</text>
  <rect x="232" y="132" width="204" height="46" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="334" y="150" text-anchor="middle" class="b1">§3 · op.acc.4.5 y op.acc.5</text><text x="334" y="164" text-anchor="middle" class="d1">Política específica de acceso remoto</text><text x="334" y="175" text-anchor="middle" class="d1">con autorización expresa. MFA desde MEDIO</text>
  <rect x="444" y="132" width="216" height="46" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="552" y="150" text-anchor="middle" class="b1">§4 · mp.com.2 · §5 · mp.eq y op.exp.6</text><text x="552" y="164" text-anchor="middle" class="d1">VPN cifrada fuera del dominio propio.</text><text x="552" y="175" text-anchor="middle" class="d1">Portátiles, bloqueo, antimalware y EDR</text>

  <text x="20" y="202" class="k1">EL RECORRIDO DE UN ATAQUE, Y DÓNDE LO PARA CADA CAPA</text>
  <rect x="20" y="210" width="640" height="86" rx="5" fill="#fbfbfd" stroke="#ccc"/>
  <rect x="32" y="222" width="118" height="28" rx="4" fill="#d13c3c"/><text x="91" y="240" text-anchor="middle" class="w1">1 · PHISHING</text>
  <text x="158" y="240" class="d1">→</text>
  <rect x="172" y="222" width="118" height="28" rx="4" fill="#d13c3c"/><text x="231" y="240" text-anchor="middle" class="w1">2 · PUESTO INFECTADO</text>
  <text x="298" y="240" class="d1">→</text>
  <rect x="312" y="222" width="118" height="28" rx="4" fill="#d13c3c"/><text x="371" y="240" text-anchor="middle" class="w1">3 · MOV. LATERAL</text>
  <text x="438" y="240" class="d1">→</text>
  <rect x="452" y="222" width="118" height="28" rx="4" fill="#d13c3c"/><text x="511" y="240" text-anchor="middle" class="w1">4 · SALIDA DE DATOS</text>
  <rect x="32" y="258" width="118" height="26" rx="4" fill="#2d8659"/><text x="91" y="275" text-anchor="middle" class="s1">§5.4 concienciación</text>
  <rect x="172" y="258" width="118" height="26" rx="4" fill="#2d8659"/><text x="231" y="275" text-anchor="middle" class="s1">§5.2 EDR y §5.3 parches</text>
  <rect x="312" y="258" width="118" height="26" rx="4" fill="#2d8659"/><text x="371" y="275" text-anchor="middle" class="s1">§2.4 segmentación · IDS</text>
  <rect x="452" y="258" width="118" height="26" rx="4" fill="#2d8659"/><text x="511" y="275" text-anchor="middle" class="s1">§2.2 proxy de salida</text>
  <text x="580" y="240" class="d1">Cada casilla roja</text>
  <text x="580" y="252" class="d1">tiene debajo su</text>
  <text x="580" y="264" class="d1">casilla verde: es</text>
  <text x="580" y="276" class="d1">el art. 9 del ENS</text>

  <rect x="20" y="306" width="640" height="34" rx="5" fill="#fff5e6" stroke="#e89822"/>
  <text x="340" y="322" text-anchor="middle" class="b1">La idea que ordena el tema: NINGUNA capa sustituye a otra</text>
  <text x="340" y="334" text-anchor="middle" class="d1">Art. 9 del ENS — líneas de defensa: el diseño debe suponer que alguna capa fallará, y que el fallo de una no comprometa el conjunto</text>

  <text x="20" y="360" class="n1">[Fuente: ENS, RD 311/2022, arts. 9 y 23 y anexo II · ENISA ETL 2025]</text>
</svg>
```

---
## D2 · Las cinco dimensiones de seguridad y los principios del ENS

**Sección**: §1.1 — Principios de la seguridad de la información y de las comunicaciones
**Propósito**: Fijar las **cinco** dimensiones (CITAD) frente a la tríada CIA, con qué las rompe y qué las protege en una red, y enlazarlas con la regla de derivación de la **categoría** del sistema, que es donde se concentran los errores.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 352" role="img" aria-label="Las cinco dimensiones de seguridad del Esquema Nacional de Seguridad: confidencialidad, integridad, trazabilidad, autenticidad y disponibilidad, con el ataque que rompe cada una y el mecanismo de red que la protege; y la regla de derivación de la categoría del sistema a partir de la dimensión más exigente">
  <style>.h2{font:700 13px system-ui,sans-serif;fill:#0055a0}.k2{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t2{font:700 9.5px system-ui,sans-serif;fill:#fff}.s2{font:8.5px system-ui,sans-serif;fill:#fff}.d2{font:8.5px system-ui,sans-serif;fill:#333}.b2{font:700 9px system-ui,sans-serif;fill:#0055a0}.n2{font:8px system-ui,sans-serif;fill:#666}.hd2{font:700 8.5px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h2">En España son CINCO dimensiones, no tres: C · I · T · A · D</text>

  <text x="26" y="42" class="hd2">DIMENSIÓN</text><text x="136" y="42" class="hd2">QUÉ GARANTIZA</text><text x="336" y="42" class="hd2">QUÉ LA ROMPE EN UNA RED</text><text x="506" y="42" class="hd2">CON QUÉ SE PROTEGE</text>

  <rect x="20" y="48" width="106" height="34" rx="4" fill="#0055a0"/><text x="73" y="62" text-anchor="middle" class="t2">CONFIDENCIALIDAD</text><text x="73" y="76" text-anchor="middle" class="s2">C</text>
  <text x="136" y="62" class="d2">Solo accede quien está</text><text x="136" y="74" class="d2">autorizado</text>
  <text x="336" y="62" class="d2">Escucha del tráfico, acceso</text><text x="336" y="74" class="d2">a un segmento ajeno</text>
  <text x="506" y="62" class="d2">Cifrado: IPsec, TLS,</text><text x="506" y="74" class="d2">MACsec. Segmentación</text>

  <rect x="20" y="88" width="106" height="34" rx="4" fill="#0055a0"/><text x="73" y="102" text-anchor="middle" class="t2">INTEGRIDAD</text><text x="73" y="116" text-anchor="middle" class="s2">I</text>
  <text x="136" y="102" class="d2">La información no se altera,</text><text x="136" y="114" class="d2">y si se altera se detecta</text>
  <text x="336" y="102" class="d2">Alteración en tránsito,</text><text x="336" y="114" class="d2">inyección de datos falsos</text>
  <text x="506" y="102" class="d2">HMAC dentro de IPsec,</text><text x="506" y="114" class="d2">TLS o SSH</text>

  <rect x="20" y="128" width="106" height="34" rx="4" fill="#0055a0"/><text x="73" y="142" text-anchor="middle" class="t2">TRAZABILIDAD</text><text x="73" y="156" text-anchor="middle" class="s2">T</text>
  <text x="136" y="142" class="d2">Se puede reconstruir quién</text><text x="136" y="154" class="d2">hizo qué y cuándo</text>
  <text x="336" y="142" class="d2">Falta de registros, cuentas</text><text x="336" y="154" class="d2">compartidas, reloj desfasado</text>
  <text x="506" y="142" class="d2">op.exp.8, sincronización</text><text x="506" y="154" class="d2">horaria, SIEM</text>

  <rect x="20" y="168" width="106" height="34" rx="4" fill="#0055a0"/><text x="73" y="182" text-anchor="middle" class="t2">AUTENTICIDAD</text><text x="73" y="196" text-anchor="middle" class="s2">A</text>
  <text x="136" y="182" class="d2">El origen es quien dice</text><text x="136" y="194" class="d2">ser</text>
  <text x="336" y="182" class="d2">Suplantación de IP o MAC,</text><text x="336" y="194" class="d2">punto de acceso impostor</text>
  <text x="506" y="182" class="d2">Certificados, 802.1X,</text><text x="506" y="194" class="d2">autenticación mutua</text>

  <rect x="20" y="208" width="106" height="34" rx="4" fill="#0055a0"/><text x="73" y="222" text-anchor="middle" class="t2">DISPONIBILIDAD</text><text x="73" y="236" text-anchor="middle" class="s2">D</text>
  <text x="136" y="222" class="d2">El servicio está accesible</text><text x="136" y="234" class="d2">cuando se necesita</text>
  <text x="336" y="222" class="d2">DDoS, corte de enlace,</text><text x="336" y="234" class="d2">saturación del cortafuegos</text>
  <text x="506" y="222" class="d2">Redundancia, mp.s.4,</text><text x="506" y="234" class="d2">mitigación aguas arriba</text>

  <text x="20" y="264" class="k2">DE NIVEL A CATEGORÍA: LA REGLA CLAVE</text>
  <rect x="20" y="272" width="206" height="46" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="123" y="290" text-anchor="middle" class="b2">El NIVEL se fija POR DIMENSIÓN</text><text x="123" y="304" text-anchor="middle" class="d2">Cada una de las cinco recibe</text><text x="123" y="315" text-anchor="middle" class="d2">su propio BAJO, MEDIO o ALTO</text>
  <rect x="236" y="272" width="206" height="46" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="339" y="290" text-anchor="middle" class="b2">La CATEGORÍA se DERIVA</text><text x="339" y="304" text-anchor="middle" class="d2">Alguna ALTO → categoría ALTA.</text><text x="339" y="315" text-anchor="middle" class="d2">Si no, alguna MEDIO → MEDIA. Resto: BÁSICA</text>
  <rect x="452" y="272" width="208" height="46" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="556" y="290" text-anchor="middle" class="b2">EL ERROR MÁS PENALIZADO</text><text x="556" y="304" text-anchor="middle" class="d2">Confundir dimensión (C, I, T, A, D)</text><text x="556" y="315" text-anchor="middle" class="d2">con categoría (BÁSICA, MEDIA, ALTA)</text>

  <text x="20" y="340" class="n2">[Fuente: ENS, RD 311/2022, arts. 5 a 11 y anexos I y II — verificado contra el PDF del BOE]</text>
</svg>
```

---
## D3 · Amenazas y vectores de ataque: qué dice el ETL 2025

**Sección**: §1.2 — Amenazas, vulnerabilidades y vectores de ataque
**Propósito**: Separar los cuatro conceptos del análisis de riesgos, clasificar los ataques por la dimensión que rompen y contrastarlo con las **cifras reales** del informe de ENISA, que corrigen la intuición: el ataque más frecuente no es el más dañino.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 364" role="img" aria-label="Amenazas y vectores de ataque: cadena de amenaza, vulnerabilidad, riesgo e impacto; clasificación de ataques en interceptación, modificación, fabricación e interrupción según la dimensión que rompen; y cifras del informe ENISA Threat Landscape 2025 con 4.875 incidentes, 77 por ciento de ataques de denegación de servicio pero solo 2 por ciento con interrupción real, 60 por ciento de phishing como vector de entrada y 21,3 por ciento de explotación de vulnerabilidades">
  <style>.h3{font:700 13px system-ui,sans-serif;fill:#0055a0}.k3{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t3{font:700 10px system-ui,sans-serif;fill:#fff}.s3{font:8.5px system-ui,sans-serif;fill:#fff}.d3{font:8.5px system-ui,sans-serif;fill:#333}.b3{font:700 9px system-ui,sans-serif;fill:#0055a0}.n3{font:8px system-ui,sans-serif;fill:#666}.big3{font:700 17px system-ui,sans-serif;fill:#fff}.hd3{font:700 8.5px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h3">Sobre la amenaza no se actúa: se actúa sobre la vulnerabilidad y el impacto</text>

  <text x="20" y="40" class="k3">LA CADENA DEL RIESGO</text>
  <rect x="20" y="48" width="118" height="42" rx="5" fill="#999"/><text x="79" y="66" text-anchor="middle" class="t3">AMENAZA</text><text x="79" y="80" text-anchor="middle" class="s3">Existe fuera de mí</text>
  <text x="145" y="73" class="d3">aprovecha</text>
  <rect x="196" y="48" width="118" height="42" rx="5" fill="#d13c3c"/><text x="255" y="66" text-anchor="middle" class="t3">VULNERABILIDAD</text><text x="255" y="80" text-anchor="middle" class="s3">Debilidad propia</text>
  <text x="321" y="73" class="d3">produce</text>
  <rect x="366" y="48" width="118" height="42" rx="5" fill="#e89822"/><text x="425" y="66" text-anchor="middle" class="t3">RIESGO</text><text x="425" y="80" text-anchor="middle" class="s3">Probabilidad × impacto</text>
  <text x="491" y="73" class="d3">lo reduce</text>
  <rect x="542" y="48" width="118" height="42" rx="5" fill="#2d8659"/><text x="601" y="66" text-anchor="middle" class="t3">SALVAGUARDA</text><text x="601" y="80" text-anchor="middle" class="s3">Deja riesgo residual</text>

  <text x="20" y="112" class="k3">CLASIFICACIÓN POR LA DIMENSIÓN QUE ROMPEN</text>
  <text x="26" y="128" class="hd3">TIPO</text><text x="176" y="128" class="hd3">DIMENSIÓN</text><text x="286" y="128" class="hd3">EJEMPLOS EN RED</text><text x="536" y="128" class="hd3">¿SE DETECTA?</text>
  <rect x="20" y="134" width="150" height="26" rx="4" fill="#0055a0"/><text x="95" y="151" text-anchor="middle" class="s3">INTERCEPTACIÓN · pasivo</text>
  <text x="176" y="151" class="d3">Confidencialidad</text><text x="286" y="151" class="d3">Escucha de tráfico, captura de credenciales</text><text x="536" y="151" class="d3">Muy difícil: prevenir</text>
  <rect x="20" y="164" width="150" height="26" rx="4" fill="#d13c3c"/><text x="95" y="181" text-anchor="middle" class="s3">MODIFICACIÓN · activo</text>
  <text x="176" y="181" class="d3">Integridad</text><text x="286" y="181" class="d3">Alterar un paquete, envenenar la caché DNS</text><text x="536" y="181" class="d3">Sí: HMAC y alertas</text>
  <rect x="20" y="194" width="150" height="26" rx="4" fill="#d13c3c"/><text x="95" y="211" text-anchor="middle" class="s3">FABRICACIÓN · activo</text>
  <text x="176" y="211" class="d3">Autenticidad</text><text x="286" y="211" class="d3">Suplantar IP o MAC, correo falsificado</text><text x="536" y="211" class="d3">Sí: autenticación</text>
  <rect x="20" y="224" width="150" height="26" rx="4" fill="#d13c3c"/><text x="95" y="241" text-anchor="middle" class="s3">INTERRUPCIÓN · activo</text>
  <text x="176" y="241" class="d3">Disponibilidad</text><text x="286" y="241" class="d3">DoS y DDoS, corte de enlace, agotamiento</text><text x="536" y="241" class="d3">Sí, y de inmediato</text>

  <text x="20" y="268" class="k3">LAS CIFRAS QUE CORRIGEN LA INTUICIÓN · ENISA ETL 2025 · 4.875 INCIDENTES · 1-7-2024 A 30-6-2025</text>
  <rect x="20" y="276" width="156" height="52" rx="5" fill="#e89822"/><text x="98" y="298" text-anchor="middle" class="big3">77 %</text><text x="98" y="313" text-anchor="middle" class="s3">de los incidentes son DDoS…</text><text x="98" y="324" text-anchor="middle" class="s3">pero solo el 2 % interrumpe</text>
  <rect x="184" y="276" width="156" height="52" rx="5" fill="#d13c3c"/><text x="262" y="298" text-anchor="middle" class="big3">60 %</text><text x="262" y="313" text-anchor="middle" class="s3">de los accesos iniciales</text><text x="262" y="324" text-anchor="middle" class="s3">son PHISHING</text>
  <rect x="348" y="276" width="156" height="52" rx="5" fill="#d13c3c"/><text x="426" y="298" text-anchor="middle" class="big3">21,3 %</text><text x="426" y="313" text-anchor="middle" class="s3">explotación de</text><text x="426" y="324" text-anchor="middle" class="s3">VULNERABILIDADES</text>
  <rect x="512" y="276" width="148" height="52" rx="5" fill="#0055a0"/><text x="586" y="298" text-anchor="middle" class="big3">80 %</text><text x="586" y="313" text-anchor="middle" class="s3">de la ingeniería social ya</text><text x="586" y="324" text-anchor="middle" class="s3">usa IA (principios de 2025)</text>

  <text x="20" y="352" class="n3">[Fuente: ENISA Threat Landscape 2025 · MAGERIT v3 · ENS, RD 311/2022, mp.com.3.2]</text>
</svg>
```

---
## D4 · Ataque por capa de la pila TCP/IP y su contramedida

**Sección**: §1.3 — Mecanismos de protección en la pila de protocolos TCP/IP
**Propósito**: Mostrar que **cada capa tiene su ataque y su defensa**, y que un mecanismo de una capa **no protege** de los ataques de otra. Es el diagrama que explica por qué un cortafuegos de capa 3 no detiene un envenenamiento ARP.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 366" role="img" aria-label="Ataques y contramedidas por capa de la pila TCP barra IP: en la capa de aplicación phishing, inyección SQL y envenenamiento de DNS, defendidos con SSH, HTTPS, DNSSEC y proxy; en transporte inundación SYN y secuestro de sesión, defendidos con TLS, DTLS y cookies SYN; en internet suplantación de IP y denegación de servicio volumétrica, defendidos con IPsec y filtrado; y en acceso al medio envenenamiento ARP, saturación de la tabla CAM y punto de acceso impostor, defendidos con 802.1X, MACsec, inspección de ARP y WPA3">
  <style>.h4{font:700 13px system-ui,sans-serif;fill:#0055a0}.k4{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t4{font:700 10.5px system-ui,sans-serif;fill:#fff}.s4{font:8.5px system-ui,sans-serif;fill:#fff}.d4{font:8.5px system-ui,sans-serif;fill:#333}.b4{font:700 9px system-ui,sans-serif;fill:#0055a0}.n4{font:8px system-ui,sans-serif;fill:#666}.hd4{font:700 8.5px system-ui,sans-serif;fill:#0055a0}.r4{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}.g4{font:700 8.5px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="20" text-anchor="middle" class="h4">Cada capa tiene su ataque y su defensa: no son intercambiables</text>

  <text x="26" y="42" class="hd4">CAPA TCP/IP</text><text x="152" y="42" class="hd4">ATAQUES CARACTERÍSTICOS</text><text x="400" y="42" class="hd4">MECANISMO DE PROTECCIÓN</text>

  <rect x="20" y="48" width="126" height="58" rx="5" fill="#0055a0"/><text x="83" y="70" text-anchor="middle" class="t4">APLICACIÓN</text><text x="83" y="86" text-anchor="middle" class="s4">Capa 4 de TCP/IP</text><text x="83" y="98" text-anchor="middle" class="s4">(5-6-7 de OSI)</text>
  <rect x="152" y="48" width="238" height="58" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="162" y="66" class="r4">Phishing e ingeniería social</text><text x="162" y="80" class="d4">Inyección SQL, XSS, recorrido de directorios</text><text x="162" y="94" class="d4">Envenenamiento de caché DNS · DDoS de aplicación</text>
  <rect x="396" y="48" width="264" height="58" rx="5" fill="#eef7f1" stroke="#2d8659"/><text x="406" y="66" class="g4">SSH · HTTPS · DNSSEC · S/MIME</text><text x="406" y="80" class="d4">Proxy y pasarela de aplicación (§2.2.2) · WAF</text><text x="406" y="94" class="d4">Formación del usuario (§5.4) · antimalware</text>

  <rect x="20" y="112" width="126" height="52" rx="5" fill="#0055a0"/><text x="83" y="134" text-anchor="middle" class="t4">TRANSPORTE</text><text x="83" y="150" text-anchor="middle" class="s4">TCP y UDP</text>
  <rect x="152" y="112" width="238" height="52" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="162" y="130" class="r4">Inundación SYN (agota la tabla de estados)</text><text x="162" y="144" class="d4">Secuestro de sesión TCP · escaneo de puertos</text><text x="162" y="157" class="d4">Degradación forzada de la versión de TLS</text>
  <rect x="396" y="112" width="264" height="52" rx="5" fill="#eef7f1" stroke="#2d8659"/><text x="406" y="130" class="g4">TLS 1.2 y 1.3 · DTLS · cookies SYN</text><text x="406" y="144" class="d4">Cortafuegos con estado (§2.2.1) · límites por origen</text><text x="406" y="157" class="d4">HSTS y prohibición de versiones antiguas</text>

  <rect x="20" y="170" width="126" height="52" rx="5" fill="#0055a0"/><text x="83" y="192" text-anchor="middle" class="t4">INTERNET</text><text x="83" y="208" text-anchor="middle" class="s4">IP, ICMP, encaminamiento</text>
  <rect x="152" y="170" width="238" height="52" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="162" y="188" class="r4">Suplantación de dirección IP</text><text x="162" y="202" class="d4">DDoS volumétrico · reconocimiento y barrido</text><text x="162" y="215" class="d4">Secuestro de prefijo y encaminamiento malicioso</text>
  <rect x="396" y="170" width="264" height="52" rx="5" fill="#eef7f1" stroke="#2d8659"/><text x="406" y="188" class="g4">IPsec: AH, ESP e IKEv2 (§4.2.1)</text><text x="406" y="202" class="d4">Filtrado en cortafuegos y encaminador · antifalsificación</text><text x="406" y="215" class="d4">Mitigación aguas arriba · RPKI en el encaminamiento</text>

  <rect x="20" y="228" width="126" height="58" rx="5" fill="#0055a0"/><text x="83" y="250" text-anchor="middle" class="t4">ACCESO AL MEDIO</text><text x="83" y="266" text-anchor="middle" class="s4">Enlace y físico</text><text x="83" y="278" text-anchor="middle" class="s4">Ethernet, Wi-Fi</text>
  <rect x="152" y="228" width="238" height="58" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="162" y="246" class="r4">Envenenamiento ARP · saturación de la tabla CAM</text><text x="162" y="260" class="d4">Salto de VLAN · servidor DHCP no autorizado</text><text x="162" y="274" class="d4">Punto de acceso impostor · escucha del cableado</text>
  <rect x="396" y="228" width="264" height="58" rx="5" fill="#eef7f1" stroke="#2d8659"/><text x="406" y="246" class="g4">802.1X con EAP · MACsec (IEEE 802.1AE)</text><text x="406" y="260" class="d4">Inspección dinámica de ARP · vigilancia de DHCP</text><text x="406" y="274" class="d4">Seguridad de puerto · VLAN · WPA3-Enterprise</text>

  <rect x="20" y="292" width="640" height="42" rx="5" fill="#fff5e6" stroke="#e89822"/>
  <text x="340" y="307" text-anchor="middle" class="b4">La regla que permite elegir capa</text>
  <text x="340" y="319" text-anchor="middle" class="d4">Cuanto más BAJA es la capa, MÁS tráfico se protege de golpe y MENOS se entiende de lo que se protege.</text>
  <text x="340" y="330" text-anchor="middle" class="d4">Por eso conviven: MACsec protege un cable, IPsec todas las aplicaciones, TLS una conexión concreta</text>

  <text x="20" y="352" class="n4">[Fuente: RFC 4301 (IPsec) · RFC 9846 (TLS 1.3) · RFC 3748 (EAP) · IEEE 802.1X y 802.1AE · ENS, mp.com]</text>
</svg>
```

---
## D5 · Protocolos en claro y su versión segura: tabla de puertos

**Sección**: §1.3.2 — Seguridad en la capa de transporte y aplicación
**Propósito**: Concentrar en una sola imagen **la tabla de puertos más rentable del tema**. Aquí los puertos van emparejados con el protocolo inseguro que sustituyen.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Tabla de protocolos en claro y su versión segura con los puertos: Telnet 23 sustituido por SSH 22; FTP 21 por SFTP 22 o FTPS 990; HTTP 80 por HTTPS 443; SMTP 25 por envío con TLS en 587 o 465; POP3 110 e IMAP 143 por POP3S 995 e IMAPS 993; LDAP 389 por LDAPS 636; SNMP versión 1 y 2c por SNMP versión 3; DNS 53 por DNS sobre TLS en 853 y DNS sobre HTTPS en 443; syslog 514 por syslog sobre TLS en 6514; y escritorio remoto RDP en 3389 que nunca se publica a internet">
  <style>.h5{font:700 13px system-ui,sans-serif;fill:#0055a0}.k5{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d5{font:8.5px system-ui,sans-serif;fill:#333}.b5{font:700 9px system-ui,sans-serif;fill:#0055a0}.n5{font:8px system-ui,sans-serif;fill:#666}.hd5{font:700 8.5px system-ui,sans-serif;fill:#fff}.pr5{font:700 9px system-ui,sans-serif;fill:#d13c3c}.pg5{font:700 9px system-ui,sans-serif;fill:#2d8659}.s5{font:8.5px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="h5">Todo protocolo clásico de internet nació en claro y tiene hoy su versión protegida</text>

  <rect x="20" y="32" width="640" height="20" rx="4" fill="#0055a0"/>
  <text x="30" y="46" class="hd5">SERVICIO</text><text x="180" y="46" class="hd5">EN CLARO — NO USAR</text><text x="316" y="46" class="hd5">PUERTO</text><text x="392" y="46" class="hd5">VERSIÓN SEGURA</text><text x="566" y="46" class="hd5">PUERTO</text>

  <rect x="20" y="54" width="640" height="24" fill="#f7f9fc"/>
  <text x="30" y="70" class="d5">Consola remota de texto</text><text x="180" y="70" class="pr5">Telnet</text><text x="316" y="70" class="d5">TCP 23</text><text x="392" y="70" class="pg5">SSH</text><text x="566" y="70" class="d5">TCP 22</text>
  <rect x="20" y="80" width="640" height="24" fill="#fff"/>
  <text x="30" y="96" class="d5">Sesión remota (heredado)</text><text x="180" y="96" class="pr5">rlogin · rsh · rcp</text><text x="316" y="96" class="d5">TCP 513-514</text><text x="392" y="96" class="pg5">SSH y sus derivados</text><text x="566" y="96" class="d5">TCP 22</text>
  <rect x="20" y="106" width="640" height="24" fill="#f7f9fc"/>
  <text x="30" y="122" class="d5">Transferencia de ficheros</text><text x="180" y="122" class="pr5">FTP · TFTP</text><text x="316" y="122" class="d5">TCP 21 · UDP 69</text><text x="392" y="122" class="pg5">SFTP (en SSH) · FTPS (en TLS)</text><text x="566" y="122" class="d5">TCP 22 · 990</text>
  <rect x="20" y="132" width="640" height="24" fill="#fff"/>
  <text x="30" y="148" class="d5">Web</text><text x="180" y="148" class="pr5">HTTP</text><text x="316" y="148" class="d5">TCP 80</text><text x="392" y="148" class="pg5">HTTPS (HTTP sobre TLS)</text><text x="566" y="148" class="d5">TCP 443</text>
  <rect x="20" y="158" width="640" height="24" fill="#f7f9fc"/>
  <text x="30" y="174" class="d5">Correo entre servidores</text><text x="180" y="174" class="pr5">SMTP sin cifrar</text><text x="316" y="174" class="d5">TCP 25</text><text x="392" y="174" class="pg5">SMTP con STARTTLS</text><text x="566" y="174" class="d5">TCP 25 · 587</text>
  <rect x="20" y="184" width="640" height="24" fill="#fff"/>
  <text x="30" y="200" class="d5">Envío desde el cliente</text><text x="180" y="200" class="pr5">SMTP en claro</text><text x="316" y="200" class="d5">TCP 25</text><text x="392" y="200" class="pg5">Envío con TLS implícito</text><text x="566" y="200" class="d5">TCP 465 · 587</text>
  <rect x="20" y="210" width="640" height="24" fill="#f7f9fc"/>
  <text x="30" y="226" class="d5">Lectura de correo</text><text x="180" y="226" class="pr5">POP3 · IMAP</text><text x="316" y="226" class="d5">TCP 110 · 143</text><text x="392" y="226" class="pg5">POP3S · IMAPS</text><text x="566" y="226" class="d5">TCP 995 · 993</text>
  <rect x="20" y="236" width="640" height="24" fill="#fff"/>
  <text x="30" y="252" class="d5">Directorio</text><text x="180" y="252" class="pr5">LDAP</text><text x="316" y="252" class="d5">TCP 389</text><text x="392" y="252" class="pg5">LDAPS o LDAP con STARTTLS</text><text x="566" y="252" class="d5">TCP 636</text>
  <rect x="20" y="262" width="640" height="24" fill="#f7f9fc"/>
  <text x="30" y="278" class="d5">Gestión de red</text><text x="180" y="278" class="pr5">SNMPv1 y v2c</text><text x="316" y="278" class="d5">UDP 161</text><text x="392" y="278" class="pg5">SNMPv3 (autenticación y cifrado)</text><text x="566" y="278" class="d5">UDP 161</text>
  <rect x="20" y="288" width="640" height="24" fill="#fff"/>
  <text x="30" y="304" class="d5">Resolución de nombres</text><text x="180" y="304" class="pr5">DNS sin cifrar</text><text x="316" y="304" class="d5">UDP/TCP 53</text><text x="392" y="304" class="pg5">DoT · DoH (DNSSEC firma, no cifra)</text><text x="566" y="304" class="d5">TCP 853 · 443</text>
  <rect x="20" y="314" width="640" height="24" fill="#f7f9fc"/>
  <text x="30" y="330" class="d5">Registro centralizado</text><text x="180" y="330" class="pr5">Syslog sin cifrar</text><text x="316" y="330" class="d5">UDP 514</text><text x="392" y="330" class="pg5">Syslog sobre TLS (RFC 5425)</text><text x="566" y="330" class="d5">TCP 6514</text>

  <rect x="20" y="342" width="640" height="16" rx="3" fill="#d13c3c"/>
  <text x="340" y="354" text-anchor="middle" class="s5">Y el que se usa mal: RDP, escritorio remoto, TCP y UDP 3389 — NUNCA se publica a internet; se accede por VPN o pasarela</text>

  <text x="20" y="368" class="n5">[Fuente: RFC 8314 (correo con TLS) · RFC 9846 (TLS 1.3) · RFC 4251-4254 (SSH) · RFC 5425 (syslog sobre TLS) · RFC 7858 y 8484 (DoT y DoH)]</text>
</svg>
```

---
## D6 · El ENS en la red: qué medida aplica en qué categoría

**Sección**: §1.4 — Cumplimiento del ENS en redes de la Administración Pública
**Propósito**: Es **la tabla que convierte una respuesta técnica en una respuesta de oposición**. Reúne las medidas del anexo II que este tema necesita, con su tabla de aplicación literal, y marca en rojo las tres que **no aplican** en el nivel o categoría más bajos, que es donde se falla.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 380" role="img" aria-label="Matriz de medidas del anexo dos del Esquema Nacional de Seguridad aplicables a este tema, con su aplicación en categoría básica, media y alta: perímetro seguro mp com uno aplica en las tres; protección de la confidencialidad mp com dos; protección de la integridad y autenticidad mp com tres; separación de flujos mp com cuatro que no aplica en básica; detección de intrusión op mon uno; vigilancia op mon tres; autenticación op acc cinco; código dañino op exp seis con EDR en alta; y las medidas del puesto mp eq uno a cuatro, más navegación web, concienciación y formación">
  <style>.h6{font:700 13px system-ui,sans-serif;fill:#0055a0}.k6{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d6{font:8.5px system-ui,sans-serif;fill:#333}.b6{font:700 9px system-ui,sans-serif;fill:#0055a0}.n6{font:8px system-ui,sans-serif;fill:#666}.hd6{font:700 8.5px system-ui,sans-serif;fill:#fff}.cd6{font:700 8.5px system-ui,sans-serif;fill:#0055a0}.na6{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}.ok6{font:8.5px system-ui,sans-serif;fill:#2d8659}.s6{font:8.5px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="h6">Las medidas del anexo II que hay que citar en este tema</text>

  <rect x="20" y="30" width="640" height="20" rx="4" fill="#0055a0"/>
  <text x="28" y="44" class="hd6">CÓDIGO</text><text x="98" y="44" class="hd6">DENOMINACIÓN OFICIAL</text><text x="330" y="44" class="hd6">DIM.</text><text x="376" y="44" class="hd6">BÁSICA</text><text x="452" y="44" class="hd6">MEDIA</text><text x="556" y="44" class="hd6">ALTA</text>

  <rect x="20" y="52" width="640" height="22" fill="#f7f9fc"/><text x="28" y="67" class="cd6">mp.com.1</text><text x="98" y="67" class="d6">Perímetro seguro</text><text x="330" y="67" class="d6">Todas</text><text x="376" y="67" class="ok6">aplica</text><text x="452" y="67" class="ok6">aplica</text><text x="556" y="67" class="ok6">aplica</text>
  <rect x="20" y="76" width="640" height="22" fill="#fff"/><text x="28" y="91" class="cd6">mp.com.2</text><text x="98" y="91" class="d6">Protección de la confidencialidad — exige VPN cifrada</text><text x="330" y="91" class="d6">C</text><text x="376" y="91" class="ok6">aplica</text><text x="452" y="91" class="ok6">+ R1</text><text x="556" y="91" class="ok6">+ R1 + R2 + R3</text>
  <rect x="20" y="100" width="640" height="22" fill="#f7f9fc"/><text x="28" y="115" class="cd6">mp.com.3</text><text x="98" y="115" class="d6">Protección de la integridad y de la autenticidad</text><text x="330" y="115" class="d6">I · A</text><text x="376" y="115" class="ok6">aplica</text><text x="452" y="115" class="ok6">+ R1 + R2</text><text x="556" y="115" class="ok6">+ R1 a R4</text>
  <rect x="20" y="124" width="640" height="22" fill="#fdeeee"/><text x="28" y="139" class="cd6">mp.com.4</text><text x="98" y="139" class="d6">Separación de flujos en la red — VLAN, VPN o física</text><text x="330" y="139" class="d6">Todas</text><text x="376" y="139" class="na6">NO APLICA</text><text x="452" y="139" class="ok6">+ [R1 o R2 o R3]</text><text x="556" y="139" class="ok6">+ [R2 o R3] + R4</text>
  <rect x="20" y="148" width="640" height="22" fill="#fff"/><text x="28" y="163" class="cd6">op.mon.1</text><text x="98" y="163" class="d6">Detección de intrusión — IDS o IPS</text><text x="330" y="163" class="d6">Todas</text><text x="376" y="163" class="ok6">aplica</text><text x="452" y="163" class="ok6">+ R1 (por reglas)</text><text x="556" y="163" class="ok6">+ R1 + R2</text>
  <rect x="20" y="172" width="640" height="22" fill="#f7f9fc"/><text x="28" y="187" class="cd6">op.mon.3</text><text x="98" y="187" class="d6">Vigilancia — recolección de eventos; R1 es el SIEM</text><text x="330" y="187" class="d6">Todas</text><text x="376" y="187" class="ok6">aplica</text><text x="452" y="187" class="ok6">+ R1 + R2</text><text x="556" y="187" class="ok6">+ R1 a R6</text>
  <rect x="20" y="196" width="640" height="22" fill="#fff"/><text x="28" y="211" class="cd6">op.acc.5</text><text x="98" y="211" class="d6">Mecanismo de autenticación (usuarios externos)</text><text x="330" y="211" class="d6">Todas</text><text x="376" y="211" class="ok6">+ [R1 a R4]</text><text x="452" y="211" class="ok6">+ [R2 o R3 o R4] + R5</text><text x="556" y="211" class="ok6">igual que MEDIA</text>
  <rect x="20" y="220" width="640" height="22" fill="#f7f9fc"/><text x="28" y="235" class="cd6">op.exp.6</text><text x="98" y="235" class="d6">Protección frente a código dañino — R4 es el EDR</text><text x="330" y="235" class="d6">Todas</text><text x="376" y="235" class="ok6">aplica</text><text x="452" y="235" class="ok6">+ R1 + R2</text><text x="556" y="235" class="ok6">+ R1 + R2 + R3 + R4</text>
  <rect x="20" y="244" width="640" height="22" fill="#fff"/><text x="28" y="259" class="cd6">mp.eq.1</text><text x="98" y="259" class="d6">Puesto de trabajo despejado</text><text x="330" y="259" class="d6">Todas</text><text x="376" y="259" class="ok6">aplica</text><text x="452" y="259" class="ok6">+ R1</text><text x="556" y="259" class="ok6">+ R1</text>
  <rect x="20" y="268" width="640" height="22" fill="#fdeeee"/><text x="28" y="283" class="cd6">mp.eq.2</text><text x="98" y="283" class="d6">Bloqueo de puesto de trabajo</text><text x="330" y="283" class="d6">A</text><text x="376" y="283" class="na6">NO APLICA</text><text x="452" y="283" class="ok6">aplica</text><text x="556" y="283" class="ok6">+ R1 (cierra sesiones)</text>
  <rect x="20" y="292" width="640" height="22" fill="#fff"/><text x="28" y="307" class="cd6">mp.eq.3</text><text x="98" y="307" class="d6">Protección de dispositivos portátiles — R1 cifra disco</text><text x="330" y="307" class="d6">Todas</text><text x="376" y="307" class="ok6">aplica</text><text x="452" y="307" class="ok6">aplica</text><text x="556" y="307" class="ok6">+ R1 + R2</text>
  <rect x="20" y="316" width="640" height="22" fill="#f7f9fc"/><text x="28" y="331" class="cd6">mp.per.3 y 4</text><text x="98" y="331" class="d6">Concienciación y Formación</text><text x="330" y="331" class="d6">Todas</text><text x="376" y="331" class="ok6">aplica</text><text x="452" y="331" class="ok6">aplica</text><text x="556" y="331" class="ok6">aplica</text>

  <rect x="20" y="344" width="640" height="18" rx="3" fill="#e89822"/>
  <text x="340" y="357" text-anchor="middle" class="s6">El detalle que casi nadie sabe: mp.com.1 remite a una ITS de INTERCONEXIÓN que NO está publicada — solo hay cuatro ITS en el BOE</text>

  <text x="20" y="374" class="n6">[Fuente: ENS, RD 311/2022, anexo II — tablas de aplicación verificadas contra el PDF del BOE, BOE-A-2022-7191]</text>
</svg>
```

---
## D7 · Del perímetro-muralla al perímetro distribuido

**Sección**: §2.1 — Concepto y arquitectura del perímetro de seguridad
**Propósito**: Contar en **tres etapas** por qué el modelo perimetral clásico entró en crisis y qué lo sustituye, dejando claro el matiz clave: el perímetro **no desaparece**, deja de ser suficiente.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Evolución del perímetro en tres etapas: primero el perímetro muralla con una sola frontera y un interior de confianza; después la defensa en profundidad con perímetro segmentado y varias fronteras internas conforme al artículo 9 del Esquema Nacional de Seguridad; y por último la confianza cero, donde la frontera se acerca a cada recurso. Se advierte de que el perímetro sigue siendo obligatorio por la medida mp punto com punto uno">
  <style>.h7{font:700 13px system-ui,sans-serif;fill:#0055a0}.k7{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t7{font:700 10.5px system-ui,sans-serif;fill:#fff}.s7{font:8.5px system-ui,sans-serif;fill:#fff}.d7{font:8.5px system-ui,sans-serif;fill:#333}.b7{font:700 9px system-ui,sans-serif;fill:#0055a0}.n7{font:8px system-ui,sans-serif;fill:#666}.r7{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h7">El perímetro no ha desaparecido: ha dejado de ser suficiente</text>

  <rect x="20" y="34" width="206" height="26" rx="4" fill="#999"/><text x="123" y="52" text-anchor="middle" class="t7">1 · PERÍMETRO-MURALLA</text>
  <rect x="236" y="34" width="206" height="26" rx="4" fill="#0055a0"/><text x="339" y="52" text-anchor="middle" class="t7">2 · DEFENSA EN PROFUNDIDAD</text>
  <rect x="452" y="34" width="208" height="26" rx="4" fill="#2d8659"/><text x="556" y="52" text-anchor="middle" class="t7">3 · CONFIANZA CERO</text>

  <rect x="20" y="66" width="206" height="92" rx="5" fill="#f4f4f6" stroke="#999"/>
  <rect x="34" y="86" width="178" height="56" rx="4" fill="none" stroke="#999" stroke-width="2"/>
  <rect x="48" y="94" width="66" height="18" rx="3" fill="#bbb"/><text x="81" y="107" text-anchor="middle" class="s7">Puestos</text>
  <rect x="122" y="94" width="76" height="18" rx="3" fill="#bbb"/><text x="160" y="107" text-anchor="middle" class="s7">Servidores</text>
  <rect x="48" y="118" width="150" height="18" rx="3" fill="#bbb"/><text x="123" y="131" text-anchor="middle" class="s7">Todo se ve con todo: red plana</text>
  <text x="123" y="80" text-anchor="middle" class="b7">Una sola frontera</text>

  <rect x="236" y="66" width="206" height="92" rx="5" fill="#eef4fa" stroke="#0055a0"/>
  <rect x="248" y="86" width="182" height="56" rx="4" fill="none" stroke="#0055a0" stroke-width="2"/>
  <rect x="258" y="94" width="80" height="20" rx="3" fill="#0055a0"/><text x="298" y="108" text-anchor="middle" class="s7">DMZ</text>
  <rect x="344" y="94" width="78" height="20" rx="3" fill="#0055a0"/><text x="383" y="108" text-anchor="middle" class="s7">Servicios</text>
  <rect x="258" y="118" width="80" height="20" rx="3" fill="#0055a0"/><text x="298" y="132" text-anchor="middle" class="s7">Usuarios</text>
  <rect x="344" y="118" width="78" height="20" rx="3" fill="#0055a0"/><text x="383" y="132" text-anchor="middle" class="s7">Administración</text>
  <text x="339" y="80" text-anchor="middle" class="b7">Varias fronteras internas · art. 9</text>

  <rect x="452" y="66" width="208" height="92" rx="5" fill="#eef7f1" stroke="#2d8659"/>
  <circle cx="500" cy="98" r="15" fill="#2d8659"/><text x="500" y="102" text-anchor="middle" class="s7">App</text>
  <circle cx="556" cy="98" r="15" fill="#2d8659"/><text x="556" y="102" text-anchor="middle" class="s7">Dato</text>
  <circle cx="612" cy="98" r="15" fill="#2d8659"/><text x="612" y="102" text-anchor="middle" class="s7">API</text>
  <circle cx="500" cy="134" r="15" fill="#2d8659"/><text x="500" y="138" text-anchor="middle" class="s7">SaaS</text>
  <circle cx="556" cy="134" r="15" fill="#2d8659"/><text x="556" y="138" text-anchor="middle" class="s7">VM</text>
  <circle cx="612" cy="134" r="15" fill="#2d8659"/><text x="612" y="138" text-anchor="middle" class="s7">Web</text>
  <text x="556" y="80" text-anchor="middle" class="b7">Una frontera POR RECURSO</text>

  <text x="20" y="180" class="k7">QUÉ ROMPIÓ EL MODELO CLÁSICO</text>
  <rect x="20" y="188" width="156" height="44" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="98" y="204" text-anchor="middle" class="r7">TELETRABAJO</text><text x="98" y="218" text-anchor="middle" class="d7">El usuario ya no está</text><text x="98" y="229" text-anchor="middle" class="d7">dentro del edificio</text>
  <rect x="184" y="188" width="156" height="44" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="262" y="204" text-anchor="middle" class="r7">NUBE</text><text x="262" y="218" text-anchor="middle" class="d7">El servicio ya no está</text><text x="262" y="229" text-anchor="middle" class="d7">dentro del CPD</text>
  <rect x="348" y="188" width="156" height="44" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="426" y="204" text-anchor="middle" class="r7">MOVILIDAD Y BYOD</text><text x="426" y="218" text-anchor="middle" class="d7">Dentro hay equipos que</text><text x="426" y="229" text-anchor="middle" class="d7">no son de la organización</text>
  <rect x="512" y="188" width="148" height="44" rx="5" fill="#fdeeee" stroke="#d13c3c"/><text x="586" y="204" text-anchor="middle" class="r7">MOVIMIENTO LATERAL</text><text x="586" y="218" text-anchor="middle" class="d7">Un puesto comprometido</text><text x="586" y="229" text-anchor="middle" class="d7">recorre la red plana</text>

  <text x="20" y="254" class="k7">LAS DOS REGLAS QUE DEFINEN UN PERÍMETRO, Y QUE SIGUEN VIGENTES</text>
  <rect x="20" y="262" width="316" height="42" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="178" y="280" text-anchor="middle" class="b7">1 · Todo el tráfico atraviesa el sistema</text><text x="178" y="295" text-anchor="middle" class="d7">mp.com.1.1 — si existe una salida alternativa, el perímetro no existe</text>
  <rect x="344" y="262" width="316" height="42" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="502" y="280" text-anchor="middle" class="b7">2 · Denegación por defecto</text><text x="502" y="295" text-anchor="middle" class="d7">mp.com.1.2 — todos los flujos autorizados PREVIAMENTE</text>

  <text x="20" y="328" class="n7">[Fuente: ENS, RD 311/2022, art. 9, art. 23 y mp.com.1 · NIST SP 800-207 (Zero Trust Architecture, 2020)]</text>
</svg>
```

---
## D8 · Las cinco generaciones de cortafuegos

**Sección**: §2.2.1 — Cortafuegos de red, estado e inspección de aplicación
**Propósito**: Ordenar las generaciones por **la capa que examina cada una** y fijar la diferencia clave —la **tabla de estados**—, además de separar el **WAF**, que no es un cortafuegos de red.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 364" role="img" aria-label="Las cinco generaciones de cortafuegos: filtro de paquetes sin estado en capas tres y cuatro; cortafuegos con estado que mantiene una tabla de conexiones; pasarela de aplicación o proxy en capa siete que rompe la conexión en dos; gestión unificada de amenazas UTM que integra varias funciones; y cortafuegos de nueva generación NGFW que identifica aplicación y usuario. Se añade que el cortafuegos de aplicaciones web WAF protege una aplicación y no la red">
  <style>.h8{font:700 13px system-ui,sans-serif;fill:#0055a0}.k8{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t8{font:700 10px system-ui,sans-serif;fill:#fff}.s8{font:8.5px system-ui,sans-serif;fill:#fff}.d8{font:8.5px system-ui,sans-serif;fill:#333}.b8{font:700 9px system-ui,sans-serif;fill:#0055a0}.n8{font:8px system-ui,sans-serif;fill:#666}.hd8{font:700 8.5px system-ui,sans-serif;fill:#0055a0}.r8{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h8">Cada generación mira una capa más arriba, y sabe algo más de lo que deja pasar</text>

  <text x="26" y="42" class="hd8">GENERACIÓN</text><text x="176" y="42" class="hd8">CAPA</text><text x="232" y="42" class="hd8">QUÉ EXAMINA</text><text x="450" y="42" class="hd8">SU LIMITACIÓN CARACTERÍSTICA</text>

  <rect x="20" y="48" width="150" height="42" rx="4" fill="#8fa8bf"/><text x="95" y="66" text-anchor="middle" class="t8">1 · FILTRO DE PAQUETES</text><text x="95" y="80" text-anchor="middle" class="s8">Sin estado (stateless)</text>
  <text x="176" y="72" class="d8">3 y 4</text>
  <text x="232" y="66" class="d8">Cada paquete AISLADO: IP origen y destino,</text><text x="232" y="79" class="d8">protocolo, puertos, banderas TCP</text>
  <text x="450" y="66" class="d8">No recuerda nada: hay que abrir</text><text x="450" y="79" class="d8">reglas en los DOS sentidos</text>

  <rect x="20" y="96" width="150" height="42" rx="4" fill="#4d7ba6"/><text x="95" y="114" text-anchor="middle" class="t8">2 · CON ESTADO</text><text x="95" y="128" text-anchor="middle" class="s8">Stateful inspection</text>
  <text x="176" y="120" class="d8">3 y 4</text>
  <text x="232" y="114" class="d8">El paquete Y LA CONEXIÓN a la que pertenece,</text><text x="232" y="127" class="d8">mediante una TABLA DE ESTADOS</text>
  <text x="450" y="114" class="d8">No entiende el contenido: para él,</text><text x="450" y="127" class="d8">todo lo que va por 443 es "web"</text>

  <rect x="20" y="144" width="150" height="42" rx="4" fill="#0055a0"/><text x="95" y="162" text-anchor="middle" class="t8">3 · PASARELA (PROXY)</text><text x="95" y="176" text-anchor="middle" class="s8">Rompe la conexión en dos</text>
  <text x="176" y="168" class="d8">7</text>
  <text x="232" y="162" class="d8">El CONTENIDO del protocolo. Rompe la</text><text x="232" y="175" class="d8">conexión en dos y actúa de intermediario</text>
  <text x="450" y="162" class="d8">Coste de proceso, y hay que</text><text x="450" y="175" class="d8">implementar un proxy POR protocolo</text>

  <rect x="20" y="192" width="150" height="42" rx="4" fill="#e89822"/><text x="95" y="210" text-anchor="middle" class="t8">UTM</text><text x="95" y="224" text-anchor="middle" class="s8">Gestión unificada</text>
  <text x="176" y="216" class="d8">3-7</text>
  <text x="232" y="210" class="d8">Varias funciones en una sola caja: cortafuegos,</text><text x="232" y="223" class="d8">IPS, antivirus, filtro web, antispam y VPN</text>
  <text x="450" y="210" class="d8">Punto único de fallo, y penaliza</text><text x="450" y="223" class="d8">el rendimiento al activarlo todo</text>

  <rect x="20" y="240" width="150" height="42" rx="4" fill="#2d8659"/><text x="95" y="258" text-anchor="middle" class="t8">NGFW</text><text x="95" y="272" text-anchor="middle" class="s8">Nueva generación</text>
  <text x="176" y="264" class="d8">3-7</text>
  <text x="232" y="258" class="d8">La APLICACIÓN y el USUARIO, no solo el puerto</text><text x="232" y="271" class="d8">y la IP. Integra IPS, antimalware y descifrado TLS</text>
  <text x="450" y="258" class="d8">Necesita descifrar TLS para ver el</text><text x="450" y="271" class="d8">contenido: mp.s.3.r1.2 lo regula</text>

  <rect x="20" y="292" width="316" height="44" rx="5" fill="#eef4fa" stroke="#0055a0"/>
  <text x="178" y="308" text-anchor="middle" class="b8">LA DIFERENCIA CLAVE</text>
  <text x="178" y="322" text-anchor="middle" class="d8">Filtro de paquetes frente a cortafuegos con estado:</text>
  <text x="178" y="333" text-anchor="middle" class="d8">la TABLA DE ESTADOS: las reglas se escriben en un solo sentido</text>

  <rect x="344" y="292" width="316" height="44" rx="5" fill="#fdeeee" stroke="#d13c3c"/>
  <text x="502" y="308" text-anchor="middle" class="r8">EL WAF NO ES UN CORTAFUEGOS DE RED</text>
  <text x="502" y="322" text-anchor="middle" class="d8">Protege UNA aplicación web frente a inyección SQL, XSS</text>
  <text x="502" y="333" text-anchor="middle" class="d8">y recorrido de directorios. mp.s.2 ya exige + [R1 o R2] en BÁSICA</text>

  <text x="20" y="356" class="n8">[Fuente: CCN-STIC-408 (Seguridad perimetral — cortafuegos) · CCN-STIC-140 (taxonomía) · ENS, mp.com.1 y mp.s.2]</text>
</svg>
```

---
## D9 · Proxy directo, proxy inverso y pasarela de aplicación

**Sección**: §2.2.2 — Pasarelas de aplicación y servidores proxy de seguridad
**Propósito**: Distinguir gráficamente **a quién protege cada proxy** y con qué medida del ENS se corresponde. La confusión entre directo e inverso es error frecuente y aquí se resuelve por su posición en el dibujo.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 348" role="img" aria-label="Comparación entre proxy directo y proxy inverso: el proxy directo se sitúa entre los clientes internos e internet y aplica la medida mp punto ese punto tres de protección de la navegación web; el proxy inverso se sitúa entre internet y los servidores publicados, termina el TLS, equilibra carga e integra el cortafuegos de aplicaciones web, y se corresponde con la medida mp punto ese punto dos">
  <style>.h9{font:700 13px system-ui,sans-serif;fill:#0055a0}.k9{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t9{font:700 9.5px system-ui,sans-serif;fill:#fff}.s9{font:8px system-ui,sans-serif;fill:#fff}.d9{font:8.5px system-ui,sans-serif;fill:#333}.b9{font:700 9px system-ui,sans-serif;fill:#0055a0}.n9{font:8px system-ui,sans-serif;fill:#666}.a9{font:8px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h9">La diferencia está en a quién tapa: al que sale o al que se publica</text>

  <text x="20" y="42" class="k9">PROXY DIRECTO (FORWARD) · PROTEGE Y CONTROLA A LOS CLIENTES QUE SALEN</text>
  <rect x="20" y="50" width="640" height="66" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <rect x="34" y="66" width="96" height="34" rx="4" fill="#0055a0"/><text x="82" y="80" text-anchor="middle" class="t9">PUESTOS</text><text x="82" y="93" text-anchor="middle" class="s9">Red interna municipal</text>
  <text x="140" y="86" class="a9">→</text>
  <rect x="158" y="66" width="126" height="34" rx="4" fill="#e89822"/><text x="221" y="80" text-anchor="middle" class="t9">PROXY DIRECTO</text><text x="221" y="93" text-anchor="middle" class="s9">Autentica al usuario</text>
  <text x="294" y="86" class="a9">→</text>
  <rect x="312" y="66" width="96" height="34" rx="4" fill="#999"/><text x="360" y="80" text-anchor="middle" class="t9">INTERNET</text><text x="360" y="93" text-anchor="middle" class="s9">Destino real</text>
  <rect x="424" y="60" width="222" height="46" rx="4" fill="#eef4fa" stroke="#0055a0"/><text x="535" y="74" text-anchor="middle" class="b9">Qué permite hacer · mp.s.3</text><text x="535" y="87" text-anchor="middle" class="d9">Filtrar por URL y categoría · registrar QUIÉN</text><text x="535" y="99" text-anchor="middle" class="d9">navegó · analizar descargas · caché · listas</text>

  <text x="20" y="136" class="k9">PROXY INVERSO (REVERSE) · PROTEGE Y OCULTA A LOS SERVIDORES PUBLICADOS</text>
  <rect x="20" y="144" width="640" height="66" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <rect x="34" y="160" width="96" height="34" rx="4" fill="#999"/><text x="82" y="174" text-anchor="middle" class="t9">CIUDADANO</text><text x="82" y="187" text-anchor="middle" class="s9">Desde internet</text>
  <text x="140" y="180" class="a9">→</text>
  <rect x="158" y="160" width="126" height="34" rx="4" fill="#2d8659"/><text x="221" y="174" text-anchor="middle" class="t9">PROXY INVERSO</text><text x="221" y="187" text-anchor="middle" class="s9">Termina TLS · WAF</text>
  <text x="294" y="180" class="a9">→</text>
  <rect x="312" y="160" width="96" height="34" rx="4" fill="#0055a0"/><text x="360" y="174" text-anchor="middle" class="t9">SEDE</text><text x="360" y="187" text-anchor="middle" class="s9">Granja de servidores</text>
  <rect x="424" y="154" width="222" height="46" rx="4" fill="#eef7f1" stroke="#2d8659"/><text x="535" y="168" text-anchor="middle" class="b9">Qué permite hacer · mp.s.2</text><text x="535" y="181" text-anchor="middle" class="d9">Terminar TLS · equilibrar carga · cachear</text><text x="535" y="193" text-anchor="middle" class="d9">ocultar la topología interna · integrar el WAF</text>

  <text x="20" y="230" class="k9">LA RUPTURA DEL CANAL CIFRADO: LO QUE EL ENS EXIGE ANTES DE INSPECCIONAR</text>
  <rect x="20" y="238" width="640" height="56" rx="5" fill="#fff5e6" stroke="#e89822"/>
  <text x="32" y="256" class="b9">mp.s.3.r1.2 — refuerzo R1, exigible en categoría ALTA</text>
  <text x="32" y="270" class="d9">«Se establecerá una función para la ruptura de canales cifrados a fin de inspeccionar su contenido, indicando QUÉ SE ANALIZA, QUÉ SE REGISTRA,</text>
  <text x="32" y="282" class="d9">DURANTE CUÁNTO TIEMPO se retienen y QUÉ USO prevé hacer el organismo de estas inspecciones», con excepción para destinos de confianza</text>

  <rect x="20" y="302" width="206" height="24" rx="4" fill="#0055a0"/><text x="123" y="318" text-anchor="middle" class="s9">mp.s.3.r1.1 · registrar la navegación</text>
  <rect x="236" y="302" width="206" height="24" rx="4" fill="#0055a0"/><text x="339" y="318" text-anchor="middle" class="s9">mp.s.3.r1.3 · lista negra de destinos</text>
  <rect x="452" y="302" width="208" height="24" rx="4" fill="#d13c3c"/><text x="556" y="318" text-anchor="middle" class="s9">mp.s.3.r2.1 · lista blanca: todo lo demás vetado</text>

  <text x="20" y="342" class="n9">[Fuente: ENS, RD 311/2022, mp.s.2 y mp.s.3 — texto literal del anexo II · RFC 1928 (SOCKS)]</text>
</svg>
```

---
## D10 · IDS frente a IPS: ubicación y matriz de decisión

**Sección**: §2.3 — Sistemas de prevención y detección de intrusiones
**Propósito**: Resolver de una vez la pareja que más se confunde, con las **dos ideas que la explican**: dónde se coloca cada uno y qué pasa cuando se equivoca. Incluye la matriz de los cuatro resultados posibles y la tabla de aplicación de `op.mon.1`.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Comparación entre sistema de detección de intrusiones IDS y sistema de prevención IPS: el IDS se coloca fuera de línea recibiendo una copia del tráfico por puerto espejo y solo alerta; el IPS se coloca en línea y bloquea. Matriz de los cuatro resultados posibles: verdadero positivo, falso positivo, falso negativo y verdadero negativo. Tabla de aplicación de la medida op punto mon punto uno: aplica en básica, más refuerzo uno en media y refuerzos uno y dos en alta">
  <style>.h10{font:700 13px system-ui,sans-serif;fill:#0055a0}.k10{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t10{font:700 10px system-ui,sans-serif;fill:#fff}.s10{font:8.5px system-ui,sans-serif;fill:#fff}.d10{font:8.5px system-ui,sans-serif;fill:#333}.b10{font:700 9px system-ui,sans-serif;fill:#0055a0}.n10{font:8px system-ui,sans-serif;fill:#666}.a10{font:8px system-ui,sans-serif;fill:#666}.hd10{font:700 8.5px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h10">IDS = espejo, avisa. IPS = camino, bloquea. Todo lo demás se deriva de ahí</text>

  <text x="20" y="42" class="k10">DÓNDE SE COLOCA CADA UNO</text>
  <rect x="20" y="50" width="316" height="82" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <text x="178" y="66" text-anchor="middle" class="b10">IDS · FUERA DE LÍNEA</text>
  <rect x="34" y="76" width="62" height="24" rx="3" fill="#999"/><text x="65" y="92" text-anchor="middle" class="s10">Internet</text>
  <text x="102" y="92" class="a10">→</text>
  <rect x="118" y="76" width="76" height="24" rx="3" fill="#0055a0"/><text x="156" y="92" text-anchor="middle" class="s10">Conmutador</text>
  <text x="200" y="92" class="a10">→</text>
  <rect x="216" y="76" width="106" height="24" rx="3" fill="#0055a0"/><text x="269" y="92" text-anchor="middle" class="s10">Red interna</text>
  <rect x="118" y="106" width="76" height="20" rx="3" fill="#2d8659"/><text x="156" y="120" text-anchor="middle" class="s10">IDS (copia)</text>
  <text x="204" y="120" class="d10">Recibe una COPIA del tráfico</text>

  <rect x="344" y="50" width="316" height="82" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <text x="502" y="66" text-anchor="middle" class="b10">IPS · EN LÍNEA</text>
  <rect x="358" y="76" width="62" height="24" rx="3" fill="#999"/><text x="389" y="92" text-anchor="middle" class="s10">Internet</text>
  <text x="426" y="92" class="a10">→</text>
  <rect x="442" y="76" width="76" height="24" rx="3" fill="#d13c3c"/><text x="480" y="92" text-anchor="middle" class="s10">IPS</text>
  <text x="524" y="92" class="a10">→</text>
  <rect x="540" y="76" width="106" height="24" rx="3" fill="#0055a0"/><text x="593" y="92" text-anchor="middle" class="s10">Red interna</text>
  <text x="358" y="114" class="d10">Todo el tráfico lo ATRAVIESA: si se avería y</text>
  <text x="358" y="126" class="d10">no tiene derivación, la red queda incomunicada</text>

  <text x="20" y="152" class="k10">CONSECUENCIAS DE LA UBICACIÓN</text>
  <rect x="20" y="160" width="640" height="20" rx="3" fill="#0055a0"/><text x="30" y="174" class="s10">CRITERIO</text><text x="240" y="174" class="s10">IDS</text><text x="450" y="174" class="s10">IPS</text>
  <rect x="20" y="182" width="640" height="20" fill="#f7f9fc"/><text x="30" y="196" class="d10">Qué hace ante un ataque</text><text x="240" y="196" class="d10">Detecta y ALERTA</text><text x="450" y="196" class="d10">Detecta y BLOQUEA o reinicia la conexión</text>
  <rect x="20" y="204" width="640" height="20" fill="#fff"/><text x="30" y="218" class="d10">Si el aparato se avería</text><text x="240" y="218" class="d10">No afecta al servicio</text><text x="450" y="218" class="d10">Puede cortar la red entera</text>
  <rect x="20" y="226" width="640" height="20" fill="#f7f9fc"/><text x="30" y="240" class="d10">Efecto de un falso positivo</text><text x="240" y="240" class="d10">Una alerta molesta</text><text x="450" y="240" class="d10">Corta TRÁFICO LEGÍTIMO: servicio público caído</text>
  <rect x="20" y="248" width="640" height="20" fill="#fff"/><text x="30" y="262" class="d10">Latencia que introduce</text><text x="240" y="262" class="d10">Ninguna</text><text x="450" y="262" class="d10">Sí: analiza antes de reenviar</text>

  <text x="20" y="288" class="k10">LOS CUATRO RESULTADOS POSIBLES</text>
  <rect x="20" y="296" width="316" height="48" rx="5" fill="#fff" stroke="#ccc"/>
  <rect x="118" y="296" width="120" height="18" fill="#0055a0"/><text x="178" y="309" text-anchor="middle" class="s10">HAY ATAQUE</text>
  <rect x="244" y="296" width="92" height="18" fill="#0055a0"/><text x="290" y="309" text-anchor="middle" class="s10">NO HAY ATAQUE</text>
  <text x="28" y="328" class="d10">Alerta</text><text x="124" y="328" class="d10">Verdadero positivo</text><text x="250" y="328" class="d10">FALSO POSITIVO</text>
  <text x="28" y="340" class="d10">Calla</text><text x="124" y="340" class="d10">FALSO NEGATIVO (peor)</text><text x="250" y="340" class="d10">Verdadero negativo</text>

  <rect x="344" y="296" width="316" height="48" rx="5" fill="#eef4fa" stroke="#0055a0"/>
  <text x="502" y="311" text-anchor="middle" class="b10">op.mon.1 Detección de intrusión — aplica ya en BÁSICA</text>
  <text x="502" y="325" text-anchor="middle" class="d10">MEDIA: + R1, detección BASADA EN REGLAS</text>
  <text x="502" y="337" text-anchor="middle" class="d10">ALTA: + R1 + R2, PROCEDIMIENTOS DE RESPUESTA a las alertas</text>

  <text x="20" y="362" class="n10">[Fuente: ENS, RD 311/2022, op.mon.1 y op.mon.3 — texto y tablas del anexo II verificados contra el PDF del BOE]</text>
</svg>
```

---
## D11 · DMZ: tres patas, doble cortafuegos y segmentación interna

**Sección**: §2.4.1 — Redes desmilitarizadas y subredes internas
**Propósito**: Dibujar las **dos arquitecturas de DMZ**, fijar la regla direccional que la define y enlazar con los cuatro refuerzos de `mp.com.4`, incluida la segmentación mínima obligatoria en tres subredes.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Arquitecturas de zona desmilitarizada: cortafuegos de tres patas con una sola caja de tres interfaces exterior, DMZ e interior; y doble cortafuegos con dos equipos en serie y la DMZ en medio, preferiblemente de fabricantes distintos. Se destaca la regla de que desde la DMZ no se puede iniciar ninguna conexión hacia la red interna, y los cuatro refuerzos de la medida mp punto com punto cuatro: VLAN, VPN, separación física y control de los puntos de interconexión">
  <style>.h11{font:700 13px system-ui,sans-serif;fill:#0055a0}.k11{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t11{font:700 9.5px system-ui,sans-serif;fill:#fff}.ts11{font:700 8px system-ui,sans-serif;fill:#fff}.s11{font:8px system-ui,sans-serif;fill:#fff}.d11{font:8.5px system-ui,sans-serif;fill:#333}.b11{font:700 9px system-ui,sans-serif;fill:#0055a0}.n11{font:8px system-ui,sans-serif;fill:#666}.a11{font:8px system-ui,sans-serif;fill:#666}.r11{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h11">Desde la DMZ NO se inicia hacia dentro. Desde dentro SÍ se inicia hacia la DMZ</text>

  <text x="20" y="42" class="k11">ARQUITECTURA A · CORTAFUEGOS DE TRES PATAS</text>
  <rect x="20" y="50" width="316" height="94" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <rect x="32" y="86" width="60" height="26" rx="3" fill="#999"/><text x="62" y="103" text-anchor="middle" class="s11">INTERNET</text>
  <text x="97" y="103" class="a11">→</text>
  <rect x="112" y="72" width="72" height="54" rx="4" fill="#0055a0"/><text x="148" y="94" text-anchor="middle" class="ts11">CORTAFUEGOS</text><text x="148" y="108" text-anchor="middle" class="s11">3 interfaces</text><text x="148" y="119" text-anchor="middle" class="s11">1 sola política</text>
  <rect x="200" y="62" width="122" height="28" rx="3" fill="#e89822"/><text x="261" y="80" text-anchor="middle" class="s11">DMZ · sede, correo, DNS</text>
  <rect x="200" y="100" width="122" height="28" rx="3" fill="#2d8659"/><text x="261" y="118" text-anchor="middle" class="s11">RED INTERNA</text>
  <text x="188" y="78" class="a11">→</text>
  <text x="188" y="116" class="a11">→</text>
  <text x="28" y="66" class="d11">Ventaja: sencillo y barato</text>
  <text x="28" y="139" class="d11">Riesgo: un solo dispositivo separa internet de la red interna</text>

  <text x="344" y="42" class="k11">ARQUITECTURA B · DOBLE CORTAFUEGOS (SUBRED APANTALLADA)</text>
  <rect x="344" y="50" width="316" height="94" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <rect x="354" y="86" width="52" height="26" rx="3" fill="#999"/><text x="380" y="103" text-anchor="middle" class="s11">INTERNET</text>
  <text x="410" y="103" class="a11">→</text>
  <rect x="424" y="86" width="46" height="26" rx="3" fill="#0055a0"/><text x="447" y="103" text-anchor="middle" class="s11">CF-1</text>
  <text x="474" y="103" class="a11">→</text>
  <rect x="488" y="86" width="62" height="26" rx="3" fill="#e89822"/><text x="519" y="103" text-anchor="middle" class="s11">DMZ</text>
  <text x="554" y="103" class="a11">→</text>
  <rect x="568" y="86" width="46" height="26" rx="3" fill="#0055a0"/><text x="591" y="103" text-anchor="middle" class="s11">CF-2</text>
  <rect x="620" y="86" width="30" height="26" rx="3" fill="#2d8659"/><text x="635" y="103" text-anchor="middle" class="s11">LAN</text>
  <text x="352" y="66" class="d11">Ventaja: defensa en profundidad real,</text>
  <text x="352" y="78" class="d11">sobre todo si CF-1 y CF-2 son de FABRICANTES DISTINTOS</text>
  <text x="352" y="132" class="d11">Inconveniente: mayor coste y complejidad de gestión de dos políticas</text>

  <text x="20" y="164" class="k11">LA REGLA DIRECCIONAL QUE DEFINE UNA DMZ</text>
  <rect x="20" y="172" width="640" height="42" rx="5" fill="#fdeeee" stroke="#d13c3c"/>
  <text x="32" y="190" class="r11">Si el servidor web de la DMZ puede abrir sesiones contra la base de datos interna, eso NO es una DMZ: es red interna con otro nombre</text>
  <text x="32" y="205" class="d11">Si la DMZ necesita un dato de dentro, la conexión debe ORIGINARSE en la red interna, o pasar por un elemento intermedio en la propia DMZ</text>

  <text x="20" y="234" class="k11">LOS CUATRO REFUERZOS DE mp.com.4 · MEDIA = + [R1 o R2 o R3] · ALTA = + [R2 o R3] + R4</text>
  <rect x="20" y="242" width="156" height="56" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="98" y="258" text-anchor="middle" class="b11">R1 · LÓGICA BÁSICA</text><text x="98" y="272" text-anchor="middle" class="d11">VLAN (IEEE 802.1Q)</text><text x="98" y="284" text-anchor="middle" class="d11">Mínimo tres subredes:</text><text x="98" y="294" text-anchor="middle" class="d11">usuarios, servicios, administración</text>
  <rect x="184" y="242" width="156" height="56" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="262" y="258" text-anchor="middle" class="b11">R2 · LÓGICA AVANZADA</text><text x="262" y="272" text-anchor="middle" class="d11">Los segmentos se</text><text x="262" y="284" text-anchor="middle" class="d11">implementan mediante</text><text x="262" y="294" text-anchor="middle" class="d11">redes privadas virtuales (VPN)</text>
  <rect x="348" y="242" width="156" height="56" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="426" y="258" text-anchor="middle" class="b11">R3 · FÍSICA</text><text x="426" y="272" text-anchor="middle" class="d11">Medios físicos</text><text x="426" y="284" text-anchor="middle" class="d11">separados: no existe</text><text x="426" y="294" text-anchor="middle" class="d11">camino posible entre ellos</text>
  <rect x="512" y="242" width="148" height="56" rx="5" fill="#eef4fa" stroke="#0055a0"/><text x="586" y="258" text-anchor="middle" class="b11">R4 · INTERCONEXIÓN</text><text x="586" y="272" text-anchor="middle" class="d11">Control de entrada de</text><text x="586" y="284" text-anchor="middle" class="d11">usuarios e información.</text><text x="586" y="294" text-anchor="middle" class="d11">Punto de unión monitorizado</text>

  <rect x="20" y="308" width="640" height="32" rx="5" fill="#fff5e6" stroke="#e89822"/>
  <text x="340" y="323" text-anchor="middle" class="b11">Y las dos obligaciones que no son refuerzo, sino requisito base</text>
  <text x="340" y="335" text-anchor="middle" class="d11">mp.com.4.1 — cada equipo solo accede a lo que necesita · mp.com.4.2 — si hay comunicaciones inalámbricas, será en SEGMENTO SEPARADO</text>

  <text x="20" y="360" class="n11">[Fuente: ENS, RD 311/2022, mp.com.4 — texto literal del anexo II · art. 23 (interconexión) · IEEE 802.1Q]</text>
</svg>
```

---
## D12 · Confianza cero: los siete principios y los componentes

**Sección**: §2.4.2 — Modelo de seguridad de confianza cero
**Propósito**: Fijar los **siete principios** de la NIST SP 800-207 y la separación **PDP / PEP** —quién decide frente a quién ejecuta—, con la advertencia de qué **no** es la confianza cero.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Confianza cero según la publicación NIST SP 800-207: los siete principios, desde considerar recurso a toda fuente de datos hasta recopilar información y usarla para mejorar la política; y los componentes lógicos, con el motor de políticas y el administrador de políticas formando el punto de decisión, y el punto de aplicación de políticas en el camino del tráfico. Se advierte de que la confianza cero no elimina el perímetro ni la VPN, que siguen siendo obligatorios en España">
  <style>.h12{font:700 13px system-ui,sans-serif;fill:#0055a0}.k12{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t12{font:700 9.5px system-ui,sans-serif;fill:#fff}.s12{font:8px system-ui,sans-serif;fill:#fff}.d12{font:8.5px system-ui,sans-serif;fill:#333}.b12{font:700 9px system-ui,sans-serif;fill:#0055a0}.n12{font:8px system-ui,sans-serif;fill:#666}.a12{font:8px system-ui,sans-serif;fill:#666}.num12{font:700 10px system-ui,sans-serif;fill:#fff}.r12{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h12">«Nunca confíes, verifica siempre»: estar dentro de la red ya no da ningún derecho</text>

  <text x="20" y="42" class="k12">LOS SIETE PRINCIPIOS · NIST SP 800-207 (AGOSTO DE 2020)</text>
  <circle cx="32" cy="58" r="9" fill="#0055a0"/><text x="32" y="62" text-anchor="middle" class="num12">1</text><text x="48" y="62" class="d12">Todas las fuentes de datos y servicios de computación se consideran RECURSOS</text>
  <circle cx="32" cy="82" r="9" fill="#0055a0"/><text x="32" y="86" text-anchor="middle" class="num12">2</text><text x="48" y="86" class="d12">TODA comunicación se protege, con independencia de la ubicación en la red — también la interna</text>
  <circle cx="32" cy="106" r="9" fill="#0055a0"/><text x="32" y="110" text-anchor="middle" class="num12">3</text><text x="48" y="110" class="d12">El acceso a cada recurso se concede POR SESIÓN, de una en una</text>
  <circle cx="32" cy="130" r="9" fill="#0055a0"/><text x="32" y="134" text-anchor="middle" class="num12">4</text><text x="48" y="134" class="d12">El acceso se determina por POLÍTICA DINÁMICA: identidad, aplicación, estado del dispositivo, comportamiento y entorno</text>
  <circle cx="32" cy="154" r="9" fill="#0055a0"/><text x="32" y="158" text-anchor="middle" class="num12">5</text><text x="48" y="158" class="d12">La organización MIDE Y VIGILA la integridad y el estado de seguridad de todos sus activos</text>
  <circle cx="32" cy="178" r="9" fill="#0055a0"/><text x="32" y="182" text-anchor="middle" class="num12">6</text><text x="48" y="182" class="d12">Autenticación y autorización son DINÁMICAS y estrictamente exigidas ANTES de permitir el acceso</text>
  <circle cx="32" cy="202" r="9" fill="#0055a0"/><text x="32" y="206" text-anchor="middle" class="num12">7</text><text x="48" y="206" class="d12">Se recopila toda la información posible sobre activos, infraestructura y comunicaciones, y SE USA PARA MEJORAR la política</text>

  <text x="20" y="230" class="k12">LOS COMPONENTES LÓGICOS: QUIÉN DECIDE Y QUIÉN EJECUTA</text>
  <rect x="20" y="238" width="256" height="70" rx="5" fill="#eef4fa" stroke="#0055a0"/>
  <text x="148" y="254" text-anchor="middle" class="b12">PDP · PUNTO DE DECISIÓN</text>
  <rect x="32" y="262" width="112" height="36" rx="4" fill="#0055a0"/><text x="88" y="278" text-anchor="middle" class="t12">MOTOR (PE)</text><text x="88" y="291" text-anchor="middle" class="s12">Decide SI se concede</text>
  <rect x="152" y="262" width="112" height="36" rx="4" fill="#0055a0"/><text x="208" y="278" text-anchor="middle" class="t12">ADMIN. (PA)</text><text x="208" y="291" text-anchor="middle" class="s12">Ejecuta la decisión</text>

  <text x="286" y="278" class="a12">consulta</text>
  <text x="286" y="290" class="a12">cada vez →</text>

  <rect x="352" y="238" width="150" height="70" rx="5" fill="#eef7f1" stroke="#2d8659"/>
  <text x="427" y="254" text-anchor="middle" class="b12">PEP · APLICACIÓN</text>
  <rect x="364" y="262" width="126" height="36" rx="4" fill="#2d8659"/><text x="427" y="278" text-anchor="middle" class="t12">DEJA PASAR O NO</text><text x="427" y="291" text-anchor="middle" class="s12">Pasarela, agente, proxy</text>

  <rect x="512" y="238" width="148" height="70" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <text x="586" y="254" text-anchor="middle" class="b12">SOBRE QUÉ DECIDE</text>
  <text x="522" y="270" class="d12">Identidad y MFA (§3.2)</text>
  <text x="522" y="282" class="d12">Estado del dispositivo (§5)</text>
  <text x="522" y="294" class="d12">Microsegmentación (§2.4.1)</text>

  <rect x="20" y="312" width="640" height="44" rx="5" fill="#fdeeee" stroke="#d13c3c"/>
  <text x="340" y="326" text-anchor="middle" class="r12">LO QUE LA CONFIANZA CERO NO ES</text>
  <text x="340" y="339" text-anchor="middle" class="d12">No es un producto · no elimina el cortafuegos · no deroga la VPN · no es incompatible con el ENS</text>
  <text x="340" y="350" text-anchor="middle" class="d12">En España, mp.com.1 (perímetro) y mp.com.2 (VPN cifrada) siguen siendo obligatorios</text>

  <text x="20" y="368" class="n12">[Fuente: NIST SP 800-207, Zero Trust Architecture (agosto de 2020) · ENS, RD 311/2022, mp.com.1, mp.com.2, mp.com.4 y op.acc.4]</text>
</svg>
```

---
## D13 · Acceso remoto del empleado municipal, paso a paso

**Sección**: §3.1 — Requisitos y arquitectura de acceso remoto en el ámbito público
**Propósito**: Recorrer la **secuencia completa** de una conexión de teletrabajo conforme al ENS, marcando en cada paso la medida que lo respalda. Es el diagrama que se copia como esqueleto de respuesta en un caso práctico.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Secuencia de acceso remoto del empleado municipal en seis pasos: portátil corporativo con disco cifrado; conexión del cliente VPN a la pasarela situada en la zona desmilitarizada; segundo factor de autenticación validado contra el servidor AAA y el directorio; comprobación del estado del dispositivo con desvío a cuarentena si no cumple; acceso a un segmento de teletrabajo con permisos mínimos; y registro de toda la actividad en el sistema de correlación de eventos. Cada paso cita la medida del Esquema Nacional de Seguridad que lo respalda">
  <style>.h13{font:700 13px system-ui,sans-serif;fill:#0055a0}.k13{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t13{font:700 9.5px system-ui,sans-serif;fill:#fff}.ts13{font:700 8px system-ui,sans-serif;fill:#fff}.s13{font:8px system-ui,sans-serif;fill:#fff}.d13{font:8.5px system-ui,sans-serif;fill:#333}.b13{font:700 9px system-ui,sans-serif;fill:#0055a0}.n13{font:8px system-ui,sans-serif;fill:#666}.a13{font:8px system-ui,sans-serif;fill:#666}.num13{font:700 11px system-ui,sans-serif;fill:#fff}.r13{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h13">Seis pasos, seis medidas del ENS: el teletrabajador NO entra en «la red»</text>

  <rect x="20" y="34" width="640" height="106" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <text x="30" y="50" class="k13">DOMICILIO DEL EMPLEADO</text>
  <text x="270" y="50" class="k13">DMZ DEL AYUNTAMIENTO</text>
  <text x="500" y="50" class="k13">RED CORPORATIVA</text>

  <rect x="30" y="58" width="118" height="42" rx="4" fill="#0055a0"/><text x="89" y="76" text-anchor="middle" class="ts13">PORTÁTIL CORPORATIVO</text><text x="89" y="90" text-anchor="middle" class="s13">Cifrado · EDR · parcheado</text>
  <text x="154" y="82" class="a13">→</text>
  <rect x="172" y="58" width="82" height="42" rx="4" fill="#999"/><text x="213" y="76" text-anchor="middle" class="t13">INTERNET</text><text x="213" y="90" text-anchor="middle" class="s13">Red no controlada</text>
  <text x="260" y="82" class="a13">→</text>
  <rect x="276" y="58" width="118" height="42" rx="4" fill="#e89822"/><text x="335" y="76" text-anchor="middle" class="t13">PASARELA VPN</text><text x="335" y="90" text-anchor="middle" class="s13">En la DMZ, nunca dentro</text>
  <text x="400" y="82" class="a13">→</text>
  <rect x="416" y="58" width="110" height="42" rx="4" fill="#0055a0"/><text x="471" y="76" text-anchor="middle" class="t13">AAA + DIRECTORIO</text><text x="471" y="90" text-anchor="middle" class="s13">RADIUS · MFA</text>
  <text x="532" y="82" class="a13">→</text>
  <rect x="548" y="58" width="102" height="42" rx="4" fill="#2d8659"/><text x="599" y="76" text-anchor="middle" class="t13">SEGMENTO</text><text x="599" y="90" text-anchor="middle" class="s13">de teletrabajo</text>

  <rect x="30" y="108" width="242" height="24" rx="3" fill="#fdeeee" stroke="#d13c3c"/><text x="151" y="124" text-anchor="middle" class="d13">Si no supera el estado: VLAN de CUARENTENA</text>
  <rect x="286" y="108" width="364" height="24" rx="3" fill="#eef4fa" stroke="#0055a0"/><text x="468" y="124" text-anchor="middle" class="d13">Todo lo que ocurre se registra y se envía al SIEM · op.exp.8 y op.mon.3.r1</text>

  <text x="20" y="160" class="k13">LOS SEIS PASOS Y SU RESPALDO NORMATIVO</text>
  <circle cx="32" cy="178" r="9" fill="#0055a0"/><text x="32" y="182" text-anchor="middle" class="num13">1</text><text x="48" y="176" class="d13">El equipo arranca con disco cifrado y el usuario se autentica en él</text><text x="48" y="188" class="b13">mp.eq.3.r1 (cifrado si la confidencialidad es MEDIA) · mp.eq.2 (bloqueo)</text>
  <circle cx="32" cy="206" r="9" fill="#0055a0"/><text x="32" y="210" text-anchor="middle" class="num13">2</text><text x="48" y="204" class="d13">El cliente VPN establece el túnel cifrado con la pasarela publicada en la DMZ</text><text x="48" y="216" class="b13">mp.com.2.1 (VPN cifrada fuera del dominio propio) · mp.com.3</text>
  <circle cx="32" cy="234" r="9" fill="#0055a0"/><text x="32" y="238" text-anchor="middle" class="num13">3</text><text x="48" y="232" class="d13">Se exige SEGUNDO FACTOR y se valida contra el servidor AAA y el directorio</text><text x="48" y="244" class="b13">op.acc.5 en nivel MEDIO: + [R2 o R3 o R4] + R5 — la contraseña sola ya no vale</text>
  <circle cx="32" cy="262" r="9" fill="#0055a0"/><text x="32" y="266" text-anchor="middle" class="num13">4</text><text x="48" y="260" class="d13">Se comprueba el ESTADO del dispositivo: corporativo, cifrado, parcheado, con EDR activo</text><text x="48" y="272" class="b13">op.exp.4 y op.exp.6 · principio 4 y 5 de la NIST SP 800-207</text>
  <circle cx="32" cy="290" r="9" fill="#0055a0"/><text x="32" y="294" text-anchor="middle" class="num13">5</text><text x="48" y="288" class="d13">Se concede acceso a un SEGMENTO DE TELETRABAJO con lo mínimo imprescindible</text><text x="48" y="300" class="b13">mp.eq.3.3 (mínimos imprescindibles desde redes no controladas) · mp.com.4</text>
  <circle cx="32" cy="318" r="9" fill="#0055a0"/><text x="32" y="322" text-anchor="middle" class="num13">6</text><text x="48" y="316" class="d13">Todo queda registrado, incluidos los intentos fallidos, y se revoca al cesar el empleado</text><text x="48" y="328" class="b13">op.exp.8 · op.acc.5.r5 · op.acc.5.6 · y sobre todo op.acc.4.5</text>

  <rect x="20" y="336" width="640" height="20" rx="3" fill="#e89822"/>
  <text x="340" y="350" text-anchor="middle" class="s13">Base legal: art. 47 bis del TREBEP (RDL 29/2020) — teletrabajo autorizado, voluntario y reversible, con MEDIOS a cargo de la Administración</text>

  <text x="20" y="368" class="n13">[Fuente: ENS, RD 311/2022, op.acc.4.5, op.acc.5, mp.com.2, mp.eq.3 · TREBEP art. 47 bis (RDL 29/2020)]</text>
</svg>
```

---
## D14 · Los tres factores de autenticación y qué exige el ENS

**Sección**: §3.2.1 — Autenticación multifactor y uso de certificados digitales
**Propósito**: Separar los **tres factores** —y desmontar los falsos MFA— y traducir la tabla de aplicación de `op.acc.5`, que es donde se decide si un teletrabajo cumple o no cumple.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 364" role="img" aria-label="Los tres factores de autenticación: algo que se sabe como la contraseña, algo que se tiene como la tarjeta criptográfica o el token, y algo que se es como la biometría. La autenticación multifactor exige dos factores de categorías distintas. Se incluye la tabla de aplicación de la medida op punto acc punto cinco, según la cual en nivel medio y alto desaparece la opción de contraseña sola y se hace obligatorio el registro de accesos con éxito y fallidos">
  <style>.h14{font:700 13px system-ui,sans-serif;fill:#0055a0}.k14{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t14{font:700 10px system-ui,sans-serif;fill:#fff}.s14{font:8.5px system-ui,sans-serif;fill:#fff}.d14{font:8.5px system-ui,sans-serif;fill:#333}.b14{font:700 9px system-ui,sans-serif;fill:#0055a0}.n14{font:8px system-ui,sans-serif;fill:#666}.r14{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}.g14{font:700 8.5px system-ui,sans-serif;fill:#2d8659}.hd14{font:700 8.5px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="h14">MFA = dos factores de CATEGORÍAS DISTINTAS. Contraseña + PIN no es MFA</text>

  <text x="20" y="42" class="k14">LOS TRES ÚNICOS FACTORES</text>
  <rect x="20" y="50" width="206" height="76" rx="5" fill="#0055a0"/>
  <text x="123" y="68" text-anchor="middle" class="t14">ALGO QUE SE SABE</text>
  <text x="123" y="84" text-anchor="middle" class="s14">Contraseña · PIN · pregunta</text>
  <text x="123" y="100" text-anchor="middle" class="hd14">Su debilidad</text>
  <text x="123" y="114" text-anchor="middle" class="s14">Se adivina, se reutiliza, se roba</text>
  <rect x="236" y="50" width="206" height="76" rx="5" fill="#0055a0"/>
  <text x="339" y="68" text-anchor="middle" class="t14">ALGO QUE SE TIENE</text>
  <text x="339" y="84" text-anchor="middle" class="s14">Tarjeta criptográfica · token OTP</text>
  <text x="339" y="100" text-anchor="middle" class="hd14">Su debilidad</text>
  <text x="339" y="114" text-anchor="middle" class="s14">Se pierde, se roba, puede clonarse</text>
  <rect x="452" y="50" width="208" height="76" rx="5" fill="#0055a0"/>
  <text x="556" y="68" text-anchor="middle" class="t14">ALGO QUE SE ES</text>
  <text x="556" y="84" text-anchor="middle" class="s14">Huella · iris · rostro · voz</text>
  <text x="556" y="100" text-anchor="middle" class="hd14">Su debilidad</text>
  <text x="556" y="114" text-anchor="middle" class="s14">NO se puede cambiar si se compromete</text>

  <rect x="20" y="134" width="316" height="28" rx="4" fill="#fdeeee" stroke="#d13c3c"/><text x="178" y="152" text-anchor="middle" class="r14">NO es MFA: contraseña + PIN (los dos son «algo que se sabe»)</text>
  <rect x="344" y="134" width="316" height="28" rx="4" fill="#eef7f1" stroke="#2d8659"/><text x="502" y="152" text-anchor="middle" class="g14">SÍ es MFA: contraseña + código del móvil, o certificado + PIN</text>

  <text x="20" y="182" class="k14">LOS REFUERZOS DE op.acc.5, ORDENADOS POR ROBUSTEZ</text>
  <rect x="20" y="190" width="640" height="20" rx="3" fill="#0055a0"/>
  <text x="30" y="204" class="hd14">REFUERZO</text><text x="130" y="204" class="hd14">MECANISMO</text><text x="392" y="204" class="hd14">¿VALE EN NIVEL BAJO?</text><text x="536" y="204" class="hd14">¿VALE EN MEDIO Y ALTO?</text>
  <rect x="20" y="212" width="640" height="22" fill="#fdeeee"/><text x="30" y="227" class="b14">R1</text><text x="130" y="227" class="d14">Contraseña con complejidad y robustez mínimas</text><text x="392" y="227" class="g14">SÍ</text><text x="536" y="227" class="r14">NO — ya no vale</text>
  <rect x="20" y="236" width="640" height="22" fill="#fff"/><text x="30" y="251" class="b14">R2</text><text x="130" y="251" class="d14">Contraseña de un solo uso (OTP)</text><text x="392" y="251" class="g14">SÍ</text><text x="536" y="251" class="g14">SÍ</text>
  <rect x="20" y="260" width="640" height="22" fill="#f7f9fc"/><text x="30" y="275" class="b14">R3 y R4</text><text x="130" y="275" class="d14">Certificado CUALIFICADO protegido por segundo factor</text><text x="392" y="275" class="g14">SÍ</text><text x="536" y="275" class="g14">SÍ</text>
  <rect x="20" y="284" width="640" height="22" fill="#fff"/><text x="30" y="299" class="b14">R5</text><text x="130" y="299" class="d14">Registro de accesos con ÉXITO y FALLIDOS</text><text x="392" y="299" class="d14">Opcional</text><text x="536" y="299" class="r14">OBLIGATORIO</text>

  <rect x="20" y="314" width="640" height="26" rx="4" fill="#e89822"/>
  <text x="340" y="331" text-anchor="middle" class="s14">Tabla literal · BAJO: op.acc.5 + [R1 o R2 o R3 o R4] · MEDIO: op.acc.5 + [R2 o R3 o R4] + R5 · ALTO: igual que MEDIO</text>

  <text x="20" y="358" class="n14">[Fuente: ENS, RD 311/2022, op.acc.5 y op.acc.6 — texto y tabla del anexo II · Reglamento (UE) 2024/1183 (eIDAS 2)]</text>
</svg>
```

---
## D15 · AAA y 802.1X: RADIUS, TACACS+ y el flujo de autenticación

**Sección**: §3.2.2 — Servidores de autenticación, autorización y auditoría
**Propósito**: Comparar los tres protocolos AAA por sus tres diferencias y dibujar el flujo **802.1X** con sus tres actores, incluida la asignación dinámica de VLAN.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Comparación de los protocolos AAA: RADIUS sobre UDP puertos 1812 y 1813 que cifra solo la contraseña y junta autenticación y autorización; TACACS+ sobre TCP puerto 49 que cifra todo el cuerpo y separa las tres funciones; y Diameter sobre TCP o SCTP con TLS. Se añaden las novedades del RFC 9887 de diciembre de 2025 que lleva TACACS+ sobre TLS 1.3 y del RFC 9765 de abril de 2025 con RADIUS 1.1. Y el flujo de 802.1X con suplicante, autenticador y servidor de autenticación, incluida la asignación dinámica de VLAN">
  <style>.h15{font:700 13px system-ui,sans-serif;fill:#0055a0}.k15{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t15{font:700 9.5px system-ui,sans-serif;fill:#fff}.s15{font:8px system-ui,sans-serif;fill:#fff}.d15{font:8.5px system-ui,sans-serif;fill:#333}.b15{font:700 9px system-ui,sans-serif;fill:#0055a0}.n15{font:8px system-ui,sans-serif;fill:#666}.a15{font:8px system-ui,sans-serif;fill:#666}.hd15{font:700 8.5px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="h15">RADIUS para el acceso de usuarios a la red · TACACS+ para administrar los equipos</text>

  <rect x="20" y="32" width="640" height="20" rx="3" fill="#0055a0"/>
  <text x="30" y="46" class="hd15">CRITERIO</text><text x="200" y="46" class="hd15">RADIUS</text><text x="368" y="46" class="hd15">TACACS+</text><text x="536" y="46" class="hd15">DIAMETER</text>
  <rect x="20" y="54" width="640" height="20" fill="#f7f9fc"/><text x="30" y="68" class="d15">Norma</text><text x="200" y="68" class="d15">RFC 2865 y 2866</text><text x="368" y="68" class="d15">RFC 8907 (informativo)</text><text x="536" y="68" class="d15">RFC 6733</text>
  <rect x="20" y="76" width="640" height="20" fill="#fff"/><text x="30" y="90" class="d15">Transporte y puertos</text><text x="200" y="90" class="d15">UDP 1812 y 1813</text><text x="368" y="90" class="d15">TCP 49</text><text x="536" y="90" class="d15">TCP o SCTP con TLS/DTLS</text>
  <rect x="20" y="98" width="640" height="20" fill="#f7f9fc"/><text x="30" y="112" class="d15">Qué cifra</text><text x="200" y="112" class="d15">SOLO la contraseña</text><text x="368" y="112" class="d15">TODO el cuerpo del mensaje</text><text x="536" y="112" class="d15">Todo, con TLS</text>
  <rect x="20" y="120" width="640" height="20" fill="#fff"/><text x="30" y="134" class="d15">¿Separa las tres A?</text><text x="200" y="134" class="d15">NO: van juntas</text><text x="368" y="134" class="d15">SÍ: las tres independientes</text><text x="536" y="134" class="d15">Sí</text>
  <rect x="20" y="142" width="640" height="20" fill="#f7f9fc"/><text x="30" y="156" class="d15">Uso típico</text><text x="200" y="156" class="d15">802.1X, Wi-Fi corporativa, VPN</text><text x="368" y="156" class="d15">Administración de equipos de red</text><text x="536" y="156" class="d15">Redes de operador, 4G y 5G</text>

  <rect x="20" y="170" width="640" height="30" rx="4" fill="#fff5e6" stroke="#e89822"/>
  <text x="340" y="185" text-anchor="middle" class="b15">Dos novedades verificadas contra el índice del RFC Editor que casi ningún temario recoge</text>
  <text x="340" y="196" text-anchor="middle" class="d15">RFC 9887 (diciembre de 2025): TACACS+ sobre TLS 1.3 · RFC 9765 (abril de 2025): RADIUS/1.1 elimina MD5 usando ALPN — estado Experimental</text>

  <text x="20" y="220" class="k15">802.1X · CONTROL DE ACCESO A LA RED BASADO EN PUERTO: TRES ACTORES</text>
  <rect x="20" y="228" width="640" height="76" rx="5" fill="#f7f9fc" stroke="#ccc"/>
  <rect x="34" y="248" width="140" height="42" rx="4" fill="#0055a0"/><text x="104" y="266" text-anchor="middle" class="t15">1 · SUPLICANTE</text><text x="104" y="280" text-anchor="middle" class="s15">El equipo que se conecta</text>
  <text x="182" y="266" class="a15">EAPOL</text><text x="182" y="278" class="a15">→</text>
  <rect x="224" y="248" width="140" height="42" rx="4" fill="#e89822"/><text x="294" y="266" text-anchor="middle" class="t15">2 · AUTENTICADOR</text><text x="294" y="280" text-anchor="middle" class="s15">Conmutador o punto de acceso</text>
  <text x="372" y="266" class="a15">RADIUS</text><text x="372" y="278" class="a15">→</text>
  <rect x="418" y="248" width="140" height="42" rx="4" fill="#2d8659"/><text x="488" y="266" text-anchor="middle" class="t15">3 · SERVIDOR AAA</text><text x="488" y="280" text-anchor="middle" class="s15">RADIUS: es quien DECIDE</text>
  <rect x="568" y="248" width="80" height="42" rx="4" fill="#0055a0"/><text x="608" y="266" text-anchor="middle" class="t15">DIRECTORIO</text><text x="608" y="280" text-anchor="middle" class="s15">Identidades</text>
  <text x="34" y="242" class="d15">Hasta que la autenticación tiene éxito, el puerto está NO AUTORIZADO y solo deja pasar EAPOL: ni siquiera se obtiene dirección IP</text>

  <text x="20" y="324" class="k15">MÉTODOS EAP Y LA FUNCIÓN MÁS ÚTIL</text>
  <rect x="20" y="332" width="316" height="22" rx="3" fill="#eef4fa" stroke="#0055a0"/><text x="178" y="347" text-anchor="middle" class="d15">EAP-TLS (RFC 5216, y 9190 para TLS 1.3): certificado en AMBOS extremos</text>
  <rect x="344" y="332" width="316" height="22" rx="3" fill="#eef7f1" stroke="#2d8659"/><text x="502" y="347" text-anchor="middle" class="d15">El RADIUS puede devolver el ID de VLAN: asignación DINÁMICA de VLAN</text>

  <text x="20" y="368" class="n15">[Fuente: RFC 2865, 2866, 6733, 8907, 9765, 9887, 3748, 5216 y 9190 — verificados contra el índice del RFC Editor · IEEE 802.1X]</text>
</svg>
```

---
## D16 · Taxonomía de VPN: tipo, nivel y protocolo

**Sección**: §4.1 — Conceptos generales y clasificaciones de VPN
**Propósito**: Cruzar las **dos clasificaciones** —por topología y por nivel del modelo— y dejar en una sola imagen qué protocolo **cifra** y cuál no, que es el error más repetido de la sección.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 364" role="img" aria-label="Taxonomía de redes privadas virtuales: por topología, de sitio a sitio que une dos redes entre pasarelas, y de acceso remoto que une un dispositivo con una red; por nivel del modelo, protocolos de nivel dos como PPTP y L2TP, de nivel tres como IPsec y GRE, y de niveles superiores como las VPN basadas en TLS. Se marca cuáles cifran y cuáles no: L2TP, GRE y MPLS no cifran, PPTP está roto, y ESP y TLS sí cifran">
  <style>.h16{font:700 13px system-ui,sans-serif;fill:#0055a0}.k16{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t16{font:700 9.5px system-ui,sans-serif;fill:#fff}.s16{font:8px system-ui,sans-serif;fill:#fff}.d16{font:8.5px system-ui,sans-serif;fill:#333}.b16{font:700 9px system-ui,sans-serif;fill:#0055a0}.n16{font:8px system-ui,sans-serif;fill:#666}.a16{font:8px system-ui,sans-serif;fill:#666}.hd16{font:700 8.5px system-ui,sans-serif;fill:#fff}.r16{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}.g16{font:700 8.5px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="20" text-anchor="middle" class="h16">Túnel + cifrado = VPN. Sin cifrado solo hay túnel</text>

  <text x="20" y="42" class="k16">CLASIFICACIÓN 1 · POR TOPOLOGÍA Y PROPÓSITO</text>
  <rect x="20" y="50" width="316" height="86" rx="5" fill="#eef4fa" stroke="#0055a0"/>
  <text x="178" y="66" text-anchor="middle" class="b16">SITIO A SITIO — une DOS REDES</text>
  <rect x="34" y="76" width="76" height="30" rx="3" fill="#0055a0"/><text x="72" y="95" text-anchor="middle" class="s16">Red CPD</text>
  <rect x="118" y="76" width="42" height="30" rx="3" fill="#e89822"/><text x="139" y="95" text-anchor="middle" class="s16">GW</text>
  <rect x="168" y="76" width="42" height="30" rx="3" fill="#999"/><text x="189" y="95" text-anchor="middle" class="s16">WAN</text>
  <rect x="218" y="76" width="42" height="30" rx="3" fill="#e89822"/><text x="239" y="95" text-anchor="middle" class="s16">GW</text>
  <rect x="268" y="76" width="54" height="30" rx="3" fill="#0055a0"/><text x="295" y="95" text-anchor="middle" class="s16">Distrito</text>
  <text x="34" y="122" class="d16">Permanente · autentican las PASARELAS · el usuario no instala nada</text>
  <text x="34" y="132" class="d16">Tecnología: IPsec en MODO TÚNEL con ESP</text>

  <rect x="344" y="50" width="316" height="86" rx="5" fill="#eef7f1" stroke="#2d8659"/>
  <text x="502" y="66" text-anchor="middle" class="b16">ACCESO REMOTO — une UN DISPOSITIVO</text>
  <rect x="358" y="76" width="76" height="30" rx="3" fill="#2d8659"/><text x="396" y="95" text-anchor="middle" class="s16">Portátil</text>
  <rect x="442" y="76" width="42" height="30" rx="3" fill="#999"/><text x="463" y="95" text-anchor="middle" class="s16">Internet</text>
  <rect x="492" y="76" width="54" height="30" rx="3" fill="#e89822"/><text x="519" y="95" text-anchor="middle" class="s16">Pasarela</text>
  <rect x="554" y="76" width="92" height="30" rx="3" fill="#2d8659"/><text x="600" y="95" text-anchor="middle" class="s16">Segmento teletrabajo</text>
  <text x="358" y="122" class="d16">Por sesión · autentica el USUARIO · requiere cliente o navegador</text>
  <text x="358" y="132" class="d16">Tecnología: SSL/TLS VPN o IPsec con IKEv2</text>

  <text x="20" y="158" class="k16">CLASIFICACIÓN 2 · POR NIVEL DEL MODELO, Y QUIÉN CIFRA DE VERDAD</text>
  <rect x="20" y="166" width="640" height="20" rx="3" fill="#0055a0"/>
  <text x="30" y="180" class="hd16">NIVEL</text><text x="110" y="180" class="hd16">PROTOCOLO</text><text x="242" y="180" class="hd16">RFC</text><text x="330" y="180" class="hd16">PUERTO O Nº</text><text x="440" y="180" class="hd16">¿CIFRA?</text><text x="524" y="180" class="hd16">SITUACIÓN EN 2026</text>

  <rect x="20" y="188" width="640" height="20" fill="#fdeeee"/><text x="30" y="202" class="d16">2 · Enlace</text><text x="110" y="202" class="d16">PPTP</text><text x="242" y="202" class="d16">2637</text><text x="330" y="202" class="d16">TCP 1723 + GRE</text><text x="440" y="202" class="r16">Sí, pero ROTO</text><text x="524" y="202" class="r16">PROHIBIDO</text>
  <rect x="20" y="210" width="640" height="20" fill="#fff"/><text x="30" y="224" class="d16">2 · Enlace</text><text x="110" y="224" class="d16">L2TP y L2TPv3</text><text x="242" y="224" class="d16">2661 · 3931</text><text x="330" y="224" class="d16">UDP 1701</text><text x="440" y="224" class="r16">NO</text><text x="524" y="224" class="d16">Válido SOLO como L2TP/IPsec</text>
  <rect x="20" y="232" width="640" height="20" fill="#f7f9fc"/><text x="30" y="246" class="d16">3 · Red</text><text x="110" y="246" class="d16">GRE</text><text x="242" y="246" class="d16">2784</text><text x="330" y="246" class="d16">Protocolo IP 47</text><text x="440" y="246" class="r16">NO</text><text x="524" y="246" class="d16">Vigente, siempre bajo IPsec</text>
  <rect x="20" y="254" width="640" height="20" fill="#fff"/><text x="30" y="268" class="d16">3 · Red</text><text x="110" y="268" class="d16">IPsec — AH</text><text x="242" y="268" class="d16">4302</text><text x="330" y="268" class="d16">Protocolo IP 51</text><text x="440" y="268" class="r16">NO — integridad</text><text x="524" y="268" class="d16">En desuso; falla con NAT</text>
  <rect x="20" y="276" width="640" height="20" fill="#eef7f1"/><text x="30" y="290" class="d16">3 · Red</text><text x="110" y="290" class="d16">IPsec — ESP</text><text x="242" y="290" class="d16">4303</text><text x="330" y="290" class="d16">Protocolo IP 50</text><text x="440" y="290" class="g16">SÍ</text><text x="524" y="290" class="g16">EL ESTÁNDAR</text>
  <rect x="20" y="298" width="640" height="20" fill="#fff"/><text x="30" y="312" class="d16">— · Claves</text><text x="110" y="312" class="d16">IKEv2</text><text x="242" y="312" class="d16">7296 (STD 79)</text><text x="330" y="312" class="d16">UDP 500 y 4500</text><text x="440" y="312" class="d16">Negocia las claves</text><text x="524" y="312" class="d16">Vigente; IKEv1 obsoleto</text>
  <rect x="20" y="320" width="640" height="20" fill="#eef7f1"/><text x="30" y="334" class="d16">4-7</text><text x="110" y="334" class="d16">SSL/TLS VPN</text><text x="242" y="334" class="d16">9846</text><text x="330" y="334" class="d16">TCP 443</text><text x="440" y="334" class="g16">SÍ</text><text x="524" y="334" class="g16">Vigente: TLS 1.2 y 1.3</text>

  <text x="20" y="356" class="n16">[Fuente: RFC 2637, 2661, 2784, 3931, 4302, 4303, 7296, 9395 y 9846 — verificados contra el índice oficial del RFC Editor · CCN-STIC-836]</text>
</svg>
```

---
## D17 · IPsec: AH y ESP, modo transporte y modo túnel

**Sección**: §4.2.1 — Arquitectura y protocolos IPSec
**Propósito**: El diagrama más denso del tema. Muestra **la estructura del paquete** en los dos modos, la diferencia entre AH y ESP, las dos fases de IKEv2 y el problema de NAT, que son los cuatro puntos clave.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Estructura del paquete IPsec en modo transporte y en modo túnel: en modo transporte se conserva la cabecera IP original y se cifra solo la carga útil; en modo túnel se cifra el paquete IP completo y se añade una cabecera IP nueva de las pasarelas. Se comparan AH, que da integridad y autenticación pero no cifra y usa el protocolo IP 51, y ESP, que cifra y autentica con el protocolo IP 50. Se describen las dos fases de IKEv2 y el problema de la traducción de direcciones, resuelto encapsulando ESP en UDP 4500">
  <style>.h17{font:700 13px system-ui,sans-serif;fill:#0055a0}.k17{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t17{font:700 9px system-ui,sans-serif;fill:#fff}.s17{font:7.5px system-ui,sans-serif;fill:#fff}.d17{font:8.5px system-ui,sans-serif;fill:#333}.b17{font:700 9px system-ui,sans-serif;fill:#0055a0}.n17{font:8px system-ui,sans-serif;fill:#666}.a17{font:8px system-ui,sans-serif;fill:#666}.r17{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}.g17{font:700 8.5px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="20" text-anchor="middle" class="h17">AH no cifra (protocolo 51). ESP sí cifra (protocolo 50). Y el modo decide qué se tapa</text>

  <text x="20" y="40" class="k17">PAQUETE ORIGINAL, SIN PROTEGER</text>
  <rect x="20" y="46" width="120" height="24" rx="3" fill="#999"/><text x="80" y="62" text-anchor="middle" class="t17">Cabecera IP</text>
  <rect x="142" y="46" width="200" height="24" rx="3" fill="#bbb"/><text x="242" y="62" text-anchor="middle" class="t17">Cabecera TCP/UDP + Datos</text>
  <text x="356" y="62" class="d17">Todo visible y alterable por cualquiera que esté en el camino</text>

  <text x="20" y="88" class="k17">MODO TRANSPORTE · SE CONSERVA LA CABECERA IP ORIGINAL · EXTREMO A EXTREMO</text>
  <rect x="20" y="94" width="120" height="24" rx="3" fill="#999"/><text x="80" y="110" text-anchor="middle" class="t17">Cabecera IP original</text>
  <rect x="142" y="94" width="76" height="24" rx="3" fill="#0055a0"/><text x="180" y="110" text-anchor="middle" class="t17">ESP</text>
  <rect x="220" y="94" width="200" height="24" rx="3" fill="#2d8659"/><text x="320" y="110" text-anchor="middle" class="t17">TCP/UDP + Datos — CIFRADO</text>
  <rect x="422" y="94" width="60" height="24" rx="3" fill="#0055a0"/><text x="452" y="110" text-anchor="middle" class="t17">ESP auth</text>
  <text x="496" y="106" class="d17">Se protege el CONTENIDO,</text><text x="496" y="117" class="d17">no las partes: las IP son visibles</text>

  <text x="20" y="136" class="k17">MODO TÚNEL · SE CIFRA EL PAQUETE ENTERO Y SE AÑADE CABECERA IP NUEVA · ENTRE PASARELAS</text>
  <rect x="20" y="142" width="112" height="24" rx="3" fill="#e89822"/><text x="76" y="158" text-anchor="middle" class="t17">Cabecera IP NUEVA</text>
  <rect x="134" y="142" width="60" height="24" rx="3" fill="#0055a0"/><text x="164" y="158" text-anchor="middle" class="t17">ESP</text>
  <rect x="196" y="142" width="226" height="24" rx="3" fill="#2d8659"/><text x="309" y="158" text-anchor="middle" class="t17">IP original + TCP/UDP + Datos — CIFRADO</text>
  <rect x="424" y="142" width="58" height="24" rx="3" fill="#0055a0"/><text x="453" y="158" text-anchor="middle" class="t17">ESP auth</text>
  <text x="496" y="154" class="d17">En internet SOLO se ven las IP</text><text x="496" y="165" class="d17">de las dos PASARELAS</text>

  <text x="20" y="186" class="k17">AH FRENTE A ESP</text>
  <rect x="20" y="192" width="316" height="52" rx="5" fill="#fdeeee" stroke="#d13c3c"/>
  <text x="178" y="208" text-anchor="middle" class="r17">AH · RFC 4302 · protocolo IP 51</text>
  <text x="30" y="222" class="d17">Integridad y autenticación del origen, con parte de la cabecera IP</text>
  <text x="30" y="236" class="d17">NO CIFRA. Y por proteger la cabecera IP, es INCOMPATIBLE CON NAT</text>
  <rect x="344" y="192" width="316" height="52" rx="5" fill="#eef7f1" stroke="#2d8659"/>
  <text x="502" y="208" text-anchor="middle" class="g17">ESP · RFC 4303 · protocolo IP 50</text>
  <text x="354" y="222" class="d17">CIFRA la carga útil y además da integridad y autenticación</text>
  <text x="354" y="236" class="d17">Hace casi todo lo de AH: se usa ESP y AH está en desuso</text>

  <text x="20" y="264" class="k17">IKEv2 · RFC 7296 (STD 79) · CÓMO SE ESTABLECE EL TÚNEL</text>
  <rect x="20" y="270" width="200" height="42" rx="4" fill="#0055a0"/><text x="120" y="286" text-anchor="middle" class="t17">1 · IKE_SA_INIT</text><text x="120" y="299" text-anchor="middle" class="s17">Negocia algoritmos y ejecuta Diffie-Hellman.</text><text x="120" y="309" text-anchor="middle" class="s17">Crea la IKE SA (canal de control)</text>
  <text x="226" y="292" class="a17">→</text>
  <rect x="240" y="270" width="200" height="42" rx="4" fill="#0055a0"/><text x="340" y="286" text-anchor="middle" class="t17">2 · IKE_AUTH</text><text x="340" y="299" text-anchor="middle" class="s17">Autentica por certificado, clave precompartida</text><text x="340" y="309" text-anchor="middle" class="s17">o EAP. Crea la primera Child SA (los datos)</text>
  <rect x="452" y="270" width="208" height="42" rx="4" fill="#eef4fa" stroke="#0055a0"/><text x="556" y="286" text-anchor="middle" class="b17">Una SA es UNIDIRECCIONAL</text><text x="556" y="299" text-anchor="middle" class="d17">Hacen falta DOS por conexión. Se identifica</text><text x="556" y="309" text-anchor="middle" class="d17">por SPI + IP de destino + protocolo</text>

  <rect x="20" y="320" width="640" height="30" rx="5" fill="#fff5e6" stroke="#e89822"/>
  <text x="340" y="335" text-anchor="middle" class="b17">IPsec y NAT: la respuesta completa a «qué puertos abro»</text>
  <text x="340" y="346" text-anchor="middle" class="d17">UDP 500 (IKE) · UDP 4500 (ESP con NAT-T, RFC 3948) · protocolo IP 50 (ESP) y 51 (AH). Con solo el 500, el túnel se levanta pero NO pasa tráfico</text>

  <text x="20" y="366" class="n17">[Fuente: RFC 4301, 4302, 4303, 7296, 3948, 8221, 8247 y 9395 — verificados contra el índice del RFC Editor · CCN-STIC-807 y 836]</text>
</svg>
```

---
## D18 · IPsec frente a SSL/TLS: tabla de decisión

**Sección**: §4.2.2 — VPN basadas en SSL y TLS
**Propósito**: Dar la **tabla de decisión** que resuelve el caso práctico típico —qué tecnología para qué necesidad— y fijar la razón real del éxito de las VPN SSL/TLS: el puerto 443.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 356" role="img" aria-label="Tabla de decisión entre VPN IPsec y VPN basada en SSL o TLS, comparando capa, alcance, necesidad de cliente, paso por cortafuegos ajenos, traducción de direcciones, rendimiento y granularidad de la autorización; con la conclusión de que IPsec es idóneo para uniones de sitio a sitio y las VPN TLS para el acceso remoto de usuarios. Se explican las dos modalidades sin cliente y con cliente, y el fenómeno de degradación al encapsular TCP dentro de TCP">
  <style>.h18{font:700 13px system-ui,sans-serif;fill:#0055a0}.k18{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d18{font:8.5px system-ui,sans-serif;fill:#333}.b18{font:700 9px system-ui,sans-serif;fill:#0055a0}.n18{font:8px system-ui,sans-serif;fill:#666}.hd18{font:700 8.5px system-ui,sans-serif;fill:#fff}.s18{font:8.5px system-ui,sans-serif;fill:#fff}.g18{font:700 8.5px system-ui,sans-serif;fill:#2d8659}.r18{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h18">No se elige «la mejor»: se elige la que encaja con el escenario</text>

  <rect x="20" y="32" width="640" height="20" rx="3" fill="#0055a0"/>
  <text x="30" y="46" class="hd18">CRITERIO</text><text x="250" y="46" class="hd18">IPsec</text><text x="470" y="46" class="hd18">SSL/TLS VPN</text>
  <rect x="20" y="54" width="640" height="20" fill="#f7f9fc"/><text x="30" y="68" class="d18">Capa en la que opera</text><text x="250" y="68" class="d18">Red (3)</text><text x="470" y="68" class="d18">Transporte-aplicación (4-7)</text>
  <rect x="20" y="76" width="640" height="20" fill="#fff"/><text x="30" y="90" class="d18">Alcance</text><text x="250" y="90" class="g18">TODO el tráfico IP, transparente</text><text x="470" y="90" class="d18">Solo lo que se encamine al túnel</text>
  <rect x="20" y="98" width="640" height="20" fill="#f7f9fc"/><text x="30" y="112" class="d18">Software en el extremo</text><text x="250" y="112" class="d18">Cliente necesario y configurado</text><text x="470" y="112" class="g18">Navegador o cliente ligero</text>
  <rect x="20" y="120" width="640" height="20" fill="#fff"/><text x="30" y="134" class="d18">Paso por cortafuegos ajenos</text><text x="250" y="134" class="r18">Problemático: protocolos 50/51, UDP 500/4500</text><text x="470" y="134" class="g18">Excelente: TCP 443, como HTTPS</text>
  <rect x="20" y="142" width="640" height="20" fill="#f7f9fc"/><text x="30" y="156" class="d18">Traducción de direcciones (NAT)</text><text x="250" y="156" class="d18">Requiere NAT-T (RFC 3948)</text><text x="470" y="156" class="g18">Nativo, sin configuración</text>
  <rect x="20" y="164" width="640" height="20" fill="#fff"/><text x="30" y="178" class="d18">Rendimiento bruto</text><text x="250" y="178" class="g18">Mejor, con aceleración por hardware</text><text x="470" y="178" class="r18">Peor: TCP dentro de TCP degrada</text>
  <rect x="20" y="186" width="640" height="20" fill="#f7f9fc"/><text x="30" y="200" class="d18">Granularidad de la autorización</text><text x="250" y="200" class="d18">Por subredes y servicios</text><text x="470" y="200" class="g18">Por aplicación y usuario</text>
  <rect x="20" y="208" width="640" height="20" fill="#e89822"/><text x="30" y="222" class="s18">ESCENARIO IDEAL</text><text x="250" y="222" class="s18">SITIO A SITIO y enlaces permanentes</text><text x="470" y="222" class="s18">ACCESO REMOTO de usuarios</text>

  <text x="20" y="248" class="k18">LAS DOS MODALIDADES DE VPN SSL/TLS</text>
  <rect x="20" y="256" width="316" height="52" rx="5" fill="#eef4fa" stroke="#0055a0"/>
  <text x="178" y="272" text-anchor="middle" class="b18">SIN CLIENTE (clientless)</text>
  <text x="30" y="286" class="d18">Solo navegador. Portal con aplicaciones web publicadas</text>
  <text x="30" y="299" class="d18">Nivel efectivo: aplicación. Control del puesto: mínimo. Para terceros</text>
  <rect x="344" y="256" width="316" height="52" rx="5" fill="#eef7f1" stroke="#2d8659"/>
  <text x="502" y="272" text-anchor="middle" class="b18">CON CLIENTE (túnel completo)</text>
  <text x="354" y="286" class="d18">Adaptador virtual: encamina CUALQUIER tráfico IP</text>
  <text x="354" y="299" class="d18">Nivel efectivo: red. Permite comprobar el estado del dispositivo</text>

  <rect x="20" y="316" width="640" height="24" rx="4" fill="#fdeeee" stroke="#d13c3c"/>
  <text x="340" y="332" text-anchor="middle" class="d18">Mismos límites de versión que HTTPS: prohibidos SSL 3.0 (RFC 7568) y TLS 1.0 y 1.1 (RFC 8996). Admisibles TLS 1.2 y TLS 1.3 (RFC 9846)</text>

  <text x="20" y="350" class="n18">[Fuente: RFC 9846, 8996, 7568, 3948 y 7296 — verificados contra el índice del RFC Editor · ENS, mp.com.2 · CCN-STIC-836]</text>
</svg>
```

---
## D19 · El puesto blindado: de antivirus a EDR y capas de defensa

**Sección**: §5.1 y §5.2 — Protección del puesto y del punto final
**Propósito**: Cerrar el tema con la **escalera antivirus → EPP → EDR → XDR** y con las capas de defensa del puesto, cada una con su medida del ENS. Incluye los dos datos que más se fallan: qué exige el ENS en categoría ALTA y qué **no** protege el cifrado de disco.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Evolución de la protección del punto final en cuatro escalones: antivirus por firmas, plataforma de protección EPP, detección y respuesta EDR que el Esquema Nacional de Seguridad exige literalmente en categoría alta, y detección extendida XDR. Debajo, las capas de defensa del puesto municipal, desde el arranque seguro y el cifrado de disco hasta el cortafuegos personal, la gestión centralizada y la concienciación, cada una con su medida. Se advierte de que el cifrado de disco protege solo el equipo apagado y no frente al malware">
  <style>.h19{font:700 13px system-ui,sans-serif;fill:#0055a0}.k19{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.t19{font:700 9.5px system-ui,sans-serif;fill:#fff}.s19{font:8px system-ui,sans-serif;fill:#fff}.d19{font:8.5px system-ui,sans-serif;fill:#333}.b19{font:700 9px system-ui,sans-serif;fill:#0055a0}.n19{font:8px system-ui,sans-serif;fill:#666}.a19{font:8px system-ui,sans-serif;fill:#666}.r19{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h19">El ENS nombra el EDR por su sigla, en op.exp.6.r4, y lo exige en categoría ALTA</text>

  <text x="20" y="42" class="k19">LA ESCALERA DE LA PROTECCIÓN DEL PUNTO FINAL: QUÉ AÑADE CADA ESCALÓN</text>
  <rect x="20" y="50" width="156" height="70" rx="5" fill="#8fa8bf"/><text x="98" y="68" text-anchor="middle" class="t19">ANTIVIRUS</text><text x="98" y="84" text-anchor="middle" class="s19">Firmas y heurística</text><text x="98" y="96" text-anchor="middle" class="s19">sobre FICHEROS</text><text x="98" y="112" text-anchor="middle" class="s19">Ciego ante lo desconocido</text>
  <rect x="184" y="50" width="156" height="70" rx="5" fill="#4d7ba6"/><text x="262" y="68" text-anchor="middle" class="t19">EPP</text><text x="262" y="84" text-anchor="middle" class="s19">Plataforma: antivirus +</text><text x="262" y="96" text-anchor="middle" class="s19">cortafuegos + cifrado + control</text><text x="262" y="112" text-anchor="middle" class="s19">Sigue centrado en PREVENIR</text>
  <rect x="348" y="50" width="156" height="70" rx="5" fill="#2d8659"/><text x="426" y="68" text-anchor="middle" class="t19">EDR</text><text x="426" y="84" text-anchor="middle" class="s19">Telemetría de COMPORTAMIENTO,</text><text x="426" y="96" text-anchor="middle" class="s19">investigación y AISLAMIENTO remoto</text><text x="426" y="112" text-anchor="middle" class="s19">op.exp.6.r4 — exigible en ALTA</text>
  <rect x="512" y="50" width="148" height="70" rx="5" fill="#0055a0"/><text x="586" y="68" text-anchor="middle" class="t19">XDR</text><text x="586" y="84" text-anchor="middle" class="s19">Correlación extendida: puesto,</text><text x="586" y="96" text-anchor="middle" class="s19">red, correo, identidad y nube</text><text x="586" y="112" text-anchor="middle" class="s19">MDR: lo mismo, por un tercero</text>

  <text x="20" y="142" class="k19">LAS CAPAS DEL PUESTO MUNICIPAL, DE ABAJO ARRIBA, Y SU MEDIDA</text>
  <rect x="20" y="150" width="640" height="22" rx="3" fill="#0055a0"/><text x="30" y="165" class="s19">6 · LA PERSONA — concienciación y formación, incluida la ingeniería social</text><text x="470" y="165" class="s19">mp.per.3 y mp.per.4 — en las TRES categorías</text>
  <rect x="20" y="174" width="640" height="22" rx="3" fill="#1a66ab"/><text x="30" y="189" class="s19">5 · GESTIÓN CENTRALIZADA — línea base por GPO o MDM, parcheado por anillos, inventario</text><text x="470" y="189" class="s19">op.exp.2, op.exp.3, op.exp.4 y op.exp.1</text>
  <rect x="20" y="198" width="640" height="22" rx="3" fill="#2d7ab8"/><text x="30" y="213" class="s19">4 · DETECCIÓN Y RESPUESTA — antimalware en tiempo real, escaneo periódico, lista blanca, EDR</text><text x="470" y="213" class="s19">op.exp.6 y sus refuerzos R1 a R4</text>
  <rect x="20" y="222" width="640" height="22" rx="3" fill="#4d8ec5"/><text x="30" y="237" class="s19">3 · AISLAMIENTO LOCAL — cortafuegos personal con perfiles «en la oficina» y «fuera»</text><text x="470" y="237" class="s19">Frena el MOVIMIENTO LATERAL · art. 9</text>
  <rect x="20" y="246" width="640" height="22" rx="3" fill="#6ea2d2"/><text x="30" y="261" class="s19">2 · DATOS EN REPOSO — cifrado de disco completo anclado al TPM, bloqueo por inactividad</text><text x="470" y="261" class="s19">mp.eq.3.r1, mp.eq.2 y mp.si.2</text>
  <rect x="20" y="270" width="640" height="22" rx="3" fill="#8fb6de"/><text x="30" y="285" class="s19">1 · ARRANQUE Y HARDWARE — UEFI con arranque seguro, contraseña de firmware, control de USB</text><text x="470" y="285" class="s19">op.exp.2 (mínima funcionalidad) y art. 22</text>

  <rect x="20" y="300" width="316" height="42" rx="5" fill="#fdeeee" stroke="#d13c3c"/>
  <text x="178" y="316" text-anchor="middle" class="r19">EL ERROR QUE MÁS SE PENALIZA</text>
  <text x="30" y="330" class="d19">El cifrado de disco protege SOLO el equipo APAGADO. Con la sesión</text>
  <text x="30" y="340" class="d19">abierta el disco está descifrado, también para el ransomware</text>

  <rect x="344" y="300" width="316" height="42" rx="5" fill="#eef7f1" stroke="#2d8659"/>
  <text x="502" y="316" text-anchor="middle" class="b19">op.exp.6 · LA TABLA QUE HAY QUE SABER</text>
  <text x="354" y="330" class="d19">BÁSICA: la medida · MEDIA: + R1 + R2 (escaneo periódico y al arranque)</text>
  <text x="354" y="340" class="d19">ALTA: + R1 + R2 + R3 (LISTA BLANCA) + R4 (EDR)</text>

  <text x="20" y="362" class="n19">[Fuente: ENS, RD 311/2022, op.exp.6, op.exp.2, op.exp.4, mp.eq.1 a mp.eq.4 y mp.per.3 y 4 — verificado contra el PDF del BOE]</text>
</svg>
```
