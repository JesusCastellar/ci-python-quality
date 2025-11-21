// Cómo identificar fallos de linter, pruebas y cobertura en logs.
Para detectar un error del linter reviso la seccion donde se ejecuta flake8 y Cuando hay un problema, el run aparece como fallido viendode se esta manera:
❌ Failure - Main Run Linter (flake8)
src/calculator.py:3:5: E306 expected 1 blank line...
entonces ahy identifico la ruta del archivo y la linea exacta que esta reportando el flake8 y tambien el tipo de error

Si una prueba falla, en los logs aparece un AssertionError o el detalle del fallo dentro del bloque de FAILURES de esta manera:
E   AssertionError
=================================== FAILURES ===================================
Cuando esto pasa el job termina:
❌ Failure - Main Run Tests
esto lo que quiere decir es que alguna prueba no paso correctamente y por ultimo cuando hay un fallo de cobertura por debajo de lo establecido en la configuracion busco el mensaje de identificacion del coverage, entonces si no cumple se ve asi 
Coverage FAIL: 65% < 80% minimum
❌ Failure - Main Fail if coverage < 80% 
asi identifico que la pipeline esta fallando especificamente por no alcanzar el porcentaje minimo requerido


//- Generar un run fallido y uno exitoso y explicar la diferencia.

en el Run fallido El pipeline se detuvo en el paso "Run Linter" tambien Se muestran errores E302 y E306 y por el orden no se ejecutan los pasos siguientes
pero en el run exitoso todos los pasos aparecen como Success siendo la cobertura 95%, por encima del umbral asi que esta bien y sigue el proceso, entonces el pipeline llega al final con Job succeeded