---
title: Mini Home Display 
date: 2025-06-02
categories: [PCB, Programming]
tags: []     # TAG names should always be lowercase
author: <author_id>
description: My first project, a mini home display that utilizes an lcd as a display that takes sensor inputs
toc: false
---

<!-- ![Desktop View](/assets/lib/Home-Display/Schematic.png){: w="700" h="400"}

{% include embed/youtube.html id='8RjkiRD_ySs' %} 
5687190801612800-proj-->


<div id="commentbox"></div>

<script>
  function loadCommentBoxTheme() {
    const theme = document.documentElement.getAttribute('data-theme') === 'dark' ? 'dark' : 'light';
    const container = document.getElementById('commentbox');
    if (!container) return;

    container.innerHTML = ''; // clear previous

    const script = document.createElement('script');
    script.src = 'https://commentbox.io/client.js';
    script.async = true;
    script.setAttribute('data-commentbox-id', '5687190801612800-proj'); // replace if needed
    script.setAttribute('data-theme', theme);
    container.appendChild(script);
  }

  // Run after page load
  document.addEventListener('DOMContentLoaded', () => {
    loadCommentBoxTheme();

    // Observe theme changes via MutationObserver
    const observer = new MutationObserver(() => {
      loadCommentBoxTheme();
    });

    observer.observe(document.documentElement, {
      attributes: true,
      attributeFilter: ['data-theme']
    });
  });
</script>
