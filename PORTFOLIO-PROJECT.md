# BOGAÇ ÜLKER — Video Editor Portfolio

## Proje Özeti

Spor odaklı video editör ve motion designer için minimalist portfolyo websitesi. İrlanda merkezli, global hedef kitle.

**Site:** bogaculker.com (veya tercih edilen domain)  
**Dil:** İngilizce (tek dil)  
**Stil:** Siyah-beyaz minimalist, koyu tema

---

## Tech Stack

| Bileşen | Teknoloji | Notlar |
|---------|-----------|--------|
| Framework | **Astro 4.x** | Static site generation, partial hydration |
| Styling | **Tailwind CSS** | Utility-first, custom config |
| Icons | **Phosphor Icons** | 7000+ ikon, 6 ağırlık, web package |
| Animations | **CSS transitions** | Vanilla CSS, minimal JS |
| Video (Landing) | **Bunny.net Stream** | Loop videolar için |
| Video (Long-form) | **YouTube Embed** | Mevcut içerikler |
| Video (Shorts) | **YouTube Embed** | Dikey format |
| Forms | **Formspree** | Ücretsiz tier yeterli |
| Hosting | **Cloudflare Pages** | Ücretsiz, sınırsız bandwidth |
| Analytics | **Cloudflare Analytics** | Privacy-friendly |

---

## Dosya Yapısı

```
/
├── public/
│   ├── fonts/
│   │   └── (custom font dosyaları varsa)
│   ├── images/
│   │   ├── profile.jpg
│   │   └── og-image.jpg
│   └── favicon.svg
│
├── src/
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   ├── VideoCard.astro
│   │   ├── ShortCard.astro
│   │   ├── ContactForm.astro
│   │   └── VideoModal.astro
│   │
│   ├── layouts/
│   │   ├── BaseLayout.astro      # Ortak HTML wrapper
│   │   └── PageLayout.astro      # Header + content + footer
│   │
│   ├── pages/
│   │   ├── index.astro           # Landing (3x3 grid)
│   │   ├── long-form.astro
│   │   ├── shorts.astro
│   │   ├── about.astro
│   │   └── contact.astro
│   │
│   ├── data/
│   │   ├── loops.json            # Landing loop bilgileri
│   │   ├── longform.json         # YouTube video listesi
│   │   └── shorts.json           # Shorts listesi
│   │
│   └── styles/
│       └── global.css            # Base styles, fonts
│
├── astro.config.mjs
├── tailwind.config.mjs
├── package.json
└── README.md
```

---

## Tasarım Sistemi

### Renkler

```css
:root {
  /* Backgrounds */
  --bg-primary: #000000;
  --bg-secondary: #0a0a0a;
  --bg-card: #1a1a1a;
  --bg-card-hover: #252525;
  
  /* Text */
  --text-primary: #ffffff;
  --text-secondary: #888888;
  --text-muted: #555555;
  --text-subtle: #333333;
  
  /* Borders */
  --border-primary: #333333;
  --border-subtle: #1a1a1a;
  
  /* Accent (kullanılırsa) */
  --accent: #ffffff;
}
```

### Tipografi

```css
/* Font Family */
font-family: 'Helvetica Neue', 'Arial', sans-serif;

/* Alternatif: Inter veya custom font */

/* Font Sizes */
--text-xs: 0.625rem;    /* 10px - meta, labels */
--text-sm: 0.6875rem;   /* 11px - nav, small text */
--text-base: 0.8125rem; /* 13px - body */
--text-md: 0.875rem;    /* 14px - descriptions */
--text-lg: 1.25rem;     /* 20px - logo */
--text-xl: 1.75rem;     /* 28px - headings */
--text-2xl: 2.25rem;    /* 36px - hero titles */

/* Letter Spacing */
--tracking-tight: -0.025em;
--tracking-normal: 0;
--tracking-wide: 0.05em;
--tracking-wider: 0.1em;
```

### Spacing

```css
/* Base unit: 4px */
--space-1: 0.25rem;   /* 4px */
--space-2: 0.5rem;    /* 8px */
--space-3: 0.75rem;   /* 12px */
--space-4: 1rem;      /* 16px */
--space-5: 1.25rem;   /* 20px */
--space-6: 1.5rem;    /* 24px */
--space-8: 2rem;      /* 32px */
--space-10: 2.5rem;   /* 40px */
--space-12: 3rem;     /* 48px */
--space-16: 4rem;     /* 64px */
```

### Grid Gap

```css
/* Landing grid gap */
--grid-gap: 4px;

/* Content grid gap */
--content-gap: 20px;

/* Shorts grid gap */
--shorts-gap: 16px;
```

### İkonlar (Phosphor Icons)

**Kurulum:**
```bash
npm install @phosphor-icons/web
```

**Kullanım (HTML/Astro):**
```html
<!-- Regular (varsayılan) -->
<i class="ph ph-play"></i>

<!-- Bold -->
<i class="ph-bold ph-play"></i>

<!-- Fill -->
<i class="ph-fill ph-play"></i>

<!-- Duotone (dark theme için ideal) -->
<i class="ph-duotone ph-play"></i>
```

**Global CSS'e ekle:**
```css
@import "@phosphor-icons/web/regular";
@import "@phosphor-icons/web/bold";
@import "@phosphor-icons/web/fill";
/* Sadece kullanılacaklar import edilmeli */
```

**Projede Kullanılacak İkonlar:**

| İkon | Sınıf | Kullanım |
|------|-------|----------|
| Play | `ph-play` | Video thumbnail overlay |
| X (Close) | `ph-x` | Modal kapatma |
| Envelope | `ph-envelope` | Email linki |
| LinkedinLogo | `ph-linkedin-logo` | LinkedIn |
| InstagramLogo | `ph-instagram-logo` | Instagram |
| XLogo | `ph-x-logo` | X / Twitter |
| YoutubeLogo | `ph-youtube-logo` | YouTube |
| ArrowRight | `ph-arrow-right` | CTA, linkler |
| ArrowUpRight | `ph-arrow-up-right` | External link indicator |

**İkon Boyutları:**
```css
.icon-sm { font-size: 16px; }
.icon-md { font-size: 20px; }
.icon-lg { font-size: 24px; }
.icon-xl { font-size: 32px; }
```

---

## Sayfa Spesifikasyonları

### 1. Landing Page (`/`)

**Layout:** Tam ekran 3x3 grid, scroll yok

```
┌──────────┬──────────┬──────────┐
│  Loop 1  │  Loop 2  │  Loop 3  │
├──────────┼──────────┼──────────┤
│  Loop 4  │  LOGO +  │  Loop 5  │
│          │   NAV    │          │
├──────────┼──────────┼──────────┤
│  Loop 6  │  Loop 7  │  Loop 8  │
└──────────┴──────────┴──────────┘
```

**Orta Hücre İçeriği:**
- Logo: "bogaç ülker"
- Alt başlık: "video editor & motion designer"
- Nav: Long-form | Shorts | About | Contact

**Video Loop Davranışı:**
- Autoplay, muted, loop, playsinline
- 3-5 saniye uzunluk
- Tıklanamaz (sadece vitrin)
- Hover efekti yok (veya çok subtle)

**Mobil (< 768px):**
- Logo + nav üste taşınır (ayrı header)
- Grid: 2 sütun × 4 satır
- Her hücre aspect-ratio: 16/9

**Video Kaynağı:**
```html
<video 
  autoplay 
  muted 
  loop 
  playsinline
  poster="/images/loop-1-poster.jpg"
>
  <source src="https://stream.bunny.net/xxx/loop-1.mp4" type="video/mp4">
</video>
```

---

### 2. Long-form Page (`/long-form`)

**Layout:** Header + 2 sütun video grid

**Header:**
- Sol: Logo (tıklanabilir, ana sayfaya)
- Sağ: Nav (aktif sayfa highlight)

**Video Grid:**
- 2 sütun (desktop), 1 sütun (mobil)
- Gap: 20px
- Padding: 30px

**Video Card Yapısı:**
```
┌─────────────────────────┐
│           [▶]           │
│      THUMBNAIL          │
│        16:9             │
│                 [12:34] │
├─────────────────────────┤
│ Video Title             │
│ Description text...     │
│ 2024 • Sports • Editor  │
└─────────────────────────┘
```

**Play Button Overlay:**
```html
<div class="thumbnail-overlay">
  <i class="ph-fill ph-play icon-xl"></i>
</div>
```

**Hover:**
- `transform: translateY(-4px)`
- `box-shadow: 0 10px 40px rgba(0,0,0,0.5)`

**Tıklama Davranışı:**
- Modal açılır
- YouTube iframe embed oynar
- Modal dışına tıklayınca veya ESC ile kapatılır

**Video Modal:**
```html
<div class="modal-overlay">
  <div class="modal-content">
    <button class="close-btn">
      <i class="ph ph-x icon-lg"></i>
    </button>
    <div class="video-wrapper">
      <iframe src="https://youtube.com/embed/VIDEO_ID?autoplay=1"></iframe>
    </div>
    <div class="video-details">
      <h2>Video Title</h2>
      <p>Description</p>
    </div>
  </div>
</div>
```

---

### 3. Shorts Page (`/shorts`)

**Layout:** Header + 5 sütun dikey grid

**Grid:**
- 5 sütun (desktop)
- 3 sütun (tablet)
- 2 sütun (mobil)
- Gap: 16px

**Short Card Yapısı:**
```
┌─────────┐
│         │
│  9:16   │
│ THUMB   │
│         │
│         │
├─────────┤
│ Title   │
│ 0:58    │
└─────────┘
```

**Hover:**
- `transform: scale(1.03)`

**Tıklama:**
- Modal açılır (dikey format)
- Veya YouTube Shorts linkine yönlendirme

---

### 4. About Page (`/about`)

**Layout:** Header + 2 sütun içerik

**Sol Sütun:**
- Profil fotoğrafı (180x180, border-radius: 50%)
- İsim: "Boğaç Ülker"
- Unvan: "VIDEO EDITOR & MOTION DESIGNER"
- Bio: 2-3 cümle

**Sağ Sütun:**
- Services listesi
- Tools listesi
- Experience listesi

**Mobil:** Tek sütun, dikey akış (fotoğraf > isim > bio > listeler)

**Content:**
```json
{
  "name": "Boğaç Ülker",
  "title": "Video Editor & Motion Designer",
  "location": "Dublin, Ireland",
  "bio": "I am a visual storyteller obsessed with rhythm and emotion. My work bridges the gap between raw documentary realism and stylized cinematic precision.",
  "services": [
    "Video Editing",
    "Motion Graphics", 
    "Color Grading",
    "Sound Design"
  ],
  "tools": [
    "Adobe Premiere Pro",
    "After Effects",
    "DaVinci Resolve"
  ],
  "experience": [
    {
      "company": "Socrates Magazine",
      "role": "Video Editor",
      "current": true
    },
    {
      "company": "ShyftUp",
      "role": "Motion Designer",
      "current": false
    },
    {
      "company": "TRTSPOR",
      "role": "TV Contributor",
      "current": false
    }
  ]
}
```

---

### 5. Contact Page (`/contact`)

**Layout:** Header + 2 sütun

**Sol Sütun:**
- Başlık: "Let's Work Together"
- Alt metin: 1-2 cümle
- Sosyal linkler (Phosphor Icons ile):
  - `ph-envelope` Email
  - `ph-linkedin-logo` LinkedIn
  - `ph-instagram-logo` Instagram
  - `ph-x-logo` X / Twitter
  - `ph-youtube-logo` YouTube

**Sosyal Link Component:**
```html
<a href="#" class="social-link">
  <i class="ph ph-linkedin-logo icon-md"></i>
  <span>LinkedIn</span>
  <i class="ph ph-arrow-up-right icon-sm"></i>
</a>
```

**Sağ Sütun:**
- İletişim formu:
  - Name (required)
  - Email (required)
  - Message (required, textarea)
  - Submit button

**Form İşleme:**
```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
  <!-- inputs -->
</form>
```

**Mobil:** Tek sütun (başlık > sosyal > form)

---

## Data Yapıları

### loops.json (Landing)
```json
[
  {
    "id": 1,
    "src": "https://stream.bunny.net/xxx/loop-1.mp4",
    "poster": "/images/posters/loop-1.jpg",
    "alt": "Match highlight edit"
  },
  // ... 8 loop
]
```

### longform.json
```json
[
  {
    "id": "video-1",
    "title": "Project Title",
    "description": "Brief description of the video content.",
    "youtubeId": "dQw4w9WgXcQ",
    "thumbnail": "/images/thumbnails/video-1.jpg",
    "duration": "12:34",
    "year": "2024",
    "category": "Sports",
    "role": "Editor"
  }
]
```

### shorts.json
```json
[
  {
    "id": "short-1",
    "title": "Short Title",
    "youtubeId": "abc123",
    "thumbnail": "/images/thumbnails/short-1.jpg",
    "duration": "0:58"
  }
]
```

---

## SEO & Meta

### Base Meta (tüm sayfalar)
```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="author" content="Boğaç Ülker">
<meta name="robots" content="index, follow">
<link rel="canonical" href="https://bogaculker.com{pathname}">

<!-- Favicon -->
<link rel="icon" type="image/svg+xml" href="/favicon.svg">
```

### Open Graph
```html
<meta property="og:type" content="website">
<meta property="og:site_name" content="Boğaç Ülker">
<meta property="og:title" content="{pageTitle}">
<meta property="og:description" content="{pageDescription}">
<meta property="og:image" content="https://bogaculker.com/og-image.jpg">
<meta property="og:url" content="https://bogaculker.com{pathname}">
```

### Twitter Card
```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="{pageTitle}">
<meta name="twitter:description" content="{pageDescription}">
<meta name="twitter:image" content="https://bogaculker.com/og-image.jpg">
```

### Sayfa Bazlı Meta

| Sayfa | Title | Description |
|-------|-------|-------------|
| Landing | Boğaç Ülker — Video Editor & Motion Designer | Sports-focused video editor and motion designer based in Dublin. |
| Long-form | Long-form — Boğaç Ülker | YouTube videos and long-form content edited by Boğaç Ülker. |
| Shorts | Shorts — Boğaç Ülker | Vertical short-form content and reels. |
| About | About — Boğaç Ülker | Learn about Boğaç Ülker's background, skills, and experience. |
| Contact | Contact — Boğaç Ülker | Get in touch for video editing and motion design projects. |

---

## Deployment

### Cloudflare Pages Setup

1. GitHub repo'ya push et
2. Cloudflare Dashboard → Pages → Create project
3. Connect GitHub repo
4. Build settings:
   - Framework preset: Astro
   - Build command: `npm run build`
   - Build output directory: `dist`
5. Deploy

### Environment Variables
```
# Formspree (opsiyonel, form ID zaten public)
PUBLIC_FORMSPREE_ID=your_form_id
```

### Custom Domain
1. Cloudflare Pages → Custom domains
2. Add domain: bogaculker.com
3. DNS otomatik configure edilecek

---

## Geliştirme Aşamaları

### Faz 1: Temel Yapı
- [ ] Astro projesi oluştur
- [ ] Tailwind config
- [ ] Base layout
- [ ] Global styles
- [ ] Sayfa routing

### Faz 2: Landing Page
- [ ] 3x3 grid layout
- [ ] Orta hücre (logo + nav)
- [ ] Video placeholder'lar
- [ ] Mobil responsive

### Faz 3: İç Sayfalar
- [ ] Header component
- [ ] Long-form page + video grid
- [ ] Shorts page + dikey grid
- [ ] About page
- [ ] Contact page + form

### Faz 4: Video Entegrasyonu
- [ ] Bunny.net hesabı aç
- [ ] Loop videoları yükle
- [ ] Landing'e video embed
- [ ] YouTube modal component
- [ ] Long-form videoları bağla
- [ ] Shorts videoları bağla

### Faz 5: Polish
- [ ] Geçiş animasyonları
- [ ] Hover efektleri
- [ ] Loading states
- [ ] 404 sayfası
- [ ] SEO meta tags
- [ ] OG image

### Faz 6: Deploy
- [ ] GitHub repo
- [ ] Cloudflare Pages bağla
- [ ] Custom domain
- [ ] SSL kontrol
- [ ] Performance test

---

## Notlar

- **Video loop boyutu:** Her loop max 5MB, toplam ~40MB
- **YouTube thumbnail:** Auto-generate veya custom upload
- **Form spam koruması:** Formspree'nin built-in honeypot'u yeterli
- **Analytics:** İlk aşamada Cloudflare yeterli, sonra Plausible eklenebilir
- **Performance hedefi:** Lighthouse 90+ tüm kategorilerde
- **İkonlar:** Sadece kullanılan Phosphor weight'leri import et (bundle size için)

---

## Kaynaklar

- Astro Docs: https://docs.astro.build
- Tailwind CSS: https://tailwindcss.com/docs
- Phosphor Icons: https://phosphoricons.com
- Bunny.net Stream: https://bunny.net/stream
- Formspree: https://formspree.io
- Cloudflare Pages: https://pages.cloudflare.com
