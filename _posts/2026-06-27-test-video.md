---
title: "Test: Responsive Video Embed"
date: 2026-06-27T00:00:00-04:00
categories:
  - blog
tags:
  - test
  - video
  - youtube
header:
  overlay_image: /assets/images/unsplash-image-1.jpg
  overlay_filter: 0.4
  caption: "Mountain landscape"
excerpt: "Demonstrating the **responsive video embed** helper — YouTube, Vimeo, and more with GDPR-friendly privacy-enhanced mode."
---

This post demonstrates the Minimal Mistakes **responsive video embed** helper. It supports YouTube, Vimeo, Google Drive, and Bilibili — all responsive and GDPR-compliant.

## YouTube

### Easy Leathercraft Tips and Tricks

A great starter video with practical leathercraft tips:

{% include video id="aniYTEfIe94" provider="youtube" %}

### Advanced Leather Crafting Tips and Tricks

For those looking to level up their skills:

{% include video id="jZkLydH49xM" provider="youtube" %}

## Start at a Specific Timestamp

Append `?start=SECONDS` to the video ID to begin playback at a point:

{% include video id="jZkLydH49xM?start=30" provider="youtube" %}

This one starts 30 seconds in — useful for jumping straight to the good part.

## Vimeo Example

The same helper works with Vimeo (swap `provider="vimeo"` and use the Vimeo video ID):

{% include video id="212731897" provider="vimeo" %}

*(Replace the ID above with your own Vimeo video.)*

## Google Drive

You can also embed videos hosted on Google Drive:

{% include video id="1u41lIbMLbV53PvMbyYc9HzvBug5lNWaO" provider="google-drive" %}

## Syntax Reference

```liquid
{% include video id="VIDEO_ID" provider="youtube" %}
{% include video id="VIDEO_ID" provider="vimeo" %}
{% include video id="VIDEO_ID" provider="google-drive" %}
{% include video id="VIDEO_ID" provider="bilibili" %}
```

All embeds are fully responsive — they scale with the viewport and respect the user's privacy settings.
