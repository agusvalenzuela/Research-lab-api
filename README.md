# Research-lab-api

Anita Morales
Agustín Valenzuela

### 🔹 **1. Diferencia entre HTTP y HTTPS**

- Explica qué significa cada sigla.
- Investiga cómo funciona el **cifrado SSL/TLS** en HTTPS.
- ¿Por qué HTTPS es más seguro?
- Muestra un ejemplo visual (puede ser una captura del candado del navegador).
- ¿Qué sucede si un sitio no usa HTTPS?

---

### 🔹 **2. Puertos de comunicación**

- Explica qué es un **puerto** en redes y por qué es importante para HTTP.
- Investiga el propósito de los puertos **80** y **8080**, y qué tipo de tráfico suelen manejar.
- Menciona **otros puertos conocidos** (por ejemplo: 21, 22, 443, 3306) y su función.
- Ejemplo: ¿Qué puerto utiliza HTTPS por defecto?

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
