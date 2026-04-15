# FLAT CUT - RESUMEN COMPACTO

## 🎯 DECISIONES CLAVE

### Flujo de Vendedor (8 pasos en orden visual)
1. Shape (Panel / Custom / Letters)
2. Dimensions (W × H mm) ← VALIDACIÓN: Max 1200×2400, no ambas > 1200
3. Material (ACM / Back Black / Acrylic / PVC)
4. Location (Interior / Exterior)
5. Finishing (opciones dependen de material)
6. Finish Type (Matte/Gloss - solo si Laminate/Vinyl)
7. Mounting (opciones dependen de material)
8. Notes (texto libre)

### Validación Dimensiones
```
✓ 600 × 800 = Valid
✓ 1200 × 1200 = Valid
✓ 1300 × 1000 = Valid (WARN: custom quote)
✓ 800 × 2400 = Valid (WARN: custom quote)
✗ 1300 × 1300 = Invalid (ambas > 1200)
✗ 2500 × 1000 = Invalid (> 2400)
```

---

## 📋 FINISHING OPTIONS POR MATERIAL

**ACM & Back Black**: 1.Raw | 2.UV+Lam | 3.UV+Coat | 4.Vinyl+Lam
**Acrylic**: 1.Raw | ~~2~~ | 3.UV+Coat | 4.Vinyl+Lam (nota: 2 = Decal)
**PVC**: 1.Raw | 2.UV+Lam | 3.UV+Coat | ~~4~~

---

## 🎨 FINISH TYPE (Matte/Gloss)

- **Aparece cuando**: Finishing = "UV Print + Laminate" O "Vinyl Wrap + Laminate"
- **Default**: Gloss (pre-seleccionado)
- **Oculto cuando**: Finishing = "Raw" O "UV Print + Clear Coat"

---

## 🔧 MOUNTING OPTIONS POR MATERIAL

**ACM & Back Black**: 1.Adhesive | 2.Pre-drilled | 3.Standoff | 4.Railing
**Acrylic**: 1.Adhesive | 2.Pre-drilled | 3.Standoff | ~~4~~
**PVC**: 1.Adhesive | 2.Pre-drilled | ~~3~~ | ~~4~~

### Comportamiento Standoff/Railing
- **Standoff seleccionado**: Otros campos deshabilitados
- **Railing seleccionado**: Otros campos deshabilitados
- **Adhesive/Pre-drilled**: Todos habilitados (comportamiento normal)

---

## 📦 ARCHIVOS PRINCIPALES

| Archivo | Propósito |
|---------|-----------|
| **FLAT_CUT_FORM.html** | Form de captura (abrir en navegador) |
| **FLAT_CUT_FINAL_SPECIFICATION.md** | Spec técnica exhaustiva |
| **FLAT_CUT_DECISION_TREES.md** | Árboles de decisión (material → opciones) |
| **PRODUCTO_ROADMAP.md** | 10 productos futuros identificados |
| FLAT_CUT_FORM_DOCUMENTATION.md | Docs técnicas del form |
| FLAT_CUT_VENDOR_QUICK_CARD.md | Tarjeta rápida vendedores |

---

## 🚀 PRÓXIMOS PRODUCTOS

**FASE 1** (Próximas semanas):
1. **DECAL** - Vinyl decals sin sustrato (alta ROI, maquinaria actual)
2. **3D LETTERS** - Letras tridimensionales (diferenciador premium)

**FASE 2** (1-2 meses):
3. **EDGE GLOW** - Flat Cut/3D con LED integrado
4. **PRINTED PANELS** - Supera límite 1340mm (múltiples piezas)

---

## ✅ STATUS

✅ Especificación completa
✅ Form funcional con validaciones
✅ Árboles de decisión documentados
✅ Roadmap de productos identificado
✅ Listo para implementar en código

