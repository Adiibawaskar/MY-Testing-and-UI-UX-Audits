# 🐛 UI Bug Report: Flipkart Minutes Desktop Layout & Z-Index Layering Failures

## 📌 Report Overview
| Metric | Details |
| :--- | :--- |
| **Platform** | Flipkart Minutes Web (`flipkart.com/flipkart-minutes-store`) |
| **Module** | Hyperlocal Homepage & Category Feed |
| **Tested Viewport** | Desktop (1920x1080) |
| **Severity** | High (DOM Z-Index overlaps & grid overflow collisions) |

---

## 🎯 Defect Breakdown

### 1. Navigation Bar Z-Index Overlap on Banner
* **Symptom:** Sub-category menu items (`For You`, `Party`, `Fresh`) and sponsor text (`Powered by...`) bleed directly on top of the hero carousel banner.
* **Root Cause:** Incorrect `z-index` layering on sticky sub-header relative to dynamic banner slides.

### 2. Loading State Layout Collapse & Skeleton Shift
* **Symptom:** When fetching dynamic inventory, the page body collapses into an unstyled dark container with massive vertical whitespace.
* **Impact:** Causes layout cumulative layout shifts (CLS) and visual flicker during page load.

### 3. Product Carousel Grid Truncation & Arrow Collision
* **Symptom:** Horizontal product card feeds cut off card text along right margins, while navigation arrows (`>`) render directly over price tags.
* **Root Cause:** Container overflow is set to hidden without setting proper right-side padding (`padding-right`) or responsive flex gaps.

### 4. Excessive Desktop Side Margin Waste
* **Symptom:** Main content feed uses rigid fixed-width bounds on high-resolution desktop screens.
* **Impact:** Leaves wide empty margins while squishing card elements inside tight inner columns.

---

## 📸 Visual Evidence
* **Header Z-Index Overlap:** Text bleeding over top banner art.
* **Grid Overflow:** Right-arrow nav colliding into product price text.
* **Skeleton Collapse:** Dark unstyled loading state container.

---

## 🟢 Expected vs. 🔴 Actual Behavior

* **Expected Result:** Clear z-index separation between navigation bars and page banners; fluid CSS grid layouts on desktop viewports.
* **Actual Result:** Overlapping text nodes, layout shift during data load, and arrow collisions over product card details.
