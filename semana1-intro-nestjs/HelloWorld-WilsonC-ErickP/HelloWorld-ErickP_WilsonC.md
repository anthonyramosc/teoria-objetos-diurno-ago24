# Hello, World! en NestJS
> [!info] Preámbulo
> En el mundo de la programación, el primer `"Hello World"` fue escrito por Brian Kernighan para incluirlo en el manual de usuario de C.
> 
>Se mantiene esta práctica a día de hoy y es el primer objetivo implícito tanto para programadores nuevos como para programadores experimentados que estén entrando a un nuevo lenguaje.

## Requisitos:
Para realizar este proyecto, se asumirá que el usuario tiene comprensión básica del uso de la terminal, aparte de haber leído los siguientes capítulos:
- Instalación / Configuración inicial de NestJS
- Crear un proyecto en NestJS

## Paso 1: Explorar el proyecto 
Cuando se cree el proyecto correctamente navegamos al directorio del proyecto se utiliza el comando:

```
// Nota: bash environment (los comandos para cmd son los mismos)

user@vm:~$ cd nombre-proyecto
user@vm:~/nombre-proyecto$
```

## Paso 2: Creacion de un controlador
Los controladores en NestJS manejan las solicitudesaHTTP, esto se puede hacer un controlador usando el CLI de NestJS ejecutando el siguiente comando:

`nest generate controller hello`

esto crea un controlador llamado hello

## Paso 3: Modificar el controlador
Abre el archivo generado en `src/hello/hello.controller.ts` y se puede modificar para que se vea así: 

```
import { Controller, Get } from '@nestjs/common';

@Controller()
export class HelloController {
  @Get()
  getHello(): string {
    return 'Hello, World!';
  }
}
```

## Paso 4: Editar el puerto
Antes de ejecutar la aplicación, si se tiene otro proyecto de Nest.JS corriendo en segundo plano, por defecto esta aplicación se ejecutará en el puerto `3000`, para cambiar este comportamiento ingresamos a `src/main.ts` de la aplicación que queremos modificar *(en este caso, nuestra app Hello world)*, el archivo por defecto se encuentra de la siguiente manera:

```
import { NestFactory } from '@nestjs/core';

import { AppModule } from './app.module';

  

async function bootstrap() {

const app = await NestFactory.create(AppModule);

await app.listen(3000);

}

bootstrap();
```

Vamos a cambiar el valor numérico de la línea que contiene: `await app.listen(3000)` por cualquier otro valor de 4 digitos, por ejemplo:
`await app.listen(1200)`
Esto nos permitirá ejecutar la aplicación bajo el puerto `1200`
## Paso 5: Ejecutar la aplicación.
Después los cambios realizados en el paso 4 al puerto en nuestra app Hello world, ahora estamos listos para ejecutar la aplicacion en NestJS con el siguiete comando: 

`npm run start`

Esto iniciara el servidor y se podra ver el mensaje `Hello, World!`. Esto se consigue accediendo a: http://localhost:1200 (instrucciones #paso4) desde el navegador

	// hello.controller.ts# 
## Referencias: en este caso, nuestra app Hello world)

- De Roer, D. D., & De Roer, D. D. (2022, 12 junio). Como crear un proyecto con NestJS. Disco Duro de Roer -. https://www.discoduroderoer.es/como-crear-un-proyecto-con-nestjs/

- Medina, R. (2020, 7 julio). Ejemplo con Nestjs. https://www.linkedin.com/pulse/api-con-nestjs-ronny-medina/

- Documentation | NestJS - A progressive Node.js framework. (s. f.). --Documentation | NestJS - A Progressive Node.js Framework. https://docs.nestjs.com/techniques/http-module