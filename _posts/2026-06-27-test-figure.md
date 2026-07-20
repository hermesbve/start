---
title: "Test: Figure Include"
date: 2026-06-27T00:00:00-04:00
categories:
  - blog
tags:
  - test
  - images
  - figure
header:
  overlay_image: /assets/images/unsplash-image-2.jpg
  overlay_filter: 0.4
  caption: "Forest trail — header image for this post"
excerpt: "Demonstrating the **figure** include helper — single images with captions and lightbox support."
---

This post demonstrates the Minimal Mistakes **figure** include helper.

## Single Image with Caption

A simple figure with a caption using the `{% include figure %}` tag:

{% include figure image_path="/assets/images/unsplash-image-1.jpg" alt="A landscape photograph from Picsum" caption="**Mountain** — a serene landscape captured at golden hour." %}

## Clickable Image (Popup)

With `popup=true`, the image opens in a lightbox:

{% include figure popup=true image_path="/assets/images/unsplash-image-2.jpg" alt="Forest scene" caption="*Forest* — click the image to see it full-size in a lightbox popup." %}

## Image Without Caption

{% include figure image_path="/assets/images/unsplash-image-3.jpg" alt="Ocean waves" %}

That's the figure helper — great for single-image layouts with optional captions and lightbox support.
