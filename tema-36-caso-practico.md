# Tema 36 — Casos Prácticos

> **Título oficial**: Seguridad y protección en redes de comunicaciones. Seguridad perimetral. Acceso remoto seguro a redes. Redes privadas virtuales (VPN). Seguridad en el puesto del usuario.
>
> **Formato**: 3 casos prácticos sobre supuestos reales del Ayuntamiento de Madrid. Cada caso suma **10 puntos**.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

Los tres casos giran sobre el supuesto de referencia del tema (ver tema-36-contenido.md, «Convenciones»): la **red corporativa municipal** gestionada por el IAM, con su CPD, una oficina de atención a la ciudadanía de distrito y los portátiles de los empleados que teletrabajan. El **Caso 1** trabaja el **perímetro y la segmentación** de una oficina de distrito; el **Caso 2**, el **acceso remoto y la VPN** de 900 teletrabajadores; y el **Caso 3**, un **incidente real de ransomware** que entra por un portátil, con su contención y su respuesta.

---

## Caso 1 — Rediseño del perímetro y la red de una oficina de distrito

### Enunciado

La Junta Municipal de un distrito va a reformar su Oficina de Atención a la Ciudadanía. La situación de partida, verificada en una visita técnica, es la siguiente:

- **Toda la oficina comparte un único segmento de red** (una sola VLAN, direccionamiento `10.30.7.0/24`): los 18 puestos de los tramitadores, dos impresoras multifunción, las pantallas de gestión de turnos, ocho cámaras de videovigilancia IP y un punto de acceso Wi-Fi abierto para el público.
- La oficina se conecta al CPD central por una **línea del operador contratada como «VPN MPLS»**. El pliego del operador afirma que «el tráfico viaja aislado del de otros clientes».
- Existe además un **encaminador 4G de respaldo**, contratado directamente por la Junta el año pasado, conectado a un puerto del conmutador «por si se cae la línea principal».
- El cortafuegos del CPD tiene, para esta oficina, una regla que permite **todo el tráfico** desde `10.30.7.0/24` hacia la red de servidores, «porque son de casa».
- Se quiere además **publicar en internet** un nuevo servicio de **cita previa** para trámites presenciales, alojado en un servidor que hoy está en la red de servidores del CPD.
- El sistema de información municipal afectado está categorizado **MEDIA** conforme al ENS.

Se solicita un informe técnico de rediseño previo a la reforma.

### Cuestiones

**Cuestión 1 — Segmentación de la oficina (3 puntos).** Analice el diseño de red actual de la oficina, identifique los riesgos y proponga la segmentación que exige el ENS, indicando la medida y el refuerzo aplicables.

**Cuestión 2 — El perímetro y sus dos reglas (2,5 puntos).** Valore el encaminador 4G de respaldo y la regla del cortafuegos del CPD. Cite los preceptos y medidas que resultan vulnerados.

**Cuestión 3 — La «VPN MPLS» del operador (2 puntos).** ¿Cumple el enlace contratado la medida `mp.com.2` del ENS? Justifique la respuesta y proponga la solución conforme.

**Cuestión 4 — Publicación del servicio de cita previa (2,5 puntos).** Diseñe la publicación del nuevo servicio indicando dónde se ubica, qué arquitectura de DMZ propone y qué reglas direccionales deben respetarse.

### Solución orientativa

**Cuestión 1 — Segmentación (§2.4.1, §1.4)**

El diseño actual concentra en un único dominio de difusión cinco poblaciones con perfiles de riesgo radicalmente distintos. Los riesgos concretos:

| Elemento en el segmento común | Riesgo que introduce |
|---|---|
| **Wi-Fi abierto al público** | Cualquier ciudadano en la sala de espera obtiene enlace en la misma red que los puestos de tramitación: puede escanear, envenenar ARP y colocarse como intermediario |
| **Cámaras IP** | Dispositivos IoT, con firmware raramente actualizado y credenciales por defecto frecuentes: son la puerta de entrada clásica |
| **Impresoras multifunción** | Almacenan temporalmente documentos escaneados y suelen exponer interfaces de administración sin autenticar |
| **Puestos de tramitación** | Tratan datos personales de ciudadanos; comprometer uno da acceso al gestor de expedientes |

Propuesta de segmentación, con su respaldo normativo:

- **`mp.com.4.2`** —obligación base, no refuerzo— exige que, si hay comunicaciones inalámbricas, sea **en un segmento separado**: el Wi-Fi público sale a una VLAN propia, con salida directa a internet y **sin ninguna ruta hacia la red municipal**.
- **`mp.com.4.r1.2`** exige segregar como mínimo en **usuarios, servicios y administración**. Se propone: VLAN de puestos, VLAN de dispositivos (impresoras, turnos, cámaras), VLAN de administración de los equipos de red y VLAN de invitados.
- Como el sistema es de **categoría MEDIA**, la tabla de aplicación de `mp.com.4` es **`+ [R1 o R2 o R3]`**: basta con **VLAN (R1)**, aunque conviene anotar que en categoría **ALTA** el R1 dejaría de ser suficiente.
- **`mp.eq.4`** alcanza expresamente a **impresoras, dispositivos multimedia, IoT y BYOD**, exigiéndoles configuración de seguridad adecuada; en nivel MEDIO de confidencialidad añade **R1**, productos del **CPSTIC**.
- Medidas complementarias de capa 2 (§1.3.1): **802.1X** en las rosetas de la zona de público, **seguridad de puerto**, **inspección dinámica de ARP** y **vigilancia de DHCP**.

**Cuestión 2 — El perímetro (§2.1, §1.4)**

**El encaminador 4G es el hallazgo más grave del caso.** Constituye una **salida alternativa no controlada** que vulnera directamente `mp.com.1.1`: «Todo el tráfico deberá atravesar dicho sistema». Si existe un camino que no pasa por el perímetro, **el perímetro no existe**. Además:

- Vulnera el **art. 21 del ENS**: la inclusión de cualquier elemento en el catálogo de activos **requiere autorización formal previa**, y este fue contratado por la Junta al margen del IAM.
- Vulnera el **art. 23**, porque introduce una **interconexión** cuyos riesgos no se han analizado y cuyo punto de unión no se controla.
- La solución no es retirar la redundancia —que es legítima y deseable por disponibilidad— sino **integrarla**: el respaldo debe terminar en el **mismo equipo perimetral**, con la misma política, conmutación automática y el túnel cifrado levantándose igualmente sobre él.

**La regla «permitir todo desde la oficina hacia los servidores»** vulnera `mp.com.1.2` («todos los flujos… autorizados previamente»), el principio de **denegación por defecto** y el **mínimo privilegio** del art. 20 y de `op.acc.4.2`. Debe sustituirse por reglas explícitas: **origen** la VLAN de puestos —no la oficina entera—, **destino** los servidores concretos del gestor de expedientes y del directorio, **servicios** los puertos concretos, y regla final de **denegar y registrar**.

**Cuestión 3 — La «VPN MPLS» (§4.1, §4.2.3)**

**No cumple `mp.com.2`.** El razonamiento, que es el núcleo de la cuestión:

- `mp.com.2.1` exige «**redes privadas virtuales cifradas** cuando la comunicación discurra por **redes fuera del propio dominio de seguridad**». La red del operador **es un dominio ajeno**.
- **MPLS aísla, pero no cifra**: proporciona privacidad **administrativa** —el tráfico de un cliente no se entrega a otro— pero no **criptográfica**. El operador, o quien comprometa su red, ve el tráfico en claro.
- El nombre comercial «VPN MPLS» induce a error, y es exactamente el tipo de afirmación de pliego que un técnico debe saber contradecir.

Solución conforme: **cifrar por encima** con un túnel **IPsec en modo túnel con ESP** entre la pasarela de la oficina y la del CPD, autenticado **por certificados** —no por clave precompartida—, sobre el enlace MPLS. Al ser el sistema de categoría MEDIA, aplica `mp.com.2 + R1`: **algoritmos y parámetros autorizados por el CCN**, es decir, conformes a la **CCN-STIC-807**; y `mp.com.3 + R1 + R2` para integridad y autenticidad. Es, además, la arquitectura habitual de **SD-WAN sobre MPLS**.

**Cuestión 4 — Publicación de la cita previa (§2.4.1)**

El servicio **no puede quedarse en la red de servidores**: pasa a ser alcanzable desde internet y debe alojarse en una **DMZ**.

- **Arquitectura propuesta**: **doble cortafuegos** (subred apantallada) si el presupuesto lo permite, idealmente de **fabricantes distintos**, por defensa en profundidad; o **cortafuegos de tres patas** como mínimo aceptable, documentando el riesgo de concentrar en un solo equipo la separación entre internet y la red interna.
- **Reglas direccionales**: internet → DMZ solo por **TCP 443**; DMZ → red interna **prohibido iniciar**. Si la aplicación de cita previa necesita consultar el calendario de la oficina, la conexión debe **originarse en la red interna** o resolverse con un servicio intermedio en la propia DMZ.
- Delante del servicio, un **proxy inverso** que termine el TLS, equilibre carga, oculte la topología e integre **WAF** — medida **`mp.s.2`**, que ya en categoría BÁSICA exige `+ [R1 o R2]`.
- **`op.mon.1 + R1`** por ser categoría MEDIA: detección de intrusiones **basada en reglas** sobre el tráfico publicado.
- **`mp.s.4`**, protección frente a denegación de servicio: **aplica desde nivel MEDIO** de disponibilidad, y la mitigación real debe estar **aguas arriba**, en el operador, porque el cortafuegos propio no sirve contra un ataque volumétrico.

### Criterios de evaluación

| Cuestión | Elemento evaluado | Puntos |
|---|---|---|
| **C1** | Identificar los riesgos del segmento único, en especial Wi-Fi público y cámaras IoT | 1,0 |
| **C1** | Citar `mp.com.4.2` (inalámbrica en segmento separado) y `mp.com.4.r1.2` (usuarios, servicios, administración) | 1,0 |
| **C1** | Situar correctamente la tabla de aplicación en categoría MEDIA y citar `mp.eq.4` | 1,0 |
| **C2** | Detectar el encaminador 4G como salida no controlada y vincularlo a `mp.com.1.1` | 1,5 |
| **C2** | Corregir la regla «permitir todo» invocando `mp.com.1.2` y el mínimo privilegio | 1,0 |
| **C3** | Afirmar que MPLS **no cifra** y que por sí solo no cumple `mp.com.2.1` | 1,2 |
| **C3** | Proponer IPsec ESP en modo túnel con certificados y citar el refuerzo R1 (CCN-STIC-807) | 0,8 |
| **C4** | Ubicar el servicio en DMZ y elegir arquitectura justificándola | 1,0 |
| **C4** | Enunciar correctamente la regla direccional DMZ → interna | 1,0 |
| **C4** | Añadir proxy inverso con WAF (`mp.s.2`) y mitigación DDoS aguas arriba (`mp.s.4`) | 0,5 |

---

## Caso 2 — Acceso remoto y VPN para 900 empleados en teletrabajo

### Enunciado

El Ayuntamiento va a regularizar el teletrabajo de **900 empleados municipales**, dos días por semana. La propuesta que llega a la mesa técnica es la siguiente:

- Se usará una **VPN de acceso remoto** con la pasarela **instalada en la red interna**, publicada a internet mediante una redirección de puertos en el cortafuegos.
- Autenticación con **usuario y contraseña** del directorio corporativo, «con política de contraseña robusta de 12 caracteres y caducidad de 90 días».
- **Túnel dividido**, «para no saturar el enlace de la sede central con el vídeo de las reuniones y la navegación personal».
- Una vez conectado, el empleado **queda en la misma VLAN de puestos** que si estuviera en la oficina, «para que todo le funcione igual».
- Los empleados usarán **su equipo personal**, «porque no hay presupuesto para 900 portátiles», con un cliente VPN instalado.
- Para los proveedores externos se creará **una cuenta por empresa**, compartida entre sus técnicos.
- Además, se pide dimensionar la solución para el **enlace permanente con el centro de proceso de respaldo** que el Ayuntamiento tiene en otro emplazamiento.
- El sistema está categorizado **MEDIA**, con confidencialidad de nivel **MEDIO**.

### Cuestiones

**Cuestión 1 — Identificación y autenticación (3 puntos).** Valore la propuesta de autenticación y la de cuentas de proveedor. Indique qué exige el ENS y cuál es el mínimo para cumplir.

**Cuestión 2 — Arquitectura del acceso (3 puntos).** Analice la ubicación de la pasarela, la decisión sobre el túnel y el alcance concedido al empleado conectado. Proponga el diseño correcto.

**Cuestión 3 — El equipo del empleado (2 puntos).** Valore el uso del equipo personal y proponga alternativas viables, con su fundamento jurídico.

**Cuestión 4 — Tecnología para cada escenario (2 puntos).** Elija la tecnología de VPN para el teletrabajo y para el enlace con el centro de respaldo, justificando ambas decisiones.

### Solución orientativa

**Cuestión 1 — Identificación y autenticación (§3.2)**

**La autenticación propuesta no cumple.** Con confidencialidad de nivel **MEDIO**, `op.acc.5` exige **`+ [R2 o R3 o R4] + R5`**:

- **La opción R1 —contraseña sola— deja de estar disponible** a partir de nivel MEDIO, **por robusta que sea**. La longitud y la caducidad son irrelevantes para la conformidad: lo que falta es un **segundo factor**.
- Mínimo para cumplir: añadir **R2** (contraseña de un solo uso, por aplicación autenticadora preferentemente al SMS) o **R3/R4** (**certificado cualificado** protegido por segundo factor, con registro previo); **más R5**: registrar los accesos **con éxito y fallidos** e informar al usuario de su **último acceso**.
- Debe añadirse la **limitación del número de intentos** (`op.acc.5.8`) y la **política específica de acceso remoto con autorización expresa** (`op.acc.4.5`).

**Las cuentas compartidas por empresa proveedora están prohibidas.** `op.acc.1.3` exige un **identificador singular** por cada entidad, y una cuenta compartida **destruye la trazabilidad**: ninguna acción es atribuible a una persona, lo que además incumple `op.exp.8` y el art. 24. Lo correcto: **cuenta nominal** para cada técnico del proveedor, **certificado** emitido para él, **ventana temporal acotada al ticket**, acceso **exclusivamente al servidor de salto** y **revocación automática** al cierre. Complementariamente, `op.acc.1.2`: los administradores no administran con su cuenta ofimática.

**Cuestión 2 — Arquitectura (§3.1, §4.1.2)**

Tres errores encadenados:

1. **La pasarela no puede estar en la red interna.** Debe ubicarse en la **DMZ**, publicada con la superficie mínima. Una redirección de puertos hacia un equipo interno significa que, si se compromete la pasarela, el atacante está **dentro** sin cruzar ninguna otra frontera. Es contrario al art. 23 y a la lógica de `mp.com.1`.
2. **El túnel dividido es la opción incorrecta por defecto en un entorno del ENS.** Con él, la navegación del empleado **escapa al control corporativo** y `mp.s.3` (protección de la navegación web, con su normativa de uso, sus listas y su registro) deja de ser aplicable; y el equipo queda **con un pie en cada red**, convertido en puente potencial, lo que compromete el art. 9. Lo correcto es **túnel completo**, y si el ancho de banda es un problema real, tratarlo como **excepción justificada y acotada** —por ejemplo, excluyendo únicamente el servicio corporativo de videoconferencia—, nunca como regla general que incluya la navegación personal.
3. **Dejar al teletrabajador en la VLAN de puestos vulnera `mp.eq.3.3`**, que obliga a limitar «la información y los servicios accesibles a los mínimos imprescindibles» cuando la conexión llega por redes no controladas. Diseño correcto: **segmento de teletrabajo** propio, desde el que se alcanzan el gestor de expedientes, el correo, la intranet y la impresión, y **no** se alcanzan la red de administración de sistemas, la de videovigilancia ni los puestos de otros compañeros.

Debe añadirse **comprobación del estado del dispositivo** antes de conceder acceso, con desvío a **cuarentena** para remediación si no cumple, y **registro** completo enviado al SIEM (`op.mon.3.r1`, exigible en MEDIA).

**Cuestión 3 — El equipo del empleado (§5, §3.1)**

El uso del equipo personal es la decisión de mayor riesgo del caso, y además es **jurídicamente discutible**:

- El **art. 47 bis del TREBEP** dispone que **«la Administración proporcionará a la persona los medios tecnológicos necesarios»** para el teletrabajo. La propuesta traslada al empleado una obligación que la norma sitúa en la Administración.
- Técnicamente, un equipo personal **no puede cumplir** `op.exp.2` (bastionado y mínima funcionalidad), `op.exp.4` (parcheado gestionado), `op.exp.6` (antimalware corporativo con protección en tiempo real) ni `mp.eq.3.r1` (cifrado de disco), y no es inventariable conforme a `mp.eq.3.1`. Una VPN sobre un equipo no controlado es un túnel cifrado y seguro que lleva el problema directamente al centro de la red: **la VPN protege el canal, no los extremos**.

Alternativas viables, en orden de preferencia:

1. **Portátil corporativo gestionado**, con MDM/UEM, cifrado, EDR y línea base — la opción conforme.
2. **Escritorio virtual (VDI)** o publicación de aplicaciones: el dato **nunca sale** del CPD y el equipo personal actúa solo como terminal, con el portapapeles y la redirección de unidades deshabilitados. Es la solución de compromiso más defendible si no hay presupuesto para equipos.
3. **VPN SSL/TLS sin cliente** contra un portal de aplicaciones web concretas, para casos puntuales y de bajo riesgo.
4. Si aun así se admitiera BYOD, **`mp.eq.4`** lo alcanza expresamente y exigiría, como mínimo, contenedor corporativo separado, exigencia de cifrado y PIN, y borrado remoto del contenedor.

**Cuestión 4 — Tecnología para cada escenario (§4.2)**

**Teletrabajo — VPN de acceso remoto con cliente.** Se propone un producto que ofrezca **IKEv2 como camino principal** —mejor rendimiento, y **MOBIKE** permite pasar del Wi-Fi doméstico a la red móvil sin que se caiga el túnel— y **TLS sobre TCP 443 como respaldo**, para redes ajenas que bloqueen IPsec. La decisión no es «IPsec **o** TLS», sino un diseño con **camino principal y alternativo**. Configuración: túnel completo, MFA, certificado de dispositivo, comprobación de estado y segmento de teletrabajo.

**Enlace con el centro de respaldo — IPsec en modo túnel con ESP.** Argumentos: son **dos redes** con direccionamiento fijo y pasarelas propias; el enlace es **permanente y de alto caudal** —por él irán replicación de bases de datos y copias de seguridad—, y ahí IPsec rinde mejor y se acelera por hardware; la **transparencia para las aplicaciones** es imprescindible; y no hay cortafuegos ajenos que atravesar. Autenticación **por certificados**, **rekey** periódico, algoritmos conformes a la **CCN-STIC-807**, y producto del **CPSTIC** por exigirlo `op.pl.5` desde categoría MEDIA. Recuérdese abrir **UDP 500 y 4500** y los protocolos IP **50** —y no solo el 500, error clásico que deja el túnel levantado sin cursar tráfico—.

### Criterios de evaluación

| Cuestión | Elemento evaluado | Puntos |
|---|---|---|
| **C1** | Afirmar que la contraseña sola no cumple en nivel MEDIO y citar `+ [R2 o R3 o R4] + R5` | 1,5 |
| **C1** | Prohibir la cuenta compartida por trazabilidad, citando `op.acc.1.3` y `op.exp.8` | 1,0 |
| **C1** | Añadir `op.acc.4.5`, política específica con autorización expresa | 0,5 |
| **C2** | Trasladar la pasarela a la DMZ y justificarlo | 1,0 |
| **C2** | Rechazar el túnel dividido con el argumento de `mp.s.3` y del art. 9 | 1,0 |
| **C2** | Crear un segmento de teletrabajo invocando `mp.eq.3.3` | 1,0 |
| **C3** | Invocar el art. 47 bis del TREBEP (medios a cargo de la Administración) | 1,0 |
| **C3** | Proponer una alternativa viable (equipo corporativo o VDI) con su razonamiento | 1,0 |
| **C4** | Elegir IKEv2 con respaldo TLS para el acceso remoto, con argumentos | 1,0 |
| **C4** | Elegir IPsec ESP en modo túnel para el enlace permanente, con argumentos | 1,0 |

---

## Caso 3 — Incidente: ransomware entrado por un portátil municipal

### Enunciado

Un lunes a las 08:40, el CAU municipal recibe tres llamadas de una misma unidad administrativa: «los ficheros de la carpeta compartida se abren con caracteres raros y ha aparecido un documento de texto pidiendo dinero». La investigación inicial establece:

- El **viernes anterior a las 19:10**, una empleada recibió en su correo corporativo un mensaje que aparentaba proceder de un proveedor habitual, redactado en castellano correcto y con el asunto de un expediente real en tramitación. Abrió el enlace y **escribió sus credenciales** en una página que imitaba el acceso a la intranet.
- La empleada **se dio cuenta a los diez minutos** de que la página no era la corporativa, pero **no avisó**: «era viernes por la tarde y me dio apuro, pensé que si no había pasado nada no hacía falta molestar».
- El **sábado por la mañana**, esas credenciales se usaron para conectarse a la **VPN de acceso remoto**, que solo pide usuario y contraseña.
- Desde el segmento de teletrabajo, el atacante alcanzó **un servidor de ficheros** cuya versión de sistema operativo **está fuera de soporte desde octubre de 2025**, y desde él se movió a otros seis servidores.
- El **antivirus** de los servidores estaba actualizado y **no detectó nada**: el atacante empleó herramientas legítimas del propio sistema.
- Los **registros del cortafuegos** existen, pero **nadie los revisa**: no hay correlación ni alertas.
- Las **copias de seguridad** se guardan en un recurso compartido de la propia red, montado permanentemente en el servidor de copias. **Están cifradas por el atacante**.
- El sistema está categorizado **ALTA** por su dimensión de disponibilidad.

### Cuestiones

**Cuestión 1 — Cadena del incidente y medidas incumplidas (3 puntos).** Reconstruya la cadena del ataque paso a paso e identifique, en cada eslabón, la medida del ENS que habría debido detenerlo.

**Cuestión 2 — Contención inmediata (2,5 puntos).** Enumere y ordene las acciones de contención de las primeras dos horas, justificando el orden.

**Cuestión 3 — Obligaciones de notificación (2 puntos).** Indique a quién y en qué plazo debe notificarse el incidente, distinguiendo las obligaciones que concurren.

**Cuestión 4 — Plan de mejora (2,5 puntos).** Proponga las medidas que impedirían la repetición, ordenadas por eficacia y con su respaldo normativo.

### Solución orientativa

**Cuestión 1 — La cadena y sus eslabones (§1.2, §5, §2.3)**

| Eslabón | Qué ocurrió | Medida del ENS que lo habría detenido |
|---|---|---|
| **1. Acceso inicial** | Phishing dirigido, con contexto real y castellano correcto — coherente con el dato de que más del 80 % de la ingeniería social ya usa IA | `mp.per.3` (concienciación: ingeniería social) y `mp.s.1` (protección del correo, con SPF, DKIM y DMARC y aislamiento de enlaces) |
| **2. No notificación** | La empleada detectó el error y **no avisó** por temor al reproche | `mp.per.3.3`: el procedimiento para informar **«sean reales o falsas alarmas»**. Es un fallo **de cultura organizativa**, no de la persona |
| **3. Entrada por la VPN** | Credencial robada + VPN **sin segundo factor** | `op.acc.5`: en categoría ALTA, `+ [R2 o R3 o R4] + R5`. **Un segundo factor habría cortado el ataque aquí**, con la credencial ya en poder del atacante |
| **4. Alcance excesivo** | Desde el segmento de teletrabajo se llegaba a servidores de ficheros | `mp.eq.3.3` (mínimos imprescindibles desde redes no controladas) y `mp.com.4` (en ALTA, `+ [R2 o R3] + R4`) |
| **5. Servidor vulnerable** | Sistema **fuera de soporte** desde octubre de 2025 | `op.exp.4`: procedimiento de análisis, priorización y aplicación de actualizaciones. Y art. 21 (integridad y actualización del sistema) |
| **6. Movimiento lateral** | Seis servidores más, con herramientas legítimas del sistema | `op.exp.6.r4` (**EDR**, exigible en ALTA) y `op.exp.6.r3` (**lista blanca**). El antivirus por firmas es ciego ante el **malware sin fichero** |
| **7. Nadie lo vio** | Registros sin revisar, sin correlación ni alertas | `op.mon.1` (detección de intrusión; en ALTA, `+ R1 + R2` con **procedimientos de respuesta**) y `op.mon.3.r1` (**correlación**, el SIEM) |
| **8. Copias cifradas** | Recurso de copia **montado permanentemente** en la red | **`mp.info.6.r2.1`**, exigible en nivel **ALTO**: «al menos, una de las copias de seguridad se almacenará de forma **separada en lugar diferente**, de tal manera que **un incidente no pueda afectar tanto al repositorio original como a la copia simultáneamente**». Es literalmente lo que ocurrió |

La lectura de conjunto es la que importa: **ninguno de los ocho eslabones era inevitable**, y el art. 9 del ENS —líneas de defensa— presupone precisamente que varios fallarán. Aquí fallaron **todos**, porque en realidad **no había capas independientes**: había una sola, la contraseña.

**Cuestión 2 — Contención en las dos primeras horas (§2.3, §5.2.1)**

Orden propuesto, con su justificación:

1. **Activar el procedimiento de gestión de incidentes** y constituir el equipo (`op.exp.7`). Sin mando único, las acciones se pisan.
2. **Cortar el acceso remoto**: deshabilitar la cuenta comprometida y, si es necesario, **suspender la VPN** completa. Es el camino por el que el atacante sigue entrando.
3. **Aislar en red los sistemas afectados**, con EDR si lo hay, o desconectando el puerto del conmutador. **No apagar los equipos**: apagar destruye la memoria volátil, que es la evidencia más valiosa.
4. **Segmentar de urgencia**: cortar el tráfico entre el segmento afectado y el resto, para frenar la propagación.
5. **Preservar evidencias**: registros del cortafuegos, de la VPN, del directorio y de los servidores, con **copia y sellado** antes de que roten.
6. **Rotar credenciales** de las cuentas privilegiadas y forzar cambio de contraseña, empezando por las de administración del dominio.
7. **Verificar el estado real de las copias**: localizar la copia más reciente **no comprometida**, incluidas cintas o copias fuera de línea, antes de plantear cualquier restauración.
8. **Comunicación interna** controlada: qué se dice al personal y a los responsables, y **canal alternativo** si el correo está comprometido.

Lo que **no** debe hacerse: pagar el rescate; restaurar sobre los mismos sistemas sin haber determinado el vector, porque se vuelven a cifrar; ni «limpiar y seguir» sin análisis forense.

**Cuestión 3 — Notificaciones (§1.1, §1.4)**

Concurren **dos obligaciones distintas, por vías distintas**, y confundirlas es error habitual:

- **Por el ENS**: notificación al **CCN-CERT** conforme al **art. 33** del ENS (capacidad de respuesta a incidentes) y a la **Instrucción Técnica de Seguridad de Notificación de Incidentes de Seguridad** (Resolución de 13 de abril de 2018), con la clasificación y los plazos que esta fija según la peligrosidad y el impacto.
- **Por protección de datos**: si el incidente afecta a datos personales —y aquí los afecta, por el contenido de los expedientes—, notificación a la **AEPD** en un plazo máximo de **72 horas** desde que se tuvo conocimiento (**art. 33 del RGPD**), y **comunicación a los interesados** si el riesgo para sus derechos es alto (**art. 34**). Debe documentarse el incidente en el **registro de violaciones de seguridad**, con independencia de que se notifique o no.
- Debe valorarse además la **denuncia** ante las Fuerzas y Cuerpos de Seguridad del Estado, y la comunicación a los responsables de la información y del servicio (art. 11).

**Cuestión 4 — Plan de mejora, ordenado por eficacia (§5, §3.2, §2.4)**

| Prioridad | Medida | Por qué es la más eficaz | Respaldo |
|---|---|---|---|
| **1** | **MFA obligatorio** en la VPN y en todo acceso remoto | Habría cortado el ataque **con la credencial ya robada**: es el único control que neutraliza el 60 % de los vectores de entrada | `op.acc.5` en nivel ALTO |
| **2** | **Copias fuera de línea o inmutables**, con prueba de restauración | Es lo único que revierte de verdad un ransomware ya consumado | `mp.info.6.r2` (copia separada) y `mp.info.6.r1` (probar la restauración) |
| **3** | **EDR** en puestos y servidores, con capacidad de aislamiento | Detecta el **malware sin fichero** y el movimiento lateral, que el antivirus no ve | `op.exp.6.r4`, exigible en ALTA |
| **4** | **Plan de salida de sistemas fuera de soporte**, con calendario y presupuesto | Elimina la vulnerabilidad explotada; ninguna otra medida la compensa | `op.exp.4` · art. 21 |
| **5** | **Segmentación efectiva** y revisión del alcance del segmento de teletrabajo | Convierte un incidente total en un incidente local | `mp.com.4` en ALTA · `mp.eq.3.3` |
| **6** | **SIEM con correlación y procedimientos de respuesta** a las alertas | Reduce el tiempo de detección, que aquí fue de **más de 48 horas** | `op.mon.3.r1` · `op.mon.1.r2` |
| **7** | **Programa de concienciación** con simulaciones y, sobre todo, **cultura de notificación sin reproche** | Diez minutos de aviso el viernes habrían evitado todo lo demás | `mp.per.3` y `mp.per.4` |

**El punto 7 merece un desarrollo propio**, porque es el que suele quedar peor tratado. El indicador que hay que medir no es solo el **porcentaje de clics** —que debe bajar— sino el **porcentaje de notificaciones** —que debe **subir**— y el **tiempo hasta la primera notificación** —que debe bajar—. Un organismo donde el 20 % pincha pero el 60 % avisa en cinco minutos está objetivamente mejor protegido que otro donde solo pincha el 5 % y nadie avisa. Ambos indicadores alimentan `op.mon.2`, el sistema de métricas del ENS, y `mp.per.4` exige expresamente **evaluar la eficacia** de las acciones formativas.

### Criterios de evaluación

| Cuestión | Elemento evaluado | Puntos |
|---|---|---|
| **C1** | Reconstruir la cadena completa en orden, sin saltarse eslabones | 1,0 |
| **C1** | Identificar el MFA ausente como el punto de corte más eficaz | 1,0 |
| **C1** | Vincular al menos cuatro eslabones con su medida concreta del ENS | 1,0 |
| **C2** | Ordenar correctamente: cortar el acceso antes de aislar y aislar antes de restaurar | 1,0 |
| **C2** | Indicar que **no se apagan** los equipos, por preservación de evidencias | 0,7 |
| **C2** | Verificar el estado de las copias antes de plantear la restauración | 0,8 |
| **C3** | Distinguir las dos vías: CCN-CERT por el ENS y AEPD en 72 horas por el RGPD | 1,2 |
| **C3** | Citar el art. 33 del ENS y la ITS de Notificación de Incidentes | 0,8 |
| **C4** | Priorizar el MFA y las copias inmutables por delante del resto | 1,2 |
| **C4** | Incluir la cultura de notificación y proponer indicadores medibles | 1,3 |
