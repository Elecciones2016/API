# RESTful api #

Proyecto open source que utilizá la información pública del Gobierno de Chile

## Instalación ##

Para instalar primero es necesario clonar el repositorio

    $ git clone https://github.com/Elecciones2016/API.git

Luego, hay que instalar los modulos de node en la carpeta del proyecto

    $ npm install

Y listo!

## Ejecutar aplicación ##

Para ejecutar la aplicación, hay que correr el servidor node, en el directorio raiz del proyecto

    $ node app.js


### Senadores ###

- `GET /senadores/`

#### Response Body ####

    [
      {
        "nombre" : String,
        "rut" : Integer,
        "region" : "String",
        "circunscripcion" : Integer,
        "telefono" : String,
        "mail" : String,
        "partido": {
          "nombre" : String,
          "siglas" : String,
          "codigo" : Integer
        },
        "asistencia" : Integer,
        "comisiones" : [
          {
            "nombre" : String,
            "tipo" : String,
            "fecha" : Date
          }
        ],
        "votos" : [
          {
            "fecha" : String,
            "tema" : String,
            "voto" : String,
            "partido" : String
          }
        ],
        "sueldo" : Integer
      }
    ]


- `/senadores/:id`
- `/senadores/:id/asistencia`
- `/senadores/:id/comisiones`
- `/senadores/:id/patrimonio`
- `/senadores/:id/sueldosGastos`

### Diputados ###

- `/diputados/`
- `/diputados/:id`
- `/diputados/:id/asistencia`
- `/diputados/:id/comisiones`
- `/diputados/:id/patrimonio`
- `/diputados/:id/sueldosGastos`

### Partidos ###

- `/partidos/`
- `/partidos/:id`

### Presidentes ###

- `/presidentes/`
- `/presidentes/:id`

### Comisiones ###

- `/comisiones/`
- `/comisiones/:id`
- `/comisiones/:id/participantes`
- `/comisiones/:id/votaciones`
- `/comisiones/:id/participantes/votaciones`

### Proyectos ###

- `/proyectos/`
- `/proyectos/:id`
- `/proyectos/:id/votaciones`
