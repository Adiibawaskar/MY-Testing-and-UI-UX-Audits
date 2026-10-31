# 🐛 UI Bug Report: Cross-Viewport Breakpoint Failures & Media Query Overlaps

## 📌 Report Summary
| Metric | Details |
| :--- | :--- |
| **Platform** | Flipkart Web (`flipkart.com`) |
| **Tested Breakpoints** | Mobile S (320px), Mobile M (375px), Mobile L (425px), Tablet (768px) |
| **Severity** | High (Degrades core navigation legibility & product presentation) |
| **Modules Affected** | Global Utility Bar, Header Flex Container, Hero Carousel Images |

---

## 🎯 Defect Breakdown

### 1. Header Node Collision & Brand Logo Overlay (Mobile S, M, L)
* **Symptom:** Primary logo SVG/PNG overlaps with sub-brand links ("Minutes", "Travel") and location text nodes.
* **Root Cause:** Absence of media query CSS rules (`@media (max-width: 768px)`) to collapse desktop headers into a unified mobile nav bar.

### 2. Product Banner & Card Image Aspect Ratio Clipping
* **Symptom:** Product images zoom excessively and cut off visual details rather than dynamically scaling down.
* **Root Cause:** Container styling uses fixed height dimensions without setting `object-fit: contain` or `max-width: 100%`.

### 3. Utility Element Overlap on Tablet Breakpoints
* **Symptom:** Address selector strings collide directly into the SuperCoin balance pill (`⚡ 0`).
* **Root Cause:** Missing `flex-shrink: 0` or min-width constraints on top utility items.

---

## 📸 Visual Evidence
* **Mobile Viewport Collisions:** Header links overlapping brand assets.
* **Tablet Utility Misalignment:** Location bar bleeding into SuperCoin container.
* **Media Scaling:** Non-responsive crop on promotional hero images.

---

## 🟢 Expected vs. 🔴 Actual Behavior

* **Expected Result:** Header elements should cleanly collapse into a responsive mobile header drawer; images should preserve aspect ratios using fluid scaling rules.
* **Actual Result:** Text nodes collide and overlap, while product banners truncate image edges across mobile viewports.
