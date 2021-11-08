# Configurar auth
## Facebook Android

### Paquetes y configuración de proyecto

**Incorporar paquete** [flutter_facebook_login][1] y seguir los pasos de implementación que muestra el paquete. Tambien podemos seguir los pasos de la documentación de [Facebook Developers][2]

### Generar un hash de clave de desarrollo
Este **hash** es solicitado por facebook developers para poder realizar pruebas de inicio de sesión, se genera uno para desarrollo y otro para lanzamiento(***release***).
#### Requisitos
* **JDK java** instalado
* [openssl-for-windows][3]
* Instalación de Android studio

#### Pasos windows
1. ubicar debug.keystore ubicado normalmente en ``C:\Users\User\.android`` 
2. ubicar keytool.exe que biene con la instalación del **jdk**, de java ubicado en la siguiente ruta: ``C:\Program Files\Java\jdk-15 0.2\bin``
3. Obtener la ruta de **openssl.exe** ejemplo: ``C:\Users\User\Downloads\software\Generate hash\bin``
4. abrir la **consola** o **powerShel**
5. Movernos hasta la ruta de **keytool.exe** ``C:\Program Files\Java\jdk-15.0.2\bin``
6. sustituir las rutas por las propias y ejecutar el comando para generar el **hash** deseado
7. Pedira una contraseña en este caso usamos: **android**

#### MODO DEBUG(conectado a la pc que genera la clave)      
**opcion sin comillas**

``keytool -exportcert -alias androiddebugkey -keystore "C:\Users\Richard\.android\debug.keystore" | C:\Users\Richard\Downloads\software\GenerateHash\bin\openssl sha1 -binary | C:\Users\Richard\Downloads\software\GenerateHash\bin\openssl base64``

**opción con comillas**

`keytool -exportcert -alias androiddebugkey -keystore "C:\Users\Richard\.android\debug.keystore" | "C:\Users\Richard\Downloads\software\GenerateHash\bin\openssl" sha1 -binary | "C:\Users\Richard\Downloads\software\GenerateHash\bin\openssl" base64`

      
#### Modo RELEASE
      
`keytool -exportcert -alias himnia -keystore C:\Users\Richard\Documents\Trabajo\himnia\keystore-himnia-letra.jks | C:\Users\Richard\Downloads\software\GenerateHash\bin\openssl sha1 -binary | C:\Users\Richard\Downloads\software\GenerateHash\bin\openssl base64`

#### NOTA
*las rutas en ocaciones puede ir entre comillas dobles `"`.
en algunas ocaciones funciona mejor en cmd, por que para powershell puede que requiera de una mejor
configuración del path*

## Donde colocar `meta-data`?
Cuando seguimos la documentación de [Facebook Developers][2] nos encontramos con un punto en el que nos dice:
> Agrega el siguiente elemento `meta-data`

Eso se agrega en el archivo `AndroidManifest.xml` que suele encontrarse en `Android/app/src/main/AndroidManifest.xml`, ahí antes del cierre de `application` colocamos el código que nos da de ejemplo la documentación

[1]: https://pub.dev/packages/flutter_facebook_login
[2]: https://developers.facebook.com/docs/facebook-login?locale=es_ES
[3]: https://code.google.com/archive/p/openssl-for-windows/downloads