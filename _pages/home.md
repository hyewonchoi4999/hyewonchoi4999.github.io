---
layout: splash
permalink: /home/
header:
  overlay_color: "#5e616c"
  overlay_image: /assets/images/background.png
  actions:
    # - label: "<i class='fas fa-download'></i> Install now"
      # url: "/docs/quick-start-guide/"
      - label: "About Me"
        url: /about/
excerpt: >
  Wellcome to my technological blog.<br />
  I will post lecture notes, paper review and projects all related to Artificial Intelligence.<br />
feature_row:
  - image_path: /assets/images/notes.png
    alt: "Lecture Notes"
    title: "Lecture Notes"
    excerpt: "Reviews of lectures taken and to be taken which is related to AI."
    url: "/categories/lectures/"
    btn_class: "btn--primary"
    btn_label: "Go"
  - image_path: /assets/images/papers.png
    alt: "Paper Review"
    title: "Paper Review"
    excerpt: "Reviews of papers published in conferences and arXiv"
    url: "/categories/papers/"
    btn_class: "btn--primary"
    btn_label: "Go"
  - image_path: /assets/images/project.png
    alt: "Personal Project"
    title: "Personal Project"
    excerpt: "Records of all the process, difficulties and challenges of various projects"
    url: "/categories/projects/"
    btn_class: "btn--primary"
    btn_label: "Go"
---

{% include feature_row %}