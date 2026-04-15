# FLAT CUT - DECISION TREES

## 🌳 TREE 1: MATERIAL → FINISHING AVAILABILITY

```
┌──────────────────────────────────────────────────────────────────────────────┐
│ ACM 3mm                                                                      │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Raw                                                                        │
│ ✓ UV Print + Laminate                                                       │
│ ✓ UV Print + Clear Coat                                                     │
│ ✓ Vinyl Wrap + Laminate                                                     │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ Back Black ACM 3mm (reverso gloss para fences)                              │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Raw                                                                        │
│ ✓ UV Print + Laminate                                                       │
│ ✓ UV Print + Clear Coat                                                     │
│ ✓ Vinyl Wrap + Laminate                                                     │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ Acrylic 3-10mm                                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Raw                                                                        │
│ ✗ UV Print + Laminate      [NOT available]                                  │
│ ✓ UV Print + Clear Coat                                                     │
│ ✓ Vinyl Wrap + Laminate    (Decal si es parcial)                            │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ Acrylic 10-20mm                                                             │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Raw                                                                        │
│ ✗ UV Print + Laminate      [NOT available]                                  │
│ ✓ UV Print + Clear Coat                                                     │
│ ✓ Vinyl Wrap + Laminate    (Decal si es parcial)                            │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ PVC 10-30mm   ⚠️ INTERIOR ONLY                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Raw                                                                        │
│ ✓ UV Print + Laminate                                                       │
│ ✓ UV Print + Clear Coat                                                     │
│ ✗ Vinyl Wrap + Laminate    [NOT available]                                  │
└──────────────────────────────────────────────────────────────────────────────┘
```

## 🌳 TREE 2: MATERIAL → MOUNTING AVAILABILITY

```
┌──────────────────────────────────────────────────────────────────────────────┐
│ ACM 3mm                                                                      │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Adhesive Backing                                                           │
│ ✓ Pre-drilled Holes with Threads                                            │
│ ✓ Standoff                                                                   │
│ ✓ Railing                                                                    │
│                                                                              │
│ NOTE: Standoff & Railing are mutually exclusive                             │
│       When selected, other mounting options are disabled                     │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ Back Black ACM 3mm                                                           │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Adhesive Backing                                                           │
│ ✓ Pre-drilled Holes with Threads                                            │
│ ✓ Standoff                                                                   │
│ ✓ Railing                                                                    │
│                                                                              │
│ NOTE: Standoff & Railing are mutually exclusive                             │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ Acrylic 3-10mm                                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Adhesive Backing                                                           │
│ ✓ Pre-drilled Holes with Threads                                            │
│ ✓ Standoff                                                                   │
│ ✗ Railing             [NOT available for Acrylic]                           │
│                                                                              │
│ NOTE: Standoff is mutually exclusive with others                            │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ Acrylic 10-20mm                                                             │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Adhesive Backing                                                           │
│ ✓ Pre-drilled Holes with Threads                                            │
│ ✓ Standoff                                                                   │
│ ✗ Railing             [NOT available for Acrylic]                           │
│                                                                              │
│ NOTE: Standoff is mutually exclusive with others                            │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ PVC 10-30mm   ⚠️ LIMITED OPTIONS (Heavy material)                           │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Adhesive Backing                                                           │
│ ✓ Pre-drilled Holes with Threads                                            │
│ ✗ Standoff            [NOT available for PVC - too heavy]                   │
│ ✗ Railing            [NOT available for PVC]                                │
└──────────────────────────────────────────────────────────────────────────────┘
```

## 🌳 TREE 3: FINISH TYPE VISIBILITY & DEFAULT

```
Finish Type appears ONLY if:
├─ UV Print + Laminate
├─ UV Print + Clear Coat
└─ Vinyl Wrap + Laminate

Finish Type is HIDDEN if:
└─ Raw

DEFAULT when appears:
└─ Gloss (always pre-selected)

Options always available when visible:
├─ Matte
└─ Gloss (DEFAULT)
```

## 📊 VALIDATION RULES

### Dimension Validation (Max 1200×2400)
```
RULES:
1) If W > 2400 or H > 2400
   └─ ERROR: "Maximum dimension is 2400mm"

2) If W > 1200 AND H > 1200
   └─ ERROR: "If one exceeds 1200mm, other max 1200mm"

VALID combinations:
✓ 1200 × 2400
✓ 2400 × 1200
✓ 1000 × 1000
✓ 600 × 600

INVALID:
✗ 2401 × 1000 (exceeds 2400)
✗ 1100 × 1100 (both > 1100)
✗ 2400 × 2400 (both max)
```

### Material Warnings
```
PVC + Exterior
  └─ ⚠️ "PVC NOT recommended (UV decolouration)"

Exterior + UV Print
  └─ 💡 "Use Vinyl Wrap for better durability"
```

### Mounting Mutual Exclusion
```
Standoff selected:
├─ DISABLE: Adhesive, Pre-drilled, Railing
└─ ENABLE: Only Standoff

Railing selected:
├─ DISABLE: Adhesive, Pre-drilled, Standoff
└─ ENABLE: Only Railing

Other (Adhesive/Pre-drilled):
└─ ENABLE: All options available
```

---

**Form Status**: ✅ v3 implements all logic
**Next Steps**: Quote engine + approval workflow
