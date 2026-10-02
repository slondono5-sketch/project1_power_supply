# 01 – Especificaciones del Proyecto

## 1. Descripción general

Fuente de alimentación multisalida, alimentada desde un transformador AC del laboratorio, destinada a energizar prototipos y proyectos electrónicos de laboratorio. La energía AC se rectifica con un puente de diodos, se filtra capacitivamente para formar un bus DC no regulado (VIN DC) y desde este bus cinco convertidores DC/DC independientes, integrados en la misma PCB, generan las salidas reguladas.

## 2. Especificaciones de entrada

| Parámetro | Valor |
|---|---|
| Red eléctrica | 120 VAC ±10 %, 60 Hz (Colombia) |
| Transformador | Primario 120 VAC / secundario 18 VAC, potencia ≥ 300 VA |
| Rectificación | Puente de diodos de onda completa |
| Frecuencia de rizado | 120 Hz |
| Filtrado | Banco capacitivo ≈ 30 000 µF |
| Bus DC (VIN DC) nominal | ≈ 24 V |
| Bus DC mínimo (valle de rizado, carga plena, red −10 %) | ≈ 21 V |
| Bus DC máximo (sin carga, red +10 %) | ≈ 30 V |

## 3. Especificaciones de salida

| Salida | Tensión | Corriente máx. | Corriente de diseño (+25 %) | Potencia máx. | Topología |
|---|---|---|---|---|---|
| OUT1 | +12 V | 5 A | 6.25 A | 60 W | Buck |
| OUT2 | +5 V | 5 A | 6.25 A | 25 W | Buck |
| OUT3 | +3.3 V | 3 A | 3.75 A | 9.9 W | Buck |
| OUT4 | −12 V | 1 A | 1.25 A | 12 W | Buck-boost inversor |
| OUT5 | 1.25 – 15 V ajustable | 3 A | 3.75 A | 45 W | Buck ajustable |
| **Total** | | | | **≈ 152 W** | |

Parámetros de calidad objetivo en todas las salidas:

| Parámetro | Objetivo |
|---|---|
| Tolerancia de tensión (salidas fijas) | ±3 % |
| Rizado de salida | ≤ 100 mVpp (≤ 50 mVpp en +3.3 V) |
| Regulación de carga (10 % → 100 %) | ≤ 2 % |
| Eficiencia por convertidor | ≥ 80 % a carga plena |

## 4. Presupuesto de potencia (power budget)

| Salida | P salida | η estimada | P entrada |
|---|---|---|---|
| +12 V | 60 W | 90 % | 66.7 W |
| +5 V | 25 W | 88 % | 28.4 W |
| +3.3 V | 9.9 W | 85 % | 11.6 W |
| −12 V | 12 W | 80 % | 15.0 W |
| Variable | 45 W | 85 % | 52.9 W |
| **Total sobre el bus DC** | **152 W** | | **≈ 175 W** |

- Corriente promedio del bus DC a tensión mínima: 175 W / 21 V ≈ **8.3 A**
- Potencia aparente del transformador (factor ≈ 1.7 por filtro capacitivo): 175 W × 1.7 ≈ **300 VA**
- Corriente de primario: 300 VA / 120 V ≈ **2.5 A**

## 5. Cálculos de la etapa de entrada

**Tensión del bus:**

- Pico del secundario: 18 V × √2 ≈ 25.5 V
- Caída del puente (2 diodos a ~8 A): ≈ 2 V → pico DC ≈ 23.5 V
- Sin carga, la regulación del transformador (~8 %) y la red al +10 % llevan el bus a ≈ 30 V

**Capacitor de filtro:**

C = I / (f · ΔV) = 8.3 A / (120 Hz × 3 V) ≈ 23 000 µF → se especifican 3 × 10 000 µF (30 000 µF), con lo que ΔV ≈ 2.3 Vpp.

**Margen para la salida variable:** con 21 V de bus mínimo y 15 V de salida, el ciclo de trabajo máximo es ≈ 0.71, dentro del rango del convertidor.

## 6. Protecciones especificadas

| Protección | Ubicación |
|---|---|
| Fusible de acción lenta | Primario del transformador |
| Varistor (MOV) | Entrada AC |
| Interruptor de encendido | Primario |
| TVS | Bus DC |
| Fusible / PTC por salida | Cada salida |
| Limitación de corriente y apagado térmico | Integrados en cada regulador |
| Diodo de protección contra tensión inversa | Cada salida |
| Resistencia de descarga | Banco de capacitores |
| LED indicador | Bus DC y cada salida |
