# Tareas para la semana del 23 de febrero

Después de la clase de teoría del 24 de febrero, habréis adquirido los conocimientos necesarios (temas 2 y 3) para implementar la capa Modelo y las pruebas automatizadas de los servicios locales (capa Lógica de Negocio). 

Para la semana del 23 de febrero, os aconsejamos que hagáis las siguientes tareas en la capa Modelo:

- **Tarea 1**: implementación del caso de uso "visualizar la cartelera (FUNC-1)", así como sus pruebas automatizadas.

- **Tarea 2**: implementación del caso de uso "visualizar la información detallada de una sesión (FUNC-3)", así como sus pruebas automatizadas.

- **Tarea 3**: implementación del caso de uso "comprar entradas (FUNC-4)", así como sus pruebas automatizadas.

Un aspecto que tenéis que tener en cuenta es que, a diferencia del enfoque que seguisteis en ISD, la implementación de los casos de uso en los servicios locales no deben realizar validaciones básicas de formato de datos (aquellas que en ISD originaban que se devolviese `InputValidationException`). Por ejemplo, la implementación del caso de uso "comprar entradas" no debe verificar si el número de entradas está entre 1 y 10 o si la tarjeta bancaria tiene un determinado número de caracteres (e.g. 16). Como aprenderéis en el tema 4, este tipo de variaciones las haréis cómodamente desde la capa de servicios REST usando un enfoque declarativo basado en anotaciones. Consecuentemente, las operaciones de los servicios locales no devolverán ninguna excepción del tipo `InputValidationException`.

