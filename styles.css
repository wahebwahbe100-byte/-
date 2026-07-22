(() => {
  const menuButton = document.querySelector('.menu-toggle');
  const nav = document.querySelector('.primary-nav');

  menuButton?.addEventListener('click', () => {
    const open = menuButton.getAttribute('aria-expanded') === 'true';
    menuButton.setAttribute('aria-expanded', String(!open));
    menuButton.classList.toggle('active', !open);
    nav?.classList.toggle('open', !open);
  });

  nav?.querySelectorAll('a').forEach(link => {
    link.addEventListener('click', () => {
      menuButton?.setAttribute('aria-expanded', 'false');
      menuButton?.classList.remove('active');
      nav.classList.remove('open');
    });
  });

  const observer = 'IntersectionObserver' in window
    ? new IntersectionObserver((entries, obs) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('is-visible');
            obs.unobserve(entry.target);
          }
        });
      }, { threshold: 0.12 })
    : null;

  document.querySelectorAll('.reveal').forEach(el => {
    if (observer) observer.observe(el);
    else el.classList.add('is-visible');
  });

  document.getElementById('year').textContent = new Date().getFullYear();

  const form = document.getElementById('contact-form');
  const toast = document.getElementById('toast');

  form?.addEventListener('submit', event => {
    event.preventDefault();
    if (!form.reportValidity()) return;

    const data = new FormData(form);
    const subject = `Anfrage: ${data.get('service')}`;
    const body = [
      'Guten Tag MasterCleanNord,',
      '',
      `Name: ${data.get('name')}`,
      `Unternehmen: ${data.get('company') || '-'}`,
      `E-Mail: ${data.get('email')}`,
      `Telefon: ${data.get('phone') || '-'}`,
      `Leistung: ${data.get('service')}`,
      '',
      'Nachricht:',
      data.get('message'),
      '',
      'Mit freundlichen Grüßen'
    ].join('\n');

    toast?.classList.add('show');
    window.setTimeout(() => toast?.classList.remove('show'), 2600);
    window.location.href = `mailto:info@mastercleannord.de?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
  });
})();
