---
layout: page
title: Model-free control and optimization
description: Extremum seeking and zeroth-order methods that steer systems to optimal operating points using measurements alone.
img:
importance: 3
category:
related_publications: true # lists the papers named in the nocite tag below under "References"
---

Many control problems must be solved without an accurate model: the objective is available only through measurements, and the system can only be probed, not predicted. We develop feedback laws that optimize or stabilize dynamical systems in this setting. A central tool is extremum seeking, in which small periodic or stochastic perturbations reveal gradient information online; we analyze such schemes through Lie-bracket averaging and singular perturbation theory, and extend them to hybrid, event-triggered, and resetting architectures that provide robust global guarantees, including under unknown control directions.

This thrust also covers feedback optimization of stochastic plants, zeroth-order optimization on manifolds, and the stability of learning dynamics driven by non-conservative vector fields, such as those arising in games. Applications range from bio-inspired source seeking, motivated by how sperm cells locate an egg, to the real-time optimization of engineered systems.

{% nocite abdelgalil2026synergistic abdelgalil2026resetting tang2026separation abdelgalil2025liebracket ochoa2025nesterov abdelgalil2025eventtriggered abdelgalil2025manifolds abdelgalil2024initialization abdelgalil2023multitime abdelgalil2023singularly abdelgalil2022seaurchin abdelgalil2022recursive abdelgalil2021vanishing %}
