### Ejemplo de Uso de Providers en NestJS

Aquí hay un ejemplo de cómo utilizar los proveedores en una aplicación NestJS:

#### Definición del Proveedor

```typescript
// cats.service.ts

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

#### Controlador que Utiliza el Proveedor

```typescript
// cats.controller.ts

import { Controller, Get, Post, Body } from '@nestjs/common';
import { CreateCatDto } from './dto/create-cat.dto';
import { CatsService } from './cats.service';
import { Cat } from './interfaces/cat.interface';

@Controller('cats')
export class CatsController {
  constructor(private catsService: CatsService) {}

  @Post()
  async create(@Body() createCatDto: CreateCatDto) {
    this.catsService.create(createCatDto);
  }

  @Get()
  async findAll(): Promise<Cat[]> {
    return this.catsService.findAll();
  }
}
```

#### Ejemplo de Uso en un Módulo

```typescript
// cats.module.ts

import { Module } from '@nestjs/common';
import { CatsController } from './cats.controller';
import { CatsService } from './cats.service';

@Module({
  controllers: [CatsController],
  providers: [CatsService],
})
export class CatsModule {}
```

#### Inyección de Dependencias en un Componente Externo

```typescript
// app.module.ts

import { Module } from '@nestjs/common';
import { CatsModule } from './cats/cats.module';

@Module({
  imports: [CatsModule],
})
export class AppModule {}
```

En este ejemplo, el proveedor `CatsService` es utilizado por el controlador `CatsController` para manejar las solicitudes HTTP relacionadas con los gatos. Luego, el módulo `CatsModule` se importa en el módulo raíz `AppModule` para que los proveedores estén disponibles en toda la aplicación.

Este es solo un ejemplo básico de cómo utilizar los proveedores en NestJS. Puedes combinarlos y organizarlos de muchas formas diferentes según las necesidades de tu aplicación.