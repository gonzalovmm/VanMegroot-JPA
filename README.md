# Proyecto de Persistencia con JPA

**Autor:** Gonzalo Van Megroot  
**Materia:** Desarrollo de Software - Comisión 3K10

## Descripción

Este proyecto demuestra la implementación de persistencia de datos utilizando JPA (Java Persistence API) para manejar transacciones, entidades y relaciones en una base de datos. Se incluyen las entidades `Factura`, `Domicilio`, `Cliente`, `Categoria`, `Articulo` y `DetalleFactura`.

## Funcionalidades principales

- Creación de una factura con detalles de artículos.
- Asociación de artículos con múltiples categorías.
- Manejo de clientes con datos de domicilio.
- Cálculo del total de una factura basada en los artículos y cantidades.

## Estructura del código

El archivo principal es `Main.java`, donde se configuran las transacciones de JPA y se persisten las entidades en la base de datos. Se utilizan los métodos `persist()` para guardar los datos y `flush()` para limpiar las transacciones. En caso de error, se aplica `rollback()` para asegurar la atomicidad.

## Ejecución

1. Clona el repositorio o descarga los archivos.
2. Configura la base de datos y asegúrate de tener un archivo `persistence.xml` con los datos correctos de conexión.
3. Compila y ejecuta el archivo `Main.java`.

## Ejemplo de código

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("example-unit");
EntityManager entityManager = entityManagerFactory.createEntityManager();

Factura factura1 = Factura.builder()
    .numero(11)
    .fecha("2023-01-01")
    .build();

// Transacciones y persistencia de datos
entityManager.persist(factura1);
entityManager.getTransaction().commit();
