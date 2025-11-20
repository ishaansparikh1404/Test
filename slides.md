---
marp: true
theme: custom-theme
paginate: true
footer: "© 2025 — Product Documentation | 25f1000038@ds.study.iitm.ac.in"
---
---
marp: true
theme: custom-theme
paginate: true
footer: "© 2025 — Product Documentation | 25f1000038@ds.study.iitm.ac.in"
---

<!--
This is a Marp presentation with:
✔ Custom theme
✔ Page numbers
✔ Background image slide
✔ Math equations
✔ Custom styling
✔ Email included
-->

# Product Documentation  
### Technical Writer Presentation  
**Contact:** 25f1000038@ds.study.iitm.ac.in

---

# Overview

- Product architecture  
- Key components  
- Installation  
- API usage examples  
- Complexity analysis  

---

<!-- Background image slide -->
![bg](https://images.unsplash.com/photo-1518770660439-4636190af475)

# System Architecture

System consists of:  
- Frontend  
- Backend  
- Database  
- Messaging Layer  

---

# Algorithmic Complexity

Example function performance:

\[
T(n) = 3n^2 + 2n + 5 \implies O(n^2)
\]

Another example:

\[
T(n) = \log n + n \implies O(n)
\]

---

# Custom Styled Slide  
<style>
h1 {
  color: #0080ff;
  text-shadow: 1px 1px 2px #0003;
}
ul li {
  font-size: 1.2rem;
  padding: 5px 0;
}
</style>

# Key Features (Styled)

- Auto-scaling architecture  
- Secure authentication  
- Multi-region deployment  
- REST + WebSocket API  

---

# API Example

```bash
curl -X POST https://api.example.com/v1/analyze \
  -H "Authorization: Bearer <token>" \
  -d '{"query": "sample input"}'
