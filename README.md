# BASE DE DATOS Agencia de Viajes
Trabajo colaborativo de la materia de Base de Datos.
---

<p>

### ¡Ejercicio 5!

A partir del siguiente enunciado, diseñar una base de datos.

"La agencia desea guardar la siguiente información de los viajeros:
dni, nombre, dirección y teléfono. De cada uno de los viajes que maneja la agencia interesa guardar el código de viaje, número de plazas, fecha en la que se realiza el viaje y otros datos. 

Un viajero puede realizar tantos viajes como desee con la agencia. Un viaje determinado sólo puede ser cubierto por un viajero. Cada viaje realizado tiene un destino y un lugar de origen. De cada uno de ellos se quiere almacenar el código, nombre y otros datos que puedan ser de interés. Un viaje tiene un único lugar de destino y un único lugar de origen".

“Todo viajero debe tener referencias familiares a la agenda de viajes.”


<div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/Captura%20de%20pantalla%202023-04-10%20215610.png" alt="Ejercicio">
</div>

</p>

<br>

---
<details><summary>Consulta 1</summary>
<p>

#### Obtener el nombre del usuario que presto más libros, y la cantidad de veces que presto un libro

```SQL
  select nombre, count(p.idPrestar) as 'Cantidad de veces que presto un libro'
  from usuarios u join prestar p on(u.idUsuario =p.idUsuario)
  group by p.idUsuario
  order by count(p.idPrestar) desc
  limit 1;
```

<div>
  <img src="images/Consulta1.png" alt="Consulta 1">
</div>

</p>
</details>

<br>

---
<details><summary>Consulta 2</summary>
<p>

#### Obtener el nombre de los autores, la cantidad de libros que escribio en un rango de fecha y el titulo de los libros

```SQL
  select a.nombre, count(e.idLibro) as Num_Lib, GROUP_CONCAT(l.titulo SEPARATOR ', ') as "Titulo del libro"
  from autor a left join escribir e on (a.idAutor = e.idAutor)
  right join libros l on (e.idLibro = l.idLibro) WHERE e.dia_mes_anio BETWEEN '2023-01-01' AND '2023-12-31'
  group by a.idAutor
  order by Num_Lib desc;
```

<div>
  <img src="images/Consulta2.png" alt="Consulta 2">
</div>

</p>
</details>

<br>

---
<details><summary>Consulta 3</summary>
<p>

#### Consultar el título y la fecha de los libros prestados en un rango de fecha mediante procedimiento almacenado

```SQL
  delimiter //
  CREATE procedure libros_x_fecha (IN fechaIni date, fechaFin date)
  BEGIN
   SELECT l.titulo, p.fecha_pres
    FROM prestar p JOIN ejemplares e ON (p.idEjemplares = e.idEjemplares)
    JOIN libros l ON (e.id_libros = l.idLibro)
    WHERE p.fecha_pres BETWEEN fechaIni AND fechaFin
    order by p.fecha_pres asc;
  END//
```

<div>
  <img src="images/Consulta3.PNG" alt="Consulta 13">
</div>

</p>
</details>
