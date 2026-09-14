---
layout: about
title: about
permalink: /
show_title: false

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false
  more_info: >
    <p>Mahmoud Abdelgalil</p>
    <p>Mechanical and Aerospace Engineering</p>
    <p>University at Buffalo (SUNY)</p>
    <p>1006 Furnas Hall</p>
    <p>Buffalo, NY 14260</p>
    <p>maabdelg [at] buffalo [dot] edu</p>

selected_papers: true # includes a list of papers marked as "selected={true}"
social: false # icons live in the navigation (sidebar, or top bar on narrow screens)

announcements:
  enabled: true
  scrollable: true
  limit: 5

latest_posts:
  enabled: false
  scrollable: true
  limit: 3
---

<style>
  /* Keep each line of the contact block under the photo on one line: the photo column is 30% of the page,
     so shrink the monospace font with the window (13px max). Phones stack the photo full width. */
  .profile .more-info p { display: block; white-space: nowrap; } /* theme uses inline-block, which pairs short lines */
  @media (min-width: 576px) { .profile .more-info { font-size: min(13px, 1.4vw); } }
  @media (max-width: 575.98px) { .profile .more-info { font-size: 13px; } }
  /* Next to the sidebar navigation (>= 992px) the photo column is narrower, so scale the font with the remaining width. */
  @media (min-width: 992px) { .profile .more-info { font-size: min(13px, calc((100vw - 240px) * 0.0146)); } }
  /* The photo and contact block run past the intro text; let "news" start right after the text, with the
     news list narrowed beside the contact block (flow-root), instead of leaving a blank band until the photo ends. */
  article > .clearfix::after { clear: none; }
  article > .news { display: flow-root; }
  /* News date column: fit the date instead of the theme's fixed 20% (inline style, hence !important). */
  .news table tr > :first-child { width: 1% !important; white-space: nowrap; padding-right: 1.5rem; }
</style>

I am an Assistant Professor of Mechanical and Aerospace Engineering at the University at Buffalo (SUNY), where I joined the faculty in Fall 2026. Before coming to Buffalo, I was a postdoctoral researcher at UC San Diego, and I received my PhD from UC Irvine.

My group studies how dynamical systems, from single robots to large collectives, can be steered, coordinated, and made robust in the presence of uncertainty, adversaries, and limited information. Representative problems include distribution steering, model-free and extremum-seeking control, and multi-agent coordination under adversarial interference. Our work draws on geometric control theory, optimal mass transport, and stochastic analysis, toward autonomous systems that act reliably in the physical world.

**I am recruiting funded PhD students for Fall 2027.** If you have a strong mathematical background and an interest in control, optimization, or learning for autonomous systems, see the [team page](/team/) for details on how to apply.
