<script>
(function(){
  if (!/^\/partnerek(\/|$)/i.test(location.pathname)) return;

  // LOGÓK – a repo gyökeréből
  const IMG = {
    mostbet  : ['/mostbet.png'],
    nv       : ['/nv.png'],
    winspirit: ['/winspirit.jpg'],
    '1xslots': ['/1xslots.png']
  };

  // Ha a korábbi kódod is IMG-t használ, innentől a jó helyre mutat.
  // Ha nem, akkor a kártyacímek alapján illesztünk képet:
  document.querySelectorAll('.card, article.card').forEach(card=>{
    const title = (card.querySelector('h2,h3,.h2,.h3')||{}).textContent||'';
    const key = /mostbet/i.test(title) ? 'mostbet'
            : /nv/i.test(title) ? 'nv'
            : /win\s*spirit/i.test(title) ? 'winspirit'
            : /1x\s*slots/i.test(title) ? '1xslots'
            : null;
    if (!key) return;
    if (card.querySelector('.spx-logo')) return; // már be lett téve

    const img = document.createElement('img');
    img.src = IMG[key][0];
    img.alt = title.trim() + ' logo';
    img.className = 'spx-logo';
    img.style.display='block';
    img.style.maxWidth='160px';
    img.style.margin='8px auto 10px';

    const head = card.querySelector('h2,h3,.h2,.h3');
    if (head) head.replaceWith(img); else card.prepend(img);
  });
})();
</script>
