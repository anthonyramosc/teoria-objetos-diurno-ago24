### Servicio de Ninjas

En el siguiente ejemplo va a estar una de las principales formas de uso de un servicio, en este caso usando el ejemplo de unos **ninjas**. El servicio de Ninjas maneja el almacenamiento y la recuperación de datos relacionados con los ninjas.

```typescript
import { Injectable } from '@nestjs/common';
import { Ninja } from './interfaces/ninja.interface';

@Injectable()
export class NinjasService {
  private readonly ninjas: Ninja[] = [];

  create(ninja: Ninja) {
    this.ninjas.push(ninja);
  }

  findAll(): Ninja[] {
    return this.ninjas;
  }
}
```

### Interfaz de Ninja

```typescript
// `interfaces/ninja.interface.ts`

export interface Ninja {
  name: string;
  age: number;
  rank: string;
}
```

### Controlador de Ninjas

El controlador de Ninjas maneja las solicitudes HTTP relacionadas con los ninjas.

```typescript
import { Controller, Get, Post, Body } from '@nestjs/common';
import { CreateNinjaDto } from './dto/create-ninja.dto';
import { NinjasService } from './ninjas.service';
import { Ninja } from './interfaces/ninja.interface';

@Controller('ninjas')
export class NinjasController {
  constructor(private ninjasService: NinjasService) {}

  @Post()
  async create(@Body() createNinjaDto: CreateNinjaDto) {
    this.ninjasService.create(createNinjaDto);
  }

  @Get()
  async findAll(): Promise<Ninja[]> {
    return this.ninjasService.findAll();
  }
}
```

### Ejemplo de Uso

```typescript
// Ejemplo de cómo se usarían los servicios y controladores en algún otro lugar de la aplicación
import { NinjasController } from './`ninjas`/ninjas.controller';
import { NinjasService } from './`ninjas`/ninjas.service';

const ninjasController = new NinjasController(new NinjasService());

async function someFunction() {
  const newNinja = { name: 'Hattori Hanzo', age: 35, rank: 'Jonin' };
  await ninjasController.create(newNinja);
  const allNinjas = await ninjasController.findAll();
  console.log(allNinjas);
}

someFunction();
```