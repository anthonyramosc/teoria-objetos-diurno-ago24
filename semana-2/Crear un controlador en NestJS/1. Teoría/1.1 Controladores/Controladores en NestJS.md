## ¿Qué es un controlador?

Los controladores en NestJS son los responsables de manejar las solicitudes entrantes y devolver respuestas al cliente. Actúan como la interfaz entre el cliente y la lógica de la aplicación, recibiendo y procesando los datos de entrada y enviando los datos de salida apropiados.

![](https://thewhitecode.com/public/uploaded_images/9885_2792064606)

Dentro del [Manual de NestJS](https://desarrolloweb.com/manuales/manual-nestjs) se encuentra toda la información acerca de los controladores en NestJS. Al momento de crear una aplicación, **los controladores son una de las piezas principales de las aplicaciones**. Básicamente nos sirven para dar soporte o responder las solicitudes realizadas al servidor. 

El siguiente código es acerca de un controlador llamado '**cats**':

``` typescript
import { Body, Controller, Get, Param, Post, Put } from '@nestjs/common';
import { CreateCatDto } from './dto/create-cat.dto';
import { UpdateCatDto } from './dto/update-cat.dto';
import { Cat } from './entities/cat.entity';
import { CatsService } from './cats.service';

@Controller('cats')
export class CatsController {
  constructor(private readonly catsService: CatsService) {}

  @Get()
  findAll(): Cat[] {
    return this.catsService.findAll();
  }

  @Get(':id')
  findOne(@Param('id') id: string): Cat {
    return this.catsService.findOne(id);
  }

  @Post()
  create(@Body() createCatDto: CreateCatDto): Cat {
    return this.catsService.create(createCatDto);
  }

  @Put(':id')
  update(@Param('id') id: string, @Body() updateCatDto: UpdateCatDto): Cat {
    return this.catsService.update(id, updateCatDto);
  }
}
```

Si quieres saber más a detalle sobre los decoradores y sobre la explicación del ejemplo de arriba, ingresa a  [[Decoradores en NestJS#Explicación de Controlador| Explicación de Controlador]]. 

##### Referencias:
- _Manual de NeSTJS_. (s. f.). DesarrolloWeb.com. https://desarrolloweb.com/manuales/manual-nestjs.