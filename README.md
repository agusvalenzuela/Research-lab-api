# 🌐 Tarea de investigación
**Nombre:** Agustín Valenzuela y Anita Morales
**Cohorte:** Full Stack Java C22 
**Fecha:** 03 de Noviembre, 2025
---

## 📑 Tabla de Contenidos
1. Diferencia entre HTTP y HTTPS
2. Puertos de comunicación
3. Códigos de estado de respuesta HTTP
4. Métodos HTTP
5. Cabeceras (Headers)

## 1. Diferencia entre HTTP y HTTPS

### ¿Qué significa cada sigla?

**HTTP** 
- HyperText Transfer Protocol (Protocolo de Transferencia de Hipertexto)
- Es el sistema de reglas entre el cliente y el servidor. Es un protocolo entre ambos. Ese intecambio entre cliente y servidor también puede entenderse como un intercambio solicitud y respuesta. HTTP son las normas que regulan ese intercambio.
- Fue creado por Tim Berners-Lee en 1989 bajo el proyecto que dio vida a "www" o World wide Web.
- HTTP se utiliza principalmente para mensajería de internet. Por ejemplo, navegadores como Chrome o Safari utilizan en su sitio web el prefijo "http", para poder conectarse con el servidor.
- El viaje sucede de la siguiente forma: El explorador web envía una solicitud HTTP al servidor que aloja el contenido y ese servidor, enviará también una respuesta HTTP a dicho explorador.

#Fuente: Microsoft Learn

**HTTPS** 
- HyperText Transfer Protocol Secure (Protocolo de Transferencia de Hipertexto Seguro)
- Como lo dice su nombre, es la versión segura de HTTP. La "S" final significa "Secure" (Seguro)
- Su seguridad radica en que la información intercambiada es cifrada, haciéndola ilegible para cualquier otro agente que quiera acceder a dicha información. En otras palabras, el intecambiode información, solo ocurre entre cliente y servidor, volviendo más seguro y protegido el intercambio. Además, asegura que los datos no tengan cambios durante su intercambio. No pueden ser alterados, por lo que es recibido tal cual se envió.
- Utiliza cifrado mediante SSL/TLS para proteger los datos transmitidos porque reconoce quién los envía. Es un reconocimiento de autentificación y por tanto, reduce los riesgos de suplantación y alteración de la información.
- Es reconocido por utilizar un candado visible al costado de la dirección web. Es posible encontrarlo, por ejemplo, en sitios web bancarios.

#Fuente: Banco Santander y su protocolo HTTPS

### ¿Cómo funciona el cifrado SSL/TLS en HTTPS?

El cifrado SSL/TLS funciona mediante un proceso de varias etapas:

1. **Handshake (o apretón de manos)**
   - El cliente (navegador) se conecta al servidor y solicita una conexión segura. Por ejemplo, cuando vas a un banco queriendo hacer un depósito.
   - El servidor envía su certificado SSL/TLS al cliente. Es decir, el banco te muestra su certificación, que es un banco real y confiable, registrado en Chile.
   - El cliente verifica la validez del certificado con una Autoridad Certificadora (CA)1. Handshake (Apretón de manos).  Es como si uno consultara a un amigo que sabe de bancos si efectivamente el banco tiene los permisos de funcionamientos y es legal.

2. **Intercambio de claves**
   - Se establece una clave de sesión única usando criptografía asimétrica. Esta clave será usada para el cifrado simétrico de los datos. 
   - Siguiendo con el caso del banco, antes de generar el depósito, tenemos dos claves diferentes: una pública y una privada: una llega al teléfono antes de la transacción y la otra, es una clave que te dieron al entrar al banco. La idea es identificar y estar de acuerdo que son las personas correctas con un "código secreto" compartido. Una vez acordado, ambos tendrán la misma "clave de sesión". Es como acordar una misma clave que solo entre el banco y uno, entenderemos y solo esta transacción.

3. **Cifrado de datos**
   - Todos los datos transmitidos se cifran con la clave de sesión. Con la clave en común, los datos personales, tarjetas, cuentas, etc. queda solo en la transacción entre el banco y yo.
   - Solo el cliente y el servidor pueden descifrar la información. Si alguien intercepta los datos, solo verá un montón de caracteres sin sentido. O en el caso del banco, no entendería el tipo de transacción que se realizó.


4. **Integridad de datos**
   - Se utilizan códigos de autenticación de mensajes (MAC) para verificar que los datos no han sido alterados. Es como si cada movimiento de la transacción llevara un "sello" matemático (MAC o Message Authentication Code) Es como un código de verificación que confirma: "este mensaje llegó exactamente como se envió". O como si la persona del banco dijera: correcto, cada vez que uno le da un dato para la transacción.

**Diferencia entre SSL y TLS:**
- SSL (Secure Sockets Layer) es el protocolo original, ahora obsoleto
- TLS (Transport Layer Security) es su sucesor más seguro y moderno
- Actualmente se usa TLS, aunque coloquialmente se sigue diciendo "SSL"

### ¿Por qué HTTPS es más seguro?

HTTPS proporciona tres pilares fundamentales de seguridad:

1. **Confidencialidad**
   - Los datos están cifrados, por lo que un atacante no puede leer la información aunque la intercepte. Solo pueden acceder el cliente y el servidor, es ilegible para otros actores.
   - Protege contraseñas, datos bancarios, información personal, etc.

2. **Integridad**
   - Garantiza que los datos no han sido modificados durante la transmisión. Se entrega exactamente como es enviado.
   - Previene ataques de tipo "man-in-the-middle" (intermediario)

3. **Autenticación**
   - El certificado SSL/TLS verifica que estás conectado al servidor correcto. Que te estás relacionando con el sitio web correcto, por ejemplo.
   - Previene suplantación de identidad (phishing)

**Comparación práctica:**
- **HTTP**: Como enviar una postal - cualquiera puede leerla
- **HTTPS**: Como enviar una carta en sobre cerrado y sellado - solo el destinatario puede abrirla

### Ejemplo visual del candado del navegador

Cuando visitas un sitio con HTTPS, verás indicadores de seguridad en tu navegador:

```
🔒 https://www.ejemplo.com
```

**Indicadores de seguridad:**
- ✅ Candado cerrado verde o gris: Conexión segura
- ⚠️ Triángulo de advertencia: Certificado con problemas
- ❌ Sin candado o tachado: Conexión no segura (HTTP). Incluso en algunos navegadores puede indicar "conexión no segura" y uno debe pinchar en que está de acuerdo con seguir el proceso.

**Al hacer clic en el candado puedes ver:**
- Información del certificado
- Entidad emisora del certificado
- Fecha de validez
- Permisos del sitio

### ¿Qué sucede si un sitio no usa HTTPS?

**Riesgos de seguridad:**

1. **Interceptación de datos**
   - Cualquier persona en la misma red puede "escuchar" el tráfico o acceder a la información.
   - Especialmente peligroso en WiFi público y con datos sensibles como los bancarios.

2. **Robo de credenciales**
   - Contraseñas y datos sensibles viajan sin protección. 
   - Facilidad para capturar información de inicio de sesión. Robar claves y acceder a cuentas de otras personas.

3. **Ataques Man-in-the-Middle**
   - Un atacante puede posicionarse entre el usuario y el servidor.
   - Puede modificar el contenido de la página o inyectar código malicioso, por ejemplo, si un sitio web gubernamental fuese alterado con información errónea.

4. **Pérdida de confianza**
   - Los navegadores modernos marcan sitios HTTP como "No seguro".
   - Los usuarios desconfían y pueden abandonar el sitio. No es confiable contratar los servicios de un banco cuyo sitio no sea seguro.

5. **Penalización SEO**
   - Google prioriza sitios HTTPS en los resultados de búsqueda
   - Sitios HTTP tienen menor ranking. 
   - Son sitios penalizados en buscadores como Google, bajando en su lista de opciones o posicionamiento en las búsquedas.

6. **Cumplimiento normativo**
   - Regulaciones como GDPR, PCI DSS requieren HTTPS para proteger datos personales.
   - Puede haber consecuencias legales en algunos países.

**Advertencias de los navegadores:**
- Chrome, Firefox y otros marcan sitios HTTP como "No seguro"
- Algunos navegadores bloquean funcionalidades en sitios HTTP (geolocalización, cámara, etc.)

---

## 2. Puertos de Comunicación

### ¿Qué es un puerto en redes?

Un **puerto** es un número lógico (del 0 al 65535) que identifica un proceso o servicio específico en un dispositivo conectado a una red.

**Analogía práctica:**
- Si la dirección IP es como la dirección de un edificio de apartamentos.
- El puerto es como el número de apartamento específico.
- Permite que múltiples servicios funcionen simultáneamente en el mismo servidor y poder identificar las conexiones, con qué actores se está realizando.

**Importancia para HTTP:**
- Permite que un servidor ejecute múltiples servicios al mismo tiempo.
- Separa el tráfico web de otros servicios (email, FTP, bases de datos, etc.)
- Facilita la configuración de firewalls (o reglas de seguridad).
- Permite ejecutar múltiples aplicaciones web en el mismo servidor

**Formato de conexión:**
```
IP:Puerto
Ejemplo: 192.168.1.100:8080
```

### Puertos 80 y 8080

#### **Puerto 80**
- **Uso**: Puerto estándar para HTTP
- **Tipo de tráfico**: Tráfico web no cifrado
- **Características**:
  - Puerto predeterminado para servidores web
  - No necesita especificarse en la URL (http://ejemplo.com es lo mismo que http://ejemplo.com:80)
  - Puerto "bien conocido" (Well-Known Port)
  - Requiere privilegios de administrador para usarlo en sistemas Unix/Linux

#### **Puerto 8080**
- **Uso**: Puerto alternativo para HTTP
- **Tipo de tráfico**: Tráfico web, generalmente en desarrollo o servicios alternativos
- **Características**:
  - Usado para servidores web alternativos o de desarrollo
  - Común en servidores proxy y aplicaciones web durante desarrollo
  - No requiere privilegios especiales para usarlo
  - Debe especificarse explícitamente en la URL: http://ejemplo.com:8080
  - Popular en servidores de aplicaciones (Tomcat, Jenkins, etc.)

**Casos de uso comunes del puerto 8080:**
- Entornos de desarrollo local
- Servidores proxy HTTP
- Aplicaciones que corren sin privilegios de root
- Múltiples servidores web en la misma máquina

### Otros puertos conocidos

| Puerto | Protocolo/Servicio | Función |
|--------|-------------------|---------|
| **21** | FTP | File Transfer Protocol - Transferencia de archivos |
| **22** | SSH | Secure Shell - Acceso remoto seguro a servidores |
| **23** | Telnet | Acceso remoto no seguro (obsoleto) |
| **25** | SMTP | Simple Mail Transfer Protocol - Envío de correos |
| **53** | DNS | Domain Name System - Resolución de nombres de dominio |
| **110** | POP3 | Post Office Protocol - Recepción de correos |
| **143** | IMAP | Internet Message Access Protocol - Gestión de correos |
| **443** | HTTPS | HTTP Seguro - Tráfico web cifrado |
| **3306** | MySQL | Base de datos MySQL |
| **3389** | RDP | Remote Desktop Protocol - Escritorio remoto Windows |
| **5432** | PostgreSQL | Base de datos PostgreSQL |
| **27017** | MongoDB | Base de datos MongoDB |
| **8000** | HTTP Alt | Servidor web alternativo (usado en desarrollo) |
| **8443** | HTTPS Alt | HTTPS alternativo |

**Clasificación de puertos:**
- **0-1023**: Puertos bien conocidos (Well-Known Ports) - Servicios estándar
- **1024-49151**: Puertos registrados - Aplicaciones específicas
- **49152-65535**: Puertos dinámicos/privados - Uso temporal

### Ejemplo: ¿Qué puerto utiliza HTTPS por defecto?

**Respuesta: Puerto 443**

**Detalles:**
- HTTPS utiliza el puerto **443** como estándar predeterminado
- Al igual que con el puerto 80, no es necesario especificarlo en la URL
- Cuando escribes `https://www.ejemplo.com`, el navegador automáticamente se conecta al puerto 443

**Comparación:**
```
http://www.ejemplo.com      → Puerto 80  (HTTP)
https://www.ejemplo.com     → Puerto 443 (HTTPS)
http://www.ejemplo.com:8080 → Puerto 8080 (HTTP alternativo)
https://www.ejemplo.com:8443 → Puerto 8443 (HTTPS alternativo)
```

**Ventajas del puerto 443:**
- Reconocido universalmente como puerto seguro
- Permitido por la mayoría de firewalls corporativos
- No requiere especificación en URLs
- Soportado por todos los navegadores modernos

---

## Resumen

### HTTP vs HTTPS
- **HTTP** transmite datos sin cifrar (puerto 80)
- **HTTPS** cifra los datos con SSL/TLS (puerto 443)
- HTTPS es **esencial** para proteger información sensible
- Los sitios modernos **deben** usar HTTPS

### Puertos
- Identifican servicios específicos en un servidor
- Permiten múltiples servicios en la misma máquina
- Los puertos estándar (80, 443) no necesitan especificarse
- Los puertos alternativos (8080, 8443) requieren especificación explícita

### Mejores prácticas
✅ Siempre usar HTTPS para sitios en producción  
✅ Verificar el candado de seguridad antes de ingresar datos sensibles  
✅ No confiar en sitios que no usan HTTPS para transacciones  
✅ Configurar correctamente los puertos en servidores y firewalls  
✅ Mantener certificados SSL/TLS actualizados# Research-lab-api

---

### 🔹 **3. Códigos de estado de respuesta HTTP**

- Investiga qué son los **status codes** y para qué sirven.

#### Status Codes

#### ¿Qué son?
Son códigos de estado que los servidores web envían en respuesta a las solicitudes realizadas por los clientes. Estos códigos son respuestas numéricas y son parte del protocolo HTTP e indican el resultado de una solicitud.

#### ¿Para qué sirven?
Son importantes para la comunicación entre clientes y servidores, proporcionan información sobre el resultado de las solicitudes y ayuda a diagnosticar problemas.

- Crea una **tabla organizada por categoría**:


| Categoría | Rango | Descripción general | Ejemplo de código |
| --- | --- | --- | --- |
| **1xx – Informativos** | 100–199 | El servidor recibió la solicitud y continúa el proceso. | 100 Continue |
| **2xx – Éxito** | 200–299 | La solicitud fue procesada correctamente. | 200 OK |
| **3xx – Redirección** | 300–399 | La solicitud fue redirigida a otro recurso. | 301 Moved Permanently |
| **4xx – Error del Cliente** | 400–499 | Error causado por la solicitud del cliente. | 404 Not Found |
| **5xx – Error del Servidor** | 500–599 | El servidor tuvo un problema al procesar la solicitud. | 500 Internal Server Error |
- Luego, profundiza **por qué debemos conocer y reconocer especialmente estos tres códigos:**
    - `200 OK` → cuando todo sale bien.
    - `404 Not Found` → cuando el recurso no existe o fue movido.
    - `500 Internal Server Error` → cuando el problema está en el servidor.

#### Códigos importantes de entender

- Código 200: Este código indica que las solicitud del cliente se procesó con éxito. Es importante porque ya que asegura que los recursos están disponibles y
brinda confianza a los usuarios y desarrolladores. En el caso de que el usuario sea un navegador, si este solicita una pagina web, al recibir el código 200 puede mostrar la página al usuario final. 
Para el caso de depuraciones, el código 200 indica que la parte de la solicitud se maneja bien, lo que permite enfocar la atención en otros puntos en caso de problemas.

- Código 404: señala que el servidor no pudo encontrar el recurso solicitado. Por ejmplo al ingresar mal la URL, por lo tanto, no corresponde a ninguna página válida. Con este código, los desarrolladores pueden crear una página de error personalizado y mejorar la experiencia general. También permite a los motores de búsqueda identificar páginas que ya no existen, lo que permite realizar correcciones necesarias. Y permite comunicar claramente que el recurso no está disponible.

- Código 500: Es un mensaje de error que el servidor ha encontrado un problema inesperado que impide cumplir con la solicitud. El error puede deberse a problemas de configuración, errores en el código de la página, fallos en el servidor de la página o problemas temporales.
Al aparecer indica que el problema es del lado del servidor y no de parte del cliente. Por parte de los motores de búsqueda, este código indica que un sitio web está con problemas de disponibilidad, lo uqe impacta el ranking del sitio en los resultados de búsqueda.

> 💬 Explica con tus palabras cómo podrías usar estos códigos para diagnosticar errores en una API o en un proyecto web.
> 

---

### 🔹 **4. Métodos HTTP**

Investiga los principales métodos HTTP utilizados en APIs RESTful:

- **GET**, **POST**, **PUT**, **DELETE**
    
    y responde:
    
- ¿Qué hace cada uno?
- ¿En qué tipo de operación se usa (consultar, crear, actualizar, eliminar)?
- Agrega un ejemplo práctico de cada uno con una URL o pseudocódigo.

#### Métodos HTTP

#### ¿Qué hace cada uno?

- Método Get: Se utiliza para obtener datos del servidor. 
Ej: GET /index.html HTTP/1.1

- Método Post: Envía datos al servidor para crear o actualizar un recurso.
Ej: POST /contacto HTTP/1.1

- Método Put: Envía datos que reemplazarán el contenido del reurso que se especifica. 
Ej: PUT /usuarios/123 HTTP/1.1
Host: www.ejemplo.com
Content-Type: application/json

{
    "nombre": "Juan Pérez",
    "email": "juan@example.com"
}

- Método Delete: Se usa para borrar datos. Ej: eliminar un artículo de una lista.
Ej: DELETE /articulos/456 HTTP/1.1
Host: www.ejemplo.com

💡 *Bonus:* menciona otros métodos menos comunes como `PATCH`, `HEAD`, `OPTIONS`.

- Método Patch: Actualiza ciertas partes de un recurso, a diferencia del método Put que reemplaza de forma completa

- Método Head: Entrega metainformación  sobre el recurso, como tamaño o tipo de contenido.

- Método Options: Muestra qué métodos HTTP son admitidos por el servidor para un recurso en específico. 

### 🔹 **5. Tema adicional sugerido: Cabeceras (Headers)**

#### ¿Qué son los **headers** en una solicitud HTTP?

Son campos que se envían junto con la solicitud para proporcionar información adicional sobre la misma. Permiten a los clientes y servidores intercambiar metadatos y especificar detalles sobre la solicitud, como el tipo de contenido, la autenticación, el agente del usuario y más.

#### ¿Qué tipo de información contienen (por ejemplo: `Content-Type`, `Authorization`, `User-Agent`)?

Los encabezados se componen de un nombre y un valor, separados por dos puntos. Cada encabezado se encuentra en una nueva línea.

Content-Type: Indica el tipo de contenido que se está enviando en el cuerpo de la solicitud. Ej: Content-Type: application/json

Authorization: Proporciona credenciales para la autenticación (como tokens o credenciales de usuario). Ej: Authorization: Bearer token123

User-Agent:  Identifica el software del cliente (como el navegador o la aplicación) que está realizando la solicitud. Ej: User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)

Accept: Especifica los tipos de contenido que el cliente está dispuesto a recibir (como JSON, HTML, etc.) Ej: Accept: application/json

#### ¿Por qué son importantes al consumir APIs?

Son importantes por varias razones:

- Para autenticar usuarios en que se solicitan tokens o credenciales
- Verificar qué tipo de contenido acepta el cliente
- Para manejar sesiones, pues los headers pueden incluir cookies que mantienen la conexión abierta.



#### Muestra un ejemplo de una solicitud completa con cabeceras incluidas.
