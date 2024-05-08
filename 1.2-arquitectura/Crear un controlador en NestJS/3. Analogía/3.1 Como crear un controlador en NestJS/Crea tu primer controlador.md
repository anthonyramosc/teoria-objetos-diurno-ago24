Para crear un controlador en NestJS, puedes utilizar el comando:

```cmd
nest generate controller name
```
o también puedes usar una abreviación de la misma, con el comando:

```cmd
nest g co name
```

Antes de crear un controlador, puedes ver las diferentes opciones al momento de crear un controlador en la nota de [[Funcionamiento de los controladores#Comandos CLI para crear un controlador| Comandos CLI para crear un controlador]].

Cualquiera de estos dos comando generará un archivo de controlador con la estructura básica, incluyendo los métodos HTTP (GET, POST, PUT, DELETE) y las rutas correspondientes.

Imagina que estás construyendo una máquina de ensamblaje de automóviles. Cada estación de trabajo (controlador) tiene una función específica, como instalar el motor, ensamblar la carrocería o instalar los neumáticos. Cada estación sigue un proceso estandarizado para garantizar la eficiencia y la calidad del producto final.

## Pasos para crear un controlador

1. **Generar el archivo del controlador utilizando el comando `nest generate controller`:**
   - Este comando de la CLI de NestJS crea el archivo base del controlador, que incluye la estructura básica y los decoradores necesarios.
   - Al ejecutar `nest generate controller cats`, NestJS genera el archivo `cats.controller.ts` con el siguiente contenido:

     ```typescript
     import { Controller, Get } from '@nestjs/common';

     @Controller('cats')
     export class CatsController {
       @Get()
       findAll(): string {
         return 'This action returns all cats';
       }
     }
     ```
   
   - Este archivo contiene la definición de un controlador básico de gatos, con un único método `findAll()` que responde a la ruta `/cats` con el mensaje "This action returns all cats".

2. **Definir las rutas y los métodos HTTP en el controlador:**
   - Dentro del archivo del controlador, puedes agregar más métodos y decorar cada uno de ellos con los decoradores HTTP apropiados, como `@Get()`, `@Post()`, `@Put()`, `@Patch()` y `@Delete()`.
   - Estos decoradores se colocan antes de cada método y definen la ruta y el método HTTP que manejarán.
   - Puedes utilizar parámetros de ruta, como `@Param('id')`, para acceder a los parámetros de la URL.
   - También puedes utilizar decoradores como `@Body()` y `@Query()` para acceder a los datos enviados en el cuerpo y los parámetros de consulta de la solicitud, respectivamente.

3. **Inyectar los servicios necesarios en el controlador:**
   - Los controladores a menudo necesitan acceder a la lógica de negocio, que se suele encapsular en servicios.
   - Para inyectar un servicio en un controlador, debes definir una propiedad privada en el constructor del controlador y marcarla con el decorador `@Injectable()`.
   - Por ejemplo, si tienes un servicio `CatsService`, puedes inyectarlo de la siguiente manera:
     ```typescript
     import { Controller, Get } from '@nestjs/common';
     import { CatsService } from './cats.service';

     @Controller('cats')
     export class CatsController {
       constructor(private readonly catsService: CatsService) {}

       @Get()
       findAll(): any {
         return this.catsService.findAll();
       }
     }
     ```
   - Esto permite que el controlador acceda a los métodos y la lógica definidos en el servicio inyectado.

4. **Implementar la lógica de negocio en los métodos del controlador:**
   - Una vez que has definido las rutas y métodos HTTP, y has inyectado los servicios necesarios, puedes implementar la lógica de negocio en los métodos del controlador.
   - Esto puede incluir la llamada a los métodos del servicio inyectado, la transformación de los datos, la validación de los parámetros de entrada, el manejo de errores, etc.
   - El objetivo es que el controlador se encargue de la interfaz con el cliente (rutas, solicitudes y respuestas HTTP), mientras que la lógica de negocio se mantenga encapsulada en los servicios.

Siguiendo estos cuatro pasos, puedes crear controladores robustos y bien estructurados en tu aplicación NestJS.

Cuando se crea un controlador(cats) en NestJS, se generan los siguientes archivos:

1. **`cats.controller.ts`**
```typescript
import { Controller, Get } from '@nestjs/common';

@Controller('cats')
export class CatsController {
  @Get()
  findAll(): string {
    return 'This action returns all cats';
  }
}
```

2. **`cats.module.ts`**
```typescript
import { Module } from '@nestjs/common';
import { CatsController } from './cats.controller';

@Module({
  controllers: [CatsController]
})
export class CatsModule {}
```

3. **`cats.service.ts`**
```typescript
import { Injectable } from '@nestjs/common';
import { Cat } from './entities/cat.entity';

@Injectable()
export class CatsService {
  private readonly cats: Cat[] = [];

  create(cat: Cat) {
    this.cats.push(cat);
  }

  findAll(): Cat[] {
    return this.cats;
  }
}
```

4. **`cat.entity.ts`**
```typescript
export class Cat {
  id: number;
  name: string;
  breed: string;
}
```

5. **`create-cat.dto.ts`**
```typescript
export class CreateCatDto {
  name: string;
  breed: string;
}
```

6. **`update-cat.dto.ts`**
```typescript
export class UpdateCatDto {
  name?: string;
  breed?: string;
}
```

Estos son los archivos típicos que se generan al crear un controlador en NestJS. Cada archivo tiene una responsabilidad específica.