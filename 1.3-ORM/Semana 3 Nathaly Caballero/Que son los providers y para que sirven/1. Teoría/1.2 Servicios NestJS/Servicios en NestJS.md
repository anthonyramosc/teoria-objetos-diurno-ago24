## Servicios / Services

### ¿Qué es un Servicio?

Los servicios son una pieza esencial de las aplicaciones realizadas con el framework NestJS. Están pensados para **proporcionar una capa de acceso a los datos** que necesitan las aplicaciones para funcionar. Mediante los servicios podemos liberar de código a los controladores y conseguir desacoplar éstos de las tecnologías de almacenamiento de datos que estemos utilizando.

Además, los servicios son clases incluidas dentro del conjunto de **providers**, y tienen la responsabilidad de gestionar el trabajo con los datos de la aplicación. Aparte de descargar de responsabilidad a los controladores, gracias a los servicios podemos:

* Aislar la lógica de negocio en una clase aparte.
* Reutilizar fácilmente el código de trabajo con los datos a lo largo de varios controladores.

Un servicio tiene la responsabilidad de **gestionar el trabajo con los datos de la aplicación**, de modo que realiza las operaciones para obtener esos datos, modificarlos, etc. Es decir, un servicio tiene que ofrecer los métodos adecuados para que los controladores puedan realizar las operaciones necesarias para controlar los datos que necesiten usar.

El siguiente código trata de un servicio llamado **"cats"**:

`cats.service.ts`

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

  findOne(id: number): Cat {
    return this.cats.find(cat => cat.id === id);
  }

  update(id: number, newData: Partial<Cat>): Cat {
    const index = this.cats.findIndex(cat => cat.id === id);
    if (index === -1) {
      throw new Error('Cat not found');
    }
    this.cats[index] = { ...this.cats[index], ...newData };
    return this.cats[index];
  }

  remove(id: number): Cat {
    const index = this.cats.findIndex(cat => cat.id === id);
    if (index === -1) {
      throw new Error('Cat not found');
    }
    const removedCat = this.cats[index];
    this.cats.splice(index, 1);
    return removedCat;
  }
}
```
