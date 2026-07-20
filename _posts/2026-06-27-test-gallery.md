---
title: "Test: Gallery Include"
date: 2026-06-27T00:00:00-04:00
categories:
  - blog
tags:
  - test
  - images
  - gallery
header:
  overlay_image: /assets/images/unsplash-image-3.jpg
  overlay_filter: 0.4
  caption: "Ocean waves — header image for the gallery post"
excerpt: "Demonstrating the **gallery** include helper — image grids with lightbox and multiple layouts."
gallery:
  - url: /assets/images/unsplash-image-1.jpg
    image_path: /assets/images/unsplash-image-1.jpg
    alt: "Mountain landscape"
    title: "Mountainscape"
  - url: /assets/images/unsplash-image-2.jpg
    image_path: /assets/images/unsplash-image-2.jpg
    alt: "Forest path"
    title: "Forest Trail"
  - url: /assets/images/unsplash-image-3.jpg
    image_path: /assets/images/unsplash-image-3.jpg
    alt: "Ocean waves"
    title: "Ocean Breeze"
  - url: /assets/images/unsplash-image-4.jpg
    image_path: /assets/images/unsplash-image-4.jpg
    alt: "Desert dunes"
    title: "Desert Solitude"
  - url: /assets/images/unsplash-image-5.jpg
    image_path: /assets/images/unsplash-image-5.jpg
    alt: "City skyline"
    title: "City Lights"
---

This post demonstrates the Minimal Mistakes **gallery** include helper.

## Default Gallery (3-up Layout)

5 images will auto-layout as `third` (3-column grid):

{% include gallery caption="A collection of placeholder images from **Picsum** — click any image to view full-size." %}

## Gallery with `layout: half`

Using `layout="half"` overrides the auto-detection to 2 columns:

{% include gallery id="gallery" layout="half" caption="Same gallery, but in a 2-column layout with `layout='half'`." %}

The gallery helper is great for image sets — portfolios, travel diaries, product shots, and more.
