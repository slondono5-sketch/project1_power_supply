# 04 – Restricciones de Diseño

## Restricciones eléctricas

| ID | Restricción | Impacto en el diseño |
|---|---|---|
| RD-01 | La entrada es un transformador AC del laboratorio. | Su tensión y potencia limitan el bus DC y la potencia simultánea disponible. Si es menor a 300 VA, no todas las salidas podrán operar a plena carga al mismo tiempo. |
| RD-02 | La rectificación debe hacerse con puente de diodos y filtrado capacitivo. | Se descarta la corrección de factor de potencia y la rectificación síncrona. |
| RD-03 | La tensión del bus DC debe quedar entre ≈ 21 V y ≈ 30 V. | El mínimo garantiza la salida de 15 V; el máximo debe quedar por debajo de la tensión máxima de entrada de los reguladores (40 V). |
| RD-04 | Red eléctrica de 120 VAC, 60 Hz. | El rizado del bus es de 120 Hz, lo que define el tamaño del banco capacitivo. |
| RD-05 | La salida de −12 V debe generarse desde el mismo bus positivo. | Exige una topología inversora; el regulador soporta Vin + |Vout| ≈ 42 V entre sus terminales. |
| RD-06 | Toda la conversión DC/DC debe integrarse en la PCB. | No se permiten módulos DC/DC comerciales externos. |

## Restricciones térmicas

| ID | Restricción | Impacto en el diseño |
|---|---|---|
| RD-07 | Temperatura ambiente de operación de 0 a 40 °C (laboratorio). | Cálculo de disipadores con este ambiente máximo. |
| RD-08 | El puente rectificador y los reguladores disipan varios vatios. | Se requieren disipadores y encapsulados de montaje en disipador (TO-220 / TO-263, puente tipo GBJ o KBPC). |

## Restricciones de fabricación (DFM)

| ID | Restricción | Impacto en el diseño |
|---|---|---|
| RD-09 | Herramienta de diseño: Altium Designer. | Esquemáticos, PCB y librerías propias en Altium. |
| RD-10 | PCB de 2 capas, cobre de 2 oz (70 µm). | Pistas de potencia anchas o polígonos de cobre; el ancho se calcula según IPC-2221 para ≥ 10 A en el bus. |
| RD-11 | Se priorizan componentes THT y SMD de tamaño manejable (≥ 0805). | Facilita el ensamble y la reparación manual. |
| RD-12 | Separación entre la zona de 120 VAC y la de baja tensión. | Distancias de aislamiento (creepage/clearance) en la PCB o primario fuera de la PCB. |

## Restricciones mecánicas

| ID | Restricción | Impacto en el diseño |
|---|---|---|
| RD-13 | Las salidas deben conectarse con bornes de laboratorio. | Bornes tipo binding post / banana de 4 mm rateados para ≥ 10 A. |
| RD-14 | El transformador, los disipadores y el banco de capacitores son voluminosos. | Definen el tamaño mínimo de la PCB y del encapsulado. |
| RD-15 | Se requiere ventilación. | Encapsulado con perforaciones o ventilador. |

## Restricciones del proyecto

| ID | Restricción | Impacto en el diseño |
|---|---|---|
| RD-16 | Presupuesto académico limitado. | Se priorizan reguladores integrados de bajo costo frente a controladores con MOSFET externos. |
| RD-17 | Tiempo de desarrollo de un semestre (2026-2). | Se usan topologías con diseños de referencia del fabricante. |
| RD-18 | Disponibilidad de componentes en Colombia. | Se selecciona una alternativa para cada componente crítico. |
