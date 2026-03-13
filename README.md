# 🔐 Glosario de Seguridad en Redes de Comunicaciones

---

### 1. Firewall (Cortafuegos)

**Definición:** Sistema de seguridad de red que monitorea y controla el tráfico de entrada y salida según reglas predefinidas, actuando como barrera entre redes confiables y no confiables.
```

```



> 💼 **Aplicación práctica:** En una empresa, el firewall bloquea conexiones no autorizadas desde Internet, permite solo HTTP/HTTPS y bloquea puertos peligrosos como el 23 (Telnet).

---

### 2. VPN (Red Privada Virtual)

**Definición:** Tecnología que crea un túnel cifrado seguro sobre una red pública, permitiendo acceso remoto a recursos privados de forma segura.
```
[💻 Empleado] ══🔒 TÚNEL VPN CIFRADO 🔒══► [🏢 Servidor Empresarial]
     Casa/Cafetería          Internet              Red Corporativa
```

| Aspecto | Detalle |
|---------|---------|
| Protocolo | OpenVPN / IPSec |
| Cifrado | AES-256 |
| Uso | Teletrabajo seguro |
| Protección | Anti Man-in-the-Middle |

> 💼 **Aplicación práctica:** Un empleado en teletrabajo se conecta a servidores corporativos como si estuviera en la oficina, con comunicación completamente cifrada.

---

### 3. MFA — Autenticación Multifactor

**Definición:** Método de verificación que requiere dos o más factores independientes para confirmar la identidad de un usuario.
```
[1️⃣ Contraseña] ──► [2️⃣ Código OTP] ──► [3️⃣ Huella] ──► ✅ ACCESO
```

| Factor | Ejemplo | Seguridad |
|--------|---------|-----------|
| Algo que **SABES** | Contraseña, PIN | 🟡 Bajo-Medio |
| Algo que **TIENES** | Token, Smartphone | 🟠 Medio-Alto |
| Algo que **ERES** | Huella, Facial | 🟢 Alto |

> 💼 **Aplicación práctica:** Al acceder al banco online, el usuario ingresa contraseña + código OTP en su smartphone, bloqueando accesos no autorizados aunque la contraseña sea robada.

---

### 4. RBAC — Control de Acceso Basado en Roles

**Definición:** Modelo donde los permisos se asignan a roles específicos y los usuarios heredan los permisos del rol asignado.

| Rol | Leer | Escribir | Eliminar | Configurar | Auditar |
|-----|------|----------|----------|------------|---------|
| 👑 Admin | ✅ | ✅ | ✅ | ✅ | ✅ |
| 👨‍💼 Supervisor | ✅ | ✅ | ✅ | ❌ | ✅ |
| 👤 Usuario | ✅ | ✅ | ❌ | ❌ | ❌ |
| 🔍 Auditor | ✅ | ❌ | ❌ | ❌ | ✅ |

> 💼 **Aplicación práctica:** En un hospital, médicos leen y escriben historias clínicas, enfermeras solo leen, y administrativos acceden únicamente a facturación — cumpliendo HIPAA/GDPR.

---

## 🔒 Cifrado

### 5. SSL/TLS

**Definición:** Protocolos criptográficos que proporcionan comunicación segura en Internet usando certificados digitales para autenticar servidores y cifrar el tráfico.
```
CLIENTE                                          SERVIDOR
  │──── 1. ClientHello ───────────────────────────►│
  │◄─── 2. ServerHello + Certificado ──────────────│
  │──── 3. Verificación de Certificado ───────────►│
  │◄─── 4. Intercambio de Claves ──────────────────│
  │════════ 🔒 CANAL CIFRADO AES-256 (Puerto 443) ═│
```

> 💼 **Aplicación práctica:** El candado 🔒 en tu navegador al acceder a `https://` indica SSL/TLS activo, protegiendo credenciales y transacciones de ataques intermediarios.

---

### 6. AES — Advanced Encryption Standard

**Definición:** Algoritmo de cifrado simétrico estándar del gobierno de EE.UU., opera en bloques de 128 bits. Considerado el estándar de oro en cifrado moderno.

| Versión | Tamaño Clave | N° Rondas | Seguridad |
|---------|-------------|-----------|-----------|
| AES-128 | 128 bits | 10 | 🟢 Alto |
| AES-192 | 192 bits | 12 | 🟢 Muy Alto |
| AES-256 | 256 bits | 14 | 🔴 Máximo (Militar) |

> 💼 **Aplicación práctica:** BitLocker (Windows) y FileVault (Mac) usan AES-256 para cifrar discos duros, haciendo ilegible la información si el dispositivo es robado.

---

### 7. PKI — Infraestructura de Clave Pública

**Definición:** Sistema de políticas y tecnologías para crear, gestionar, distribuir y revocar certificados digitales que vinculan claves públicas con identidades verificadas.
```
        🏛️ CA RAÍZ
            │
    ┌───────┼───────┐
    │       │       │
🏢 CA   🏢 CA   🏢 CA
Intermedia Intermedia Intermedia
```

| Componente | Función |
|------------|---------|
| CA | Autoridad que emite certificados |
| RA | Verifica identidad de solicitantes |
| CRL | Lista de certificados revocados |
| OCSP | Verificación en tiempo real |

> 💼 **Aplicación práctica:** Una empresa emite certificados a empleados para firmar documentos electrónicos y autenticarse en sistemas internos, con posibilidad de revocar accesos comprometidos.

---

### 8. Criptografía Asimétrica

**Definición:** Sistema que usa un par de claves matemáticamente relacionadas: clave pública (cifrar) y clave privada (descifrar), basado en problemas matemáticos computacionalmente difíciles.
```
🔑 Clave Pública          🗝️ Clave Privada
  (Compartida)               (Secreta)
       │                         │
📧 "Hola Mundo" ──► 🔒 "x9$K2m#..." ──► 📧 "Hola Mundo"
```

| Característica | Simétrica (AES) | Asimétrica (RSA) |
|----------------|-----------------|------------------|
| Claves | 1 clave | 2 claves (par) |
| Velocidad | 🟢 Muy rápida | 🔴 Lenta |
| Uso típico | Datos grandes | Claves, firmas |
| Ejemplo | AES-256 | RSA-2048, ECC |

> 💼 **Aplicación práctica:** PGP usa criptografía asimétrica: cualquiera cifra con tu clave pública, solo tú descifras con tu clave privada — sin necesidad de compartir secretos previamente.

---

## 👁️ Monitoreo

### 9. IDS/IPS

**Definición:** IDS detecta actividades sospechosas y genera alertas. IPS va más allá bloqueando activamente las amenazas en tiempo real.
```
🔍 IDS (Pasivo)          🛡️ IPS (Activo)
  1. Detecta               1. Detecta
  2. Analiza               2. Analiza
  3. 🚨 Alerta             3. 🚫 BLOQUEA
                           4. 🚨 Alerta
```

| Tipo | Descripción |
|------|-------------|
| NIDS | Network IDS — Monitorea tráfico de red |
| HIDS | Host IDS — Monitorea un sistema específico |
| NIPS | Network IPS — Bloquea amenazas en red |
| HIPS | Host IPS — Bloquea amenazas en el host |

> 💼 **Aplicación práctica:** El IPS detecta un escaneo de puertos masivo desde una IP externa y la bloquea automáticamente durante 24 horas, notificando al equipo de seguridad.

---

### 10. SIEM

**Definición:** Plataforma que centraliza y correlaciona en tiempo real los eventos y logs de múltiples fuentes para detectar amenazas complejas y facilitar la respuesta a incidentes.
```
🔥 Firewall ────┐
🖥️ Servidores ──┤
💻 Endpoints ───┼──► 📊 SIEM CENTRAL ──► 🚨 Alertas
☁️ Cloud ───────┤                    ──► 📈 Dashboards
📱 Mobile ──────┘                    ──► 📋 Reportes
```

| Función | Descripción |
|---------|-------------|
| Correlación | Relaciona eventos de múltiples fuentes |
| Análisis | Detecta comportamientos anómalos |
| Alertas | Notificaciones inteligentes en tiempo real |
| Forense | Soporte para investigación post-incidente |

> 💼 **Aplicación práctica:** El SIEM detecta login fallido desde China + login exitoso desde España 2 minutos después (físicamente imposible), generando alerta crítica de cuenta comprometida.

---

### 11. Análisis de Tráfico de Red

**Definición:** Proceso de captura, inspección y análisis de paquetes para detectar anomalías, comportamientos maliciosos y fugas de datos.

| Origen IP | Destino | Protocolo | Puerto | Estado |
|-----------|---------|-----------|--------|--------|
| 192.168.1.50 | 8.8.8.8 | DNS | 53 | 🟢 Normal |
| 192.168.1.50 | Google | HTTPS | 443 | 🟢 Normal |
| 192.168.1.75 | 45.142.x.x | UNKNOWN | 4444 | 🔴 Sospechoso |

**Indicadores de tráfico anómalo:**
- 🔴 Puertos no estándar (`4444`, `31337`, `12345`)
- 🔴 Tráfico cifrado hacia IPs desconocidas
- 🔴 Volumen excesivo de datos salientes
- 🔴 Patrones repetitivos cada N minutos *(beacon de malware)*

> 💼 **Aplicación práctica:** Con Wireshark se descubre que un equipo envía datos cifrados cada 5 minutos a una IP en Rusia — indicador de malware C&C (Command & Control beacon).

---

### 12. Log de Auditoría

**Definición:** Registro cronológico e inmutable de todas las actividades en un sistema, incluyendo quién hizo qué, cuándo, desde dónde y con qué resultado.

| Timestamp | Usuario | Acción | IP Origen | Resultado |
|-----------|---------|--------|-----------|-----------|
| 2026-03-13 08:15 | jsmith | LOGIN | 192.168.1.10 | ✅ OK |
| 2026-03-13 14:33 | mjones | DELETE | 192.168.1.20 | ✅ OK |
| 2026-03-13 15:45 | unknown | LOGIN_ATTEMPT | 94.23.157.8 | ❌ FAIL |
| 2026-03-13 15:45 | unknown | LOGIN_ATTEMPT | 94.23.157.8 | ❌ FAIL |
| 2026-03-13 15:45 | unknown | LOGIN_ATTEMPT | 94.23.157.8 | ❌ FAIL |

> ⚠️ 3 intentos fallidos consecutivos = **posible ataque de fuerza bruta**

> 💼 **Aplicación práctica:** Tras una brecha, el equipo forense reconstruye exactamente qué archivos accedió el atacante, qué copió y cuánto tiempo estuvo — información crítica para el análisis post-incidente.

---

## ⚠️ Gestión de Amenazas

### 13. DDoS — Denegación de Servicio Distribuida

**Definición:** Ataque que usa múltiples sistemas comprometidos (botnet) para inundar un servidor con tráfico masivo, agotando recursos y haciéndolo inaccesible.
```
🤖 Bot 1 ──┐
🤖 Bot 2 ──┤
🤖 Bot 3 ──┼──► [Miles de peticiones] ──► 🖥️ VÍCTIMA 💥
🤖 Bot N ──┘          ↑
                  [BOTNET C&C]
                  Atacante 👨‍💻
```

| Tipo | Descripción |
|------|-------------|
| 📊 Volumétrico | Inunda con tráfico masivo (UDP/ICMP flood) |
| 🔌 Protocolo | Agota recursos de conexión (SYN flood) |
| 🖥️ Capa Aplicación | Ataca la app web (HTTP flood) |

> 💼 **Mitigación:** CDN (Cloudflare/Akamai) + Rate limiting + Anycast + Filtrado por geolocalización.

---

### 14. Phishing

**Definición:** Técnica de ingeniería social donde el atacante suplanta entidades legítimas para robar credenciales o instalar malware.
```
1️⃣ Email falso       2️⃣ Enlace malicioso      3️⃣ Sitio clonado
banco@baneo.com ──► http://ban-co.xyz ──► [Formulario falso]
     ⚠️ Error              ⚠️ Dominio              ↓
                           sospechoso       4️⃣ Robo de credenciales
```

**Señales de alerta:**
- ⚠️ Errores ortográficos en el dominio del remitente
- ⚠️ Urgencia excesiva: *"Actúe ahora o su cuenta será bloqueada"*
- ⚠️ URLs sospechosas al pasar el cursor
- ⚠️ Solicitud de datos sensibles por email

> 💼 **Contramedidas:** Verificar dominio, gestor de contraseñas, simulacros de phishing para empleados.

---

### 15. Vulnerabilidad Zero-Day

**Definición:** Fallo desconocido para el fabricante sin parche disponible. *"Zero-day"* = los desarrolladores tienen 0 días para corregirlo antes de ser explotado.
```
Día 0      Día 15         Día 30        Día 45
  │           │              │             │
🔍 Atacante  🕵️ Fabricante  ⚙️ Desarrollo  📦 Parche
  descubre    descubre       del parche    publicado
  el fallo    el fallo
  │←──────────────────────────────────────►│
            🚨 ZONA DE PELIGRO (sin protección)
```

**Caso real — Log4Shell (CVE-2021-44228):**

| Fecha | Evento |
|-------|--------|
| 24-Nov-2021 | 🔍 Alibaba descubre la vulnerabilidad |
| 09-Dic-2021 | 📢 Divulgación pública |
| 10-Dic-2021 | 🚨 Millones de intentos de explotación |
| 13-Dic-2021 | 📦 Apache publica parche v2.15.0 |

> 💼 **Mitigación:** Segmentación de red, WAF, monitoreo continuo y aplicación inmediata de parches al ser publicados.
