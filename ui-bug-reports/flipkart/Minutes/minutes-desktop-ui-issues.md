# ⚡ Flipkart Minutes - UI/UX & QA Audit Suite

This directory contains specialized quality assurance audits, layout test cases, and responsive breakpoint evaluations for **Flipkart Minutes** (Flipkart's hyperlocal quick-commerce vertical).

---

## 📂 Audit Reports Index

| Module / Component | Defect Focus | Severity | Report Link |
| :--- | :--- | :--- | :--- |
| **Desktop Homepage & Feed** | Sub-nav Z-Index Overlap, Loading State Layout Shift & Carousel Arrow Clipping | **High** | [View Minutes Desktop Audit](./minutes-desktop-ui-issues.md) |

---

## 🎯 Key Test Scenarios Covered
1. **Hyperlocal State Initialization:** Verifying how the web client handles zip-code mapping, dark-store asynchronous data fetching, and loading state skeletons.
2. **DOM Layering & Z-Index:** Checking sticky sub-category navigation bars against hero banner art elements to prevent text collision.
3. **Horizontal Feed Margins:** Auditing card overflow boundaries and navigation arrow alignment on ultra-wide desktop monitors.
