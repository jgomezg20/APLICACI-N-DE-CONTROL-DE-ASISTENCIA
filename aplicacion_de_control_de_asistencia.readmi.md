/aplicacion\_de\_control\_de\_asistencia

├── README.md

├── Requerimientos/

│   ├── Requerimientos Funcionales



1\.	Registro de Asistencia: El sistema debe permitir al instructor seleccionar una clase, ver la lista de estudiantes inscritos y registrar la asistencia de cada uno con estados (Presente, Ausente, Tarde)

2\.	Reporte Histórico por Clase: El sistema debe permitir al instructor generar un reporte consolidado de la asistencia de todos los estudiantes para un curso específico.

3\.	Modificación de asistencia: El sistema debe permitir a los usuarios autorizados modificar el estado de asistencia de un estudiante hasta 24 horas después de la hora programada de la sesión

4\.	Alerta de Ausencia: El sistema debe notificar automáticamente al instructor cuando un estudiante acumule más del 20% de inasistencias en el curso

5\.	Gestión de Cursos: El administrador del sistema debe poder crear, editar y eliminar cursos, y asignar instructores a dichos cursos

Requerimientos No Funcionales



1\.	Seguridad (Autorización): Solo los usuarios con rol de "Instructor" deben tener permiso para registrar o modificar la asistencia de los cursos que les han sido asignados

2\.	Rendimiento (Capacidad): El sistema debe ser capaz de procesar el registro de asistencia para una clase de 60 estudiantes en un tiempo no mayor a 5 segundos

3\.	Recuperación (Disponibilidad): En caso de un fallo inesperado del sistema, el servicio debe restablecerse completamente y restaurar los datos de asistencia no guardados en un plazo máximo de 30 minutos



│   └── 

├── pruebas/

│   └── Tipo de Prueba	Requerimiento Asociado	Datos de Entrada	Resultado Esperado	Resultado Obtenido

Unitario	Registro de Asistencia	Estudiante ID: 1234. Clase ID: MAT101.

Estado ingresado: Tarde.	El módulo de persistencia debe insertar el registro en la base de datos con la marca de tiempo actual y estado 'Tarde'.	Éxito. El registro se insertó correctamente.

Unitario	Gestión de Cursos	Intento de crear un curso con ID ya existente	El módulo de creación de cursos debe retornar un error de unicidad y no crear el registro duplicado.	Éxito. Se previno la duplicación de datos.

Unitario	Modificación de asistencia	Modificación 25 horas después del registro.	El módulo de modificación debe rechazar la solicitud debido al límite de tiempo y retornar un mensaje de error.	Éxito. Se aplica la restricción de 24 horas.

Validación	Reporte Histórico por Clase	Solicitud de reporte para MAT101. DB contiene 30 registros de 'Ausente' para el Estudiante A.	El sistema debe mostrar al Estudiante A en la lista y calcular su porcentaje de ausencia correctamente, reflejando el 30% del total de clases.	Éxito. El cálculo del reporte cumple la lógica de negocio.

Validación	Seguridad (Autorización)	Usuario "Estudiante" intenta acceder a la interfaz de registro de asistencia.	El sistema debe bloquear el acceso a esa ruta y redirigir al usuario, validando la restricción de seguridad.	Éxito. Se denegó el acceso al usuario no autorizado.

├── mantenimiento/

│   └── Determinación y Justificación de los Tipos de Mantenimiento



Problema: Seguridad Vaga y Riesgosa

El problema se centra en que la Seguridad de Acceso es insuficiente al solo requerir un

inicio de sesión con contraseña. Esta debilidad puede llevar a fallas críticas de seguridad en el futuro.





Tipo de Mantenimiento	Justificación Técnica







Mantenimiento Preventivo	Se aplica para prevenir futuros problemas mediante mejoras internas de código y estructura. Dado que la estructura de

seguridad es deficiente, la implementación de políticas de

contraseñas robustas y gestión segura de sesiones fortalece el sistema, contribuyendo a reducir los costos de mantenimiento a largo plazo





Mantenimiento Perfectivo	Aunque la intención principal es la prevención, las mejoras como la autenticación multifactor (2FA) añaden funciones que

optimizan el uso (seguridad) Este tipo de acción busca producir un sistema más mantenible



├── investigacion/

│   └── ¿Qué es Markdown?

Markdown es un lenguaje de marcado ligero que se utiliza para dar formato a texto plano. Fue creado por John Gruber en 2004 con el objetivo de permitir a la gente "escribir usando un formato de texto plano fácil de leer y escribir, y luego convertirlo a HTML (o a otros formatos) de forma estructuralmente válida."

En esencia, te permite escribir usando una sintaxis sencilla (como asteriscos, guiones y corchetes) que luego se puede renderizar (convertir) en una estructura visualmente atractiva, como páginas web.

Por qué se utiliza en proyectos de software?

Markdown es el formato estándar de facto para la documentación y la comunicación en proyectos de software por varias razones:

•	Legibilidad: El texto fuente de Markdown es muy legible incluso antes de ser renderizado.

•	Simplicidad: Su sintaxis es fácil de aprender y escribir, lo que acelera el proceso de documentación.

•	Control de Versiones (Git): Como los archivos Markdown son solo texto plano, son ideales para el control de versiones con herramientas como Git. Los cambios (o diffs) son limpios y fáciles de revisar.

•	Portabilidad: Se puede abrir y editar en prácticamente cualquier editor de texto o IDE.

•	Integración: Plataformas como GitHub, GitLab, Bitbucket, y la mayoría de los generadores de documentación lo soportan de forma nativa.

En proyectos de software, Markdown se utiliza comúnmente en:

•	READMEs: El archivo principal que presenta un proyecto.

•	Documentación: Manuales, guías de instalación y guías de contribución.

•	Notas de Lanzamiento (Release Notes): Resúmenes de nuevas características y correcciones.

•	Comentarios y Discusiones: En issues y pull requests.



EJEMPLO PRACTICO

Elemento	Sintaxis Markdown	Descripción

Encabezados	# Título Principal





\## Subtítulo





\### Sección	Se utilizan del # al ###### para estructurar el contenido (como HTML h1 a h6).

Listas	\* Elemento 1





\* Elemento 2





1\. Primer paso





2\. Segundo paso	Los asteriscos (\*, +, o -) crean listas no ordenadas. Los números seguidos de un punto (1.) crean listas ordenadas.

Tablas		Encabezado 1

Enlaces	\[Texto del Enlace](https://ejemplo.com)	Los corchetes encierran el texto visible, y los paréntesis encierran la URL.

Imágenes	!\[Descripción de la Imagen](ruta/imagen.png)	Similar a un enlace, pero con un signo de exclamación (!) al principio.

Énfasis	\*\*Negrita\*\* o \*Cursiva\*	Se usan dos asteriscos para negrita y uno para cursiva.





Ventajas de utilizar Markdown en combinación con GitHub

Usar Markdown dentro de GitHub ofrece múltiples beneficios:

✔ 1. Renderizado automático

GitHub muestra automáticamente archivos .md con formato, lo que hace que los repositorios se vean profesionales y fáciles de entender.

✔ 2. Ideal para documentar proyectos

Los archivos README.md, wikis y documentación de GitHub usan Markdown como estándar.

✔ 3. Integración con GitHub Pages

Markdown se puede usar para crear sitios web estáticos mediante GitHub Pages.

✔ 4. Facilita la colaboración

Los colaboradores pueden editar la documentación directamente desde el navegador usando Markdown.

✔ 5. Versionamiento claro

Al estar basado en texto plano, Markdown funciona perfectamente con Git y permite ver cambios línea por línea.

✔ 6. Portabilidad

Los documentos en Markdown pueden transformarse fácilmente a HTML, PDF, DOCX y otros formatos.





└── evidencias/

&nbsp;   ├── 

&nbsp;   ├── 

&nbsp;   └── 

