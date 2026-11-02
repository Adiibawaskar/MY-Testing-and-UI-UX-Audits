# ⚡ Sitewide QA Audit: Viewport Transition & State Initialization Defect

## 📌 Report Summary
| Metric | Details |
| :--- | :--- |
| **Platform** | Flipkart Web App (Sitewide: Main, Minutes, Travel, Grocery) |
| **Defect Type** | Viewport Transition State Failure / Dynamic Reflow Defect |
| **Impact Level** | High (Requires hard manual reload across all sub-modules) |
| **Severity** | Medium-High |

---

## 🔍 Phenomenon Description
When switching viewports (e.g., from Desktop view to Mobile S, M, or L screen dimensions via browser emulation or device orientation shifts), elements across all Flipkart modules display severe grid scattering, overlapping text, and layout misalignments. 

The layout fails to dynamically adjust to the new dimensions **until a manual page reload (F5 / Refresh) is triggered**. Once refreshed, the DOM re-initializes properly and the page displays as expected for that specific viewport size.

---

## 🎯 Technical Root Cause Analysis

1. **Initialization-Only Script Execution:**
   * CSS media queries and JavaScript layout scripts compute device dimensions strictly upon the `DOMContentLoaded` or `onload` browser events.
   * Key layout calculations (container widths, flex-wrap properties, carousel item offsets) execute only once during initial page fetch.

2. **Missing Active Window Resize Listeners:**
   * The web application lacks dynamic event listeners (`window.addEventListener('resize', ...)`) to handle view transitions without a hard state refresh.

3. **Inline Style Persistence:**
   * Computed pixel values applied directly to inline styles during desktop render persist in memory when transitioning to smaller viewports, causing UI clipping and overflow.

---

## 🔴 Actual vs. 🟢 Expected Behavior

* **🔴 Actual Behavior:** Switching viewport dimensions without reloading results in overlapping header elements, clipped product cards, and broken grid alignments across all Flipkart sub-domains.
* **🟢 Expected Behavior:** The DOM should dynamically recalculate layout dimensions and reflow all components smoothly in real time upon any screen resize, without requiring the user to reload the page.

---

## 📸 Reproduction Steps
1. Open any Flipkart module (`flipkart.com`, `/minutes-store`, `/travel`, etc.) on a desktop browser.
2. Open Chrome Developer Tools (`F12`) and enable the Toggle Device Toolbar (`Ctrl + Shift + M`).
3. Switch the viewport mode from **Responsive / Desktop** to **Mobile S (320px)** or **Mobile M (375px)**.
4. **Observe:** Visual components shatter, overlap, or clip off-screen.
5. Press **F5 / Refresh**.
6. **Observe:** The layout re-renders cleanly and aligns perfectly for the mobile view.
