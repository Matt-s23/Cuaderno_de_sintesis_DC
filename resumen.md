[← Semana 4](semana-04.md) · [Índice](README.md)

## Resumen y errores frecuentes

| Tema | Regla |
|---|---|
| Negativo | −B = invertir bits + 1 |
| Canónicas | Σm = filas con 1 · ΠM = filas con 0 |
| De Morgan | (AB)' = A' + B' · (A + B)' = A'B' |
| Karnaugh | 2ᵏ celdas elimina k variables · SOP agrupa 1 · POS agrupa 0 |
| NAND / NOR | SOP → NAND-NAND · POS → NOR-NOR |
| Sumador | S = A ⊕ B ⊕ Cin · Cout = AB + A·Cin + B·Cin |
| Resta / overflow | B ⊕ M y Cin = M · V = C3 ⊕ C4 |

**Errores a evitar:** confundir «al menos dos» con «exactamente dos» · poner m2 antes que m3 (el orden es 00, 01, **11, 10**) · grupos en L o que no son potencia de 2 · olvidar bordes y esquinas · grupos solo de X · no invertir la lectura en POS · confundir Cout con overflow · dejar entradas de CI sin conectar.

**Conexión:** esto es el bloque combinacional del proyecto integrador (semana 6, Logisim-evolution); la Unidad 2 agrega memoria y la Unidad 3 pasa a VHDL en la Basys 3.
