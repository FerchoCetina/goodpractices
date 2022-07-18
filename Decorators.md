Los decoradores son funciones especiales que reciben casi siempre de parametro una funcion, y retornan otra funcion. 
Una funcion a, recibe una funcion b y retorna una funcion c

    a(b) -> c

Podriamos decirle a una funciona que hacer antes y después de ser ejecutada con una funcion




### Ejemplo:
El siguiente decorador dormira lo segundos que recibe antes de ejecutar la funciona que sea decorada

```python
import time 
def wait_seconds_decorator(seconds):
    """
    This is a decorator for waiting before a function or tasks
    Args:
        seconds: num seconds to waiting before the function

    Returns:
        return the same result that decored function
    """
    def decorator_custom(function):
        def sleep_function(*args,  **kwargs):
            time.sleep(seconds)
            t = function(*args, **kwargs)
            return t
        return sleep_function
    return decorator_custom
    
```

Decoraremos una funcion suma
```python

@wait_seconds_decorator(10)
def suma(n: int, m: int) -> int:
  return n + m
    
```

Esta funciona esperara 10 segundos y despues procedera a ejecutar la funcion suma()
