[← Semana 3](semana-03.md) · [Índice](README.md) · [Resumen de la unidad →](resumen.md)

## Semana 4 · Circuitos aritméticos

### Semisumador y sumador completo
La columna 0 suma 2 bits (**semisumador**); las demás suman 3 bits: A, B y Cin (**sumador completo**).

**Semisumador:** `S = A ⊕ B` (XOR), `C = A·B` (AND). Solo sirve para la columna 0.

| A | B | Cin | # de 1 | Cout | S |
|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 2 | 1 | 0 |
| 1 | 0 | 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 2 | 1 | 0 |
| 1 | 1 | 0 | 2 | 1 | 0 |
| 1 | 1 | 1 | 3 | 1 | 1 |

**S = A ⊕ B ⊕ Cin** (número **impar** de unos; en el K-map es un tablero de ajedrez) · **Cout = AB + A·Cin + B·Cin** (**al menos dos** unos).

### Ripple-carry y retardo
- Cuatro sumadores en cadena: **Cout → Cin del siguiente**. Ej.: 0110 + 0111 = 1101 (6 + 7 = 13).
- El acarreo avanza etapa por etapa: **retardo ≈ 2·n·10 ns**. 4 bits → 80 ns · 16 bits → 320 ns · 32 bits → 640 ns.

### Restar con el mismo circuito
`A − B = A + (−B)`; −B = invertir B y sumar 1. Ej.: 0110 + 1101 = 1 0011 → 3 ✓.  
**XOR como inversor controlado:** cada bit de B pasa por `B ⊕ M`. **M = 0** → suma. **M = 1** → resta, y M entra también a Cin del sumador 0 (aporta el +1).

### Overflow y comparador
- **Overflow** (4 bits con signo): 0101 + 0100 = 1001 → −7 ✗. Se detecta con **V = C3 ⊕ C4**. **Cout = 1 NO significa error.**
- **Comparador:** A = B → XNOR por bit y AND de todas. A > B → desde la izquierda, el primer bit distinto decide (integrado 7485).
- **ALU** = sumador/restador + comparador + AND/OR/XOR + multiplexor (semana 5).

### Taller resuelto
| Ejercicio | Resolución |
|---|---|
| 1011 + 0110 | acarreos 0, 1, 1, 1 → **10001** = 17 |
| 0110 − 0011 (M = 1) | 0110 + 1100 + 1 = 1 0011 → **0011 = 3** |
| Retardo 16 bits | 2 · 16 · 10 ns = **320 ns** |
| A = 10, B = 01 | **A > B** verdadero; **A = B** falso |

---
[← Semana 3](semana-03.md) · [Índice](README.md) · [Resumen de la unidad →](resumen.md)
