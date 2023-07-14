# 10 ejercicios para practicar con Express.js:

1. **Ejercicio: Ruta básica**
   - **Descripción:** Crea una ruta básica que responda a una solicitud HTTP GET con un mensaje de saludo.
   - **Ejemplo:**
     ```javascript
     const express = require('express');
     const app = express();

     app.get('/', (req, res) => {
       res.send('¡Hola, mundo!');
     });

     app.listen(3000, () => {
       console.log('Servidor escuchando en el puerto 3000');
     });
     ```
   - **Prueba:** Abre tu navegador y visita http://localhost:3000 para ver el mensaje de saludo.

2. **Ejercicio: Parámetros de ruta**
   - **Descripción:** Crea una ruta que tome un parámetro en la URL y lo muestre en la respuesta.
   - **Ejemplo:**
     ```javascript
     app.get('/saludo/:nombre', (req, res) => {
       const nombre = req.params.nombre;
       res.send(`¡Hola, ${nombre}!`);
     });
     ```
   - **Prueba:** Visita http://localhost:3000/saludo/Juan en tu navegador y verás el saludo personalizado.

3. **Ejercicio: Consulta de parámetros**
   - **Descripción:** Crea una ruta que tome parámetros de consulta (query parameters) y los muestre en la respuesta.
   - **Ejemplo:**
     ```javascript
     app.get('/buscar', (req, res) => {
       const nombre = req.query.nombre;
       const edad = req.query.edad;
       res.send(`Búsqueda - Nombre: ${nombre}, Edad: ${edad}`);
     });
     ```
   - **Prueba:** Visita http://localhost:3000/buscar?nombre=Juan&edad=25 y verás los parámetros de consulta en la respuesta.

4. **Ejercicio: Middleware personalizado**
   - **Descripción:** Crea un middleware personalizado que registre el tiempo de cada solicitud y lo muestre por consola.
   - **Ejemplo:**
     ```javascript
     const logger = (req, res, next) => {
       console.log(`Tiempo de solicitud: ${new Date().toLocaleTimeString()}`);
       next();
     };

     app.use(logger);
     ```
   - **Prueba:** Cada vez que realices una solicitud al servidor, verás la marca de tiempo en la consola del servidor.

5. **Ejercicio: Envío de formulario**
   - **Descripción:** Crea una ruta que renderice un formulario HTML y otra ruta que maneje la solicitud POST del formulario.
   - **Ejemplo:**
     ```javascript
     app.get('/formulario', (req, res) => {
       res.send(`
         <form method="POST" action="/procesar">
           <input type="text" name="nombre" placeholder="Nombre" />
           <button type="submit">Enviar</button>
         </form>
       `);
     });

     app.post('/procesar', (req, res) => {
       const nombre = req.body.nombre;
       res.send(`¡Hola, ${nombre}!`);
     });
     ```
   - **Prueba:** Visita http://localhost:3000/formulario, ingresa un nombre y haz clic en Enviar para ver el saludo personalizado.

6. **Ejercicio: Archivos estáticos**
   - **Descripción:** Configura una carpeta pública para servir archivos estáticos, como imágenes o archivos CSS.
   - **Ejemplo:**
     ```javascript
     app.use(express.static('public'));
     ```
   - **Prueba:** Coloca un archivo de imagen llamado "imagen.jpg" en la carpeta "public" y luego visita http://localhost:3000/imagen.jpg para ver la imagen.

7. **Ejercicio: Middleware de manejo de errores**
   - **Descripción:** Crea un middleware de manejo de errores para capturar y responder adecuadamente a los errores.
   - **Ejemplo:**
     ```javascript
     const errorHandler = (err, req, res, next) => {
       console.error(err.stack);
       res.status(500).send('Error interno del servidor');
     };

     app.use(errorHandler);
     ```
   - **Prueba:** Introduce un error en una de tus rutas y verás el mensaje de error en la respuesta del servidor.

8. **Ejercicio: Sesiones**
   - **Descripción:** Configura las sesiones para almacenar información del usuario durante sus visitas al sitio web.
   - **Ejemplo:**
     ```javascript
     const session = require('express-session');
     app.use(session({ secret: 'mi_secreto', resave: false, saveUninitialized: true }));

     app.get('/contador', (req, res) => {
       if (req.session.visitas) {
         req.session.visitas++;
       } else {
         req.session.visitas = 1;
       }
       res.send(`Visitas: ${req.session.visitas}`);
     });
     ```
   - **Prueba:** Visita http://localhost:3000/contador y actualiza la página varias veces para ver cómo se incrementa el contador de visitas.

9. **Ejercicio: Autenticación básica**
   - **Descripción:** Implementa una autenticación básica utilizando un middleware para verificar las credenciales del usuario.
   - **Ejemplo:**
     ```javascript
     const basicAuth = require('express-basic-auth');

     app.use(basicAuth({
       users: { admin: '123456' },
       unauthorizedResponse: 'Credenciales inválidas'
     }));

     app.get('/admin', (req, res) => {
       res.send('Bienvenido al área de administración');
     });
     ```
   - **Prueba:** Visita http://localhost:3000/admin y se te pedirá que ingreses las credenciales. Ingresa "admin" como nombre de usuario y "123456" como contraseña para acceder al área de administración.

10. **Ejercicio: Subida de archivos**
    - **Descripción:** Crea una ruta que permita a los usuarios cargar archivos al servidor.
    - **Ejemplo:**
      ```javascript
      const multer = require('multer');
      const upload = multer({ dest: 'uploads/' });

      app.post('/upload', upload.single('archivo'), (req, res) => {
        res.send('Archivo cargado correctamente');
      });
      ```
    - **Prueba:** Crea un formulario HTML con un campo de entrada de tipo "file" que envíe una solicitud POST a http://localhost:3000/upload. Selecciona un archivo y envíalo para ver el mensaje de éxito.
