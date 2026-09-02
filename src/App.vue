<template>
  <div class="portfolio" :data-theme="theme">
    <!-- NAV -->
    <header class="nav" :class="{ 'is-scrolled': scrolled }">
      <div class="container nav__inner">
        <a href="#home" class="logo">meer<span>.</span>jilani</a>
        <nav class="nav__links">
          <a v-for="item in NAV" :key="item.id" :href="`#${item.id}`"
            :class="{ 'is-active': activeSection === item.id }">{{ item.label }}</a>
        </nav>
        <a href="#contact" class="btn btn--gold btn--sm nav__cta-desktop">Hire Me</a>
        <button class="nav__toggle" aria-label="Open menu" @click="drawerOpen = true">
          <i class="fa-solid fa-bars" />
        </button>
      </div>
    </header>

    <!-- DRAWER -->
    <div class="drawer-overlay" :class="{ 'is-open': drawerOpen }" @click="drawerOpen = false"
      :aria-hidden="!drawerOpen" />
    <aside class="drawer" :class="{ 'is-open': drawerOpen }" :aria-hidden="!drawerOpen">
      <div class="drawer__head">
        <a href="#home" class="logo" @click="drawerOpen = false">meer<span>.</span>jilani</a>
        <button class="drawer__close" aria-label="Close menu" @click="drawerOpen = false"><i
            class="fa-solid fa-xmark" /></button>
      </div>
      <nav class="drawer__nav">
        <a v-for="item in NAV" :key="item.id" :href="`#${item.id}`" @click="drawerOpen = false"
          :class="{ 'is-active': activeSection === item.id }">
          <i :class="`fa-solid ${item.icon}`" />{{ item.label }}
        </a>
      </nav>
      <div class="drawer__foot">
        <a href="#contact" class="btn btn--gold" @click="drawerOpen = false">Hire Me <i
            class="fa-solid fa-arrow-right" /></a>
        <div class="drawer__socials">
          <a href="#" aria-label="GitHub"><i class="fa-brands fa-github" /></a>
          <a href="#" aria-label="LinkedIn"><i class="fa-brands fa-linkedin-in" /></a>
          <a href="#" aria-label="Twitter"><i class="fa-brands fa-x-twitter" /></a>
          <a href="#" aria-label="Dribbble"><i class="fa-brands fa-dribbble" /></a>
        </div>
      </div>
    </aside>

    <!-- HERO -->
    <section class="hero" id="home">
      <div class="hero__bg"><span /><span /></div>
      <div class="container hero__inner">
        <div class="hero__content reveal">
          <span class="eyebrow"><i class="fa-solid fa-circle-dot" /> Available For New Projects</span>
          <h1>Crafting <em>premium</em> Shopify &amp; WordPress experiences for ambitious brands.</h1>
          <p>Shopify, WordPress &amp; Frontend Developer with 4+ years building fast, conversion-focused stores for DTC
            and lifestyle brands worldwide.</p>
          <div class="hero__cta">
            <a href="#portfolio" class="btn btn--gold">View Work <i class="fa-solid fa-arrow-right" /></a>
            <a href="#contact" class="btn btn--ghost">Start a Project</a>
          </div>
          <div class="hero__stats">
            <div><strong>4+</strong><span>Years of Experience</span></div>
            <div><strong>100+</strong><span>Projects Delivered</span></div>
            <div><strong>100%</strong><span>Quality Work</span></div>
          </div>
        </div>
        <div class="hero__visual reveal">
          <div class="portrait">
            <!-- <img src="/assets/img/portrait.jpeg" alt="Portrait of Ghulam Meer Jilani" loading="lazy" /> -->
             <Swiper
              :modules="[Autoplay]"
              :slidesPerView="'auto'"
              :loop="true"
              :spaceBetween="0"
              :autoplay="{
                delay: 3000,
                disableOnInteraction: false
              }"
              class="hero-swiper"
            >
              <SwiperSlide
                v-for="project in HERO_PROJECTS"
                :key="project.title"
                class="hero-slide"
              >
                <img
                  :src="`/assets/img/${project.img}`"
                  :alt="project.title"
                />
              </SwiperSlide>
            </Swiper>
            
          </div>
        </div>
      </div>
    </section>

    <!-- MARQUEE -->
    <section class="marquee">
      <!-- <div class="container">
        <p class="section-mini">Tools &amp; Stack</p>
      </div> -->
      <div class="marquee__track">
        <div class="marquee__row">
          <div v-for="(t, i) in marqueeStack" :key="i" class="marquee__item">
            <img :src="`/assets/logos/${t.file}`" :alt="t.name" loading="lazy" /><span>{{ t.name }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ABOUT -->
    <section class="section" id="about">
      <div class="container about">
        <div class="about__media reveal">
          <div class="about__img"><img src="/assets/img/ghulammeerjilani.jpeg" alt="Ghulam Meer Jilani" loading="lazy" /></div>
          <div class="about__pill"><i class="fa-solid fa-award" /> 3+ years experience</div>
        </div>
        <div class="about__content reveal">
          <p class="section-mini">About</p>
          <h2>I build stores that sell not just sites that look nice.</h2>
          <p>
            I’m Ghulam Meer Jilani, a Shopify, WordPress & Frontend Developer focused on building high-performing, conversion-focused eCommerce stores and custom web experiences.

            With 4+ years of hands-on experience, I help brands turn ideas and designs into fast, responsive, and user-friendly websites that look great and are built to perform.
          </p>
          <ul class="about__list">
            <li><i class="fa-solid fa-check" /> Shopify Liquid &amp; Custom 2.0 sections</li>
            <li><i class="fa-solid fa-check" /> WordPress, Elementor Customization</li>
            <li><i class="fa-solid fa-check" /> HTML, CSS, SCSS, JavaScript</li>
            <li><i class="fa-solid fa-check" /> Figma / XD / PSD → pixel-perfect code</li>
          </ul>
          <div class="about__cta">
            <a href="#contact" class="btn btn--gold">Let's talk <i class="fa-solid fa-arrow-right" /></a>
            <a href="/Meer-Sep-2026.pdf" download class="btn btn--ghost"><i class="fa-solid fa-download" /> Download
              CV</a>
          </div>
        </div>
      </div>
    </section>

    <!-- SERVICES -->
    <section class="section section--alt" id="services">
      <div class="container">
        <div class="section-head reveal">
          <p class="section-mini">Services</p>
          <h2>What I do <em>best</em>.</h2>
        </div>
        <div class="grid grid-3">
          <div v-for="s in SERVICES" :key="s.title" class="card reveal">
            <i :class="`${s.icon} card__icon`" />
            <h3>{{ s.title }}</h3>
            <p>{{ s.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- PORTFOLIO -->
    <section class="section" id="portfolio">
      <div class="container">
        <div class="section-head reveal">
          <p class="section-mini">Selected Work</p>
          <h2>Real builds. <em>Real results.</em></h2>
        </div>
        <div class="filters reveal">
          <div class="filters__group">
            <label class="filters__label" for="platformSelect">Platform</label>
            <div class="select-wrap">
              <select id="platformSelect" v-model="platform">
                <option value="all">All platforms</option>
                <option value="shopify">Shopify</option>
                <option value="wordpress">WordPress</option>
              </select>
              <i class="fa-solid fa-chevron-down" />
            </div>
          </div>
          <div class="filters__group">
            <label class="filters__label" for="nicheSelect">Category</label>
            <div class="select-wrap">
              <select id="nicheSelect" v-model="niche">
                <option value="all">All categories</option>
                <option value="agency">Agency</option>
                <option value="clothing">Clothing</option>
                <option value="jewellery">Jewellery</option>
                <option value="skincare">Skincare</option>
                <option value="supplements">Supplements</option>
              </select>
              <i class="fa-solid fa-chevron-down" />
            </div>
          </div>
        </div>
        <div class="grid grid-3 portfolio-grid">
          <article v-for="(p, i) in visibleProjects" :key="`${p.title}-${i}`" class="project">
            <div class="mockup mockup--desk">
              <div class="mockup__bar"><span /><span /><span /></div>
              <div class="mockup__screen"><img :src="`/assets/img/${p.img}`" :alt="p.title" loading="lazy" /></div>
            </div>
            <div class="project__meta">
              <h3>{{ p.title }}</h3><span>{{ p.sub }}</span>
            </div>
          </article>
        </div>
        <p v-if="filteredProjects.length === 0" class="empty">No projects in this filter — yet.</p>
        <div v-if="visibleCount < filteredProjects.length" class="loadmore-wrap">
          <button type="button" class="btn btn--ghost" @click="visibleCount += 6">Load more <i
              class="fa-solid fa-plus" /></button>
        </div>
      </div>
    </section>

    <!-- EXPERIENCE -->
    <section class="section section--dark" id="experience">
      <div class="container">
        <div class="section-head reveal">
          <p class="section-mini section-mini--gold">Journey</p>
          <h2>Experience <em>&amp;</em> Education.</h2>
          <p class="section-sub">3+ years shipping for global brands, backed by professional certification and
            continuous learning.</p>
        </div>
        <div class="exp-wrap">
          <div class="exp-cols">
            <div class="exp-col exp-col--left">
              <h3 class="exp-col__head"><i class="fa-solid fa-briefcase" /> Experience</h3>
              <div v-for="item in EXPERIENCE" :key="item.role" class="tl-item reveal">
                <div class="tl-card">
                  <div class="tl-head"><span class="tl-period">{{ item.period }}</span><span class="tl-tag">{{ item.tag
                      }}</span></div>
                  <h3>{{ item.role }}</h3>
                  <p class="tl-company">{{ item.company }}</p>
                  <p>{{ item.desc }}</p>
                  <ul class="tl-list">
                    <li v-for="b in item.bullets" :key="b"><i class="fa-solid fa-check" /><span>{{ b }}</span></li>
                  </ul>
                </div>
              </div>
            </div>
            <div class="exp-col exp-col--right">
              <h3 class="exp-col__head"><i class="fa-solid fa-graduation-cap" /> Education</h3>
              <div v-for="item in EDUCATION" :key="item.role" class="tl-item reveal">
                <div class="tl-card">
                  <div class="tl-head"><span class="tl-period">{{ item.period }}</span><span class="tl-tag">{{ item.tag
                      }}</span></div>
                  <h3>{{ item.role }}</h3>
                  <p class="tl-company">{{ item.company }}</p>
                  <p>{{ item.desc }}</p>
                  <ul class="tl-list">
                    <li v-for="b in item.bullets" :key="b"><i class="fa-solid fa-check" /><span>{{ b }}</span></li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- REVIEWS -->
    <section class="section" id="reviews">
      <div class="container">
        <div class="section-head reveal">
          <p class="section-mini">Client Love</p>
          <h2>What founders <em>say</em>.</h2>
        </div>
        <div class="reviews reveal">
          <div class="reviews__viewport">
            <div class="reviews__track" :style="trackStyle">
              <article v-for="r in REVIEWS" :key="r.name" class="review">
                <div class="review__stars"><i v-for="n in r.rating" :key="n" class="fa-solid fa-star" /></div>
                <p class="review__text">"{{ r.text }}"</p>
                <div class="review__author">
                  <div class="review__avatar">{{ r.initials }}</div>
                  <div>
                    <div class="review__name">{{ r.name }}</div>
                    <div class="review__role">{{ r.role }}</div>
                  </div>
                </div>
              </article>
            </div>
          </div>
          <div class="reviews__controls">
            <button aria-label="Previous" @click="reviewIndex = Math.max(0, reviewIndex - 1)"
              :disabled="reviewIndex === 0"><i class="fa-solid fa-arrow-left" /></button>
            <div class="reviews__dots"><span v-for="n in maxIndex + 1" :key="n"
                :class="{ 'is-active': n - 1 === reviewIndex }" /></div>
            <button aria-label="Next" @click="reviewIndex = Math.min(maxIndex, reviewIndex + 1)"
              :disabled="reviewIndex >= maxIndex"><i class="fa-solid fa-arrow-right" /></button>
          </div>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section class="section section--alt" id="contact">
      <div class="container contact">
        <div class="contact__intro reveal">
          <p class="section-mini">Contact</p>
          <h2>Let's build something <em>worth shipping</em>.</h2>
          <p>Have a Shopify migration, a WordPress rebuild, or a landing page that needs to convert? Drop a note — I
            reply within 24 hours.</p>
          <ul class="contact__info">
            <li><i class="fa-solid fa-envelope" /><span>ghulammeerjilani@gmail.com</span></li>
            <li><i class="fa-solid fa-location-dot" /><span>Faisalabad, Pakistan · Remote worldwide</span></li>
            <li><i class="fa-solid fa-clock" /><span>Avg. response: under 24h</span></li>
          </ul>
        </div>
        <form class="contact__form reveal" @submit.prevent="handleSubmit" novalidate>
          <div class="row">
            <div class="field"><label for="name">Name</label><input id="name" v-model="form.name" type="text"
                maxlength="100" required /></div>
            <div class="field"><label for="email">Email</label><input id="email" v-model="form.email" type="email"
                maxlength="255" required /></div>
          </div>
          <div class="row">
            <div class="field"><label for="service">Service Needed *</label>
              <select id="service" v-model="form.service" required>
                <option value="" disabled>Select a service…</option>
                <option v-for="s in SERVICE_OPTIONS" :key="s" :value="s">{{ s }}</option>
              </select>
            </div>
            <div class="field"><label for="subject">Subject</label><input id="subject" v-model="form.subject"
                type="text" maxlength="150" /></div>
          </div>
          <div class="field"><label for="message">Project details</label><textarea id="message" v-model="form.message"
              rows="6" maxlength="2000" required /></div>
          <button type="submit" class="btn btn--gold btn--block">Send Message <i
              class="fa-solid fa-paper-plane" /></button>
          <p class="form-msg" :class="formMsg.kind ? `is-${formMsg.kind}` : ''">{{ formMsg.text }}</p>
        </form>
      </div>
    </section>

    <!-- FOOTER -->
    <footer class="footer">
      <div class="container footer__top">
        <div class="footer__brand">
          <a href="#home" class="logo">meer<span>.</span>jilani</a>
          <p>Shopify, WordPress &amp; Frontend Developer crafting fast, conversion-focused experiences for ambitious
            brands worldwide.</p>
        </div>
        <div class="footer__col">
          <h4>Navigate</h4>
          <ul>
            <li v-for="n in NAV" :key="n.id"><a :href="`#${n.id}`">{{ n.label }}</a></li>
          </ul>
        </div>
        <div class="footer__col">
          <h4>Services</h4>
          <ul>
            <li><a href="#services">Shopify Development</a></li>
            <li><a href="#services">WordPress Builds</a></li>
            <li><a href="#services">Figma to Code</a></li>
          </ul>
        </div>
        <div class="footer__col footer__contact">
          <h4>Get in touch</h4>
          <div class="social_icon">
            <a href="mailto:ghulammeerjilani@gmail.com"> <i class="fa-solid fa-envelope" /></a>
            <a href="https://www.linkedin.com/in/ghulammeerjilani" aria-label="LinkedIn"><i class="fa-brands fa-linkedin-in" /></a>
            <a href="https://www.facebook.com/ghulammeerjilanie" aria-label="facebook"><i class="fa-brands fa-facebook-f" /></a>
            <a href="https://wa.me/+923156055044?text=Hi%20Meer,%20I%20would%20like%20to%20discuss%20a%20project." target="_blank" aria-label="WhatsApp"><i class="fa-brands fa-whatsapp" /></a>
            <a href="https://github.com/meerwebservices" aria-label="GitHub"><i class="fa-brands fa-github" /></a>
          </div>
        </div>
      </div>
      <div class="footer__bottom container">
        <p>© {{ year }} Ghulam Meer Jilani. All rights reserved.</p>
        <p>Designed &amp; built with intent.</p>
      </div>
    </footer>

    <!-- Floating theme gear -->
    <div class="theme-fab" :class="{ 'is-open': themeOpen }">
      <button type="button" class="theme-fab__toggle" aria-label="Change theme" @click="themeOpen = !themeOpen"><i
          class="fa-solid fa-gear" /></button>
      <div class="theme-fab__panel">
        <!-- <p class="theme-fab__title">Theme</p> -->
        <div class="theme-switch" role="group" aria-label="Theme">
          <button v-for="t in THEMES" :key="t.id" type="button" :data-theme="t.id"
            :class="{ 'is-active': theme === t.id }" :title="t.label" @click="theme = t.id" />
        </div>
      </div>
    </div>

    <button class="to-top" :class="{ 'is-visible': showTop }" @click="scrollTop" aria-label="Back to top"><i
        class="fa-solid fa-arrow-up" /></button>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted, watch, withModifiers } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, EffectCoverflow } from 'swiper/modules'
// import { Autoplay, EffectCreative } from 'swiper/modules'
import 'swiper/css'

const NAV = [
  { id: 'about', label: 'About', icon: 'fa-user' },
  { id: 'services', label: 'Services', icon: 'fa-briefcase' },
  { id: 'portfolio', label: 'Work', icon: 'fa-folder-open' },
  { id: 'experience', label: 'Experience', icon: 'fa-graduation-cap' },
  { id: 'reviews', label: 'Reviews', icon: 'fa-star' },
  { id: 'contact', label: 'Contact', icon: 'fa-envelope' },
]

const HERO_PROJECTS = [
  { img: 'belle-clothing.jpg', title: 'Belle Clothing' },
  { img: 'tamir-carpets.jpg', title: 'Tamir Carpets ' },
  { img: 'Purvena-supliment.jpg', title: 'Purvena Supplements' },
  { img: '5-hero-travling.jpg', title: 'travling' },
  { img: '6-hero-tawakkal.jpg', title: 'Tawakkal Fabric' },
  { img: '7-hero-Skin-care.jpg', title: 'skincare' },
  { img: '8-hero-walpaper.jpg', title: 'Decoration' },
  { img: '9-hero-jewlery.jpg', title: 'Centime jewellery' },
  { img: '10-hero-watch.jpg', title: 'Timepieces Finder' },
]

const STACK = [
  { name: 'HTML5', file: 'html5.svg' },
  { name: 'CSS3', file: 'css3.svg' },
  { name: 'Scss', file: 'scss.svg' },
  { name: 'Tailwind', file: 'tailwindcss.svg' },
  { name: 'JavaScript', file: 'javascript.svg' },
  { name: 'jQuery', file: 'jquery.svg' },
  // { name: 'React', file: 'react.svg' },
  { name: 'PHP', file: 'php.svg' },
  { name: 'MySQL', file: 'mysql.svg' },
  { name: 'WordPress', file: 'wordpress.svg' },
  { name: 'Shopify', file: 'shopify.svg' },
  { name: 'GitHub', file: 'github.svg' },
  { name: 'Figma', file: 'figma.svg' },
]
const marqueeStack = [...STACK, ...STACK]

const SERVICES = [
  {
    icon: 'fa-brands fa-shopify',
    title: 'Shopify Development',
    desc: 'Custom themes, Liquid sections, app integrations, and Shopify 2.0 builds engineered for conversion.'
  },
  {
    icon: 'fa-brands fa-wordpress',
    title: 'WordPress Builds',
    desc: 'Custom themes, Elementor, ACF, WooCommerce — fast, secure and SEO-ready websites.'
  },
  {
    icon: 'fa-solid fa-bolt',
    title: 'Speed & Performance',
    desc: 'Core Web Vitals optimisation, lazy loading, image pipelines, and lighthouse-perfect scores.'
  },
  {
    icon: 'fa-solid fa-pen-ruler',
    title: 'Figma → Code',
    desc: 'Pixel-perfect responsive front-end from Figma, XD or Sketch — across desktop, tablet and mobile.'
  },
  {
    icon: 'fa-solid fa-cart-shopping',
    title: 'DTC eCommerce',
    desc: 'Landing pages, product pages, upsells and storefront experiences proven to lift AOV and conversion.'

  },
  {
    icon: 'fa-solid fa-headset',
    title: 'Maintenance & Care',
    desc: 'Monthly retainers for store updates, bug fixes, theme tweaks and ongoing optimisation.'
  },
]

const PROJECTS = [
  {
    title: 'Belle',
    sub: 'Shopify · Clothing . Freelance',
    img: 'belle-home.png',
    platform: 'shopify',
    niche: 'clothing'
  },
  {
    title: 'Pottlam',
    sub: 'Shopify · jewellery . Freelance',
    img: 'portfolio-1.jpg',
    platform: 'shopify',
    niche: 'jewellery'
  },
  {
    title: 'Confiaseiter',
    sub: 'Shopify · Clothing. Freelance',
    img: 'portfolio-2.jpg',
    platform: 'shopify',
    niche: 'clothing'
  },
  {
    title: 'Supplement',
    sub: 'Shopify · supplement . Freelance',
    img: 'portfolio-3.jpg',
    platform: 'shopify',
    niche: 'supplements'
  },
  {
    title: 'Tawakkal',
    sub: 'Shopify · Clothing. Freelance',
    img: 'portfolio-4.jpg',
    platform: 'shopify',
    niche: 'clothing'
  },
  {
    title: 'Hazzard',
    sub: 'WordPress · Agency . Novaprotocol',
    img: 'portfolio-5.png',
    platform: 'wordpress',
    niche: 'agency'
  },
  {
    title: 'Baby Pandas',
    sub: 'Shopify · Clothing. Freelance',
    img: 'portfolio-6.png',
    platform: 'shopify',
    niche: 'clothing'
  },
]

const EXPERIENCE = [
  {
    period: 'Oct 2025 — May 2026', tag: 'On-site', role: 'Shopify & Frontend Developer', company: 'Kineteck · Faisalabad, Pakistan',
    desc: 'Developing and customizing Shopify themes using Liquid, JavaScript and CSS — building scalable, reusable storefront components for international brands.',
    bullets: ['Develop and customize Shopify themes using Liquid, JavaScript and CSS', 'Build reusable sections and dynamic components for scalable store management', 'Collaborate with team on UI/UX improvements and feature implementation']
  },
  {
    period: 'May 2023 — Oct 2025', tag: 'Full-time', role: 'Shopify & WordPress / Frontend Developer', company: 'Blinix Solutions (Pvt) Ltd. · Faisalabad, Pakistan',
    desc: 'Delivered Shopify stores and WordPress websites for international clients — focused on responsive UI, performance and ongoing feature enhancements.',
    bullets: ['Customized Shopify stores and WordPress websites based on client requirements', 'Developed responsive UI components and optimized frontend performance', 'Worked on bug fixing, UI improvements and feature enhancements']
  },
  {
    period: '2021 — 2022', tag: 'Internship', role: 'Web Development Trainee & Intern', company: 'Web Dexterity Training Institute',
    desc: 'Completed an intensive web development program followed by a hands-on internship building responsive sites with HTML, CSS, JavaScript and WordPress.',
    bullets: ['Hands-on training in HTML, CSS, SCSS, JavaScript & jQuery', 'Built WordPress & Elementor projects under senior mentorship']
  },
]

const EDUCATION = [
  {
    period: '2021 — 2022', tag: 'Certification', role: 'Web Development Certification + Internship', company: 'Web Dexterity Training Institute',
    desc: 'Professional web development certification covering modern frontend stack, responsive design and CMS development — followed by a hands-on internship.',
    bullets: ['Frontend stack: HTML, CSS, SCSS, JS, jQuery', 'WordPress & Elementor project work']
  },
  {
    period: '2014 — 2016',
    tag: 'Graduation',
    role: 'Bachelor of Commerce (B.Com)',
    company: 'University of the Punjab',
    desc: 'Bachelor of Commerce (B.Com) from the University of the Punjab, with a strong foundation in accounting, commerce, business, and financial management.',
    bullets: ['University of the Punjab — B.Com', 'Foundation in accounting, commerce & business']
  },
  {
    period: '2009 — 2011', tag: 'Intermediate', role: ' Commerce (I.Com) ', company: 'BISE Faisalabad',
    desc: 'Intermediate education from the Board of Intermediate & Secondary Education, Faisalabad — laying the groundwork for higher studies.',
    bullets: ['BISE Faisalabad — Intermediate', 'Foundation in mathematics & science']
  },
  {
    period: '2007 — 2009', tag: 'Matric', role: 'Matric (Science)', company: 'BISE Faisalabad',
    desc: 'Secondary School Certificate with Science from BISE Faisalabad — early exposure to computing sparked an interest in web technologies.',
    bullets: ['BISE Faisalabad — Matric (Science)', 'First exposure to computing & the web']
  },
]

const REVIEWS = [
  { name: 'Sarah Linwood', role: 'Founder · Lumière Jewelry', text: "Meer rebuilt our Shopify store from the ground up — conversion is up 38% and the site finally feels like our brand.", rating: 5, initials: 'SL' },
  { name: 'Marcus Reid', role: 'CEO · Vital Supplements', text: "Genuinely the best frontend developer we've worked with. Lighthouse 96, custom Liquid sections, zero hand-holding.", rating: 5, initials: 'MR' },
  { name: 'Anya Kovac', role: 'Marketing Lead · Fold Apparel', text: 'Pixel-perfect translation from Figma. Our PDPs are beautiful and finally fast.', rating: 5, initials: 'AK' },
  { name: 'James Whitford', role: 'Founder · Beade Agency', text: 'Shipped a complete WordPress rebuild in three weeks with cleaner code than our internal team.', rating: 5, initials: 'JW' },
  { name: 'Priya Shah', role: 'Brand Director · Lavelin', text: 'Smart, calm, and obsessed with craft. Our skincare site looks luxurious and converts.', rating: 5, initials: 'PS' },
  { name: 'Daniel Okafor', role: 'CTO · Aurea Atelier', text: 'Migrated us from a slow legacy theme to Shopify 2.0 in under a month. CWV all green.', rating: 5, initials: 'DO' },
]

const SERVICE_OPTIONS = ['Shopify Development', 'WordPress Build', 'Speed & Performance Audit', 'Figma → Code', 'DTC Landing Page', 'Maintenance & Care', 'Other / Not sure yet']

const THEMES = [
  { id: 'dark-gold', label: 'Dark + Gold' },
  { id: 'black-white', label: 'Black & White' },
  { id: 'cream-orange', label: 'Cream & Orange' },
  { id: 'light', label: 'Light' },
]

const theme = ref('dark-gold')
const themeOpen = ref(false)
const scrolled = ref(false)
const showTop = ref(false)
const drawerOpen = ref(false)
const activeSection = ref('home')
const platform = ref('all')
const niche = ref('all')
const visibleCount = ref(6)
const reviewIndex = ref(0)
const perView = ref(3)
const form = ref({ name: '', email: '', service: '', subject: '', message: '' })
const formMsg = ref({ text: '', kind: '' })
const year = new Date().getFullYear()

onMounted(() => {
  try { const s = localStorage.getItem('mj-theme'); if (s && THEMES.some(t => t.id === s)) theme.value = s } catch { }
})
watch(theme, v => { try { localStorage.setItem('mj-theme', v) } catch { } })
watch([platform, niche], () => { visibleCount.value = 6 })

const filteredProjects = computed(() => PROJECTS.filter(p => (platform.value === 'all' || p.platform === platform.value) && (niche.value === 'all' || p.niche === niche.value)))
const visibleProjects = computed(() => filteredProjects.value.slice(0, visibleCount.value))
const maxIndex = computed(() => Math.max(0, REVIEWS.length - perView.value))
const trackStyle = computed(() => ({ transform: `translateX(calc(${reviewIndex.value} * -1 * ((100% - ${(perView.value - 1) * 24}px) / ${perView.value} + 24px)))` }))

let scrollHandler, sectionObs, revealObs, reviewTimer, resizeHandler, keyHandler

onMounted(() => {
  scrollHandler = () => { const y = window.scrollY; scrolled.value = y > 30; showTop.value = y > 600 }
  window.addEventListener('scroll', scrollHandler, { passive: true })

  const ids = ['home', ...NAV.map(n => n.id)]
  const els = ids.map(id => document.getElementById(id)).filter(Boolean)
  sectionObs = new IntersectionObserver(entries => entries.forEach(e => { if (e.isIntersecting) activeSection.value = e.target.id }), { rootMargin: '-45% 0px -50% 0px' })
  els.forEach(s => sectionObs.observe(s))

  const setReveal = () => {
    const r = document.querySelectorAll('.reveal:not(.is-visible)')
    revealObs = new IntersectionObserver(entries => entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('is-visible'); revealObs.unobserve(e.target) } }), { threshold: 0.12, rootMargin: '0px 0px -60px 0px' })
    r.forEach(el => revealObs.observe(el))
  }
  setReveal()
  watch([platform, niche, visibleCount], () => { setTimeout(setReveal, 20) })

  resizeHandler = () => { const w = window.innerWidth; perView.value = w < 640 ? 1 : w < 900 ? 2 : 3 }
  resizeHandler(); window.addEventListener('resize', resizeHandler)
  reviewTimer = setInterval(() => { reviewIndex.value = reviewIndex.value >= maxIndex.value ? 0 : reviewIndex.value + 1 }, 5500)

  keyHandler = e => { if (e.key === 'Escape') drawerOpen.value = false }
  window.addEventListener('keydown', keyHandler)
})
watch(drawerOpen, v => { document.body.style.overflow = v ? 'hidden' : '' })

onUnmounted(() => {
  window.removeEventListener('scroll', scrollHandler)
  window.removeEventListener('resize', resizeHandler)
  window.removeEventListener('keydown', keyHandler)
  sectionObs && sectionObs.disconnect(); revealObs && revealObs.disconnect()
  reviewTimer && clearInterval(reviewTimer)
})

function scrollTop() {
   window.scrollTo({ top: 0, behavior: 'smooth' })
}
async function handleSubmit() {
  const { name, email, service, subject, message } = form.value

  const validEmail = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)

  if (!name.trim()) {
    formMsg.value = { text: 'Name is required.', kind: 'error' }
    return
  }

  if (!validEmail) {
    formMsg.value = { text: 'Please enter a valid email address.', kind: 'error' }
    return
  }

  if (!service) {
    formMsg.value = { text: 'Please select a service.', kind: 'error' }
    return
  }

  if (message.trim().length < 10) {
    formMsg.value = { text: 'Message must be at least 10 characters.', kind: 'error' }
    return
  }

  try {
    formMsg.value = { text: 'Sending...', kind: '' }

    const res = await fetch('https://formsubmit.co/ajax/ghulammeerjilani@gmail.com', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        Accept: 'application/json'
      },
      body: JSON.stringify({
        name,
        email,
        service,
        subject,
        message
      })
    })

    const data = await res.json()
    console.log(data)

    if (!res.ok) throw new Error(data.message || 'Submission failed')

    formMsg.value = {
      text: 'Message sent successfully!',
      kind: 'success'
    }

    form.value = {
      name: '',
      email: '',
      service: '',
      subject: '',
      message: ''
    }
  } catch (err) {
    console.error(err)

    formMsg.value = {
      text: err.message || 'Something went wrong.',
      kind: 'error'
    }
  }
}
</script>
