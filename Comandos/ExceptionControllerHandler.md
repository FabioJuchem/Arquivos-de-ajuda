#### Criar package infraestrutura



e inserir o seguintes códigos.



```
@ControllerAdvicepublic class ExceptionControllerHandler {    
@Autowired    
private HttpExceptionHandler httpExceptionHandler;   

@ExceptionHandler(Exception.class)    
public ResponseEntity handle(Exception e) {       
	return httpExceptionHandler.apply(e);    
	}
}
```