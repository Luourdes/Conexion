# **TERMINOS MONGODB VS SQL**
______

        **Sql**                   **Mongobd**   
 
        base de datos              Base de datos 
        tabla                      Colecciones
        index                      Index
        fila                       Documentos
        columna                    Campo
        Joins                      Integrados en el documento





## Operaciones de crud 

    Create => (insert) =  insertOne  insertMany
-----
    Read => (select) => *find
----
    Update => (Update)
---
    Delete => (Delete)

 ## **json** 
    Java Script Object Notation: Los datos se separan por clave valor, esto no quiere decir que san clave valor es más de tipo documental 

**estructuras:** 

**{"clave1" : "valor1"}**.

**{"clave2" : {"clave2.1":valor2.1"}}**

**{"clave3" : ["valor3.1","valor3.2","valor3.3"]}**

# COMANDOS Para usar mongosh en mongoDB:
    1. Show dbs o show database (Para ver tus bases de datos creadas).

    2. Use database (sirve para usar una de las bases de datos o para cambiar de BD).

    3. db.createCollection(“nombreDeLaColeccion”) Sirve para crear una nueva colección.

    4. show collections (Es para ver las colecciones que has creado en tu BD).

    5. cls (Para limpiar la pantalla como si fuera el clear).

    6. db.nombreDeLaColeccion.insertOne({  }) Para insertar un documento (SOLO UNO A LA VEZ) por eso es insertONE para insertar muchos es otro comando.

Podemos trabajar en un archivo .json para que sea mas facil hacer el json

Y despues solo copiar ese JSON y pegarlo en mongosh, NO OLVIDAR PONER LOS PARENTESIS y pegar el JSON despues y cerrar el parentesis.

Y asi hago una inserción de un documento con subdocumentos, y con el id personalizado:

    7. db.nombreDeLaColeccion.find() (Es como el select, sirve para ver todos los documentos de una BD)

    8. db.dropDatabase(‘nombreDeLaDataBase’) Sirve para eliminar una base de datos. No hay que estar ubicados en la BD que vamor a eliminar.
    9. db.nombreDeLaColeccion.insertMany([{  }]) Sirve para insertar varios documentos a la vez pero dentro de un arreglo, adentro del ([{ van los documentos.

    10. db.libros.find({ }) Sirve para hacer consultas con filtro

    11. db.libros.find({precio:{$eq:25}}) Sirve para hacer consultas con filtro tambien.

    12. Podemos ver para ver los operadores de consulta en la documentacion: https://www.mongodb.com/docs/manual/reference/operator/query/ 
    13. En este ejemplo agarre un operador de contulta de la documentacion (lt que significa menor que) En esta consulta le digo traeme los documentos en donde cantidad sea menor a 5.

Aquí hago otro ejemplo: Aquí le digo traeme todos los documentos de la colección libros en donde 

    14. Si utilizo findOne solo me trae el primero que encuentre con la condicion que le pedi, por ejemplo aquí le digo: Traeme el primer documento que encuentres en la colección de libros donde precio sea 20 o 25.


    15. Tambien hay consultas con and, su sintaxis es la del ejemplo: Traeme todos los documentos de la colección libros donde precio sea mayor a 25 AND cantidad menor a 15.








Aquí hago lo mismo pero con diferente sintaxis, pero igual es una consulta con AND

    16. En este ejemplo estamos haciendo una consulta con or, decimos que nos traiga todos los documentos de la colección libros


    17. Asi es para hacer una consulta en una colección solo mostrando un campo en este caso solo quiero que me muestre los titulos de los documentos:

    18. Si por ejemplo quiero mostrar solo ciertos campos y que no me muestre el id, la sintaxis es la siguiente:
    19. Aquí le digo que me traiga los documentos de la colección libros en donde el titulo exista.

    20. Aquí le digo que me traiga los documentos de la colección libros en donde el dato del campo precio sea de tipo double.




    21. Update, actualizaciones de un documento: Primero hago la consulta del documento con id 9, en la colección libros.

Ahora Hago la actualizacion: en donde en titulo tenga JSON para todos, y ahora dira Java el rey.

Si consulto de nuevo, ya se hicieron los cambios:


Si con el update queremos modificar un JSON que no tiene el campo que nosotros le dijimos que colocara, lo va a agregar como un nuevo campo:
En este caso agrego el campo de cantidad, antes no lo tenia, pero yo lo coloque en el update.

    22. Actualizar todos los documentos que encuentre:
Quiero actualizar todos los documentos donde el precio sea mayor a 9, lo vamos a actualizar para que precio sea igual a 150 en todos esos documentos.

Ahora si observamos se modificaron varios documentos a 150.

    23. Ahora ocupamos updateMany para decir que en la colección libros quiero que le aumentes a todos los documentos en su precio 5, $inc incrementa el valor de un campo. Si el precio era 150 y le incrementa 5, ahora el precio se actualizo a 155.



    24. Multiplicar el precio por 2 de las cantidades mayores a 20. Aquí con $mul que sirve para multiplicar el valor de un campo. Entonces decimos que en en la colección libros, multiplique por 2 el precio que tengan los documentos que en cantidad tengan un valor mayor a 20.

    25. El updateOne y el updateMany cambia los valores de los cambios o agrega un campo que no existe, pero con el replaceOne cambias los campos existentes en un documento, por ejemplo aquí solo dejo titulo cuando antes tenia mas campos.

    26. Eliminar Documentos(los datos) del campo. Para eso es deleteOne para uno en especifico en este caso con id 10, y si consulto el documento con id 10, ya no se ve nada porque esta eliminado.






Y eso es para eliminar muchos campos con el deleteMany. Aquí le digo que elimine los registros o documentos en donde cantidad sea mayor a 20 y al dar enter me doy cuenta de que elimino 3 registros.

    27. Expresiones Regulares. Aquí digo: Buscar todos los titulos que contengan una t minuscula, hay que ser especifico con mayusculas y minusculas





Traeme todos aquellos en donde en titulo terminen con “tos”. Para eso se ocupa el signo de pesos $

Traeme todos los documentos en donde en el titulo, su nombre comience con M mayuscula, para eso se ocupa ^ (se pone con Altgr + la tecla con su simbolo, se ocupa poner despues una letra para que salga) 


Traeme todos los documentos que en su nombre tengan la palabra para, para eso se ocupa $regex

Aquí le digo, traeme los documentos en donde titulo tengan la parabra MONGO sin importar mayuscular o minusculas, para eso le agregue options: i






    28. Ordenar documentos: Seleccionar todos los documentos de libros pero solo mostrando el titulo y el precio.

Ahora para odenar se ocupa .sort (1 o -1). Aquí le decimos que ordene los titulos de manera ascendente (1)

Aquí le digo que lo haga de manera descendente (-1)




Aquí le digo que me traiga los titulos, precios, y editoriales. Y que ordene los titulos y editoriales de manera ascendente.

    29. Skip (Sirve para saltar algunos documentos al hacer una consulta lo contrario de limit)
En esta consulta usando Skip le digo que se SALTE los primeros 2 documentos, y me traiga los demas. Por lo que no me esta mostrando los primeros 2 documentos.

    30. Size (Sirve para obtener el numero de documentos que tengo  en una BD en base a la consulta que estoy haciendo) se pone despues de un punto (.) despues de la consulta:

Aquí ya ocupo el size: Pido que me traiga cuandos documentos tengo en la collection libros.



    31. Top (Es lo contrario al skip, traer los primeros documentos que yo quiera) En esta consulta me trae los primeros 2 documentos

    32. Drop (Eliminar una colección de una Base de datos): Aquí elimine la colección ejemplo de la base de datos Tienda

    33. DropDatabase (Eliminar una base de datos) Aquí elimino la base de datos de tienda, luego hago un show dbs para ver las BD y ya no aparece tienda.

    
___

``` javascript mongobd

Pipeline 1 
[
  {
    $match:
      /**
       * query: The query in MQL.
       */
      {
        editorial: "Biblio",
      },
  },
  {
    $project:
      /**
       * specifications: The fields to
       *   include or exclude.
       */
      {
        _id: 0,
        titulo: 1,
        precio: 1,
        cantidad: 1,
        "Nombre editorial": "$editorial",
        "Total Ganancia": {
          $multiply: ["$precio", "$cantidad"],
        },
      },
  },
  {
    $sort:
      /**
       * Provide any number of field/order pairs.
       */
      {
        precio: 1,
      },
  },
]

Pipeline 2 con Group:

[
  {
    $group:
      /**
       * _id: The id of the group.
       * fieldN: The first field name.
       */
      {
        _id: "$editorial",
        "Numero Documentos": {
          $count: {},
        },
      },
  },
  {
    $sort:
      /**
       * Provide any number of field/order pairs.
       */
      {
        "Numero Documentos": 1,
      },
  },
]

Pipeline 3:

[
  {
    $group:
      /**
       * _id: The id of the group.
       * fieldN: The first field name.
       */
      {
        _id: "$editorial",
        "Numero de Documentos": {
          $count: {},
        },
        media: {
          $avg: "$precio",
        },
        "Precio Maximo": {
          $max: "$precio",
        },
      },
  },
  {
    $sort:
      /**
       * Provide any number of field/order pairs.
       */
      {
        "Precio Maximo": 1,
      },
  },
]

Pipeline 4 con out:
[
  {
    $group:
      /**
       * _id: The id of the group.
       * fieldN: The first field name.
       */
      {
        _id: "$editorial",
        Numero: {
          $count: {},
        },
        media: {
          $avg: "precio",
        },
      },
  },
  {
    $set:
      /**
       * field: The field name
       * expression: The expression.
       */
      {
        "Media Total": {
          $trunc: ["$media", 2],
        },
      },
  },
  {
    $out:
      /**
       * Provide the name of the output collection.
       */
      "Media_Editoriales",
  },
]

Pipeline 5 con unset y count
[
  {
    $group:
      /**
       * _id: The id of the group.
       * fieldN: The first field name.
       */
      {
        _id: "$editorial",
        Numero: {
          $count: {},
        },
        media: {
          $avg: "precio",
        },
      },
  },
  {
    $set:
      /**
       * field: The field name
       * expression: The expression.
       */
      {
        "Media Total": {
          $trunc: ["$media", 2],
        },
      },
  },
  {
    $unset:
      /**
       * Provide the name of the output collection.
       */
      "media",
  },
]

