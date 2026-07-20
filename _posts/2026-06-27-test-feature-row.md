---
title: "Test: Feature Row Include"
date: 2026-06-27T00:00:00-04:00
categories:
  - blog
tags:
  - test
  - images
  - feature_row
header:
  overlay_image: /assets/images/unsplash-image-4.jpg
  overlay_filter: 0.4
  caption: "Desert dunes — header image for the feature row post"
excerpt: "Demonstrating the **feature_row** include helper — image blocks with titles, text, and call-to-action buttons."
feature_row:
  - image_path: /assets/images/unsplash-image-1.jpg
    alt: "Mountain landscape"
    title: "Mountain Adventure"
    excerpt: "Explore rugged peaks and serene valleys. This feature block uses the default alignment with an image, title, and excerpt text."
  - image_path: /assets/images/unsplash-image-4.jpg
    alt: "Desert dunes"
    title: "Desert Expedition"
    excerpt: "Vast dunes stretch to the horizon. This block adds a **call-to-action button** that links to an external resource."
    url: "https://picsum.photos"
    btn_label: "View Gallery"
    btn_class: "btn--inverse"
  - image_path: /assets/images/unsplash-image-5.jpg
    alt: "City skyline"
    title: "Urban Explorer"
    excerpt: "Discover hidden corners of the city. A third feature block demonstrating how content wraps neatly in a row."
feature_row2:
  - image_path: /assets/images/unsplash-image-2.jpg
    alt: "Forest trail"
    title: "Forest Walks"
    excerpt: "Lush greenery and peaceful trails — a second row using a different YAML key (`feature_row2`)."
  - image_path: /assets/images/unsplash-image-3.jpg
    alt: "Ocean waves"
    title: "Coastal Vibes"
    excerpt: "Endless waves crashing on golden shores. No button here, just pure content."
    url: "https://picsum.photos"
    btn_label: "Learn More →"
---

This post demonstrates the Minimal Mistakes **feature_row** include helper.

## Default Feature Row

Using `{% include feature_row %}` renders the `feature_row` YAML array as three columns:

{% include feature_row %}

## Centered / Single Feature Row

Using `type="center"` centers content. Let's show just the first item with centered layout:

{% include feature_row id="feature_row2" type="center" %}

Feature rows are ideal for splash pages, landing sections, or any grid-based layout with images, text, and calls to action.
