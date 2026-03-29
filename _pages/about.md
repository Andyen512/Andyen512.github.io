---
permalink: /
title: ""
excerpt: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% if site.google_scholar_stats_use_cdn %}
{% assign gsDataBaseUrl = "https://cdn.jsdelivr.net/gh/" | append: site.repository | append: "@" %}
{% else %}
{% assign gsDataBaseUrl = "https://raw.githubusercontent.com/" | append: site.repository | append: "/" %}
{% endif %}
{% assign url = gsDataBaseUrl | append: "google-scholar-stats/gs_data_shieldsio.json" %}

<span class='anchor' id='about-me'></span>

👋 Hello, I am Qingyuan Cai.

I am a second year Ph.D. student at Beijing Normal University.

<span class='anchor' id='research'></span>

# 🔬 Research Interests
- **Computer Vision:** 3D Human Pose Estimation, Biometrics, Video Understanding, Diffusion Models
- **Embodied AI** 

<span class='anchor' id='news'></span>

# 🔥 News
- **[Mar. 2026]** 🎉 One paper accepted by ICME 2026.
- **[Feb. 2026]** 🎉🎉 Two papers accepted by CVPR 2026.
- **[Dec. 2025]** A Unified Open-source 3D Human Pose Estimation framework released on arXiv.
- **[Feb. 2025]** 🎉 One paper accepted by AAAI 2025.
- **[Oct. 2024]** 🎉 One paper accepted by ACM MM 2024.
- **[Feb. 2024]** 🎉 One paper accepted by AAAI 2024.
- **[Sep. 2023]** 🎉 One paper accepted by TMM.

<span class='anchor' id='publications'></span>

# 📚 Publications and Preprints
{% for link in site.data.publications.main %}
<div class='paper-box{% if link.compact %} paper-box-compact{% endif %}'>
  <div class='paper-box-image'>
    <div>
      {% if link.image %}
      <img src='{{ link.image }}' alt='{{ link.title }}' width="100%" style="--paper-image-scale: {{ link.image_scale | default: 1 }};">
      {% endif %}
      {% if link.conference_short %}
      <div class="badge">{{ link.conference_short }}</div>
      {% endif %}
    </div>
  </div>

  <div class='paper-box-text' markdown="1">
**{{ link.title }}**

{{ link.authors }}

<em>{{ link.conference }}</em><br/>
<div class="pub-links">
{% if link.pdf %}<a href="{{ link.pdf }}">Paper</a>{% endif %}
{% if link.code %}<a href="{{ link.code }}">Code</a>{% endif %}
{% if link.project %}<a href="{{ link.project }}">Project Page</a>{% endif %}
{% if link.bibtex %}<a href="{{ link.bibtex }}">BibTex</a>{% endif %}
</div>
{% if link.notes %} **{{ link.notes }}**{% endif %}
{% if link.others %} {{ link.others }}{% endif %}
  </div>
</div>
{% endfor %}

<span class='anchor' id='awards'></span>

# 🏅 Awards
- 🏆 2024.10, National Scholarship for Graduate Students.
- 🥉 2024.10, 3rd Place (Pose) at ACM MM'24 Gait Challenge.

<span class='anchor' id='services'></span>

# 🤝 Services
#### Conference Reviewer
- [AAAI](https://aaai.org/conference/aaai/aaai-26/), [IJCAI](https://www.ijcai.org/), [PRCV](https://www.prcv.cn/)
