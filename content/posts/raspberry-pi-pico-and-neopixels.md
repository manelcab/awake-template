---
title: Raspberry pi pico and neopixels
subtitle: How to play with neopixels and raspberry pi pico
category:
  - About Awake
author: lenambac
date: 2021-08-26T04:27:56.800Z
featureImage: /uploads/resource-grid-hero.jpg
---
These are the needed components

| #     | Description                                          | Quantity   | Default           |
| -------- | ---------------------------------------------------- | ------ | ----------------- |
| 1 | neopixels | Number | 3                 |
| 2 | total number of resources to display                 | Number | all (lazy loaded) |
| 3 | for posts filters posts only in supplied category(s) | Array  | \[]               |
| 4 | the resource to be retrieved and displayed           | String | Required          |

There are 2 simple wrappers built around the `ResourceGrid` for easily displaying a categories grid or a posts grid, easily enough they are `CategoriesGrid` and `PostsGrid`.

## Examples
```
<--! All posts in grid with 3 per row lazy loaded until no more-->
<posts-grid />

<--! 3 posts in grid in single row -->
<posts-grid :number="3" />

<--! 3 posts in grid in single row in category-1 (exactly how related posts at end of single post is accomplished) -->
<posts-grid :number="3" :category="['category-1']" />

<--! All categories in grid with 3 per row lazy loaded until no more-->
<categories-grid />

<--! etc -->
```
