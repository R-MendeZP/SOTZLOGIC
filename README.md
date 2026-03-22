SOTZLOGIC
Autor: Ricardo Emmanuel Méndez Pérez

Apodo: R. Méndez

Institución: CECyTECH 40 "Las Águilas" (Chiapas, México)

Introducción
SOTZLOGIC V0 es un proyecto basado en los principios de funcionamiento de un PLC (Controlador Lógico Programable). Utiliza como núcleo el microcontrolador ESP32-S3 N16R8.

El nombre proviene del vocablo Tzotzil "Sotz" (Murciélago), una referencia a las noches de desvelo invertidas en su desarrollo y a la versatilidad del sistema para adaptarse a distintas tareas. Este proyecto forma parte de mi formación académica en la carrera de Mecatrónica, enfocándome en el diseño de sistemas de control.

Hardware Empleado (Versión 0)
Microcontrolador: ESP32-S3 N16R8.

Salidas: Módulo de relevadores de 8 canales.

Entradas Digitales: 8 entradas optoacopladas mediante PC817.

Gestión de Energía: Módulo AMS1117 de 3.3V.

Lógica de Señales: Arreglo en Pull-up con resistencias de 4.7KΩ.

Evolución: SOTZ V0.1
A pocos días de finalizar la primera versión, surgió el reto de escalar el proyecto por petición de la dirección de carrera. Los nuevos requerimientos incluyen:

Control de 4 microcilindros neumáticos.

Operación de 2 bandas transportadoras (motorreductores).

Implementación de indicadores visuales (luces piloto).

Para lograrlo, rediseñé el circuito expandiendo de 8 a 16 salidas independientes. La clave de esta mejora fue la implementación de dos circuitos integrados 74HC595 (registros de desplazamiento). Estos integrados permiten controlar las salidas optimizando el uso de pines del ESP32. Además, se incorporaron dos drivers ULN2803 (uno para cada registro) para invertir el nivel lógico y manejar adecuadamente la potencia de las bobinas de los relevadores.

Pruebas Realizadas
Fecha: 14 de marzo de 2026 | Hora: 15:32

Se realizó la primera prueba de esfuerzo de la V0 utilizando 4 salidas:

Q1: Control de contactor Schneider (M4).

Q2: Relevador OMRON de 24VDC.

Q3: Luz piloto verde (Marcha).

Q4: Luz piloto roja (Paro).

Resultado: Se controló exitosamente un motor de AC de 171.6W (110VAC / 1.56A). El sistema ejecutó la secuencia: Arranque --> Giro derecha (10s) --> Pausa de seguridad (2s) --> Giro izquierda (10s) --> Paro total con indicador visual rojo.

Proyecto educativo bajo licencia MIT. Desarrollado con orgullo en Chiapas, México.
