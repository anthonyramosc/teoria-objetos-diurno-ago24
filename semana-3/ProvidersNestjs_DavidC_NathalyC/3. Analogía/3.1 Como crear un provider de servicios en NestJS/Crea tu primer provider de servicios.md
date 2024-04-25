### Para crear nuestro primer servicios, debemos seguir los siguientes pasos

## 1. Generar el Servicio

Para construir un servicio podemos usar el CLI de Nest. Para crear la clase de un servicio lanzamos el siguiente comando:

```shell
nest generate service products
```

o

```shell
nest g s products
```

Una vez construido nuestro servicio con el comando anterior podemos apreciar que se crearon los siguientes archivos:

- `products/products.service.ts` -- para el código de la clase del servicio en sí.
- `products/products.service.spec.ts` -- para el código de las pruebas unitarias.

Ambos archivos los situaron dentro de la carpeta `src`, como todo código propio de la aplicación.
## 2. Revisar la importación del servicio

Usualmente se realiza automáticamente la modificación del archivo `app.module.ts`, pero si por algún motivo no está importado nuestro servicio, debemos realizar:

- El import de este servicio
- La declaración del servicio en el array de **providers**

Para hacer esto, debemos modificar el archivo `app.module.ts` de la siguiente manera:

```typescript
@Module({
  imports: [],
  controllers: [AppController, ProductsController],
  providers: [AppService, ProductsService],
})
```


### Servicio sin tests

Si no queremos que se genere el archivo de los test unitarios podemos escribir:

```shell
nest g s products --no-spec
```