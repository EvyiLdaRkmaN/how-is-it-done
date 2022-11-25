# Instalar y configurar eslint con prettier para node con typeScript
Para esta instalación y configuración se seguira lo mas posible la documentación oficial de [eslint](1).
Por lo que no especificaremos los pasos de instalación, solamente los puntos mas escenciales para integrar eslint a node


# Configuración de babel
Para su instalación se puede seguir la siguiente recomendación propia de [babel](2).
Para el caso de **nodejs** se requiere una configuración especifica, y va despues de la instalación base de [babel](2).

## Configuración para nodeJs con TypeScript
1. Seguimos las recomendación para configurar de [babel y typeScript](3).
2. Como no necesitamos compatibilidad con navegadores **@babel/preset-env** queda la siguienta manera
    ```json
    "presets": [
        [
          "@babel/preset-env",
          {
            "targets": {
              "node": true
            },
            "useBuiltIns": "usage",
            "corejs": "3.6.5"
          }
        ],
    ]
    ```
3. Para mas información de la configuración de target la puedes encontrar [aquí](4)


## Configurar importaciones de salida de Babel
Dependiendo de la configuración que se utilice con typeScript en el **tsconfig**, suele haber problemas con las importaciones, ya que si se coloca un alias, este suele dar problemas,  por lo que se recomienda la siguiente instalación de [babel-plugin-module-resolver](5).

Seguir la recomendaciones de la documentación de [babel-plugin-module-resolver](5).


## Configurar build para el proyecto
Se especifica el comando a ejecutar, que en este caso sería **babel**, para lo cual necesitamos agregar el script en el `package.json` en la parte de `escripts`. Quedando de la siguiente manera.
```json
"scripts": {
    "start": "set NODE_ENV=production && node build/app.js",
    "dev": "nodemon",
    "build": "babel src --out-dir build --extensions \".ts\"",
    "prepare": "husky install"
},
```



 
[1]: https://eslint.org/docs/latest/user-guide/getting-started
[2]: https://babeljs.io/docs/en/usage
[3]: https://babeljs.io/docs/en/babel-preset-typescript
[4]: https://babeljs.io/docs/en/options#targets
[5]: https://github.com/tleunen/babel-plugin-module-resolver/blob/master/DOCS.md#getting-started