SOTZLOGIC
Autor: Ricardo Emmanuel Méndez Pérez

Apodo: R. Méndez

Institución: CECyTECH 40 "Las Águilas" (Chiapas, México)

🦇 Concepto del Proyecto
SOTZLOGIC es un sistema de control basado en el microcontrolador ESP32 S3, que emula los principios operativos de un PLC (Controlador Lógico Programable). No pretende ser un PLC comercial, sino una plataforma de aprendizaje y prototipado para aplicar lógica de control industrial en hardware de bajo costo.

El nombre proviene del Tzotzil "Sotz" (Murciélago), una referencia a los desvelos durante su desarrollo y a la agilidad del ESP32 S3 para adaptarse a diversas tareas de automatización ligera.

Hardware Empleado (Versión 0)
Microcontrolador: ESP32-S3 N16R8.

Salidas: Módulo de relevadores de 8 canales.

Entradas Digitales: 8 entradas optoacopladas mediante PC817.

Gestión de Energía: Módulo AMS1117 de 3.3V.

Lógica de Señales: Arreglo en Pull-up con resistencias de 4.7KΩ.

🛠️ Arquitectura y Hardware (Evolución V0.1)
El diseño se centra en la escalabilidad y gestión eficiente de recursos, superando las limitaciones de los prototipos convencionales mediante:

Gestión de I/O Extendida: Uso de registros de desplazamiento 74HC595 en cascada para controlar 16 salidas independientes con un consumo mínimo de GPIOs.

Etapa de Potencia Robusta: Implementación de drivers ULN2803 para el manejo de bobinas de relevadores, garantizando una conmutación segura y eficiente.

Aislamiento de Entradas: 8 canales de entrada digital con optoacopladores PC817 y pull-ups de 4.7KΩ, diseñados para filtrar ruido y proteger el núcleo del ESP32-S3 N16R8.

Integridad de Señal: Filtrado de ruido mediante capacitores de desacoplo de 100nF.

🛡️ Implementación de Lógica de Seguridad (DURANTE PRUEBA DE ESTRÉS).
Para acercar el proyecto a un entorno real, se implementaron funciones de seguridad críticas:

Prevención de Glitches (Hardware Enable): Control maestro vía pin: Output Enable (OE). El sistema mantiene las salidas en alta impedancia durante el arranque del microcontrolador, evitando activaciones erráticas.

Gestión de Paro de Emergencia (E-Stop): * Lógica basada en contactos NC (Normalmente Cerrados).

Interrupción Crítica: El sistema bloquea físicamente las salidas al detectar la apertura del circuito de seguridad.

State Memory: A diferencia de un ciclo de código simple, SOTZLOGIC es capaz de reanudar la secuencia de trabajo exactamente en el paso donde se detuvo tras liberar el bloqueo.

Pruebas Realizadas
Fecha: 14 de marzo de 2026 | Hora: 15:32

Se realizó la primera prueba de esfuerzo de la V0 utilizando 4 salidas:

Q1: Control de contactor Schneider (M4).

Q2: Relevador OMRON de 24VDC.

Q3: Luz piloto verde (Marcha).

Q4: Luz piloto roja (Paro).

Resultado: Se controló exitosamente un motor de AC de 171.6W (110VAC / 1.56A). El sistema ejecutó la secuencia: Arranque --> Giro derecha (10s) --> Pausa de seguridad (2s) --> Giro izquierda (10s) --> Paro total con indicador visual rojo.

Fecha : 1 de abril de 2026 | Hora: 15:58

Stress Test de Potencia: Ciclo de intermitencia con los 16 relevadores activos simultáneamente (Duty Cycle 50% a 1Hz).Resultado Térmico: Tras 11 minutos de operación continua a máxima carga, los drivers ULN2803 y la etapa de regulación mantuvieron estabilidad térmica absoluta.

📜 Licencia y Propósito
Este es un proyecto educativo bajo licencia MIT. Está diseñado para estudiantes y entusiastas de la mecatrónica que buscan entender cómo se integran los registros de desplazamiento, el aislamiento galvánico y la lógica de seguridad en un sistema de control.
