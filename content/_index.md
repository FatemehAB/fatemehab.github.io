---
# Leave the homepage title empty to use the site title
title: ""
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: "6rem"

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ""
      # Show a call-to-action button under your biography? (optional)
#      button:
#        text: Download CV
#        url: uploads/resume.pdf
    design:
      css_class: dark
      background:
        color: black
        image:
          # Add your image background to `assets/media/`.
          filename: aurora.jpeg
          filters:
            brightness: 0.5
          size: cover
          position: center
          parallax: false
  - block: markdown
    content:
      title: 'My Research'
      subtitle: ''
      text: |-
        My primary research interest is in reinforcement learning (RL) and its application to real-world problems. I'm interested in incorporating human feedback into RL systems to better align them with human preferences, and I'm exploring ways to automate this process using large language models (LLMs) as substitutes for direct human input. Additionally, I'm interested in integrating neural networks with symbolic reasoning methods to improve the interpretability and generalizability of RL agents. I believe by combining these approaches, we can develop more effective and understandable RL systems that perform better in complex, real-world scenarios.

        In addition, I'm interested in integrating neural networks, known for their ability to recognize complex patterns in data, with symbolic reasoning systems capable of abstracting higher-level concepts.
        This integration aims to improve the RL agent's ability to identify logical and hierarchical patterns in complex tasks, thereby increasing clarity, interpretability, and generalizability.
    design:
      columns: '1'
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publication
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: collection
    id: projects
    content:
      title: Selected Projects
      filters:
        folders:
          - project
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: collection
    content:
      title: Recent Publications
      text: ""
      filters:
        folders:
          - publication
        exclude_featured: false
    design:
      view: citation
---
