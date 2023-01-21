.insertOne: Para insertar un solo documento.
.insertMany: Para insertar varios documentos.

.updateMany: para autualizar varios documentos
.updateOne: Para actualizar un solo documento

.deleteOne: para eliminar un documento de la coleccion
.deleteMany: Para eliminar varios elementos de la coleccion
.drop: Para eliminar todos los documentos de la coleccion

upsert: Esta condición permite agregar un elemento en un array dentro de un documento. Lo que lo hace especial es que si el documento no existe, este operador lo crea, y si ya existe,  inserta los nuevo elementos del array sobre el documento existente.


el "ObjectId" sirve para buscar por los ID generados automaticamente por MongoDB "ObjID", "$oid", sin ese operador nunca lo encontrara


$set:     Establece el valor del campo en un documento y sirve para actualizar
          Permite agregar o modificar un atributo.
$inc:     incrementa los valores numericos Incrementa el valor del campo por la cantidad especificada
$rename:  Podemos renombrar un atributo sin necesidad de meterme con los valores.
$unset:   Eliminar algun atributo.
$pull:    Permite eliminar elementos a una Array
$push:    Permite agregar elementos a un Array
$pop:     Elimina el elemento dentro de un array colocado indicado el numero de la casilla donde se encuentra
          Ejemeplo:
          db.iot.insertMany([
            { _id: 1, sensor: "A001", date: "2022-01-03", readings: [A,B,C,D] },
          ])

          Estos son los elementos de un Array y estan ubicado de la siguente forma: A = -1, B = 1, C = 2, D = 3
          Si deseao borra el elemento B uso la siguente sintaxis:

          db.iot.updateOne({
            _id: 1,
            sensor: "A001",
            date: "2022-01-03",
          },
          { $pop:{
              readings: 1
            }
          })

$eq:      (igual que) es un Comparison Query Operators (Operadores de consulta de comparación) es para buscar documentos
$ne:      (Diferente que) es un Comparison Query Operators (Operadores de consulta de comparación) es para buscar documentos
$gt:      (greater than (>)): Mayor que.
$gte:     (greater than or equal (>=)): Mayor o igual que.
$lt:      (less than (<)): Menor que.
$lte:     (less than or equal (<=)): Menor o igual que.
$regex:   Permite buscar palabra especificar dentro de un documento:
          Buscar parablas que empieza con "ma" = {$regex: /^ma/}
          Buscar parablas que terminen con "ma" = {$regex: /ma$/}
          Buscar parablas que contenga "ma" = {$regex: /ma/}
          Buscar parablas que empieza con "ma" sin importar si es minuscula o mayusculas = {$regex: /ma/i}. La (i) sig. permite mayusculas y minusculas
          Buscar parablas que empieza con "ma" sin importar si es minuscula o mayusculas o si tiene salto de lineas = {$regex: /ma/im]}. la (m) sig. Multilinea
$and:     Une cláusulas de consulta con un AND lógico y devuelve todos los documentos que coinciden con las condiciones de ambas cláusulas
          [{},{},{}] Operarador logico (Y) Incluye A y B
$or:      Une cláusulas de consulta con un OR lógico y devuelve todos los documentos que coinciden con las condiciones de cualquiera de las cláusulas
          [{},{},{}] Operarador logico (O) Incluye A o B
$nor:     Une cláusulas de consulta con un NOR lógico y devuelve todos los documentos que no coinciden con ambas cláusulas
          [{},{},{}] Operarador logico (o No) excluye A o B
$not:     invierte el efecto de una expresión de consulta y devuelve documentos que no coinciden con la expresión de consultada
          [{},{},{}] Operarador logico (NO) No incluya A
$expr:    Permite al usuario expresiones de agregación dentro del lenguaje de consulta

