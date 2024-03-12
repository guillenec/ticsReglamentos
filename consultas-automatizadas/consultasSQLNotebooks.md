# 📂 consultas AUTOMATIZADAS

En esta sección, encontrarás documentación sobre consultas SQL automatizadas para gestionar el inventario de notebooks.

## ✨ Creación de Consultas

* trae las compus disponibles

  ```sql
  MariaDB [esrn6_tics]> CREATE VIEW   compusDisponibles AS SELECT NumeroSerie,  Marca, Modelo, Procesador, RAM,  Almacenamiento FROM InventarioNotebooks  WHERE Estado = 'disponible';
  Query OK, 0 rows affected (0,002 sec)
  ```

* trae las compus prestadas

  ```sql
  MariaDB [esrn6_tics]> CREATE VIEW   compusPrestadas AS SELECT NumeroSerie,  Marca, Modelo, Procesador, RAM,  Almacenamiento FROM InventarioNotebooks  WHERE Estado = 'prestada';
  Query OK, 0 rows affected (0,002 sec)
  ```

* permite traer por estado

  ```sql
  MariaDB [esrn6_tics]> DELIMITER //
  MariaDB [esrn6_tics]> CREATE PROCEDURE  ObtenerCompusPorEstado(IN estado_param   VARCHAR(20))
      -> BEGIN
      ->     SELECT NumeroSerie, Marca,   Modelo, Procesador, RAM,  Almacenamiento
      ->     FROM InventarioNotebooks
      ->     WHERE Estado = estado_param;
      -> END //
  Query OK, 0 rows affected (0,003 sec)

  MariaDB [esrn6_tics]> DELIMITER ;
  ```

## 🛠 Probando las Consultas Automatizadas

* traemos las prestadas:

  ```sql
  MariaDB [esrn6_tics]> SELECT * FROM   compusPrestadas;
  +--------------+-------+--------- +----------------------------------------- +------+----------------+
  | NumeroSerie  | Marca | Modelo  |  Procesador                              |  RAM  | Almacenamiento |
  +--------------+-------+--------- +----------------------------------------- +------+----------------+
  | AA2852012457 | cx    | SF20GM7 | Intel  (R) Celeron(R) N4020 CPU @ 1.10GHz | 4Gb    | 215Gb          |
  +--------------+-------+--------- +----------------------------------------- +------+----------------+
  1 row in set (0,001 sec)

  MariaDB [esrn6_tics]> 
  ```

* probamos las compus disponibles:

  ```sql
  MariaDB [esrn6_tics]> SELECT * FROM   compusDisponibles;;
  +--------------+--------+---------  +-----------------------------------------  +-------+----------------+
  | NumeroSerie  | Marca  | Modelo  |   Procesador                              |   RAM   | Almacenamiento |
  +--------------+--------+---------  +-----------------------------------------  +-------+----------------+
  | AA0861072998 | cx     | SF20GM7 | Intel (R) Celeron(R) N4020 CPU @ 1.10GHz |   4Gb   | 215Gb          |
  | AA2652012457 | cx     | SF20GM7 | Intel (R) Celeron(R) N4020 CPU @ 1.10GHz |   4Gb   | 215Gb          |
  | AA2852012485 | cx     | SF20GM7 | Intel (R) Celeron(R) N4020 CPU @ 1.10GHz |   4Gb   | 215Gb          |
  
  ```

* traemos por estado , disponible

```sql
MariaDB [esrn6_tics]> call ObtenerCompusPorEstado('disponible');
+--------------+--------+---------+-----------------------------------------+-------+----------------+
| NumeroSerie  | Marca  | Modelo  | Procesador                              | RAM   | Almacenamiento |
+--------------+--------+---------+-----------------------------------------+-------+----------------+
| AA0861072998 | cx     | SF20GM7 | Intel(R) Celeron(R) N4020 CPU @ 1.10GHz | 4Gb   | 215Gb          |
| AA2652012457 | cx     | SF20GM7 | Intel(R) Celeron(R) N4020 CPU @ 1.10GHz | 4Gb   | 215Gb          |
| AA2852012485 | cx     | SF20GM7 | Intel(R) Celeron(R) N4020 CPU @ 1.10GHz | 4Gb   | 215Gb          |
| AA2852012619 | cx     | SF20GM7 | Intel(R) Celeron(R) N4020 CPU @ 1.10GHz | 7.6Gb | 448Gb          |
| AA3852055540 | cx     | SF20GM7 | Intel(R) Celeron(R) N4020 CPU @ 1.10GHz | 4Gb   | 215Gb          |
| AA4027158293 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA6027172947 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA8027082401 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA8027147627 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA8027257270 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA9027067605 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA9027110016 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA9027190308 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA9027193921 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA9027214317 | noblex |         | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
| AA9027255036 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb   | 448Gb          |
+--------------+--------+---------+-----------------------------------------+-------+----------------+
16 rows in set (0,002 sec)

Query OK, 0 rows affected (0,002 sec)

MariaDB [esrn6_tics]> call ObtenerCompusPorEstado('disponible');

```

## 📄 Creación de Procedimientos Almacenados para Registrar un Préstamo

* creacion

  ```sql
  DELIMITER //
  CREATE PROCEDURE RegistrarPrestamo(
      IN num_serie_param VARCHAR(20),
      IN persona_param VARCHAR(100)
  )
  BEGIN
      DECLARE estado_actual VARCHAR(20);
      SELECT Estado INTO estado_actual FROM InventarioNotebooks WHERE NumeroSerie = num_serie_param;
      IF estado_actual = 'disponible' THEN
          UPDATE InventarioNotebooks
          SET Estado = 'prestada', PersonaPrestamo = persona_param
          WHERE NumeroSerie = num_serie_param;
          SELECT 'Préstamo registrado exitosamente.' AS Resultado;
      ELSE
          SELECT 'La laptop no está disponible para préstamo.' AS Resultado;
      END IF;
  END //
  DELIMITER ;
  
  ```

**Nota:**
Este procedimiento realiza las siguientes acciones:

1. Verifica si la compu con el número de serie especificado está actualmente en estado 'disponible'.
2. Si está disponible, actualiza el estado a 'prestada' y registra la información de la persona que ha tomado prestada la laptop.
    Devuelve un mensaje indicando si el préstamo se registró exitosamente o si la laptop no está disponible.

* prueba:

  ```sql
  MariaDB [esrn6_tics]> CALL RegistrarPrestamo('AA9027255036', 'Prestamo de pruebas');
  +------------------------------------+
  | Resultado                          |
  +------------------------------------+
  | Préstamo registrado exitosamente.  |
  +------------------------------------+
  1 row in set (0,003 sec)

  Query OK, 2 rows affected (0,003 sec)

  MariaDB [esrn6_tics]> 
  ```

* verifico:

  ```sql
  MariaDB [esrn6_tics]> select * from compusPrestadas;
  +--------------+--------+---------+-----------------------------------------+------+----------------+
  | NumeroSerie  | Marca  | Modelo  | Procesador                              | RAM  | Almacenamiento |
  +--------------+--------+---------+-----------------------------------------+------+----------------+
  | AA2852012457 | cx     | SF20GM7 | Intel(R) Celeron(R) N4020 CPU @ 1.10GHz | 4Gb  | 215Gb          |
  | AA9027255036 | noblex | SF20BA  | Intel(R) Celeron(R) N3060 CPU @ 1.60GHz | 4Gb  | 448Gb          |
  +--------------+--------+---------+-----------------------------------------+------+----------------+
  2 rows in set (0,001 sec)
  ```

## 📄 Creación de Procedimientos Almacenado para Devolver un Préstamo

* creacion:

  ```sql
  DELIMITER //
  CREATE PROCEDURE DevolverPrestamo(
      IN num_serie_param VARCHAR(20)
  )
  BEGIN
      DECLARE estado_actual VARCHAR(20);
      SELECT Estado INTO estado_actual FROM InventarioNotebooks WHERE NumeroSerie = num_serie_param;
      IF estado_actual = 'prestada' THEN
          UPDATE InventarioNotebooks
          SET Estado = 'disponible', PersonaPrestamo = NULL
          WHERE NumeroSerie = num_serie_param;

          SELECT 'Préstamo devuelto exitosamente.' AS Resultado;
      ELSE
          SELECT 'La laptop no está registrada como prestada.' AS Resultado;
      END IF;
  END //
  DELIMITER ;
  ```

* pruebo:

  ```sql
  MariaDB [esrn6_tics]> CALL DevolverPrestamo('AA9027255036');
  +----------------------------------+
  | Resultado                        |
  +----------------------------------+
  | Préstamo devuelto exitosamente.  |
  +----------------------------------+
  1 row in set (0,003 sec)

  Query OK, 2 rows affected (0,003 sec)
  ```

* verifico:

  ```sql
  MariaDB [esrn6_tics]> select * from compusPrestadas;
  +--------------+-------+---------+-----------------------------------------+------+----------------+
  | NumeroSerie  | Marca | Modelo  | Procesador                              | RAM  | Almacenamiento |
  +--------------+-------+---------+-----------------------------------------+------+----------------+
  | AA2852012457 | cx    | SF20GM7 | Intel(R) Celeron(R) N4020 CPU @ 1.10GHz | 4Gb  | 215Gb          |
  +--------------+-------+---------+-----------------------------------------+------+----------------+
  1 row in set (0,001 sec)

  ```
