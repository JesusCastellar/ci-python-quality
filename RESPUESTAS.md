--------------------------------------------------------------------------------------
// Parte 1 Parte 1 – Estrategia  1. Explicar la diferencia entre CI y CD.
--------------------------------------------------------------------------------------
en una gran conclucion el CI es el encargado de detectar los errores antes de integrar y el CD es el que lleva todo lo probado a produccion entonces el CI seria mas que todo un proceso en el que cada cambio del codigo es integrado, verificado y comprobado automaticamente siedo su objetivo detectar errores rapido y evitar que errores en el codigo llegue al repositorio principal, pero en cambio el CD es especificamente la fase  donde el software probado y validado puede pasar a produccion siendo manual o automaticamente.

--------------------------------------------------------------------------------------
// Parte 1 2. Indicar lenguaje, linter y herramienta de cobertura a utilizar, con justificación.
--------------------------------------------------------------------------------------
para este proyecto utilice lo siguiente
Lenguaje: Python por que para el momento y las pocas horas que nos dieron para el parcial es simple, rapido de configurar y tiene herramientas maduras para pruebas y CI
tambien use Linter, flake8 ya que encontre mucha ayuda en tutoriales de youtube de su implementacion y es un estándar en proyectos Python, detecta errores de estilo, formato y posibles bugs.
para las pruebas unitarias utilice pytest por que me permitio ejecutar pruebas simples y avanzadas con una sintaxis clara y no  muy complicada.

para la Cobertura use coverage.py integrado con pytest (pytest --cov) por que es la herramienta oficial de cobertura en Python, muy compatible con CI

--------------------------------------------------------------------------------------
// Parte 2 – Workflow CI/CD:
--------------------------------------------------------------------------------------
implementada con exito

--------------------------------------------------------------------------------------
// Parte 3 – Uso de nektos/act:
--------------------------------------------------------------------------------------
¿Qué es act? : Este actproyecto es una potente herramienta que puedes usar con GitHub Actions para probar y perfeccionar rápidamente una canalización de integración continua y entrega continua (CI/CD). Con ella act, puedes usar contenedores Docker localmente para ejecutar directamente pasos en GitHub Actions. actPermite a los desarrolladores ejecutar etapas independientes en una canalización y, en general, mejora el ciclo de retroalimentación al crear canalizaciones con GitHub Actions.
Requisitos para usar act: Docker obligatorio por que Act funciona ejecutando los jobs dentro de contenedores, por lo que necesitas:
Docker Desktop (Windows/macOS)
Docker Engine (Linux)
y el comando para ejecutar el workflow localmente es (act).


--------------------------------------------------------------------------------------
// Parte 4 – Cómo identificar fallos de linter, pruebas y cobertura en logs.
--------------------------------------------------------------------------------------

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

--------------------------------------------------------------------------------------
// Parte 4 – Generar un run fallido y uno exitoso y explicar la diferencia.
--------------------------------------------------------------------------------------
en el Run fallido El pipeline se detuvo en el paso "Run Linter" tambien Se muestran errores E302 y E306 y por el orden no se ejecutan los pasos siguientes
pero en el run exitoso todos los pasos aparecen como Success siendo la cobertura 95%, por encima del umbral asi que esta bien y sigue el proceso, entonces el pipeline llega al final con Job succeeded


--------------------------------------------------------------------------------------
// Parte 5 – Parte 5 – IA y Ética:
--------------------------------------------------------------------------------------

- Investigar dos métodos para detectar código generado por IA.
Análisis de código estático
Este es un método que analiza el código fuente antes de ejecutar un programa. El propósito y principal beneficio es identificar problemas o errores antes de ejecutar. El análisis de código estático puede encontrar errores de forma temprana, identificar problemas de seguridad y mejorar la capacidad de mantenimiento, lo que lo convierte en un componente crucial del proceso de revisión de código.
Las herramientas de análisis de código estático pueden analizar el código fuente a nivel de lenguaje de programación, lo que lo hace especialmente útil para bases de código más complejas. Con las herramientas adecuadas, el análisis de código estático puede escanear miles de líneas de código en segundos, ahorrando a las compañías tiempo y recursos valiosos. Una vez que se realiza el análisis de código estático, los algoritmos de IA pueden tomar esta información para recomendar mejoras o un nuevo curso de acción.

Análisis de código dinámico
A diferencia del análisis de código estático, el análisis de código dinámico está diseñado para probar el código o ejecutar la aplicación en busca de posibles problemas o vulnerabilidades de seguridad. El beneficio de este método es que puede probar si hay problemas mientras el software se está ejecutando y encontrar problemas que podrían no detectar cuando el código es estático.
El análisis de código dinámico también se conoce como prueba dinámica de seguridad de aplicaciones (DSAT). Estas herramientas DSAT tienen un diccionario de vulnerabilidades conocidas que se deben buscar cuando se ejecuta una aplicación. Luego, estas herramientas analizan las respuestas a las entradas y registran cualquier problema. Las herramientas de análisis dinámico de código pueden brindar tranquilidad a los desarrolladores al encontrar cuellos de botella de rendimiento y vulnerabilidades de seguridad mucho antes de que una aplicación esté disponible para los clientes.

Herramientas clave para la revisión de código de IA

watsonx Code Assistant™: La solución watsonx Code Assistant utiliza AI generativa para acelerar el desarrollo mientras se mantienen los principios de confianza y seguridad. Con watsonx Code Assistant, los desarrolladores pueden reducir errores, minimizar la curva de aprendizaje y crear código de calidad a través de la generación de código, la coincidencia de código y la modernización del código.

Codacy: Codacy ofrece revisiones de código automatizadas que admiten lenguajes como JavaScript y Python, lo que ayuda a los desarrolladores a mantener la calidad del código en todos sus proyectos. El proceso de incorporación está diseñado para integrar perfectamente en los flujos de trabajo de software, lo que permite a los equipos detectar problemas a tiempo.

DeepCode: DeepCode emplea IA para analizar el código en tiempo real, proporcionando insights procesables para proyectos de código abierto. Esta herramienta mejora la experiencia de incorporación para los nuevos desarrolladores al identificar errores comunes y promover las mejores prácticas en ingeniería de software.

IA Bito: La IA Bito se centra en agilizar la incorporación de equipos de ingeniería de software con su interfaz intuitiva y comentarios impulsados por IA. Puede proporcionar feedback inmediato y recomendaciones aplicables en la práctica, y ayudar a los nuevos miembros del equipo a adaptar rápidamente a los estándares y mejores prácticas de programación de la compañía.

PullRequest: PullRequest ofrece ambos insights impulsados por IA y experiencia humana, lo que facilita un proceso de incorporación sin problemas para los equipos de ingeniería de software. La plataforma fomenta la colaboración y el intercambio de conocimientos para alentar a los desarrolladores más nuevos a aprender de las experiencias de los revisores.

Coderabbit: Coderabbit es una plataforma de revisión de código de IA que utiliza herramientas de IA para producir análisis y feedback clara. Ofrece comentarios similares a las humanas y es personalizable ya que funciona con todos los lenguajes de programación.


Fuente: https://www.ibm.com/mx-es/think/insights/ai-code-review


Explicar por qué no es posible asegurar al 100% la autoría.

es complicado garantizar al 100 la autoria de una obra, las leyes de derechos de autor solo protegen la forma en que se expresa una idea, no la idea en sí por lo qu esto significa que diferentes personas pueden crear obras similares de manera independiente sin que eso se considere una infracción como tal, ademas a menudo es un reto demostrar con certeza que alguien ha copiado una obra, ya que el proceso de prueba puede ser complicado, especialmente si no hay un registro previo o si los cambios realizados hacen que sea difícil de rastrear. También hay excepciones legales, como el uso educativo, la investigación o el uso privado, que permiten a otros utilizar partes de una obra sin necesidad de autorización, lo que complica aun mas la posibilidad de asegurar una protección total incluso en campos tecnicos, como el desarrollo de software aunque se pueden usar metodos como el analisis de codigo estatico o dinamico para evaluar la calidad, la seguridad o las similitudes, estas herramientas no pueden confirmar de manera definitiva la originalidad del código, el analisis puede detectar errores, patrones o comportamientos, pero no puede determinar con total precisión si alguien creo un fragmento de manera independiente o si lo copio, por todas estas razones las limitaciones legales, la dificultad de probar y la naturaleza misma de las ideas no se puede asegurar la autoría de forma absoluta.


- Proponer políticas razonables de uso de IA en educación y calidad.

Ya que la inteligencia artificial está tomando muchísimo campo en la actualidad nos vemos obligados a regularlas ya que esto puede causar que la mayoría de personas no se tomen el tiempo de realizar las actividades por su cuenta y esto mas adelante afecta en el conocimiento y el razonamiento que se va adquiriendo siendo asi profesionales un poco menos preparados, entonces por esto propondría estas políticas
Política de uso ético y responsible en donde Toda implementación de IA debe alinearse con principios éticos que garantice la protección de datos personales, ausencia de manipulación y especialmente siempre supervisión humana
Política de generalización del tema de la IA específicamente en los maestros, ya que como es una tecnología que va en un crecimiento abrumador, en mi opinión los maestros de cualquier especialidad o materia deberían estar capacitados obligatoriamente de este tema 
Política de IA como herramienta complementaria, esto aplicaría para docentes y estudiantes, ya que en algún momento todos necesitamos un poco de ayuda, pero no es ppara que nos realice el trabajo completo, la ia es muy buena cuando se usa de la manera correcta
Politica de transparencia algorítmica, para mi para poder garantizar la calidad educativa, no podemos confiar en la información que de la ia al 100% para esto es mejor que este tipo de sistemas pueda ser auditable y asi confirmar que la información que de sea correcta
Política de regulación nacional, en la cual los organismos públicos establezcan reglas de ética que puedan ser usadas por estos sistemas y en especial para la protección de menores de edad asi que esto permitirá garantizar coherencia, seguridad y un desarrollo responsable 

Fuente : https://www.unesco.org/es/articles/el-uso-de-la-ia-en-la-educacion-decidir-el-futuro-que-queremos
