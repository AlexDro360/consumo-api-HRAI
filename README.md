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

![{B6C46656-4969-4D37-A325-DC805171A372}](https://github.com/user-attachments/assets/80c3981c-1774-4e5c-baa7-61dce15dc308)

Para la creacion de la tabla se crearon las variables displayedColumns que contiene las columnas de la tabla, y otro dataSource que usa la clase MatTableDataSource que contiene los datos de la tabla y facilita el uso de paginacion y filtrado en angular material.

![{75A0726E-1017-4676-BF89-A05695F12AFC}](https://github.com/user-attachments/assets/82650b3a-54e1-446a-80c9-ef22fa11fb95)

El metodo ngOnInit se ejecuta al inicio del componente y ejecuta el metodo del servicio getUsers para obetner los usuario los cuales los almacenan como datos en dataSource para que se muestren en la tabla.

![{A6DBAA2D-7523-4E02-8C5A-92AE3AB8E08C}](https://github.com/user-attachments/assets/e64ad92f-6f85-4acf-88e2-f2fff597c5fb)

El metodo ngAfterView se ejecuta despues de que se cargo toda la vista del componente el cual agrega la funcionalida de paginado y filtro a la tabla.

![{9FCF9696-FCD9-4FC0-863F-8963C3564BC0}](https://github.com/user-attachments/assets/87b323bb-938d-4641-acb6-7063ca3b9761)

El metodo applyFilter es el que realiza el filtrado de la tabla de acuerdo a lo ingresado en el cuadro de texto del html

![{6F0EB624-2DA9-4448-8097-1272AD5816AB}](https://github.com/user-attachments/assets/1b2664e8-46f1-419f-bb46-01f660a5eabd)
![{BA90F7AA-6AC6-43A5-8A3B-0DAB62FA01EE}](https://github.com/user-attachments/assets/8c83997f-a919-4ab5-84e1-3d2dc04a01e6)

En html del componente esta compuesto por un matinput para el filtro, una tabla usando mat-table de angular material la cual recibe el dataSource el cual contiene la lista de usuarios, y un matpaginator para la paginacion, todos componentes de angular material.

para usar el componente se importo en el archivo app.component.ts y se puso como etiqueta en el archivo app.component.html

# Preguntas

### ¿Qué hace el método getUsers en este servicio? 
Este método realiza una petición get al api especificado en apiUrl con la cual que se obtienen los usuarios, después retorna la respuesta del api, es decir, los usuarios.
### ¿Por qué es necesario importar HttpClientModule? 
Permite realizar solicitudes http a servidores externos, en este caso a la api, permite usar los métodos get(), post(), put(), delete(), entre otros.
### ¿Qué función cumple el método ngOnInit en el componente UserListComponent? 
Manda a llamar al método getUser que se declaró en el servicio UserService, y de esta forma obtener los usuarios, después los usuarios devueltos los guarda en el arreglo llamado users para su posterior uso.
### ¿Para qué sirve el bucle *ngFor en Angular? Explica cómo se utiliza en este ejemplo.
Es una herramienta que sirve para iterar en listas y colecciones de datos. En el código lo que hace es iterar sobre el arreglo de users, y para cada elemento o usuario de users (user) se creara una fila en la tabla con la etiqueta <tr> y en la fila se crearán 4 celdas con la etiqueta <td> las cuales contendrán el id, el nombre, el email y el rol respectivamente del usuario actual de la iteración. 
Pese a esto en la realización de la actividad no se uso ya que se optó por usar material designe para el diseño, la cual ya incluye sus propias funciones para llenar la tabla.
### ¿Qué ventajas tiene el uso de servicios en Angular para el consumo de APIs? 
Algunas ventajas que tiene es que nos permite tener un mejor control de la información, además al estar separado de los componentes nos permite una mejor reutilización de código ya que así no es necesario realizar solicitudes http cada que se requiera hacer uso del api, esto también facilita el mantenimiento puesto que permite una mejor organización.
### ¿Por qué es importante separar la lógica de negocio de la lógica de presentación? 
Es importante para lograr una aplicación más mantenible, escalable y flexible, y de esta forma facilitar el desarrollo y mantenimiento de la aplicación.
### ¿Qué otros tipos de datos o APIs podrías integrar en un proyecto como este? 
Se podrían integrar APIs que incluya productos para vender y proveedores para crear un sistema para una tienda online, o una que incluya materias y profesores para una aplicación de gestión de materias de una escuela, todo depende del tipo de software que se creara y el uso que se le dará.

