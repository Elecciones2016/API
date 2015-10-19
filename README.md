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

<table>
  <tr>
    <th>
      URI
    </th>
    <th>
      Request body
    </th>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/</pre>
    </td>
    <td>
      <pre>
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
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      - asistencia: corresponde al porcentaje de asistencia del ultimo semestre. Solo considera sesiones ordinarias, no de comisiones.
      - comiiones: solo comisiones actuales
      - votos: ultimos 5 o 10 votos, solo considera votos de sesiones normales, no de comisiones
    </td>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/:rut</pre>
    </td>
    <td>
      <pre>
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
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      - asistencia: corresponde al porcentaje de asistencia del ultimo semestre. Solo considera sesiones ordinarias, no de comisiones.
      - comiiones: solo comisiones actuales
      - votos: ultimos 5 o 10 votos, solo considera votos de sesiones normales, no de comisiones
    </td>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/:rut/votos</pre>
    </td>
    <td>
      <pre>
        [
          {
            "fecha" : String,
            "tema" : String,
            "voto" : String,
            "partido" : String
          }
        ]
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      - Se puede adicionar opciones de paginación
    </td>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/:rut/comisiones</pre>
    </td>
    <td>
      <pre>
        [
          {
            "nombre" : String,
            "tipo" : String,
            "fecha" : Date,
            "temas" : Integer,
            "asistencia" : Integer,
            "integrantes" : [
              {
                "nombre" : String,
                "rut" : Integer,
                "partido" : String
              }
            ]
          }
        ]
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/:rut/asistencia</pre>
    </td>
    <td>
      <pre>
      [
        {
          "fecha" : Date,
          "lugar" : String,
          "sala" : String,
          "comision" : String,
          "asiste" : Boolean
        }
      ]
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      - se considera todas las sesiones y comisiones a la que esta comprometido el senador, si es una sesion de sala, el atributo "comision" estará vacio, si es una sesión de comisión, el atributo "sala" estará vacio
    </td>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/:rut/sueldo</pre>
    </td>
    <td>
      <pre>
        {
          "dieta" : Integer,
          "descuentos" : Integer,
          "saldo" : Integer
        }
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/comisiones/</pre>
    </td>
    <td>
      <pre>
      [
        {
          "nombre" : String,
          "tipo" : String,
          "fecha" : Date,
          "temas" : Integer,
          "asistencia" : Integer,
          "integrantes" : [
            {
              "nombre" : String,
              "rut" : Integer,
              "partido" : String
            }
          ]
        }
      ]
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      - Debe incluir opciones de paginación
    </td>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/votos</pre>
    </td>
    <td>
      <pre>
        [
          {
            "fecha" : String,
            "senador" : {
              "nombre" : String,
              "rut" : Integer
            },
            "tema" : String,
            "voto" : String,
            "partido" : String
          }
        ]
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      - Se puede adicionar opciones de paginación
    </td>
  </tr>
  <tr>
    <td>
      <pre>GET /senadores/asistencia</pre>
    </td>
    <td>
      <pre>
      [
        {
          "fecha" : Date,
          "lugar" : String,
          "sala" : String,
          "comision" : String,
          "asisten" : Integer
        }
      ]
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      - se considera todas las sesiones y comisiones a la que esta comprometido el senador, si es una sesion de sala, el atributo "comision" estará vacio, si es una sesión de comisión, el atributo "sala" estará vacio
      - el campo "asisten" indica el porcentaje de asistencia
    </td>
  </tr>
</table>

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
