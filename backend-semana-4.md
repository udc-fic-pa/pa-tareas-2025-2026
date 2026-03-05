# Tareas para la semanas del 9 y 16 de marzo

Después de la clase de teoría del 10 de marzo, habréis adquirido los conocimientos necesarios (tema 4) para implementar la capa de Servicios REST, y consecuentemente, completar el backend. Para comprobar el correcto funcionamiento del backend, debéis emplear un cliente REST (e.g. Postman).

A continuación se comentan algunos aspectos concretos a tener en cuenta.

## Control de acceso

Un aspecto a tener en cuenta es que tanto espectadores como taquilleros deben poder editar la información de perfil y cambiar la contraseña. Para permitirlo, debéis cambiar ligeramente la configuración de base del control de acceso que figura en la clase `SecurityConfig`. Por ejemplo, asumiendo que hayáis modificado `User.RoleType` para que tenga los valores `VIEWER` y `TICKET_SELLER` (en lugar de `USER`), podéis hacer el siguiente cambio en `SecurityConfig`:

```diff
...
			.requestMatchers(HttpMethod.POST, "/users/loginFromServiceToken").permitAll()
-			.requestMatchers(HttpMethod.PUT, "/users/*").hasRole("USER")
-			.requestMatchers(HttpMethod.POST, "/users/*/changePassword").hasRole("USER")
+			.requestMatchers(HttpMethod.PUT, "/users/*").hasAnyRole("VIEWER", "TICKET_SELLER")
+			.requestMatchers(HttpMethod.POST, "/users/*/changePassword").hasAnyRole("VIEWER", "TICKET_SELLER")
			.anyRequest().denyAll();
...
```

Recordad, además, añadir las reglas de control de acceso propias de vuestra práctica.

## Parámetros LocalDate en métodos de controladores

Los grupos que hayáis diseñado el backend para que la recuperación de la cartelera sea con una petición del estilo `GET /catalog/billboard?date=2026-03-20`, podéis hacer que el método del controlador que procese esta petición declare el parámetro `date` de la siguiente manera: 

```java
@RestController
@RequestMapping("/catalog")
public class CatalogController {

	...

    @GetMapping("/billboard")
    public ... getBillboard(@RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate date) throws ... {
        ...
    }

	...

}	
```

La anotación `@DateTimeFormat` sobre el parámetro `date` provocará que el valor del parámetro HTTP `date` se convierta automáticamente a una instancia de `LocalDate`.
