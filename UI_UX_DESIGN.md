# 🎨 UI/UX Design Specification - Smart Specs With Scanner & Voice Input (MARVIS)

## 1. Design Philosophy
The MARVIS interface balances **audio-first accessibility** for wearers with a **high-tech glassmorphism dashboard** for remote monitors or caregivers.

---

## 2. Color Palette & Typography

### Color Palette
- **Background**: `#090d16` (Deep Space Dark Navy)
- **Primary Accent**: `#00f2fe` (Electric Cyan)
- **Secondary Accent**: `#39ff14` (Neon Assist Green)
- **Warning / Alert**: `#ff3366` (Crimson Red)
- **Text Primary**: `#f8fafc` (Pure Slate White)
- **Card Background**: `rgba(18, 24, 38, 0.75)` (Glassmorphism Blur)

### Typography
- **Primary Font**: `Outfit`, sans-serif
- **Code / Monospace**: `Space Mono`, monospace
- **Contrast Ratios**: Exceeds WCAG AAA standard ($7:1$) for outdoor visibility.

---

## 3. UI Component Architecture

```
+-----------------------------------------------------------------------+
|  🕶️ MARVIS SMART SPECS DASHBOARD                   [LIVE CAM] [AUDIO] |
+-----------------------------------+-----------------------------------+
|                                   |                                   |
|   LIVE CAMERA VIEWFINDER          |   REAL-TIME OCR TEXT FEED         |
|   +---------------------------+   |   +---------------------------+   |
|   |                           |   |   | "PARACETAMOL 500MG       |   |
|   |   [Bounding Box Overlay]  |   |   |  Take 1 tablet every 8h   |   |
|   |                           |   |   |  Keep out of reach..."    |   |
|   +---------------------------+   |   +---------------------------+   |
|   [ 📸 Trigger Scan ] [🔊 TTS ]   |   [ 📋 Copy ] [ 💾 Save ]     |
|                                   |                                   |
+-----------------------------------+-----------------------------------+
|  📜 SCAN HISTORY LOG & RECENT DOCUMENTS                               |
+-----------------------------------------------------------------------+
```

---

## 4. Accessibility & Audio UI Rules
- **Voice Feedback Confirmation**: Every command issued by voice provides a subtle audio chime followed by verbal confirmation (e.g. "Scanning document...").
- **High-Contrast Text Overlay**: Bounding boxes around detected text are rendered in high-contrast neon green (`#39ff14`) with dark drop shadows.
- **Screen Reader Support**: All dashboard elements feature explicit ARIA attributes (`aria-label`, `role="status"`).
