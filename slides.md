---
marp: true
theme: custom
paginate: true
footer: "© 2025 — Product Documentation | 25f1000038@ds.study.iitm.ac.in"
---

<!--
  Marp presentation: custom theme embedded below.
  The "theme: custom" in front-matter corresponds to the CSS theme comment.
-->

<style>
/* theme: custom */
/* Basic custom theme variables */
section {
  font-family: "Inter", -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
  color: #eaeef6;
  background-color: #0f1724;
}
/* Header styling */
h1, h2, h3 {
  color: #00b7ff;
  text-shadow: 0 1px 0 rgba(0,0,0,0.6);
}
/* Footer / page number styling */
.marp-footer {
  font-size: 0.8rem;
  opacity: 0.9;
}
/* Slide content max width for readability */
section .content {
  max-width: 900px;
  margin: 0 auto;
  line-height: 1.45;
}
/* Special accent for code blocks */
pre {
  border-radius: 8px;
  padding: 1rem;
  background: rgba(255,255,255,0.04);
  overflow: auto;
}

/* Background-image slide tweaks */
.background-slide {
  background-size: cover;
  background-position: center;
  color: #fff;
  text-shadow: 0 2px 6px rgba(0,0,0,0.6);
}

/* Small util */
.meta {
  font-size: 0.9rem;
  opacity: 0.85;
}
</style>

<!-- Title slide -->
# Product Documentation  
### Technical Writer Presentation  
**Contact:** 25f1000038@ds.study.iitm.ac.in

<div class="meta">Version: 1.0 • Maintained in Git</div>

---

# Overview

<div class="content">

- Product architecture  
- Key components  
- Installation  
- API usage examples  
- Complexity & performance analysis

</div>

---

<!-- Background image slide (uses a public image) -->
<!-- Marp will render the image as background if using the full-width ![bg](url) pattern -->
![bg](https://images.unsplash.com/photo-1518770660439-4636190af475)
class: background-slide

# System Architecture

- Frontend (SPA)  
- Backend (microservices)  
- Database (managed SQL + cache)  
- Messaging Layer (event streaming)

---

# Algorithmic Complexity

Consider the algorithm used in the processing pipeline:

\[
T(n) = 3n^2 + 2n + 5 \implies O(n^2)
\]

For the optimized path:

\[
T(n) = n \log n + n \implies O(n \log n)
\]

(Use these Big-O forms when selecting scaling strategies.)

---

# Code Example (CLI)

```bash
curl -X POST https://api.example.com/v1/analyze \
  -H "Authorization: Bearer <token>" \
  -d '{"query":"sample input","limit":10}'

