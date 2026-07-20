---
title: ""
date: 2025-03-23
draft: false
---

<style>
.mobile-nav {
  display: none;
}
@media (max-width: 767px) {
  .mobile-nav {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin: 28px auto 24px;
    max-width: 340px;
  }
}
.mobile-nav a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: 0.9em;
  padding: 8px 18px;
  border: 1px solid rgba(96,165,250,0.35);
  background: rgba(96,165,250,0.07);
  color: inherit;
  text-decoration: none !important;
  transition: background 0.15s, border-color 0.15s;
}
.mobile-nav a:hover {
  background: rgba(96,165,250,0.16);
  border-color: rgba(96,165,250,0.7);
}
.easter-egg-wrap {
  position: relative;
  min-height: clamp(200px, 38vh, 480px);
  width: 100%;
  display: flex;
  flex-direction: column;
}
.easter-egg {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
}
@media (max-width: 767px) {
  .easter-egg-wrap {
    position: static;
    min-height: unset;
  }
  .easter-egg {
    position: static;
    transform: none;
    margin-top: 48px;
  }
}
</style>

<p style="text-align:center; font-size:0.92em; margin:0 auto 28px; max-width:480px; line-height:1.6; font-family:'IBM Plex Mono','Courier New',monospace;"><span style="opacity:0.55;">Building data functions and AI products</span><br><span style="font-size:1.25em; font-weight:700; opacity:0.75;">that move business metrics</span></p>

<div class="mobile-nav">
  <a href="/about">About me</a>
  <a href="/jobs">Experience</a>
  <a href="/education">Education</a>
  <a href="/publications">Publications</a>
</div>

<div class="easter-egg-wrap">
<div class="easter-egg" style="text-align:center; font-size:0.78em; opacity:0.18; transition:opacity 0.3s; font-family:monospace; letter-spacing:0.03em;" onmouseenter="this.style.opacity='0.65'" onmouseleave="this.style.opacity='0.18'">
  <div style="margin-bottom:10px;">I like to play — let's try something different</div>
  <div style="display:flex; justify-content:center; gap:20px; flex-wrap:wrap;">
    <a href="/terminal" style="display:inline-flex; align-items:center; gap:6px; color:inherit; text-decoration:none; border:1px solid currentColor; padding:4px 12px; border-radius:3px;" title="Terminal version">
      <span style="font-size:1.05em;">&#62;_</span> Terminal
    </a>
    <a href="/retro" style="display:inline-flex; align-items:center; gap:6px; color:inherit; text-decoration:none; border:1px solid currentColor; padding:4px 12px; border-radius:3px;" title="Retro 90s version">
      <span style="font-size:1.05em;">📺</span> Retro
    </a>
    <a href="/notebook" style="display:inline-flex; align-items:center; gap:6px; color:inherit; text-decoration:none; border:1px solid currentColor; padding:4px 12px; border-radius:3px;" title="Jupyter notebook version">
      <span style="font-size:1.05em;">📊</span> Notebook
    </a>
  </div>
</div>
</div>
