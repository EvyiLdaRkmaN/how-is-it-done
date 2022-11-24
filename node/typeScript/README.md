# configurar Node con typeScript

## Pasos
1. Crear proyecto de node con 

        npm init
    

2. instalar typeScript.

        npm i -D typescript

3. Crear tsconfig.json

        npx tsc --init

4. Instalamos el paquete que mejor se adecue a nuestro proyecto para la configuración de typeScript con node, se puede revisar [aquí](1)
5. De igual manera de ahí se puede obtener la configuración del archivo `tsconfig.json`

## Configuración para ejecutar node con typsScript
La configuración descrita a partir de este punto, es para no tener que compilar el código typeScript y poder realizar mas rapido el desarrollo y la depuración.

1. Instalamos el paquete [ts-node](2). En este punto deberíamos ser capaz de ejecutar nuestro proyecto directamente con typeScript, de la siguiente manera

        npx ts-node src/app.ts

2. **Watching and restarting**: este paso es opcional, pero facilita mucho el tiempo de desarrolllo, ya que cada cambio que realicemos en nuestro archivo, recargará el servicio, lo que evita que tengamos que ejecutar el comando del paso anterior.
    1. Instalamos en este caso [nodemon](3), que nos ayudará a identificar cuando se guarda un archivo y hacer la carga automatica del comando necesario
    2. creamos el archivo `nodemon.json` y configuramos un archivo, para dar mas intrucciones a nodemon de que ejecutar y como.
    Ejemplo:
        ```json
        {
          "watch":[
            "src"
          ],
          "ext":"ts",
          "ignore":[
            "src/**/*.test.ts"
          ],
          "exec": "set NODE_ENV=development&&ts-node src/app.ts"
        }
        ```
    3. Ahora podemos ejecutar el siguiente comando

            nodemon --file nodemon.json

    4. Para facilitar la ejecución de nuestro proyecto, agregaremos los script de ejecución en **package.json** `dev` y `start` para ejecutar de manera mas sencilla, tomar en cuenta que `start` es para un código ya compilado a `javaScript`. Ejemplo: 
        ```json
        "scripts": {
          "dev": "nodemon",
          "start": "set NODE_ENV=production && node build/app.js"
        }
        ```
    5. 






[1]: https://github.com/tsconfig/bases/
[2]: https://typestrong.org/ts-node/docs/installation
[3]: https://github.com/remy/nodemon