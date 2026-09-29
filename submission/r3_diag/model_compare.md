# L / R / M

L/R/M là thứ tự box in-scope theo XML của từng frame.

## adasind_001320.jpg
- L1+R2+M4: LRM (center)
- L2+R3: LR_noM (mid)
- L3+R6: LR_noM (edge)
- R1+M2: RM_noL (center)
- R4+M1: RM_noL (edge)
- R5: R_only (mid)
- M3: M_only (center)
- M5: M_only (mid)
- M6: M_only (edge)
## adasind_014670.jpg
- L1+R1+M1: LRM (edge)
- L2+R2+M5: LRM (center)
- L3+R5: LR_noM (mid)
- R3: R_only (mid)
- R4+M4: RM_noL (center)
- M3: M_only (mid)
- M6: M_only (mid)
- M7: M_only (center)
## adasind_034080.jpg
- L1+R6+M2: LRM (mid)
- L3+R1+M1: LRM (mid)
- L4+R3+M5: LRM (edge)
- L2+R7: LR_noM (center)
- L5+R4+M4: LRM (mid)
- R2+M3: RM_noL (center)
- R5: R_only (mid)
- R8: R_only (mid)
- R9: R_only (center)
- M7: M_only (mid)
- M8: M_only (mid)
- M9: M_only (mid)
- M10: M_only (center)
- M11: M_only (center)
- M12: M_only (mid)

## Zone × cell
| zone | LRM | LR_noM | LM_noR | L_only | RM_noL | R_only | M_only |
|---|---|---|---|---|---|---|---|
| center | 2 | 1 | 0 | 0 | 3 | 1 | 4 |
| mid | 3 | 2 | 0 | 0 | 0 | 4 | 7 |
| edge | 2 | 1 | 0 | 0 | 1 | 0 | 1 |
