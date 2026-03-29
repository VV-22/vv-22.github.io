---
layout: portfolio
title: Portfolio
permalink: /portfolio/
description: A showcase of my projects, skills, and experience as a Computer Science graduate.
skills:
  - name: Programming Languages
    items:
      - C++
      - GLSL
      - Python
      - C#
      - JavaScript
      - Java
  - name: Game Development
    items:
      - 3D Graphics
      - OpenGL
      - Vulkan
      - RenderDoc
      - Nvidia Nsight
      - Unity
      - Unreal Engine
      - Blender
  - name: Web Development
    items:
      - Salesforce Stack - Apex, LWC, SOQL
      - Spring boot
      - HTML/CSS
      - REST APIs
      - MongoDB
      - PostgreSQL
  - name: AI/ML & Cloud Tools
    items:
      - CUDA
      - OpenCV
      - Git/GitHub
      - Docker
      - Linux
      - AWS
experience:
  - company: Storm Flag Games
    role: Game Engineer Co-op
    start_date: "Jan 2026"
    end_date: "Current"
    description: "Graphics engineering at Storm Flag Games, adding new features to an in-house engine for a massively popular MMORPG. Working on the transition from a legacy forward renderer to a modernized deferred renderer with real-time lighting, shadows, post-processing and multithreading."
    technologies:
        - C++
        - OpenGL
        - Renderdoc
        - Tracy
        # - Nvidia Nsight
  - company: Northeastern University
    role: Teaching Assistant
    start_date: "Jan 2025"
    end_date: "Jan 2026"
    description: "Teaching Assistant for Game Programming, Programming in C++ and Computer Graphics courses. Responsibilities include evaluating student assignments and conducting office hours to provide academic support."
    technologies:
        - C++
        - OpenGL
        - Unity
        - C#
        - Linux
  - company: Northeastern University
    role: Research Assistant
    start_date: "Jan 2025"
    end_date: "Sep 2025"
    description: "Researching procedural content generation and AI systems. Building intelligent dungeon generators with Binary Space Partitioning and WaveFunction Collapse, coupled with AI that uses behavior trees and perception systems to create unique game environments."
    technologies:
      - Procedural Generation
      - AI Behavior Trees
      - Pathfinding Algorithms
      - Binary Space Partitioning
      - WaveFunction Collapse
      - Game AI
  - company: Deloitte
    role: Software Developer II
    start_date: "July 2021"
    end_date: "Aug 2024"
    description: "Salesforce developer specializing in end-to-end platform development. Built a high-volume notification engine processing 1000+ emails hourly, developed responsive LWC interfaces, created RESTful APIs, and integrated CTI systems."
    technologies:
      - Salesforce
      - Apex
      - LWC
      - REST APIs
      - Sales Cloud
      - Service Cloud
      - Genesys CTI
      - Platform Events
  - company: Dariyal Games
    role: Game Developer Intern
    start_date: "Dec 2019"
    end_date: "Jan 2020"
    description: "Game developer focused on performance optimization. Improved isometric game rendering performance through GPU instancing and occlusion culling, designed city management mechanics with FSM-driven NPCs, and built cross-platform leaderboards with MongoDB."
    technologies:
      - Unity
      - GPU Optimization
      - AI Systems
      - Pathfinding
      - MongoDB
      - Performance Profiling
current_focus:
  - "**Real-time graphics programming** with Vulkan and OpenGL, implementing advanced rendering techniques like deferred rendering, clustered shading, GPU Frustum Culling, PBR, Global Illumination, Multithreading, etc."
  - "**Low-level systems programming** for working on open-source graphics drivers"
  - "**Game AI** Behavior trees, spatial functions, Procedural Content Generation and pathfinding algorithms"
  - "**Web Development** for creating interactive and performant applications"
---

## About Me

<div class="about-section">
  <div class="about-content-grid">
    <div class="about-photo">
      <img src="{{ '/assets/img/photo.jpg' | relative_url }}" alt="Vishnu Vardan" class="profile-photo">
    </div>
    <div class="about-text">
      <p>Hi, I'm Vishnu Vardan, a graduate student at Northeastern University, Boston. I mainly work on graphics and game programming (Vulkan, OpenGL, Unity Engine, Unreal Engine and so on), but I also enjoy working on diverse projects that challenge me to learn and grow. My portfolio spans graphics programming, game development, systems programming, AI/ML applications and web development.</p>

      <p>I'm a former Salesforce developer, having worked at Deloitte USI for 3 years (last role was a "Consultant"(SDE II)). I've worked on a wide span of tech, varying from Frontend development with LWC in Sales and Service Cloud, Backend development using Apex, Asynchronus automations using Batch apex, Queuables and platform events, REST API development and CTI Integrations.</p>
    </div>
    <div class="about-social">
      <a href="mailto:{{ site.email }}" class="social-btn" title="Email">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
        <span>Email</span>
      </a>
      <a href="https://github.com/{{ site.github_username }}" class="social-btn" target="_blank" rel="noopener" title="GitHub">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
        <span>GitHub</span>
      </a>
      <a href="https://www.linkedin.com/in/{{ site.linkedin_username | default: 'your-linkedin' }}" class="social-btn" target="_blank" rel="noopener" title="LinkedIn">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path><rect x="2" y="9" width="4" height="12"></rect><circle cx="4" cy="4" r="2"></circle></svg>
        <span>LinkedIn</span>
      </a>
    </div>
  </div>
</div>
