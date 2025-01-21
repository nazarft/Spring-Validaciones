# Validaciones

## Generales

*NotNull*: especifica que el valor no sea nulo:

```java
@NotNull(message = "El campo no puede ser nulo")
private String name;
```

*NotEmpty*: verifica que la cadena, colección, mapa o array no sea ni nulo ni vacío:

```java
@NotEmpty(message = "El campo no puede estar vacío")
private String email;
```

*NotBlank*: es similar a *NotEmpty* pero ignora también espacios en blanco.
```java
@NotBlank(message = "El campo no puede estar vacío o ser solo espacios en blanco")
private String username;
```

*Size*: restringe la longitud de una cadena o el tamaño de una colección:
```java
@Size(min = 5, max = 20, message = "Debe tener entre 5 y 20 caracteres")
private String password;
```
*Pattern*: valida un campo que siga una expresión regular:
```java
@Pattern(regexp = "^[a-zA-Z0-9]+$", message = "Solo se permiten letras y números")
private String code;
```

## Númericas

*Min*: verifica que el número no sea menor al indicado:

```java
@Min(value = 18, message = "La edad mínima es 18")
private int age;
```

*Max*: verifica que el número no sea mayor al indicado:
```java
@Max(value = 100, message = "La edad máxima es 100")
private int age;
```

*Positive*: verifica que el número sea positivo:
```java
@Positive(message = "El valor debe ser positivo")
private int quantity;
```
*@PositiveOrZero*: que el número sea positivo o cero:

```java
@PositiveOrZero(message = "El valor debe ser positivo o cero")
private int stock;
```
*@Negative*: verifica que el número sea negativo
```java
@Negative(message = "El valor debe ser negativo")
private int balance;
```
*@NegativeOrZero: verifica que sea negativo o cero
```java
@NegativeOrZero(message = "El valor debe ser negativo o cero")
private int debt;
```
@DigitsFut
Restringe el número de digitos de la parte entera y de la decimal:
```java
@Digits(integer = 5, fraction = 2, message = "Máximo 5 dígitos enteros y 2 decimales")
private BigDecimal price;
```

## De fecha y tiempo

*@Past*: verifica que la fecha sea anterior a la fecha actual.
```java
@Past(message = "La fecha debe ser anterior a hoy")
private LocalDate birthDate;
```
*@PastOrPresent*: permite fechas pasadas o la actual:
```java
@PastOrPresent(message = "La fecha no puede ser futura")
private LocalDate createdDate;
```
*@Future*: verifica que la fecha sea posterior a la fecha actual
```java
@Future(message = "La fecha debe ser futura")
private LocalDate eventDate;
```

*@FutureOrPresent*: permite fecha futuras o la actual:
```java
@FutureOrPresent(message = "La fecha no puede ser pasada")
private LocalDateTime bookingDate;
```
## Específicas

*@Email*: verifica que sea un correo válido:
```java
@Email(message = "Debe ser un correo electrónico válido")
private String email;
```
*@URL*: verifica que sea una URL válida:
```java
@URL(message = "Debe ser una URL válida")
private String website;
```

## Combinaciones y personalizadas

*@Valid*: para validad objetos anidados o lista de objetos. Se suele usar en el controlador: 
```java
@Valid
private AddressDTO address;
```

```java
@RestController
public class UserController {

    @PostMapping("/users")
    public String createUser(@Valid @RequestBody UserDTO user) {
        return "Correo válido: " + user.getEmail();
    }
}
```

*@Constraint*: te permite crear anotaciones personailzadas
