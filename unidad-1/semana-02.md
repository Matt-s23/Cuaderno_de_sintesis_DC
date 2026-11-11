[← Semana 1](semana-01.md) · [Índice](README.md) · [Semana 3 →](semana-03.md)

## Semana 2 · Álgebra de Boole y formas canónicas

### Circuito = expresión
Cable = variable · AND = producto (·) · OR = suma (+) · NOT = complemento (') · Precedencia: **NOT → AND → OR**. Ej.: `Y = A·B + C'`. Dos expresiones son equivalentes si y solo si tienen la misma tabla de verdad.

### Postulados y dualidad
| Postulado | Forma OR | Forma AND (dual) |
|---|---|---|
| Identidad | X + 0 = X | X · 1 = X |
| Complemento | X + X' = 1 | X · X' = 0 |
| Conmutativa | X + Y = Y + X | XY = YX |
| Distributiva | X(Y+Z) = XY + XZ | **X + YZ = (X+Y)(X+Z)** |

**Dualidad:** intercambiar + ↔ · y 0 ↔ 1 (sin complementar variables) mantiene válida la identidad.

### Teoremas de consulta
| Teorema | Forma OR | Forma AND |
|---|---|---|
| Elemento nulo | X + 1 = 1 | X · 0 = 0 |
| Idempotencia | X + X = X | X · X = X |
| Involución | (X')' = X | |
| Absorción | X + XY = X | X(X + Y) = X |
| Abs. del complemento | X + X'Y = X + Y | X(X' + Y) = XY |
| Adyacencia | XY + XY' = X | (X+Y)(X+Y') = X |
| Consenso | XY + X'Z + YZ = XY + X'Z | (X+Y)(X'+Z)(Y+Z) = (X+Y)(X'+Z) |

### De Morgan: «rompe la barra, cambia el operador»
`(AB)' = A' + B'` · `(A + B)' = A'B'` · generaliza: `(A + B + C)' = A'B'C'`.  
Ej.: `(A' + BC)' = A·(BC)' = A(B' + C') = AB' + AC'`.

### Minitérminos y maxitérminos
| i | ABC | mᵢ (vale 1) | Mᵢ (vale 0) |
|:-:|:-:|---|---|
| 0 | 000 | A'B'C' | A + B + C |
| 1 | 001 | A'B'C | A + B + C' |
| 2 | 010 | A'BC' | A + B' + C |
| 3 | 011 | A'BC | A + B' + C' |
| 4 | 100 | AB'C' | A' + B + C |
| 5 | 101 | AB'C | A' + B + C' |
| 6 | 110 | ABC' | A' + B' + C |
| 7 | 111 | ABC | A' + B' + C' |

- **mᵢ:** producto; variable en 1 → sin complemento, en 0 → complementada. **Mᵢ:** suma; en 0 → sin complemento, en 1 → complementada. Mᵢ = (mᵢ)'.
- **SOP = Σm:** filas con F = 1, unidas con OR. **POS = ΠM:** filas con F = 0, unidas con AND.

### Ejemplo: alarma de 3 sensores (suena si al menos dos se activan)
- Ojo con el enunciado: «exactamente dos» = Σm(3,5,6); «al menos dos» = Σm(3,5,6,7).
- F = Σm(3,5,6,7) = A'BC + AB'C + ABC' + ABC = ΠM(0,1,2,4).
- Con idempotencia: A'BC + ABC = BC · AB'C + ABC = AC · ABC' + ABC = AB → **F = AB + AC + BC** (POS: (A+B)(A+C)(B+C)).
- **Costo:** canónica = 7404 + 2×7411 + 7432 = **4 CI**; simplificada = 7408 + 7432 = **2 CI**.

### Simplificación algebraica y criterio SOP/POS
- Procedimiento: pares adyacentes → duplicar términos (X = X + X) → absorción → absorción del complemento → consenso. No garantiza el mínimo.
- Ej.: `F = A + A'B + AB'C = (A + B) + AB'C = A + B`.
- **¿SOP o POS?** Pocos 1 → SOP · pocos 0 → POS · solo NAND → NAND-NAND (7400) · solo NOR → NOR-NOR (7402). El criterio final es el costo.

---
[← Semana 1](semana-01.md) · [Índice](README.md) · [Semana 3 →](semana-03.md)
