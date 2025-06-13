---
permalink: "/rendering-with-opengl"
description: "Transformations, Scenegraphs, Shadow Volumes and PBR"
title: "Building a software renderer with OpenGL and C++"
date: "2025-06-12"
layout: post
math: true
---

## Preface

I've been working on a rendering engine in OpenGL. Over the past couple of months, I've built enough to warrant a post here, and so this page was born. The following content works through some (not so heavy) math, a bit of graphics theory, and a sprinkling of C++.

## Premise

As a game developer who also loves playing video games, I've always worked on an abstraction layer, be it Unity or Unreal or any other application. I've never directly with the system level APIs and always wondered how these abstractions work. So when I had the chance to study computer graphics at Northeastern University, I pounced on the it. Over the course of 4 months, I built a small renderer, with support for hierarchial scenengraphs, and some sample scenes with dynamic transformations and so on and so forth. The experience was quite interesting, and left me longing for more. [^a]

And so began my journey of exploration, the ways in which devs have squeezed every last ounce of performance from a computer, how games run the way they do right now are nothing short of black magic.[^b] I've learnt of some of the smoke and mirrors that developers do to mask performance constraints , and how skillfully they blend it with gameplay so the player is never aware of the same. [^c]

## Goals

The original scope of the project was to build a simple software renderer, with support for:

- Physically Based Rendering [^d]
- Shadow Volumes [^e]
- Importance sampling for image based lighting [^f]

But, as I've explored further and further, I've decided to stray a bit from my original goal, and build something that resembles a rendering engine. This means:

- Ability to load and save scenes (text files that save hierarchial scenegraphs)
- GUI View to build complex scenes (Dear ImGUI) [^g]
- Performance uplifts using clustered forward rendering (Referenced from google filament) [^h]
- Anti-Aliasing, HDR, Bloom and Tonemapping.

(This is not an exhaustive list, just something that I've planned for now.)

## Physically Based Rendering

Popularized by Epic Games in Unreal Engine 4, Physically Based Rendering is a way of calculating the contribution of light to the color of a pixel in a way that mimics the real world.
Lets take a small step back and see what that means:

The render equation [^i] is the best way of simulating the visuals of light. This is a super compute-heavy equation, so some very smart people came up with multiple approximations to this equation so that it can be computed in realtime. This approximated equation is called as the reflectance equation, and it looks somewhat like this:

$$L_o(p, \omega_o) = \int_\Omega \left(\kappa_d \frac{c}{\pi} + \frac{DFG}{4(\omega_o \cdot n)(\omega_i \cdot n)}\right) L_i(p, \omega_i) n \cdot \omega_i d\omega_i$$

[^a]: [Github](https://github.com/VV-22/CS5310)
[^b]: [Silent Hill's fog](https://www.polygon.com/playstation/24196061/silent-hill-crash-bandicoot-tech-limitations)
[^c]: [Fast-inverse-square root](https://www.youtube.com/watch?v=p8u_k2LIZyo)
[^d]: [PBR](https://learnopengl.com/PBR/Theory)
[^e]: [Shadow Volume reference](https://ogldev.org/www/tutorial40/tutorial40.html)
[^f]: [Image based lighting](https://learnopengl.com/PBR/IBL/Diffuse-irradiance)
[^g]: [Imgui Github](https://github.com/ocornut/imgui)
[^h]: [Filament reference](https://google.github.io/filament/Filament.html#imagingpipeline/lightpath/clusteredforwardrendering)
[^i]: [Render Equation](https://en.wikipedia.org/wiki/Rendering_equation)