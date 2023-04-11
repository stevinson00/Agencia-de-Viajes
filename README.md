# Agencia de Viajes
Trabajo colaborativo de la materia de Base de Datos.
---

## Integrantes
Abraham Josue Rojas Farelo
---
Stevinson Iguaran Deluque
---
Jose Alfredo Ruedas
---
Maria Elvira Doria 
---

<p>

### ¡Ejercicio 5!

A partir del siguiente enunciado, se diseñara una base de datos.

"La agencia desea guardar la siguiente información de los viajeros:
dni, nombre, dirección y teléfono. De cada uno de los viajes que maneja la agencia interesa guardar el código de viaje, número de plazas, fecha en la que se realiza el viaje y otros datos. 

Un viajero puede realizar tantos viajes como desee con la agencia. Un viaje determinado sólo puede ser cubierto por un viajero. Cada viaje realizado tiene un destino y un lugar de origen. De cada uno de ellos se quiere almacenar el código, nombre y otros datos que puedan ser de interés. Un viaje tiene un único lugar de destino y un único lugar de origen".

“Todo viajero debe tener referencias familiares a la agenda de viajes.”


<div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/Tablas.png" alt="Ejercicio">
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
  
<div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/consulta%201.png" alt="Ejercicio">
</div>
  
#### Mostrar todos los viajes que tienen un determinado destino:

```SQL
  select vi.*, d.nombre
  from destinos d, viajes vi 
  where d.id = vi.destino_id;
```
  
  <div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/consulta%202.png" alt="Ejercicio">
</div>
  
#### Mostrar todos los viajes que tienen un determinado Origen:

```SQL
  select vi.*, o.nombre
  from origeness o, viajes vi 
  where o.id = vi.origen_id;
```
  
<div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/consulta%203.png" alt="Ejercicio">
</div>
  
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
  
 <div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/consulta%204.png" alt="Ejercicio">
</div>
  
#### Consulta para mostrar el destino del viajero:

```SQL
  SELECT *
  FROM viajeros vi
  JOIN destinos
  ON vi.id = destinos.id
  WHERE destinos.id = '2';
```
  
  <div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/consulta%205.png" alt="Ejercicio">
</div>
  
</p>
</details>

<br>

---
<details><summary>Consultas Utilizando Varios Inner Join Y Aplicando El CTE</summary>
<p>

#### Consulta basica utilizando el CTE

```SQL
WITH viajeros_registrados AS (
  SELECT dni, nombre, direccion, telefono
  FROM viajeros
  )
  SELECT * FROM viajeros_registrados;
```
  <div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/Consulta%206.png" alt="Ejercicio">
</div>
  
  #### Consulta el nombre, el destino junto con su fecha:

```SQL
  select vi.id, v.viajeros_id,v.origen_id as Origen, v.destino_id as Destino , v.fecha
  from viajeros vi
  join viajes v  on (vi.id = v.id)
  join destinos d on (v.id = d.id)
  join origeness o on (v.id = o.id)
  Where v.fecha  between "2023-04-02" and "2023-04-06";
```

<div>
  <img src="https://github.com/abram550/Agencia-de-Viajes/blob/main/Imagenes/Consulta%207.png" alt="Ejercicio">
</div>

</p>
</details>
