---
title: 'CV'
date: 2024-09-03
type: landing

design:
  spacing: '5rem'

# Note: `username` refers to the user's folder name in `content/authors/`

# Page sections
sections:
  - block: resume-experience
    content:
      username: admin
    design:
      # Hugo date format
      date_format: 'January 2006'
      # Education or Experience section first?
      is_education_first: false
  - block: collection
    content:
      title: Publications
      filters:
        folders:
          - publication
        exclude_featured: false
    design:
      view: citation
  - block: resume-skills
    content:
      title: Skills
      username: admin
    design:
      show_skill_percentage: false
  - block: resume-awards
    content:
      title: Honors and Awards
      username: admin
---
