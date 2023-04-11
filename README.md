# Agencia de Viajes
Trabajo colaborativo de la materia de Base de Datos.
---

<p>

### ¡Ejercicio 5!

A partir del siguiente enunciado, se diseñara una base de datos.

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
<details><summary>Consultas Basicas</summary>
<p>

#### Mostrar todos los viajes que tiene un determinado viajero:

```SQL
  select v.id, v.nombre
  from viajeros v, viajes vi 
  where v.id = vi.id ;
```
#### Mostrar todos los viajes que tienen un determinado destino:

```SQL
  select vi.*, d.nombre
  from destinos d, viajes vi 
  where d.id = vi.destino_id;
```
#### Mostrar todos los viajes que tienen un determinado Origen:

```SQL
  select vi.*, o.nombre
  from origeness o, viajes vi 
  where o.id = vi.origen_id;
```

</p>
</details>

<br>

---
<details><summary>Consultas Utilizando el Inner Join </summary>
<p>

  #### Mostrar los viajeros con su determinado destino y su fecha en un rango X:

```SQL
  select vi.*, d.nombre
  from destinos d
  join viajes vi on d.id = vi.destino_id
  Where vi.fecha  between "2023-04-02" and "2023-04-06";
```
#### Consulta para mostrar el destino del viajero:

```SQL
  SELECT *
  FROM viajeros vi
  JOIN destinos
  ON vi.id = destinos.id
  WHERE destinos.id = '2';
```
  
</p>
</details>

<br>

---
<details><summary>Consultas Utilizando Varios Inner Join Y Aplicando El CTE</summary>
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
