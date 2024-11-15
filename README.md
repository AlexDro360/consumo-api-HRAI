# ConsumoApiHRAI

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 18.2.10.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.dev/tools/cli) page.

# ¿Como se realizó el proyecto?
## Servicio user
Primero se creo el servicio user.service con el comando de CLI `ng generate service services/user`.
![{5CAD6F62-F4E2-4D60-A047-12FA3C9D69CC}](https://github.com/user-attachments/assets/c84f6901-8fce-43ef-8ef7-d8d76aebc930)
Este servicio se usa para obtener los datos de los usuarios del API https://api.escuelajs.co/api/v1/users.
Para el funcionamiento se importo HttpClient la cual permite realizar peticiones http a servidores, este caso la API.
En este servicio se creo el metodo getUsers el cual realiza una peticion GET al API para obtener los datos de los usuarios, posteriormente retorna estos datos obtenidos para que puedan ser usados posteriormente cuando se llame el metodo.

## Componente user list
Se creo un componente user list con el comando `ng generate component components/user-list`
Este componente se encarga de mostrar una tabla con todos los usuarios. 
Como se uso Angular Material para el dieseño se importaron los componentes necesarios para la tabla MatTableDataSource, MatTableModule, ademas se importo el servicio user y los componentes MatPaginator y MatPaginatorModule para agregar paginación y MatSort a la tabla

Para la creacion de la tabla se crearon las variables displayedColumns que contiene las columnas de la tabla, y otro dataSource que usa la clase MatTableDataSource que contiene los datos de la tabla y facilita el uso de paginacion y filtrado en angular material.

El metodo ngOnInit se ejecuta al inicio del componente y ejecuta el metodo del servicio getUsers para obetner los usuario los cuales los almacenan como datos en dataSource para que se muestren en la tabla.

El metodo ngAfterView se ejecuta despues de que se cargo toda la vista del componente el cual agrega la funcionalida de paginado y filtro a la tabla.

El metodo applyFilter es el que realiza el filtrado de la tabla de acuerdo a lo ingresado en el cuadro de texto del html

En html del componente esta compuesto por un matinput para el filtro, una tabla usando mat-table de angular material la cual recibe el dataSource el cual contiene la lista de usuarios, y un matpaginator para la paginacion, todos componentes de angular material.

para usar el componente se importo en el archivo app.component.ts y se puso como etiqueta en el archivo app.component.html


