# FLAT CUT FORM - Documentation

## Overview
Single-page HTML form for vendors to configure Flat Cut products. All fields visible at once, organized in visual order (Shape → Dimensions → Material → Location → Finishing → Mounting → Notes).

## Features

### 1. **Visual Layout**
- **Grid layout** (2 columns on desktop, 1 column on mobile)
- **Sections** for each configuration step
- **Color-coded header** (gradient purple)
- **Responsive design** (mobile-friendly)

### 2. **Form Sections (8 Steps)**

#### Step 1: Shape
- Options: Panel / Custom Shape / Letters
- Radio buttons styled as clickable cards
- Visual feedback on selection (purple background)

#### Step 2: Dimensions (W × H)
- Two input fields (Width × Height in mm)
- Side-by-side layout
- **Auto-validation**: Warns if > 1200mm (beyond capacity)
- Warning message: "Dimensions exceed standard capacity (1200mm max). May require custom quote."

#### Step 3: Material
- Dropdown select (not radio, since more than 4 options)
- Options:
  - ACM 3mm
  - Back Black ACM 3mm
  - Acrylic 3-10mm
  - Acrylic 10-20mm
  - PVC 10-30mm
- **Auto-validation**: Warns if PVC + Exterior selected

#### Step 4: Location
- Options: Interior / Exterior
- Radio buttons styled as cards
- **Auto-validation**: Warns if Exterior + UV Print (recommends Vinyl)

#### Step 5: Finishing
- Options: Raw / UV Print + Laminate / UV Print + Clear Coat / Vinyl Wrap + Laminate
- Radio buttons in 4-column grid
- Wraps to 2 rows on smaller screens

#### Step 6: Finish Type (if Laminate)
- Options: Matte / Gloss
- Only relevant if finishing includes Laminate or Vinyl
- Currently always visible (no conditional hiding as requested)

#### Step 7: Mounting
- Options: Adhesive / Pre-drilled / Standoffs / Screws
- Radio buttons in 4-column grid

#### Step 8: Notes
- Free text textarea
- Min-height: 100px
- For: Font details, rush delivery, orientation, custom requests, etc.

### 3. **Real-Time Validations**

#### Dimension Warning
- **Trigger**: Width OR Height > 1200mm
- **Message**: "⚠️ Dimensions exceed standard capacity (1200mm max). May require custom quote."
- **Icon**: Warning icon (⚠️)
- **Color**: Yellow background (#fff3cd)

#### Material Warning (PVC + Exterior)
- **Trigger**: Material = "PVC" AND Location = "Exterior"
- **Message**: "⚠️ PVC is NOT recommended for exterior use (UV decolouration risk). Consider Acrylic instead."
- **Color**: Yellow background

#### Location Warning (Exterior + UV Print)
- **Trigger**: Location = "Exterior" AND Finishing = "UV Print + Laminate" OR "UV Print + Clear Coat"
- **Message**: "💡 For exterior durability, consider "Vinyl Wrap + Laminate" (superior UV resistance)."
- **Color**: Yellow background
- **Icon**: Info icon (💡)

### 4. **Summary Panel**
- **Appears when**: All required fields are filled
- **Location**: Below form, before action buttons
- **Content**: 
  - Shape, Dimensions, Material, Location
  - Finishing, Finish Type, Mounting, Notes
  - All values displayed in clean table format
- **Background**: Light blue (#f8f9ff)
- **Update**: Real-time as user changes selections

### 5. **Action Buttons**

#### Save Configuration Button
- **Style**: Gradient purple button
- **Text**: "💾 Save Configuration"
- **Action**: Saves form data to browser localStorage
- **Feedback**: "✓ Configuration saved successfully" message appears (green, auto-hides after 3 sec)
- **Data**: JSON object with all fields + timestamp

#### Generate PDF Button
- **Style**: Gray outlined button
- **Text**: "📄 Generate PDF"
- **Disabled**: Until all required fields are filled
- **Action**: 
  1. Populates hidden PDF section with form data
  2. Generates PDF file named "FlatCut_Configuration.pdf"
  3. Auto-downloads to user's device
- **PDF Content**: 
  - Header with "FLAT CUT" title
  - Configuration details in table format
  - Date generated
  - Professional layout (Arial font, clean spacing)

### 6. **Data Persistence**
- Form saves to **browser localStorage** under key: `flatCutConfig`
- Stored as JSON string with timestamp
- Survives page refresh
- Can be retrieved programmatically via `JSON.parse(localStorage.getItem('flatCutConfig'))`

### 7. **PDF Generation**
- Uses **html2pdf.js** library (CDN)
- Generates PDF on-demand (no backend required)
- File naming: `FlatCut_Configuration.pdf`
- Format: A4 portrait
- Contains: All 8 configuration fields + generation date

## Usage Flow

```
1. Vendor opens form
2. Selects SHAPE (Panel / Custom / Letters)
3. Enters DIMENSIONS (W × H)
   - System checks if > 1200mm and warns
4. Selects MATERIAL (dropdown)
   - System checks if PVC + Exterior and warns
5. Selects LOCATION (Interior / Exterior)
   - System checks if Exterior + UV Print and suggests Vinyl
6. Selects FINISHING (4 options)
7. Selects FINISH TYPE (Matte / Gloss)
8. Selects MOUNTING (4 options)
9. Enters optional NOTES
10. Reads auto-populated SUMMARY
11. Clicks "Save Configuration" → Success message
12. Clicks "Generate PDF" → PDF downloads

Data is saved to localStorage and can be retrieved later.
```

## Technical Details

### Browser Compatibility
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Requires JavaScript enabled
- localStorage support required (all modern browsers)

### Dependencies
- **html2pdf.js** (CDN): For PDF generation
- No other external libraries
- Pure HTML/CSS/JavaScript

### Styling
- **Color scheme**:
  - Primary: Purple gradient (#667eea → #764ba2)
  - Success: Green (#d4edda)
  - Warning: Yellow (#fff3cd)
  - Text: Dark gray (#333)
  - Borders: Light gray (#e0e0e0)

- **Typography**:
  - Sans-serif (Segoe UI / system fonts)
  - Font weights: 400 (regular), 600 (bold)

### Responsive Breakpoints
- Desktop: 2-column grid
- Tablet/Mobile: 1-column grid (max-width: 768px)

## Future Enhancements

1. **Backend integration**: Send data to server instead of localStorage
2. **Conditional fields**: Hide Finish Type if Raw selected
3. **Product images**: Show visual representations of each option
4. **Calculations**: Add estimated cost/production time
5. **Email integration**: Send form as email attachment
6. **Approval workflow**: Route to production team for review
7. **Template system**: Save/load previous configurations
8. **Multi-language**: Localization for Spanish, Portuguese, etc.

## File Details

**Filename**: `FLAT_CUT_FORM.html`
**Size**: Single HTML file (~18KB)
**Format**: Self-contained (all CSS/JS inline)
**No dependencies**: Except html2pdf.js CDN

## How to Use

1. **Open in browser**: Just double-click or drag into browser
2. **Fill out form**: Follow visual order (1-8)
3. **Save**: Click "Save Configuration" button
4. **Export PDF**: Click "Generate PDF" button
5. **Retrieve data**: Check browser console or localStorage

## Customization

To modify:
- **Colors**: Edit CSS color values (#667eea, #764ba2, etc.)
- **Warnings**: Edit message text in JavaScript validation functions
- **Options**: Add/remove select options in HTML
- **Fields**: Add new form sections (copy existing template)
- **PDF layout**: Edit html2pdf options or print-section HTML

---

**Version**: 1.0
**Last Updated**: April 2026
**Status**: Production Ready
