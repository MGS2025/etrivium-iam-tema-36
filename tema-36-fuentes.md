# Tema 36 — Fuentes

> **Título oficial**: Seguridad y protección en redes de comunicaciones. Seguridad perimetral. Acceso remoto seguro a redes. Redes privadas virtuales (VPN). Seguridad en el puesto del usuario.
>
> **Criterio de cita**: en el contenido, las medidas del Esquema Nacional de Seguridad se citan **por su código del anexo II** (`mp.com.1`, `op.acc.5`, `op.exp.6`…) y las especificaciones técnicas **por su número de RFC**; el registro completo, con el identificador breve que usan el test y los diagramas (`[ENS]`, `[RFC4301]`, `[NIST-ZT]`), está en este documento. **Tier 1** = normativa española y europea directamente aplicable, guías del Centro Criptológico Nacional y especificaciones de estándares abiertos (IETF, ISO/IEC, IEEE, NIST). **Tier 2** = informes de amenazas, hojas de ruta institucionales y documentación de fabricante citada para datos de soporte y de estado actual. **Tier 3** = marco municipal de contexto.
>
> **Verificación**. Este tema se ha construido sobre **dos fuentes primarias descargadas y leídas, no sobre fuentes secundarias**: (1) el **PDF oficial del BOE** del Real Decreto 311/2022 en su texto consolidado (`BOE-A-2022-7191`), extraído con `pdftotext -layout`, de donde proceden **literales** todas las medidas, refuerzos y tablas de aplicación citadas; y (2) el **índice oficial del RFC Editor** (`rfc-index.txt`), contra el que se han comprobado uno a uno el **número, título, fecha, estado y relaciones de obsolescencia** de todos los RFC citados. De esa segunda verificación proceden tres hallazgos que prácticamente ningún material de oposición recoge todavía, detallados en el changelog: la **normalización de TACACS+ sobre TLS 1.3 (RFC 9887, diciembre de 2025)**, **RADIUS/1.1 (RFC 9765, abril de 2025)** y el **intercambio híbrido post-cuántico para TLS 1.3 (RFC 10024, agosto de 2026)**. Se ha verificado además, en la fuente oficial, que la **ITS de Interconexión a la que remite `mp.com.1` no está publicada**.

---

## Tier 1 — Normativa y estándares

### Normativa española y europea

| ID | Referencia |
|---|---|
| `[ENS]` | Real Decreto **311/2022, de 3 de mayo**, por el que se regula el **Esquema Nacional de Seguridad** (BOE núm. 106, de 4 de mayo de 2022), texto consolidado. Es la fuente principal de este tema. Se citan, **verificados contra el PDF del BOE**: los **principios básicos** de los arts. 5 a 11 —en especial el **art. 9 (líneas de defensa)**, el **art. 10 (vigilancia continua)** y el **art. 11 (diferenciación de responsabilidades)**—; el **art. 20 (mínimo privilegio)**, el **art. 21 (integridad y actualización)**, el **art. 22 (protección de la información almacenada y en tránsito)**, el **art. 23 (prevención ante otros sistemas interconectados)** —base legal de la seguridad perimetral—, el **art. 24 (registro de actividad)**, el **art. 32 (informe del estado de la seguridad)** y el **art. 33 (capacidad de respuesta a incidentes)**; y del **anexo II**, las medidas **`op.pl.5`** (componentes certificados y CPSTIC), **`op.acc.1` a `op.acc.6`** —con `op.acc.4.5`, política específica de acceso remoto—, **`op.exp.1` a `op.exp.8`** —con `op.exp.2`, `op.exp.4` y `op.exp.6` y sus refuerzos R3 (lista blanca) y **R4 (EDR)**—, **`op.mon.1` a `op.mon.3`**, **`mp.per.3` y `mp.per.4`**, **`mp.eq.1` a `mp.eq.4`**, **`mp.com.1` a `mp.com.4`**, **`mp.si.2`**, **`mp.info.6`** y **`mp.s.1` a `mp.s.4`**. |
| `[ITS]` | **Instrucciones Técnicas de Seguridad** del ENS. Las **cuatro publicadas** en el BOE: **Conformidad con el ENS** e **Informe del Estado de la Seguridad** (Resoluciones de 13 y 7 de octubre de 2016, `BOE-A-2016-10109` y `BOE-A-2016-10108`); **Auditoría de la Seguridad de los Sistemas de Información** (Resolución de 27 de marzo de 2018, `BOE-A-2018-4573`); y **Notificación de Incidentes de Seguridad** (Resolución de 13 de abril de 2018, `BOE-A-2018-5370`). **Verificado en el portal oficial del ENS del CCN**: **no** están publicadas la ITS de **Interconexión de Sistemas de Información** —a la que remite `mp.com.1`—, la de **Criptología** ni la de **Adquisición de productos de seguridad**. |
| `[L40-2015]` | Ley **40/2015, de 1 de octubre**, de Régimen Jurídico del Sector Público. **Art. 156.2**, fundamento legal del ENS y del ENI; art. 38 (sede electrónica) y art. 41 (actuación administrativa automatizada). |
| `[L39-2015]` | Ley **39/2015, de 1 de octubre**, del Procedimiento Administrativo Común. Sistemas de **identificación** (art. 9) y de **firma** (art. 10) de los interesados, y derecho a relacionarse electrónicamente (art. 14). |
| `[TREBEP]` | Real Decreto Legislativo **5/2015, de 30 de octubre**, texto refundido de la Ley del Estatuto Básico del Empleado Público. **Artículo 47 bis (teletrabajo)**, introducido por el **Real Decreto-ley 29/2020, de 29 de septiembre** (`BOE-A-2020-11415`): teletrabajo **expresamente autorizado**, **voluntario y reversible**, compatible con la modalidad presencial, y con la Administración obligada a **proporcionar los medios tecnológicos** necesarios. |
| `[RGPD]` | Reglamento (UE) **2016/679**, General de Protección de Datos. Art. **5.1.f** (integridad y confidencialidad), art. **32** (seguridad del tratamiento, con mención expresa del **cifrado**) y arts. **33 y 34** (notificación de violaciones de seguridad: **72 horas** a la autoridad de control, y comunicación a los interesados cuando el riesgo sea alto). |
| `[LOPDGDD]` | Ley Orgánica **3/2018, de 5 de diciembre**, de Protección de Datos Personales y garantía de los derechos digitales. Relevante, además, por sus derechos digitales en el ámbito laboral (arts. 87 a 91: intimidad frente al uso de dispositivos, videovigilancia y desconexión digital). |
| `[NIS2]` | Directiva (UE) **2022/2555**, relativa a las medidas destinadas a garantizar un elevado nivel común de **ciberseguridad** en la Unión. **Pendiente de transposición en España en agosto de 2026**: el **anteproyecto de Ley de Coordinación y Gobernanza de la Ciberseguridad** fue aprobado por el Consejo de Ministros el **14 de enero de 2025** y continúa en tramitación, sin publicación en el BOE; el plazo de transposición del art. 41 venció el **17 de octubre de 2024** y la Comisión Europea remitió a España **dictamen motivado** en 2025. |
| `[EIDAS2]` | Reglamento (UE) **2024/1183**, que modifica el Reglamento (UE) 910/2014 en lo relativo al **marco europeo de identidad digital**. Marco de los **certificados cualificados** exigidos por `op.acc.5.r3` y `op.acc.5.r4`, y de la **cartera de identidad digital**. |
| `[LSSI]` | Ley **34/2002, de 11 de julio**, de servicios de la sociedad de la información y de comercio electrónico. Citada por el régimen de **cookies** del art. 22.2, relevante en la política de navegación de `mp.s.3.7`. |

### Guías del Centro Criptológico Nacional (serie CCN-STIC)

| ID | Referencia |
|---|---|
| `[CCN-408]` | **CCN-STIC-408**, *Seguridad perimetral — cortafuegos*. Guía de acceso público del CCN-CERT. Referencia española para el diseño y la configuración del cortafuegos perimetral. |
| `[CCN-836]` | **CCN-STIC-836**, *Seguridad en VPN en el marco del ENS*. Guía de referencia para la sección 4 completa: selección de tecnología, algoritmos, parámetros y despliegue de VPN conformes al ENS. |
| `[CCN-807]` | **CCN-STIC-807**, *Criptología de empleo en el Esquema Nacional de Seguridad*. Fija los **algoritmos y parámetros criptográficos autorizados** y sus longitudes de clave por nivel. Es la guía a la que remiten `mp.com.2.r1` y `mp.com.3.r2` cuando exigen «algoritmos y parámetros **autorizados por el CCN**», y la referencia correcta en un pliego, en lugar de congelar un número de RFC. |
| `[CCN-105]` | **CCN-STIC-105**, *Catálogo de Productos y Servicios de Seguridad de las TIC (CPSTIC)*. Tres secciones: productos **aprobados** (información clasificada), productos y servicios **cualificados** (información sensible en el ámbito del ENS) y productos y servicios de conformidad y gobernanza. Es el catálogo al que remite **`op.pl.5`**, exigible **desde categoría MEDIA**. Versión de **agosto de 2026**. |
| `[CCN-140]` | **CCN-STIC-140**, *Taxonomía de referencia para productos y servicios de seguridad TIC*. Clasifica los productos en categorías y familias y define los **Requisitos Fundamentales de Seguridad (RFS)** de cada familia, que es lo que debe cumplir un cortafuegos, una pasarela VPN o un EDR para entrar en el CPSTIC. |
| `[CCN-500]` | Series **CCN-STIC 500 y 600**, guías de **bastionado** por tecnología (sistemas operativos, servidores web, servidores de correo, DNS, SSH, equipos de red). Exigidas por el **art. 20.d** del ENS y por `op.exp.2`. |

### Especificaciones del IETF (RFC) — verificadas contra el índice del RFC Editor

| ID | Referencia |
|---|---|
| `[RFC-ED]` | **RFC Editor**, `rfc-index.txt`. Índice oficial de la serie: número, título, autores, fecha, formato, relaciones `Obsoletes` / `Obsoleted by` / `Updates` y estado. Fuente de verificación de todas las entradas de esta tabla. |
| `[RFC4301]` | *Security Architecture for the Internet Protocol* (diciembre de 2005). Arquitectura general de **IPsec**; obsoleta el RFC 2401. Define las **SA**, la **SAD** y la **SPD** con sus tres acciones (descartar, omitir IPsec, aplicar IPsec). |
| `[RFC4302]` | *IP Authentication Header* (**AH**). Protocolo IP **51**: integridad y autenticación del origen, **sin cifrado**. Obsoleta el RFC 2402. |
| `[RFC4303]` | *IP Encapsulating Security Payload* (**ESP**). Protocolo IP **50**: cifrado, integridad y autenticación. Obsoleta el RFC 2406. Es el protocolo que se usa en la práctica. |
| `[RFC7296]` | *Internet Key Exchange Protocol Version 2* (**IKEv2**), octubre de 2014. **Internet Standard, STD 79**. Actualizado por los RFC 7427, 7670, 8247, 8983, 9370 y **9827** (noviembre de 2025). Puertos **UDP 500** y **UDP 4500**. |
| `[RFC9395]` | *Deprecation of the Internet Key Exchange Version 1 (IKEv1) Protocol and Obsoleted Algorithms* (**abril de 2023**). Declara **obsoleto IKEv1** y actualiza los RFC 8221 y 8247. |
| `[RFC3948]` | *UDP Encapsulation of IPsec ESP Packets* (enero de 2005). **Travesía de NAT**: encapsula ESP en **UDP 4500**. |
| `[RFC8221]` | *Cryptographic Algorithm Implementation Requirements and Usage Guidance for ESP and AH*. Obsoleta el RFC 7321; actualizado por el RFC 9395. |
| `[RFC8247]` | *Algorithm Implementation Requirements and Usage Guidance for IKEv2*. Obsoleta el RFC 4307; actualizado por el RFC 9395. |
| `[RFC9846]` | *The Transport Layer Security (TLS) Protocol Version 1.3*, **julio de 2026**. **Obsoleta los RFC 5077, 5246, 6961, 7627, 8422 y 8446**: es la especificación vigente de TLS 1.3 y sustituye a la de 2018. |
| `[RFC8446]` | *The Transport Layer Security (TLS) Protocol Version 1.3* (agosto de 2018). **Obsoletado por el RFC 9846**. Se conserva la referencia porque es la que recogen los temarios al uso. |
| `[RFC8996]` | *Deprecating TLS 1.0 and TLS 1.1* (marzo de 2021). Prohíbe ambas versiones. |
| `[RFC7568]` | *Deprecating Secure Sockets Layer Version 3.0* (junio de 2015). |
| `[RFC10015]` | *Deprecating Obsolete Key Exchange Methods in TLS 1.2 and DTLS 1.2*, **julio de 2026**. Actualiza, entre otros, los RFC 5246 y 9325. |
| `[RFC9325]` | *Recommendations for Secure Use of TLS and DTLS* (**BCP 195**), noviembre de 2022. Obsoleta el RFC 7525. Referencia de buenas prácticas de configuración. |
| `[RFC9147]` | *The Datagram Transport Layer Security (DTLS) Protocol Version 1.3* (abril de 2022). |
| `[RFC4251]` | *The Secure Shell (SSH) Protocol Architecture* (enero de 2006), junto con los **RFC 4252** (autenticación), **4253** (capa de transporte) y **4254** (capa de conexión y **reenvío de puertos**). Puerto **TCP 22**. |
| `[RFC9142]` | *Key Exchange (KEX) Method Updates and Recommendations for Secure Shell (SSH)* (enero de 2022). |
| `[RFC2865]` | *Remote Authentication Dial In User Service* (**RADIUS**), junio de 2000, y **RFC 2866** (contabilidad). Puertos **UDP 1812** y **1813**. Actualizados por los RFC 2868, 3575, 5080, 6929, 8044 y **9765**. |
| `[RFC9765]` | *RADIUS/1.1: Leveraging Application-Layer Protocol Negotiation (ALPN) to Remove MD5*, **abril de 2025**. Estado **Experimental**. Actualiza los RFC 2865, 2866, 5176, 6613, 6614 y 7360. |
| `[RFC6614]` | *TLS Encryption for RADIUS* (**RadSec**), mayo de 2012, estado Experimental; y **RFC 7360**, *DTLS as a Transport Layer for RADIUS*, también experimental. |
| `[RFC8907]` | *The Terminal Access Controller Access-Control System Plus (TACACS+) Protocol*, septiembre de 2020, estado **Informational**. Puerto **TCP 49**. |
| `[RFC9887]` | *TACACS+ over TLS 1.3*, **diciembre de 2025**. Estado **Proposed Standard**; actualiza el RFC 8907. Resuelve la debilidad histórica del cifrado propio de TACACS+. |
| `[RFC6733]` | *Diameter Base Protocol* (octubre de 2012). Sucesor de RADIUS; obsoleta el RFC 3588. |
| `[RFC3748]` | *Extensible Authentication Protocol* (**EAP**), junio de 2004. Obsoleta el RFC 2284. |
| `[RFC5216]` | *The EAP-TLS Authentication Protocol* (marzo de 2008). Actualizado por los RFC 8996, **9190** y 9965. |
| `[RFC9190]` | *EAP-TLS 1.3: Using the Extensible Authentication Protocol with TLS 1.3* (febrero de 2022). |
| `[RFC2637]` | *Point-to-Point Tunneling Protocol* (**PPTP**), julio de 1999, estado Informational. **Criptográficamente roto**: no debe usarse. |
| `[RFC2661]` | *Layer Two Tunneling Protocol* (**L2TP**), agosto de 1999, y **RFC 3931** (**L2TPv3**, marzo de 2005). **UDP 1701**. **No cifra**. |
| `[RFC2784]` | *Generic Routing Encapsulation* (**GRE**), marzo de 2000. Protocolo IP **47**. **No cifra**. |
| `[RFC1918]` | *Address Allocation for Private Internets* (**BCP 5**) y **RFC 3022** (NAT tradicional). |
| `[RFC1928]` | *SOCKS Protocol Version 5* (marzo de 1996). Proxy genérico de nivel de sesión; **no inspecciona contenido**. |
| `[RFC5424]` | *The Syslog Protocol* (marzo de 2009) y **RFC 5425** (syslog sobre **TLS**, puerto **TCP 6514**). |
| `[RFC4120]` | *The Kerberos Network Authentication Service (V5)* (julio de 2005). |
| `[RFC8784]` | *Mixing Preshared Keys in IKEv2 for Post-quantum Security* (junio de 2020); **RFC 9370**, *Multiple Key Exchanges in IKEv2* (mayo de 2023); y **RFC 9867** (noviembre de 2025), que extiende la mezcla a los intercambios IKE_INTERMEDIATE y CREATE_CHILD_SA. |
| `[RFC10024]` | *Post-Quantum Traditional (PQ/T) Hybrid Key Agreement Mechanisms for TLS 1.3*, **agosto de 2026**, Proposed Standard; y **RFC 9954**, *Hybrid Key Exchange in TLS 1.3* (julio de 2026, Informational). |
| `[RFC7348]` | *Virtual eXtensible Local Area Network (VXLAN)* (agosto de 2014). Superposición de segmentos de nivel 2 sobre una red IP. |
| `[RFC9525]` | *Service Identity in TLS* (noviembre de 2023). Obsoleta el RFC 6125. Validación del nombre del servidor en el certificado. |
| `[RFC6797]` | *HTTP Strict Transport Security (HSTS)* (noviembre de 2012). |

### Normas ISO/IEC, IEEE y publicaciones del NIST

| ID | Referencia |
|---|---|
| `[NIST-ZT]` | **NIST SP 800-207**, *Zero Trust Architecture*, **agosto de 2020**. Fuente de los **siete principios** de la confianza cero y de los componentes lógicos **PE**, **PA** —que forman el **PDP**— y **PEP**. Complementada por la **SP 800-207A** para entornos multinube nativos. |
| `[IEEE8021X]` | **IEEE 802.1X**, *Port-Based Network Access Control*. Suplicante, autenticador y servidor de autenticación; estado del puerto y **EAPOL**. |
| `[IEEE8021AE]` | **IEEE 802.1AE**, **MACsec**: confidencialidad e integridad **salto a salto** en la trama Ethernet. |
| `[IEEE8021Q]` | **IEEE 802.1Q**, etiquetado de **VLAN**. Mecanismo con el que se implementa `mp.com.4.r1`. |
| `[ISO27001]` | **UNE-EN ISO/IEC 27001** y **27002**, sistemas de gestión de la seguridad de la información y controles. Marco de gestión complementario al ENS. |
| `[MAGERIT]` | **MAGERIT v3** (2012), *Metodología de Análisis y Gestión de Riesgos de los Sistemas de Información*, del entonces Ministerio de Hacienda y Administraciones Públicas, y su herramienta de apoyo **PILAR**, del CCN. Origen del vocabulario activo–amenaza–vulnerabilidad–riesgo–salvaguarda–riesgo residual. |
| `[WPA3]` | **Wi-Fi Alliance**, *WPA3 Specification*. **SAE** (autenticación simultánea de iguales) y cifrado individualizado en redes abiertas. |

---

## Tier 2 — Informes, hojas de ruta y documentación de estado

| ID | Referencia |
|---|---|
| `[ENISA-ETL]` | **ENISA**, *Threat Landscape 2025* (octubre de 2025). Datos citados, verificados en la publicación oficial: **4.875 incidentes** analizados entre el **1 de julio de 2024 y el 30 de junio de 2025**; el **DDoS** supone el **77 %** de los incidentes notificados pero solo el **2 %** provocó interrupción real; el **ransomware** es la amenaza de mayor impacto en la UE; **phishing (60 %)** y **explotación de vulnerabilidades (21,3 %)** son los dos vectores de acceso inicial dominantes; y a principios de 2025 **más del 80 %** de la ingeniería social observada en el mundo se apoyaba en contenido generado o mejorado con **IA**. |
| `[PQC-EU]` | **Grupo de Cooperación NIS** y Comisión Europea, *Coordinated Implementation Roadmap for the Transition to Post-Quantum Cryptography*, **23 de junio de 2025**. Tres hitos: **31-12-2026** (hojas de ruta nacionales y primeros pasos), **31-12-2030** (casos de uso de **alto riesgo** transicionados) y **31-12-2035** (transición completa en la medida de lo posible). |
| `[MS-EOL]` | **Microsoft**, *Windows 10 support has ended on October 14, 2025* y *Extended Security Updates (ESU) program for Windows 10*. El soporte de Windows 10 finalizó el **14 de octubre de 2025**; el programa **ESU** proporciona únicamente actualizaciones **críticas e importantes**, sin correcciones funcionales ni soporte técnico, hasta el **12 de octubre de 2027**. |
| `[CCN-CERT]` | **CCN-CERT**, avisos, informes de código dañino e informes de amenazas y tendencias. Junto con **INCIBE-CERT**, es la fuente de vigilancia a la que remite `op.exp.4.1` («seguimiento continuo de los anuncios de defectos»). |
| `[OWASP]` | **OWASP Top 10:2025**. Citado únicamente como catálogo de referencia de los ataques que mitiga un **WAF**; el desarrollo seguro de aplicaciones web corresponde al **Tema 23**. |
| `[CPSTIC-WEB]` | Portal del **CPSTIC** del Centro Criptológico Nacional, con el listado vivo de productos cualificados por familia. Es la fuente que hay que consultar en el momento de redactar un pliego, porque el catálogo se actualiza periódicamente. |

---

## Tier 3 — Contexto municipal

| ID | Referencia |
|---|---|
| `[IAM]` | **Informática del Ayuntamiento de Madrid (IAM)**, organismo autónomo responsable de los sistemas de información municipales. Marco organizativo de todos los ejemplos y casos prácticos de este tema. |
| `[MADRID-SEDE]` | **Sede electrónica del Ayuntamiento de Madrid** y portal `madrid.es`. Servicio publicado que sirve de referencia en §2.4.1 y en el Caso 1. |
| `[BOAM-10032]` | **BOAM núm. 10.032**, convocatoria y temario oficial de la categoría de **Técnico Auxiliar de Informática** del Ayuntamiento de Madrid. Fuente del enunciado oficial de este tema y de las referencias cruzadas a los Temas 23, 27, 28, 29, 30, 31, 32, 33, 34, 35 y 37. |

---

## Tier 4 — Consultadas y NO utilizadas

Se dejan constancia de fuentes revisadas que finalmente **no** se han empleado como respaldo, para que la validación pueda comprobar el criterio:

- **Documentación comercial de fabricantes de cortafuegos, VPN y EDR**. Descartada como fuente: el temario debe ser **neutral respecto al producto**, y la capa de producto es volátil. Cuando hace falta una referencia de selección, la correcta es el **CPSTIC** (`op.pl.5`) y la **CCN-STIC-140**.
- **Términos de mercado sin norma: SASE, SSE, ZTNA, NGFW**. Se mencionan en el contenido porque aparecen en pliegos y en la conversación profesional, pero se advierte expresamente de que **no son estándares**, a diferencia de la NIST SP 800-207, de IPsec o de TLS.
- **WireGuard**. Protocolo VPN muy extendido en la práctica, pero **no tiene RFC**: su especificación es un artículo académico y su implementación de referencia. Por ese motivo no se ha incorporado como contenido examinable, aunque se anota aquí para la validación por si María o el IAM consideran que debe mencionarse.
- **Documentación de la red SARA**. Se cita únicamente como ejemplo de interconexión entre Administraciones; su desarrollo corresponde al **Tema 39** (ENI y ENS) y no a este.
