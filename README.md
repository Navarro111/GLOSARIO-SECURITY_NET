# 🔐 Glosario de Seguridad en Redes de Comunicaciones
> Mecanismos de Control de Acceso, Cifrado, Monitoreo y Gestión de Amenazas

![Seguridad](https://img.shields.io/badge/Tema-Seguridad%20en%20Redes-1A2B4A?style=for-the-badge)
![Términos](https://img.shields.io/badge/Términos-15-2E75B6?style=for-the-badge)
![Año](https://img.shields.io/badge/Año-2026-green?style=for-the-badge)

---

## 📑 Índice

| Categoría | Términos |
|-----------|----------|
| [🔐 Control de Acceso](#-control-de-acceso) | Firewall, VPN, MFA, RBAC |
| [🔒 Cifrado](#-cifrado) | SSL/TLS, AES, PKI, Criptografía Asimétrica |
| [👁️ Monitoreo](#️-monitoreo) | IDS/IPS, SIEM, Análisis de Tráfico, Log de Auditoría |
| [⚠️ Gestión de Amenazas](#️-gestión-de-amenazas) | DDoS, Phishing, Zero-Day |

---

## 🔐 Control de Acceso

### 1. Firewall (Cortafuegos)

<img src="https://www.conceptdraw.com/How-To-Guide/picture/Network-Security-Diagrams-Solution.png" width="500" alt="Firewall Diagram">

**Definición:** Sistema de seguridad que monitorea y controla el tráfico de red según reglas predefinidas, actuando como barrera entre redes confiables y no confiables.
```
[INTERNET 🌐] ──► [🔥 FIREWALL 🔥] ──► [RED INTERNA 🏢]
```

| Puerto | Protocolo | Acción |
|--------|-----------|--------|
| 80 | HTTP | ✅ ALLOW |
| 443 | HTTPS | ✅ ALLOW |
| 23 | Telnet | ❌ DENY |
| 3389 | RDP | ❌ DENY |

> 💼 **Aplicación práctica:** Bloquea conexiones no autorizadas, permite solo HTTP/HTTPS y bloquea puertos peligrosos como el 23 (Telnet).

---

### 2. VPN (Red Privada Virtual)

<img src="https://www.sanfoundry.com/wp-content/uploads/2023/09/vpn-diagram.png" width="500" alt="VPN Diagram">

**Definición:** Tecnología que crea un túnel cifrado sobre una red pública, permitiendo acceso remoto seguro a recursos privados.
```
[💻 Empleado] ══🔒 TÚNEL VPN CIFRADO 🔒══► [🏢 Servidor]
     Casa                Internet              Empresa
```

| Aspecto | Detalle |
|---------|---------|
| Protocolo | OpenVPN / IPSec |
| Cifrado | AES-256 |
| Uso | Teletrabajo seguro |
| Protección | Anti Man-in-the-Middle |

> 💼 **Aplicación práctica:** El empleado en teletrabajo se conecta a servidores corporativos con comunicación completamente cifrada.

---

### 3. MFA — Autenticación Multifactor

<img src="https://www.imperva.com/learn/wp-content/uploads/sites/13/2019/01/multi-factor-authentication.jpg" width="500" alt="MFA Diagram">

**Definición:** Verificación de identidad que requiere dos o más factores independientes para conceder acceso.
```
[1️⃣ Contraseña] ──► [2️⃣ Código OTP] ──► [3️⃣ Huella] ──► ✅ ACCESO
```

| Factor | Ejemplo | Seguridad |
|--------|---------|-----------|
| Algo que **SABES** | Contraseña, PIN | 🟡 Bajo-Medio |
| Algo que **TIENES** | Token, Smartphone | 🟠 Medio-Alto |
| Algo que **ERES** | Huella, Facial | 🟢 Alto |

> 💼 **Aplicación práctica:** Banca online: contraseña + OTP en smartphone bloquea accesos no autorizados aunque la contraseña sea robada.

---

### 4. RBAC — Control de Acceso Basado en Roles

<img src="https://www.treewebsolutions.com/wp-content/uploads/2021/03/rbac.png" width="500" alt="RBAC Diagram">

**Definición:** Modelo donde los permisos se asignan a roles y los usuarios heredan los permisos del rol asignado.

| Rol | Leer | Escribir | Eliminar | Configurar | Auditar |
|-----|------|----------|----------|------------|---------|
| 👑 Admin | ✅ | ✅ | ✅ | ✅ | ✅ |
| 👨‍💼 Supervisor | ✅ | ✅ | ✅ | ❌ | ✅ |
| 👤 Usuario | ✅ | ✅ | ❌ | ❌ | ❌ |
| 🔍 Auditor | ✅ | ❌ | ❌ | ❌ | ✅ |

> 💼 **Aplicación práctica:** En un hospital, cada rol accede solo a la información que necesita — cumpliendo HIPAA/GDPR.

---

## 🔒 Cifrado

### 5. SSL/TLS

<img src="https://www.cloudflare.com/img/learning/security/glossary/what-is-ssl/ssl-handshake-diffie-hellman.svg" width="500" alt="TLS Handshake">

**Definición:** Protocolos criptográficos que cifran el tráfico entre cliente y servidor usando certificados digitales.
```
CLIENTE                                    SERVIDOR
  │──── 1. ClientHello ──────────────────────►│
  │◄─── 2. ServerHello + Certificado ─────────│
  │──── 3. Verificación ──────────────────────►│
  │════════ 🔒 CANAL CIFRADO (Puerto 443) ═════│
```

> 💼 **Aplicación práctica:** El candado 🔒 en tu navegador indica SSL/TLS activo protegiendo tus datos bancarios.

---

### 6. AES — Advanced Encryption Standard

<img src="https://www.researchgate.net/publication/334925724/figure/fig2/AS:788232836091909@1564969468483/Diagram-of-the-AES-encryption-algorithm.png" width="500" alt="AES Encryption">

**Definición:** Algoritmo de cifrado simétrico estándar del gobierno de EE.UU., considerado el estándar de oro en cifrado moderno.

| Versión | Tamaño Clave | N° Rondas | Seguridad |
|---------|-------------|-----------|-----------|
| AES-128 | 128 bits | 10 | 🟢 Alto |
| AES-192 | 192 bits | 12 | 🟢 Muy Alto |
| AES-256 | 256 bits | 14 | 🔴 Máximo (Militar) |

> 💼 **Aplicación práctica:** BitLocker y FileVault usan AES-256 para cifrar discos duros completos.

---

### 7. PKI — Infraestructura de Clave Pública

<img src="https://www.keyfactor.com/wp-content/uploads/pki-diagram.png" width="500" alt="PKI Hierarchy">

**Definición:** Sistema para crear, gestionar, distribuir y revocar certificados digitales que vinculan claves públicas con identidades verificadas.

| Componente | Función |
|------------|---------|
| CA | Autoridad que emite certificados |
| RA | Verifica identidad de solicitantes |
| CRL | Lista de certificados revocados |
| OCSP | Verificación en tiempo real |

> 💼 **Aplicación práctica:** Las empresas emiten certificados digitales a empleados para firmar documentos y autenticarse en sistemas internos.

---

### 8. Criptografía Asimétrica

<img src="https://sectigo.com/uploads/images/Asymmetric-Encryption.png" width="500" alt="Asymmetric Cryptography">

**Definición:** Sistema con dos claves matemáticamente relacionadas: clave pública (cifrar) y clave privada (descifrar).
```
🔑 Clave Pública       🗝️ Clave Privada
  (Compartida)             (Secreta)
       │                       │
📧 Mensaje ──► 🔒 Cifrado ──► 📧 Mensaje
```

| Característica | Simétrica (AES) | Asimétrica (RSA) |
|----------------|-----------------|------------------|
| Claves | 1 | 2 (par) |
| Velocidad | 🟢 Rápida | 🔴 Lenta |
| Uso típico | Datos grandes | Claves, firmas |

> 💼 **Aplicación práctica:** PGP usa criptografía asimétrica — cualquiera cifra con tu clave pública, solo tú descifras con tu clave privada.

---

## 👁️ Monitoreo

### 9. IDS/IPS

<img src="https://www.thedatasilk.com/wp-content/uploads/2023/01/IDS-IPS-diagram.jpg" width="500" alt="IDS IPS Diagram">

**Definición:** IDS detecta amenazas y alerta. IPS detecta amenazas **y las bloquea** activamente en tiempo real.
```
🔍 IDS (Pasivo)        🛡️ IPS (Activo)
  1. Detecta             1. Detecta
  2. Analiza             2. Analiza
  3. 🚨 Alerta           3. 🚫 BLOQUEA
                         4. 🚨 Alerta
```

| Tipo | Descripción |
|------|-------------|
| NIDS | Monitorea tráfico de red completo |
| HIDS | Monitorea un sistema específico |
| NIPS | Bloquea amenazas a nivel de red |
| HIPS | Bloquea amenazas en el host |

> 💼 **Aplicación práctica:** El IPS detecta un escaneo de puertos masivo y bloquea automáticamente la IP atacante durante 24 horas.

---

### 10. SIEM

<img src="https://www.logsign.com/wp-content/uploads/2021/10/siem-architecture.png" width="500" alt="SIEM Architecture">

**Definición:** Plataforma que centraliza y correlaciona en tiempo real eventos y logs de múltiples fuentes para detectar amenazas complejas.
```
🔥 Firewall ──┐
🖥️ Servidores ─┤
💻 Endpoints ──┼──► 📊 SIEM ──► 🚨 Alertas
☁️ Cloud ──────┤          ──► 📈 Dashboards
📱 Mobile ─────┘          ──► 📋 Reportes
```

> 💼 **Aplicación práctica:** El SIEM detecta login desde China + login desde España con 2 minutos de diferencia → alerta crítica de cuenta comprometida.

---

### 11. Análisis de Tráfico de Red

<img src="https://www.wireshark.org/docs/wsug_html_chunked/images/ws-main.png" width="500" alt="Wireshark Traffic Analysis">

**Definición:** Captura e inspección de paquetes de datos para detectar anomalías, comportamientos maliciosos y fugas de datos.

| IP Origen | Destino | Puerto | Estado |
|-----------|---------|--------|--------|
| 192.168.1.50 | 8.8.8.8 | 53 (DNS) | 🟢 Normal |
| 192.168.1.50 | Google | 443 (HTTPS) | 🟢 Normal |
| 192.168.1.75 | IP Rusa | 4444 | 🔴 Sospechoso |

> 💼 **Aplicación práctica:** Wireshark descubre que un equipo envía datos cada 5 minutos a una IP desconocida — indicador de malware C&C beacon.

---

### 12. Log de Auditoría

<img src="https://www.digicert.com/cms/images/security-benefits-audit-logging.png" width="500" alt="Audit Log">

**Definición:** Registro cronológico e inmutable de todas las actividades del sistema — quién, qué, cuándo, desde dónde y con qué resultado.

| Timestamp | Usuario | Acción | Resultado |
|-----------|---------|--------|-----------|
| 2026-03-13 08:15 | jsmith | LOGIN | ✅ OK |
| 2026-03-13 15:45 | unknown | LOGIN_ATTEMPT | ❌ FAIL |
| 2026-03-13 15:45 | unknown | LOGIN_ATTEMPT | ❌ FAIL |
| 2026-03-13 15:45 | unknown | LOGIN_ATTEMPT | ❌ FAIL |

> ⚠️ 3 intentos fallidos = **posible ataque de fuerza bruta**

> 💼 **Aplicación práctica:** El equipo forense usa logs para reconstruir exactamente qué hizo el atacante tras una brecha de seguridad.

---

## ⚠️ Gestión de Amenazas

### 13. DDoS

<img src="https://www.cloudflare.com/img/learning/ddos/what-is-a-ddos-attack/ddos-attack-traffic-metaphor.png" width="500" alt="DDoS Attack">

**Definición:** Ataque que usa múltiples sistemas comprometidos (botnet) para inundar un servidor hasta hacerlo inaccesible.
```
🤖 Bot 1 ──┐
🤖 Bot 2 ──┤
🤖 Bot 3 ──┼──► [Miles de peticiones] ──► 🖥️ VÍCTIMA 💥
🤖 Bot N ──┘
```

| Tipo | Método |
|------|--------|
| 📊 Volumétrico | UDP/ICMP flood — satura el ancho de banda |
| 🔌 Protocolo | SYN flood — agota conexiones TCP |
| 🖥️ Aplicación | HTTP flood — colapsa la app web |

> 💼 **Mitigación:** Cloudflare CDN + Rate limiting + Anycast + Filtrado por geolocalización.

---

### 14. Phishing

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Phishingposter.svg/800px-Phishingposter.svg.png" width="500" alt="Phishing Attack">

**Definición:** Ingeniería social donde el atacante suplanta entidades legítimas para robar credenciales o instalar malware.
```
1️⃣ Email falso ──► 2️⃣ Link malicioso ──► 3️⃣ Sitio clonado ──► 4️⃣ Robo
banco@baneo.com    http://ban-co.xyz      [Formulario falso]   💳 Datos
```

**Señales de alerta:**
- ⚠️ Errores ortográficos en el dominio
- ⚠️ Urgencia excesiva: *"¡Actúe ahora!"*
- ⚠️ URLs sospechosas al pasar el cursor
- ⚠️ Solicitud de datos sensibles por email

> 💼 **Contramedidas:** Verificar dominio + gestor de contraseñas + simulacros de phishing para empleados.

---

### 15. Vulnerabilidad Zero-Day

<img src="https://www.crowdstrike.com/wp-content/uploads/2021/03/zero-day-attack-explained.png" width="500" alt="Zero Day Vulnerability">

**Definición:** Fallo desconocido para el fabricante sin parche disponible. Los desarrolladores tienen **0 días** para corregirlo antes de ser explotado.
```
Día 0        Día 15          Día 30        Día 45
  │             │               │             │
🔍 Atacante  🕵️ Fabricante   ⚙️ Desarrollo  📦 Parche
  descubre     descubre        del parche    publicado
  │◄──────────────────────────────────────────►│
              🚨 ZONA DE PELIGRO ACTIVO
```

**Caso real — Log4Shell (CVE-2021-44228):**

| Fecha | Evento |
|-------|--------|
| 24-Nov-2021 | 🔍 Alibaba descubre la vulnerabilidad |
| 09-Dic-2021 | 📢 Divulgación pública |
| 10-Dic-2021 | 🚨 Millones de intentos de explotación |
| 13-Dic-2021 | 📦 Apache publica parche v2.15.0 |

> 💼 **Mitigación:** Segmentación de red + WAF + monitoreo continuo + aplicar parches inmediatamente.

---

## 📋 Tabla Resumen

| # | Término | Categoría | Herramienta |
|---|---------|-----------|-------------|
| 1 | Firewall | 🔐 Control Acceso | pfSense, Cisco ASA |
| 2 | VPN | 🔐 Control Acceso | OpenVPN, WireGuard |
| 3 | MFA | 🔐 Control Acceso | Google Auth, FIDO2 |
| 4 | RBAC | 🔐 Control Acceso | Active Directory, AWS IAM |
| 5 | SSL/TLS | 🔒 Cifrado | Let's Encrypt, OpenSSL |
| 6 | AES | 🔒 Cifrado | BitLocker, FileVault |
| 7 | PKI | 🔒 Cifrado | DigiCert, EJBCA |
| 8 | Cript. Asimétrica | 🔒 Cifrado | RSA, ECC, PGP |
| 9 | IDS/IPS | 👁️ Monitoreo | Snort, Suricata |
| 10 | SIEM | 👁️ Monitoreo | Splunk, QRadar |
| 11 | Análisis Tráfico | 👁️ Monitoreo | Wireshark, tcpdump |
| 12 | Log Auditoría | 👁️ Monitoreo | Syslog, ELK Stack |
| 13 | DDoS | ⚠️ Amenazas | Cloudflare, AWS Shield |
| 14 | Phishing | ⚠️ Amenazas | ProofPoint, KnowBe4 |
| 15 | Zero-Day | ⚠️ Amenazas | CVE Database, NVD |

---

## 📚 Bibliografía

1. NIST (2023). *SP 800-53.* https://csrc.nist.gov
2. Stallings, W. (2022). *Cryptography and Network Security* (8th ed.). Pearson.
3. OWASP (2023). *OWASP Top Ten.* https://owasp.org
4. RFC 8446 (2018). *TLS 1.3.* IETF. https://datatracker.ietf.org/doc/html/rfc8446
5. MITRE (2024). *ATT&CK Framework.* https://attack.mitre.org/

---

<div align="center">
  <sub>🔐 Glosario de Seguridad en Redes · 2026 · Navarro111</sub>
</div>
