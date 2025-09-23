---
layout: page
title: Raytracing
description: 3D, software and math
img: assets/img/44.png
importance: 1
category: coding
related_publications: true
---

This project demonstrates the power and beauty of ray tracing to create realistic 3D graphics. With a clean, minimal setup from [Walnut](https://github.com/StudioCherno/Walnut), this application uses fundamental ray tracing techniques to render 3D spheres with accurate lighting, shadows, and reflections. This is made for educational purpose and the referenced sources are mentioned in the `Attribute` section.

## Features
* Ray Tracing Fundamentals: Implements essential ray tracing techniques, including ray-object intersection, shadows, and reflections.
* Realistic Lighting: Captures realistic light behavior to illuminate scenes beautifully, featuring emissive material to act as a light source.

## Screenshots
* Pic 1: light and shadow with emissive material
* Pic 2: spheres of different matierals (diffuse, emissive, mirror)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/22.png" title="cert1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/33.png" title="cert2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Attribute
The application uses the template [Walnut](https://github.com/StudioCherno/Walnut) as a starting point. The RayTracing techniques and code references are from [Cherno's RayTracing tutorial](https://www.youtube.com/watch?v=gfW1Fhd9u9Q) and [RayTracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html).
