# Spring에서 전역 예외 처리하기 

## @RestController = @Controller + @ResponseBody

```
// @RestController
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Controller
@ResponseBody
public @interface RestController {
    // ...
}
```

## @RestControllerAdvice = @ControllerAdvice + @ResponseBody
```
// @RestControllerAdvice
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@ControllerAdvice
@ResponseBody
public @interface RestControllerAdvice {
    // ...
}
```

## sample
```
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(LineException.class)
    public ResponseEntity<ErrorResponse> handleLineException(final LineException error) {
        // ...
    }
    
    // ...
}
```
