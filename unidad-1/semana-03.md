[← Semana 2](semana-02.md) · [Índice](README.md) · [Semana 4 →](semana-04.md)

## Semana 3 · Mapas de Karnaugh, indiferentes y NAND/NOR

### Idea clave
Si dos minitérminos difieren en **una sola variable**, esa variable desaparece (XY + XY' = X). El mapa usa **código Gray** (00-01-11-10) para que los vecinos físicos sean vecinos lógicos; los bordes opuestos también son vecinos (toroide).

Numeración del mapa de 4 variables (AB \ CD):

| AB \ CD | 00 | 01 | 11 | 10 |
|:-:|:-:|:-:|:-:|:-:|
| **00** | 0 | 1 | 3 | 2 |
| **01** | 4 | 5 | 7 | 6 |
| **11** | 12 | 13 | 15 | 14 |
| **10** | 8 | 9 | 11 | 10 |

### Reglas
- Grupos de **2ᵏ celdas**; un grupo de 2ᵏ elimina k variables.
- **Rectangulares** (sin L ni diagonales), **lo más grandes posible**, con bordes y esquinas enrollados.
- **Leer:** variable constante en 1 → A; constante en 0 → A'; si cambia → desaparece.
- **Implicante primo:** no se puede agrandar. **Primo esencial:** único que cubre algún 1. Solución mínima = esenciales + los primos mínimos para cubrir el resto (puede no ser única).
- **POS:** se agrupan los 0 y la lectura se invierte (0 → A, 1 → A').

### Ejemplo: F = Σm(0,1,2,5,8,9,10)
| AB \ CD | 00 | 01 | 11 | 10 |
|:-:|:-:|:-:|:-:|:-:|
| **00** | 1 | 1 | 0 | 1 |
| **01** | 0 | 1 | 0 | 0 |
| **11** | 0 | 0 | 0 | 0 |
| **10** | 1 | 1 | 0 | 1 |

- **B'C'** = m0, m1, m8, m9 · **B'D'** = las 4 esquinas · **A'C'D** = m1, m5.
- **SOP:** `F = B'C' + B'D' + A'C'D` (7 literales). **POS:** `F = (A'+B')(B'+D)(C'+D')` (6 literales). Se elige por costo.
- **Taller T1:** F = Σm(1,3,4,6) → A'C + AC' = A ⊕ C.

### Condiciones indiferentes (X)
Combinaciones que nunca ocurren (p. ej. 1010–1111 en BCD). Notación: `F = Σm(…) + d(…)`. **Como 1** si agrandan un grupo; **como 0** si no ayudan; **nunca solas** en un grupo.

Ejemplo BCD ≥ 5: `F = Σm(5,6,7,8,9) + d(10…15)`

| AB \ CD | 00 | 01 | 11 | 10 |
|:-:|:-:|:-:|:-:|:-:|
| **00** | 0 | 0 | 0 | 0 |
| **01** | 0 | 1 | 1 | 1 |
| **11** | X | X | X | X |
| **10** | 1 | 1 | X | X |

- Sin X: AB'C' + A'BD + A'BC → 9 literales, 3 CI (7404 + 7411 + 7432).
- Con X: **F = A + BD + BC** → 5 literales, 2 CI (7408 + 7432).

### Universalidad NAND y NOR
| Función | Solo NAND | Solo NOR |
|---|---|---|
| NOT | (A·A)' | (A + A)' |
| AND | ((AB)')' | (A' + B')' |
| OR | (A'·B')' | ((A+B)')' |

**SOP mínima → NAND-NAND · POS mínima → NOR-NOR.** Pasos (F = A + BD + BC): doble negación → De Morgan → `F = NAND( A', NAND(B,D), NAND(B,C) )`. El literal que entra solo se complementa. Dos niveles de retardo, una sola familia (7400 + 7410 = 2 CI). El ahorro vino de las X, no de la NAND.

---
[← Semana 2](semana-02.md) · [Índice](README.md) · [Semana 4 →](semana-04.md)
