# 05 – Lista Preliminar de Componentes Principales

> Lista preliminar sujeta a validación en el diseño detallado. Los datasheets se almacenan en `Documentacion/Datasheets/`.

## Resumen

| # | Bloque | Componente propuesto | Especificación clave | Alternativa |
|---|---|---|---|---|
| 1 | Transformador de entrada | Transformador 120 VAC / 18 VAC | ≥ 300 VA, 60 Hz (toroidal preferido) | Transformador de laboratorio equivalente |
| 2 | Puente rectificador | GBJ2510 | 25 A, 1000 V | KBPC3510 (35 A) |
| 3 | Capacitores de filtrado | 3 × electrolítico snap-in 10 000 µF / 50 V | 105 °C, baja ESR | 4 × 6 800 µF / 50 V |
| 4 | Buck +12 V | LM2678-12 | 5 A, Vin 8–40 V, 260 kHz | LM5116 (controlador, MOSFET externos) |
| 5 | Buck +5 V | LM2678-5.0 | 5 A, Vin 8–40 V | LM5116 |
| 6 | Buck +3.3 V | LM2678-3.3 | 5 A, Vin 8–40 V | LM2596-3.3 (3 A, sin margen) |
| 7 | Convertidor −12 V | LM2576HV-ADJ (buck-boost inversor) | 3 A de switch, Vin hasta 60 V | LM2576-ADJ (40 V) |
| 8 | Regulador variable | LM2678-ADJ + potenciómetro multivuelta | 5 A, Vref ≈ 1.21 V | LM2596-ADJ (3 A, sin margen) |
| 9 | Fusible de entrada | Fusible 5×20 mm T3.15 A / 250 V + portafusible | Acción lenta | T4 A según transformador |
| 10 | Interruptor | Interruptor basculante DPST 250 VAC / 10 A con luz | Corta fase y neutro | SPST 10 A |
| 11 | Conectores | Entrada: bornera 2 pines 5.08 mm. Salidas: bornes banana 4 mm | ≥ 15 A | Bornera de tornillo 7.62 mm |

## Justificación por bloque

### 1. Transformador de entrada
Un secundario de 18 VAC genera un bus de ≈ 24 V, suficiente para la salida de 15 V con margen de caída, y por debajo de los 40 V máximos de los reguladores incluso sin carga y con la red al +10 %. La potencia de ≥ 300 VA cubre los ≈ 175 W del bus con el factor de forma del filtro capacitivo (≈ 1.7).

### 2. Puente rectificador – GBJ2510
La corriente promedio del bus es ≈ 8.3 A y los picos de carga del capacitor son varias veces mayores. Un puente de 25 A ofrece un margen holgado y su encapsulado plano se monta fácilmente en disipador.

### 3. Capacitores de filtrado – 3 × 10 000 µF / 50 V
C = 8.3 A / (120 Hz × 3 V) ≈ 23 000 µF; con 30 000 µF el rizado baja a ≈ 2.3 Vpp. Los 50 V dan un margen de ≈ 1.6 veces sobre los 30 V máximos del bus. Repartir en tres capacitores distribuye la corriente de rizado (≈ 13 A RMS en total). Se debe verificar el rating de rizado de la referencia final.

### 4, 5 y 6. Buck +12 V, +5 V y +3.3 V – familia LM2678
- Tensión de entrada de hasta 40 V, compatible con el bus.
- Versiones fijas de 3.3, 5 y 12 V, lo que reduce componentes externos.
- Limitación de corriente y apagado térmico integrados (RF-13, RF-14).
- Usar la misma familia en cuatro salidas simplifica la librería de Altium y la compra.

**Riesgo identificado:** en +12 V y +5 V la corriente requerida (5 A) coincide con la nominal del LM2678, por lo que no cumple el margen de 25 % de RNF-05. Para el prototipo se acepta con un diseño térmico cuidadoso. Si se exige el margen completo, la alternativa es el controlador LM5116 con MOSFET externos. En +3.3 V el LM2678 sí cumple el margen (5 A frente a 3.75 A requeridos).

### 7. Convertidor −12 V – LM2576HV-ADJ en buck-boost inversor
Genera tensión negativa desde el bus positivo sin necesidad de un devanado adicional. En configuración inversora el regulador soporta Vin + |Vout| ≈ 30 + 12 = 42 V, por encima de los 40 V del LM2576 estándar, y por eso se elige la versión HV (60 V). La corriente pico del switch es ≈ 1.25 A × (21 + 12) / 21 ≈ 2 A más el rizado, dentro de los 3 A del dispositivo.

### 8. Regulador variable – LM2678-ADJ
Su tensión de referencia de ≈ 1.21 V cubre el mínimo de 1.25 V especificado. Ser conmutado evita la disipación de un regulador lineal: un LM317 a 1.25 V y 3 A disiparía (21 − 1.25) × 3 ≈ 60 W. La capacidad de 5 A cumple el margen sobre los 3 A requeridos. El ajuste se hace con un potenciómetro multivuelta de 10 kΩ en la red de realimentación: con R1 = 820 Ω, Vout = 1.21 × (1 + R2 / R1) va de ≈ 1.21 V a ≈ 15.9 V; se puede añadir una resistencia en serie para limitar el máximo a 15 V.

### 9. Fusible de entrada – T3.15 A
La corriente nominal del primario es ≈ 2.5 A. Se requiere acción lenta por la corriente de arranque del transformador y del banco de 30 000 µF.

### 10. Interruptor – DPST 10 A
Interrumpe fase y neutro por seguridad. El indicador luminoso cumple parte de RF-15.

### 11. Conectores
Los bornes banana de 4 mm son el estándar de laboratorio (RNF-12) y soportan las corrientes de salida. La entrada desde el transformador usa una bornera de potencia.

## Componentes complementarios

| Componente | Referencia preliminar | Función |
|---|---|---|
| Varistor de entrada | 14D241K (150 VAC) | Supresión de transitorios de red |
| TVS del bus DC | SMCJ33A | Supresión de transitorios en el bus (verificar tensión de clamp frente al máximo de los reguladores) |
| Diodos Schottky de los buck | MBR1045 (10 A, 45 V) | Diodo de rueda libre |
| Inductores de potencia | Según tablas del datasheet o TI WEBENCH (≥ 7 A de saturación en 12 V y 5 V) | Almacenamiento de energía |
| Fusibles de salida | PTC reseteable o fusible de cuchilla por salida | Protección por salida |
| Resistencia de descarga | 4.7 kΩ / 1 W | Descarga del banco de capacitores |
| LEDs indicadores | LED 3 mm + resistencia limitadora | Indicación de bus y salidas |
| Disipadores | Aluminio para TO-220 y puente | Gestión térmica |

## Distribuidores sugeridos

Nacionales: I+D Electrónica, Sigma Electrónica, Vistronica, Ferretrónica.
Internacionales: Digi-Key, Mouser, LCSC, Octopart (comparador).
