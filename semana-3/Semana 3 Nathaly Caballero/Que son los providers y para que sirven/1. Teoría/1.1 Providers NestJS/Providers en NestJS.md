## ¿Qué es un Provider?

Los **providers** son un concepto fundamental en Nest. Muchas de las clases básicas de Nest pueden tratarse como **providers**: services, repositories, factories, helpers, etc. La idea principal de un proveedor es que se puede inyectar como una dependencia; esto significa que los objetos pueden crear varias relaciones entre sí, y la función de "cablear" estos objetos se puede delegar en gran medida al sistema de ejecución de Nest.

![](https://docs.nestjs.com/assets/Components_1.png)


Dentro de la [Documentación de NestJS](https://docs.nestjs.com/providers) se encuentra toda la información acerca de los providers en NestJS. 

El siguiente código es acerca de un servicio llamado '**cats**':

``` typescript
import { Injectable } from '@nestjs/common';
import { Cat } from './interfaces/cat.interface';

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

---

**Inyección de Dependencias**

Nest está construido en torno al sólido patrón de diseño comúnmente conocido como Inyección de Dependencias. Recomendamos leer un excelente artículo sobre este concepto en la documentación oficial de Angular.

En Nest, gracias a las capacidades de TypeScript, es extremadamente fácil gestionar las dependencias porque se resuelven simplemente por tipo. En el siguiente ejemplo, Nest resolverá el catsService creando y devolviendo una instancia de CatsService (o, en el caso normal de un singleton, devolviendo la instancia existente si ya ha sido solicitada en otro lugar). Esta dependencia se resuelve y se pasa al constructor de tu controlador (o se asigna a la propiedad indicada):

```typescript
constructor(private catsService: CatsService) {}
```
---

## Proveedores Personalizados

Nest tiene un contenedor de inversión de control ("IoC") integrado que resuelve las relaciones entre **providers**. Esta característica subyace en la función de inyección de dependencias. Hay varias formas de definir un proveedor: puedes usar valores simples, clases y fábricas asíncronas o síncronas.

## Proveedores Opcionales

Ocasionalmente, es posible que tengas dependencias que no necesariamente deben ser resueltas. Por ejemplo, tu clase puede depender de un objeto de configuración, pero si no se pasa ninguno, se deben usar los valores predeterminados. En tal caso, la dependencia se vuelve opcional, porque la falta del proveedor de configuración no conduciría a errores.

Para indicar que un proveedor es opcional, utiliza el decorador `@Optional()` en la firma del constructor.

```typescript
import { Injectable, Optional, Inject } from '@nestjs/common';

@Injectable()
export class HttpService<T> {
  constructor(@Optional() @Inject('HTTP_OPTIONS') private httpClient: T) {}
}
```

## Registro de Proveedores

Ahora que hemos definido un proveedor (CatsService) y tenemos un consumidor de ese servicio (CatsController), necesitamos registrar el servicio con Nest para que pueda realizar la inyección. Hacemos esto editando nuestro archivo de módulo (app.module.ts) y agregando el servicio al arreglo de proveedores del decorador @Module().

`app.module.ts`

```typescript
import { Module } from '@nestjs/common';
import { CatsController } from './cats/cats.controller';
import { CatsService } from './cats/cats.service';

@Module({
  controllers: [CatsController],
  providers: [CatsService],
})
export class AppModule {}
```

Ahora, Nest podrá resolver las dependencias de la clase **CatsController**. Así es como debería lucir nuestra estructura de directorios ahora:

```
src/
  cats/
    dto/
      create-cat.dto.ts
    interfaces/
      cat.interface.ts
    cats.controller.ts
    cats.service.ts
  app.module.ts
  main.ts
```
