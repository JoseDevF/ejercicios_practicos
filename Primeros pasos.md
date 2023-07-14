# Primeros pasos

### Para realizar los ejercicios de Express.js, necesitarás seguir los siguientes pasos para configurar tu entorno de desarrollo:

1. **Instalación de Node.js:** 
   - Descarga e instala Node.js desde el sitio oficial: [https://nodejs.org](https://nodejs.org).
   - Sigue las instrucciones de instalación para tu sistema operativo.

2. **Creación de un proyecto de Express.js:**
   - Abre una terminal o línea de comandos.
   - Navega hasta la ubicación donde deseas crear tu proyecto.
   - Ejecuta el siguiente comando para crear un nuevo proyecto de Express.js:
     ```shell
     npx express-generator my-express-app
     ```
     *Nota: "my-express-app" es el nombre de tu aplicación, puedes cambiarlo a tu preferencia.*
   - Accede al directorio de tu aplicación:
     ```shell
     cd my-express-app
     ```

3. **Instalación de dependencias:**
   - Ejecuta el siguiente comando para instalar las dependencias del proyecto:
     ```shell
     npm install
     ```

4. **Configuración del servidor de desarrollo:**
   - Abre el archivo `bin/www` en un editor de texto.
   - Modifica la línea `var port = normalizePort(process.env.PORT || '3000');` para establecer el puerto en el valor deseado (por ejemplo, 3000).
   - Guarda los cambios y cierra el archivo.

5. **Ejecución del servidor de desarrollo:**
   - En la terminal, ejecuta el siguiente comando para iniciar el servidor:
     ```shell
     npm start
     ```
   - Verás el mensaje "Servidor escuchando en el puerto 3000" si el servidor se inicia correctamente.

Una vez que hayas configurado tu entorno de desarrollo y ejecutado el servidor de Express.js, puedes proceder a realizar los ejercicios utilizando el código y las instrucciones proporcionadas.
