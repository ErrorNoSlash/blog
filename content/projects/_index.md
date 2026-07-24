+++
title = "Projects"
template = "section.html"
sort_by = "date"
+++

# Projects

Things I've built and keep online. Most of these live under the
`errornoslash.be` domain. Hover a card to see what it is.

<style>
.proj-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:1rem;margin:1.75rem 0 0.5rem;align-items:start;}
.proj-card{display:block;border:1px solid color-mix(in srgb, var(--text-color) 22%, transparent);border-radius:6px;padding:1rem 1.15rem;text-decoration:none;color:var(--text-color);transition:border-color .15s ease, transform .15s ease, box-shadow .15s ease;}
.proj-card:hover{border-color:var(--accent-color);transform:translateY(-2px);box-shadow:0 4px 14px color-mix(in srgb, var(--accent-color) 12%, transparent);}
.proj-card .proj-name{color:var(--accent-color);font-weight:700;display:flex;align-items:baseline;gap:.45rem;}
.proj-card .proj-name::before{content:"$";opacity:.55;font-weight:400;}
.proj-card .proj-url{display:flex;gap:.4rem;align-items:baseline;margin-top:.7rem;font-size:.8em;line-height:1.4;color:var(--footnote-color);}
.proj-card .proj-url::before{content:"\2197";flex:none;}
.proj-url-vp{flex:1;min-width:0;overflow:hidden;white-space:nowrap;}
.proj-url-text{display:inline-block;will-change:transform;}
.proj-url-text.marquee{animation:proj-marquee var(--dur,7s) ease-in-out infinite alternate;}
@keyframes proj-marquee{0%,8%{transform:translateX(0);}92%,100%{transform:translateX(var(--shift,0));}}
@media (prefers-reduced-motion: reduce){.proj-url-text.marquee{animation:none;}.proj-url-vp{overflow-x:auto;}}
.proj-card .proj-desc{display:grid;grid-template-rows:0fr;opacity:0;overflow:hidden;font-size:.9em;line-height:1.5;transition:grid-template-rows .2s ease, opacity .2s ease, margin .2s ease;margin:0;}
.proj-card .proj-desc > span{min-height:0;}
.proj-card:hover .proj-desc,.proj-card:focus-visible .proj-desc{grid-template-rows:1fr;opacity:1;margin:.6rem 0 0;border-top:1px solid color-mix(in srgb, var(--text-color) 15%, transparent);padding-top:.6rem;}
@media (hover: none){
.proj-card .proj-desc{grid-template-rows:1fr;opacity:1;margin:.6rem 0 0;border-top:1px solid color-mix(in srgb, var(--text-color) 15%, transparent);padding-top:.6rem;}
}
</style>
<div class="proj-grid">
<a class="proj-card" href="https://hello.errornoslash.be">
<span class="proj-name">Portfolio</span>
<span class="proj-desc"><span>My main site and the front door to everything else.</span></span>
<span class="proj-url"><span class="proj-url-vp"><span class="proj-url-text">hello.errornoslash.be</span></span></span>
</a>
<a class="proj-card" href="https://docs.errornoslash.be">
<span class="proj-name">Docs</span>
<span class="proj-desc"><span>Longer-form write-ups and documentation that don't fit in a blog post.</span></span>
<span class="proj-url"><span class="proj-url-vp"><span class="proj-url-text">docs.errornoslash.be</span></span></span>
</a>
<a class="proj-card" href="https://blog.errornoslash.be">
<span class="proj-name">Blog</span>
<span class="proj-desc"><span>This site. A Zola + Terminus setup where I document the projects I make.</span></span>
<span class="proj-url"><span class="proj-url-vp"><span class="proj-url-text">blog.errornoslash.be</span></span></span>
</a>
<a class="proj-card" href="https://contact.errornoslash.be">
<span class="proj-name">Contact</span>
<span class="proj-desc"><span>U can see my socials here.</span></span>
<span class="proj-url"><span class="proj-url-vp"><span class="proj-url-text">contact.errornoslash.be</span></span></span>
</a>
<a class="proj-card" href="https://docs.errornoslash.be/slashyos/">
<span class="proj-name">SlashyOS</span>
<span class="proj-desc"><span>My flake i use for my laptop and desktop.</span></span>
<span class="proj-url"><span class="proj-url-vp"><span class="proj-url-text">docs.errornoslash.be/slashyos/</span></span></span>
</a>
</div>
<script>
(function(){
  function setup(){
    document.querySelectorAll('.proj-url').forEach(function(u){
      var vp=u.querySelector('.proj-url-vp'), t=u.querySelector('.proj-url-text');
      if(!vp||!t) return;
      var ov=t.scrollWidth - vp.clientWidth;
      if(ov>1){
        t.style.setProperty('--shift', (-ov)+'px');
        t.style.setProperty('--dur', Math.max(4, ov/22).toFixed(1)+'s');
        t.classList.add('marquee');
      } else {
        t.classList.remove('marquee');
        t.style.removeProperty('--shift');
      }
    });
  }
  if(document.readyState!=='loading'){setup();} else {document.addEventListener('DOMContentLoaded', setup);}
  window.addEventListener('resize', setup);
})();
</script>
