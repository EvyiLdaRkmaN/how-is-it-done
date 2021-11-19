# SHA-1
Normalimente utilizado para la utentificación, de momento se me biene a la mente **Firebase** cunado se registro el auth con **Google**.

## Como generar un SHA1
Actualmente conozco 2 formas de generarlo una posiblemente mas facil que la otra.

### Generar con android studio
Una ves abierto el proyecto podemos seguir los siguientes pasos para poder realizar la generación del SHA1

1. Click en `Gradle` (Desde el panel lateral derecho, verá Gradle Bar )
2. Click en `Tasks`
3. Click en `Android`
4. Doble click en `signingReport`(Obtendrá SHA-1 y MD5, en la consola de la parte inferior de **Android studio**)

### Generar con `PowerShell` o `CMD`
Esta opción no es complicada pero si un poco mas molesta por que se tiene que ubiscar el `keytool` que biene con la instalación del **SDK de java**.

podemos seguir la siguiente [documentación][1]

Hay dos opciones a ejecutar.
* **modo debug**  
* **modo release**

Generar **modo debug**
1. Ubicamos el `keytool` en la instalación de java y nos posicionamos en el, como en el siguiente ejemplo de `powerShell`

        C:\Program Files\Java\jdk-15.0.2\bin>

2. Tenemos que indicar el `keystore` que suele estar ya creado al instalar Android Studio y el ejemplo de su ruta es como la del comando siguiente

        keytool -list -v -alias androiddebugkey -keystore C:\Users\UserName\.android\debug.keystore

3. Solicitara una clave, por default suele se **android**

Generar **modo release**

Los mismos pasos seguidos anteriormente lo unico que cambia es que tendremos que ubicar la `key.jks` que generamos para nuestro release.

Por lo tanto puede quedar nuestra comando de la siguiente manera

    ​keytool -list -v -alias myAlias -keystore C:/Users/UserName/Documents/my-keystore

Igual nos pedira la contraseña y sera la que nosotros colocamos a la hora de generar la `key.jks`

[1]: https://developers.google.com/android/guides/client-auth