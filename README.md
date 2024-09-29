# Informe del Diagrama ER
## 1. Descripción de cada una de las entidades definidas
_ Cliente con Crédito: Representa a los clientes que tienen la posibilidad de realizar compras a crédito. Estos clientes deben estar registrados para poder usar esta opción de pago.
_ Farmacia: Es la entidad que adquiere los medicamentos. Representa a los establecimientos que compran medicamentos a los laboratorios para su venta al público.
_ Medicamento: Es la entidad central que representa los productos farmacéuticos que son vendidos en la farmacia.
_ Laboratorio: Representa a las entidades que fabrican medicamentos.
_ Familia: Es la clasificación a la que pertenece cada medicamento. Puede estar relacionada con grupos de enfermedades o tratamientos específicos.
## 2. Descripción y ejemplos ilustrativos del dominio de cada uno de los atributos de las entidades
_ Cliente con Crédito:
  _ Dato Bancario: Datos relacionados con la cuenta bancaria del cliente. Ejemplo: número de cuenta, banco asociado.
  _ Fecha de Pago: Fecha en la que un cliente realiza la compra de un medicamento. Ejemplo: “29/09/2024”.
_ Farmacia: No se especifican atributos en el diagrama.
_ Medicamento:
  _ Código: Un identificador único del medicamento. Ejemplo: "MED12345".
  _ Nombre: Nombre comercial del medicamento. Ejemplo: "Paracetamol 500mg".
  _ Precio: El valor monetario del medicamento. Ejemplo: 10€.
  _ Fecha de Venta: Fecha en que el medicamento fue vendido. Ejemplo: "15/09/2024".
  _ Unidades Stock: Cantidad de unidades disponibles en inventario. Ejemplo: 100.
  _ Unidades Vendidas: Cantidad de unidades que han sido vendidas. Ejemplo: 50.
_ Laboratorio:
  _ Código: Un identificador único del laboratorio. Ejemplo: "LAB001".
  _ Nombre: Nombre del laboratorio. Ejemplo: "Laboratorios Farmacéuticos XYZ".
  _ Teléfono: Número de contacto del laboratorio. Ejemplo: "922123456".
  _ Dirección Postal: Dirección física del laboratorio. Ejemplo: "Calle 123, Ciudad, País".
  _ Fax: Número de fax del laboratorio. Ejemplo: "922654321".
  _ Persona de Contacto: Persona responsable de las comunicaciones del laboratorio. Ejemplo: "Juan Pérez".
_ Familia:
  _ Enfermedad que se Aplica: Nombre de la enfermedad o dolencia que trata el medicamento. Ejemplo: "Dolor de cabeza", "Gripe".
## 3. Descripción de cada una de las relaciones definidas y sus cardinalidades
_ Compra (Cliente con Crédito - Medicamento):
  _ Cardinalidad: (1,N) Un cliente puede realizar una o varias compras de medicamentos, pero cada compra está asociada a un único cliente.
  _ Ejemplo: Un cliente compra paracetamol y aspirinas en diferentes días.
_ Compra (Medicamento - Cliente con Crédito):
  _ Cardinalidad: (1,N) Un medicamento puede ser comprado por uno o varios clientes.
  _ Ejemplo: El paracetamol fue comprado por diez clientes a lo largo del día.
_ Fabrica (Farmacia - Medicamento):
  _ Cardinalidad: (0,N) La farmacia puede no fabricar o fabricar varios medicamentos.
  _ Ejemplo: La farmacia fabrica las pastillas para el dolor de garganta pero no fabrica el paracetamol.
_ Fabrica (Medicamento - Farmacia):
  _ Cardinalidad: (1,1) Un medicamento es fabricado por una farmacia.
  _ Ejemplo: Las pastillas para el dolor de garganta son fabricadas por la farmacia.
_ Compra (Farmacia - Medicamento - Laboratorio):
  _ Cardinalidad: (0,N) Una farmacia puede comprar uno o ningún medicamento específico de un solo laboratorio a la vez.
  _ Ejemplo: La farmacia compra una caja de aspirinas del laboratorio XYZ.
_ Compra (Medicamento - Laboratorio - Farmacia):
  _ Cardinalidad: (1,1) Un medicamento de un laboratorio es comprado por una farmacia.
  _ Ejemplo: La caja de aspirinas del laboratorio XYZ es comprada por una farmacia.
_ Compra (Laboratorio - Medicamento - Farmacia):
  _ Cardinalidad: (1,N) Un laboratorio puede vender a una farmacia ninguno o algunos medicamentos.
  _ Ejemplo: El laboratorio XYZ vende una caja de aspirinas a una farmacia.
_ Se compone de (Familia - Medicamento):
  _ Cardinalidad: (1,N) Una familia puede estar compuesta por varios medicamentos que afecten a la misma enfermedad.
  _ Ejemplo: Los medicamentos MED1 y MED2 pertenecen a la familia FAM1.
_ Pertenece (Medicamento - Familia):
  _ Cardinalidad: (1,1) Un medicamento pertenece a una única familia farmacéutica.
  _ Ejemplo: El "Ibuprofeno" pertenece a la familia de "Analgésicos".
## 4. Restricciones semánticas
_ Restricción de unicidad en los códigos: Tanto los laboratorios como los medicamentos deben tener códigos únicos para evitar confusión entre diferentes instancias.
_ Unidades en Stock: El valor de las unidades en stock no puede ser negativo.
_ Compatibilidad entre Receta y Medicamento: Los medicamentos que requieren receta no deben ser vendidos sin la misma, por lo que es importante incluir una verificación en el sistema que asegure que los medicamentos de este tipo solo se venden si tienen una receta vinculada.
_ Fechas de Venta y Pago: La fecha de venta de un medicamento debe ser anterior o igual a la fecha de pago en los casos de compras a crédito.
