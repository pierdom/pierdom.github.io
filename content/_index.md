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
</style>

<div class="mobile-nav">
  <a href="/about">About me</a>
  <a href="/jobs">Experience</a>
  <a href="/education">Education</a>
  <a href="/publications">Publications</a>
</div>

<div style="margin-top:64px; text-align:center; font-size:0.78em; opacity:0.18; transition:opacity 0.3s; font-family:monospace; letter-spacing:0.03em;" onmouseenter="this.style.opacity='0.65'" onmouseleave="this.style.opacity='0.18'">
  <div style="margin-bottom:10px;">I like to play — let's try something different</div>
  <div style="display:flex; justify-content:center; gap:20px; flex-wrap:wrap;">
    <a href="/terminal" style="display:inline-flex; align-items:center; gap:6px; color:inherit; text-decoration:none; border:1px solid currentColor; padding:4px 12px; border-radius:3px;" title="Terminal version">
      <span style="font-size:1.05em;">&#62;_</span> Terminal
    </a>
    <a href="/retro" style="display:inline-flex; align-items:center; gap:6px; color:inherit; text-decoration:none; border:1px solid currentColor; padding:4px 12px; border-radius:3px;" title="Retro 90s version">
      <span style="font-size:1.05em;">📺</span> Retro
    </a>
  </div>
</div>
