[← Índice de la unidad](README.md) · [Índice](README.md) · [Semana 2 →](semana-02.md)

## Semana 1 · Sistemas numéricos, códigos y compuertas

### Por qué binario
- Un transistor es un interruptor controlado por voltaje: dos estados (0 y 1) se distinguen fácil aunque haya ruido.
- Un «1» es un **rango**. En 74LS: salida 1 ≥ 2,7 V, salida 0 ≤ 0,5 V; la entrada lee 1 si ≥ 2,0 V y 0 si ≤ 0,8 V. Entre 0,8 y 2,0 V hay **zona indefinida** (típico de una entrada sin conectar).
- **Margen de ruido:** alto = 2,7 − 2,0 = 0,7 V; bajo = 0,8 − 0,5 = 0,3 V.

### Sistemas posicionales y conversiones
- Cada posición vale una potencia de la base. Pesos binarios: 128 · 64 · 32 · 16 · 8 · 4 · 2 · 1. Bit = 1 dígito; byte = 8 bits.
- **Decimal → binario:** dividir entre 2 y leer los restos de abajo hacia arriba. Ej.: 25 = 11001₂ (16 + 8 + 1).
- **Hexadecimal:** grupos de 4 bits (A=10 … F=15). **Octal:** grupos de 3 bits.
- Ej.: 157 = 10011101₂ = 9D₁₆ = 235₈.

### Suma y números con signo
- Suma binaria: 0+0=0 · 0+1=1 · 1+1=10 (escribo 0, llevo 1) · 1+1+1=11. Ej.: 1011 + 0110 = 10001 (11 + 6 = 17).
- **Complemento a dos:** el bit izquierdo es el signo. Negativo = **invertir bits y sumar 1**. Con 4 bits: −8 a +7 (8 bits: −128 a +127).
- Ej.: 5 − 3 = 5 + (−3): `0101 + 1101 = 1 0010` → se descarta el 1 sobrante → `0010` = 2 ✓.
- **Desbordamiento:** `0111 + 0001 = 1000` = −8 ✗ (no cabe). Igual que un `int` de 32 bits en Java.

### Códigos
| Código | Qué es | Para qué sirve |
|---|---|---|
| BCD | Cada dígito decimal en 4 bits (157 → 0001 0101 0111). 1010–1111 no se usan | Displays, relojes, contadores |
| Gray | Entre vecinos cambia **un solo bit** (00-01-11-10); método del espejo | Encoders; orden del mapa de Karnaugh |
| ASCII | 7 bits, 128 caracteres: «A» = 65 = 0x41. Sin ñ ni tildes → UTF-8 | Texto |

### Las 7 compuertas
| A | B | NOT A | AND | OR | NAND | NOR | XOR | XNOR |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 1 |

- AND: 1 solo si **todas** valen 1 · OR: 1 si **al menos una** vale 1 · XOR: 1 si son **distintas** · XNOR: 1 si son **iguales**.
- Con solo NAND (o solo NOR) se construye cualquier circuito.
- **74LS08** (4 AND de 2 entradas, DIP-14): VCC = pin 14 (+5 V), GND = pin 7; pin 1 junto a la muesca, conteo antihorario. Código SN 74 LS 08 N: fabricante - rango comercial - familia (LS = TTL, HC = CMOS) - función - encapsulado.

---
[← Índice de la unidad](README.md) · [Índice](README.md) · [Semana 2 →](semana-02.md)
