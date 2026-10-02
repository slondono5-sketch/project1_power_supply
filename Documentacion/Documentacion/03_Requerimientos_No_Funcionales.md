# 03 – Requerimientos No Funcionales

Los requerimientos no funcionales describen **cómo** debe comportarse el sistema: calidad, seguridad, confiabilidad y facilidad de uso.

## Desempeño

| ID | Requerimiento |
|---|---|
| RNF-01 | El rizado de cada salida debe ser ≤ 100 mVpp (≤ 50 mVpp en +3.3 V). |
| RNF-02 | La regulación de carga debe ser ≤ 2 % entre 10 % y 100 % de carga. |
| RNF-03 | La eficiencia de cada convertidor DC/DC debe ser ≥ 80 % a carga plena. |
| RNF-04 | La respuesta transitoria ante escalones de carga no debe superar ±5 % de la tensión nominal. |

## Confiabilidad y seguridad

| ID | Requerimiento |
|---|---|
| RNF-05 | Los componentes de potencia deben dimensionarse con un margen de seguridad de 20–30 % sobre la corriente máxima. |
| RNF-06 | Los capacitores deben tener una tensión nominal de al menos 1.5 veces la tensión máxima del bus. |
| RNF-07 | La temperatura de unión de los semiconductores debe permanecer al menos 20 °C por debajo de su máximo a carga plena. |
| RNF-08 | La fuente debe operar en régimen continuo a carga plena durante al menos 1 hora sin degradación. |
| RNF-09 | La sección de 120 VAC debe quedar aislada y protegida contra contacto accidental. |
| RNF-10 | La fuente debe incluir conexión a tierra de protección para el chasis o encapsulado metálico. |

## Usabilidad

| ID | Requerimiento |
|---|---|
| RNF-11 | Las salidas deben estar claramente identificadas por tensión y polaridad. |
| RNF-12 | Los conectores de salida deben permitir conectar cables de laboratorio (bornes banana de 4 mm). |
| RNF-13 | El ajuste de la salida variable debe ser fino (potenciómetro multivuelta). |

## Mantenibilidad y fabricación

| ID | Requerimiento |
|---|---|
| RNF-14 | Los fusibles deben poder reemplazarse sin desoldar componentes. |
| RNF-15 | La PCB debe incluir puntos de prueba en el bus DC y en cada salida. |
| RNF-16 | Cada convertidor debe ocupar una zona propia de la PCB para facilitar diagnóstico y reparación. |
| RNF-17 | Los componentes deben conseguirse en distribuidores nacionales (I+D Electrónica, Sigma Electrónica, Vistronica, Ferretrónica) o internacionales (Digi-Key, Mouser, LCSC). |
| RNF-18 | El proyecto debe documentarse y versionarse en el repositorio Git con la estructura definida. |

## Costo

| ID | Requerimiento |
|---|---|
| RNF-19 | Se deben preferir componentes de bajo costo y amplia disponibilidad sin comprometer los requerimientos eléctricos. |
