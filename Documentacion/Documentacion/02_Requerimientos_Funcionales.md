# 02 – Requerimientos Funcionales

Los requerimientos funcionales describen **qué debe hacer** la fuente de alimentación.

| ID | Requerimiento | Criterio de verificación |
|---|---|---|
| RF-01 | La fuente debe recibir energía desde el transformador AC del laboratorio. | Operación correcta con el transformador especificado. |
| RF-02 | La fuente debe rectificar la tensión AC mediante un puente de diodos de onda completa. | Forma de onda rectificada observada en osciloscopio. |
| RF-03 | La fuente debe filtrar la tensión rectificada mediante un banco capacitivo y generar un bus DC (VIN DC). | Rizado del bus ≤ 3 Vpp a carga plena. |
| RF-04 | La fuente debe entregar +12 V con una corriente de hasta 5 A. | Medición con carga electrónica a 5 A, tolerancia ±3 %. |
| RF-05 | La fuente debe entregar +5 V con una corriente de hasta 5 A. | Medición con carga electrónica a 5 A, tolerancia ±3 %. |
| RF-06 | La fuente debe entregar +3.3 V con una corriente de hasta 3 A. | Medición con carga electrónica a 3 A, tolerancia ±3 %. |
| RF-07 | La fuente debe entregar −12 V con una corriente de hasta 1 A. | Medición con carga electrónica a 1 A, tolerancia ±3 %. |
| RF-08 | La fuente debe entregar una salida ajustable entre 1.25 V y 15 V con una corriente de hasta 3 A. | Barrido del potenciómetro de mínimo a máximo con carga de 3 A. |
| RF-09 | El usuario debe poder ajustar la salida variable mediante un potenciómetro accesible. | Ajuste manual sin herramientas. |
| RF-10 | La conversión DC/DC de todas las salidas debe estar integrada en la PCB de la fuente. | Inspección de la PCB. |
| RF-11 | La fuente debe poder encenderse y apagarse mediante un interruptor general. | Prueba de encendido y apagado. |
| RF-12 | La fuente debe proteger la entrada contra sobrecorriente mediante un fusible. | Inspección y coordinación del fusible. |
| RF-13 | Cada salida debe limitar su corriente ante sobrecarga o cortocircuito sin dañarse. | Prueba de cortocircuito de cada salida. |
| RF-14 | Los reguladores deben apagarse ante sobretemperatura y recuperarse al enfriarse. | Verificación con datasheet y prueba térmica. |
| RF-15 | La fuente debe indicar visualmente la presencia de tensión en el bus DC y en cada salida. | LEDs encendidos en operación normal. |
| RF-16 | Las salidas deben poder usarse simultáneamente y de forma independiente. | Prueba con varias cargas conectadas a la vez. |
| RF-17 | Todas las salidas deben compartir una referencia común (GND). | Verificación de continuidad. |
| RF-18 | El banco de capacitores debe descargarse de forma segura al apagar la fuente. | Tensión del bus < 5 V antes de 60 s después del apagado. |
