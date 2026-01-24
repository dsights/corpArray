# CorpArray Website Reference Document

This document serves as a comprehensive reference for the CorpArray website, detailing its structure, technology stack, design system, and recommendations for future maintenance and enhancements.

## 1. Project Overview

CorpArray is a corporate governance and legal compliance services website. It is currently built as a static HTML/CSS site using Bootstrap 5 for responsiveness.

### Directory Structure

```text
/
├── index.html          # Homepage
├── about.html          # About Us page
├── contact.html        # Contact Us page
├── style.css           # Global custom styles
├── images/             # Image assets (logos, icons, etc.)
├── services/           # Individual service pages
│   ├── fema-consultancy.html
│   ├── securities-laws.html
│   └── ... (other service pages)
└── blog/               # Blog article pages
    ├── fema-compliance-updates.html
    └── ... (other blog pages)
```

## 2. Technology Stack

-   **HTML5**: Semantic markup.
-   **CSS3**: Custom styling in `style.css` and inline styles.
-   **Framework**: [Bootstrap 5.3.0](https://getbootstrap.com/) (CDN).
-   **Icons**: [FontAwesome 6.4.0](https://fontawesome.com/) (CDN).
-   **Fonts**: 
    -   Headings: 'Inter', sans-serif
    -   Body: 'Roboto', sans-serif
    -   Source: Google Fonts.
-   **Scripts**: Bootstrap Bundle JS (CDN).
-   **Forms**: HubSpot embedded forms.

## 3. Design System

### Color Palette

Defined in `:root` variables in CSS:

| Variable            | Color Code | Usage                          |
| ------------------- | ---------- | ------------------------------ |
| `--primary-color`   | `#003366`  | Headings, Footer, Brand, Nav   |
| `--secondary-color` | `#00509E`  | Icons, Secondary Backgrounds   |
| `--accent-color`    | `#FFD700`  | Buttons, Highlights, Links     |
| `--light-gray`      | `#f8f9fa`  | Section Backgrounds            |
| `--dark-gray`       | `#343a40`  | Body Text                      |

### Typography

-   **Headings**: `Inter` (Weights: 400, 700)
-   **Body**: `Roboto` (Weights: 400, 500)

### Common Components

1.  **Navbar**: Fixed top, contains Logo and links to Home, About, Services, Blog, Contact.
2.  **Hero Section**: Large visual header with title, subtitle, and CTA. Home page uses a video background.
3.  **Cards**:
    -   `service-card`: Icon, Title, Description, Hover effect.
    -   `blog-card`: Image, Title, Excerpt, "Read More" button.
    -   `testimonial-card`: Quote, Author.
4.  **Footer**: Copyright info, Social links (LinkedIn, Twitter, Facebook).
5.  **CTA Section**: "Ready to Secure Your Business's Future?", Blue gradient background, Yellow button.

## 4. Key Pages & Features

### `index.html` (Home)
-   **Hero**: Video background (`images/home.mp4`).
-   **Services**: Grid of service cards linking to `services/` directory.
-   **Testimonials**: Carousel of client feedback.
-   **Blog**: Recent articles grid linking to `blog/` directory.
-   **Contact**: Embedded HubSpot form.

### `about.html`
-   **Content**: About Us, Mission, Vision.
-   **Layout**: Simple text-heavy layout.

### `contact.html`
-   **Content**: Contact details (Address, Email, Phone), Map (Google Maps iframe), HubSpot Form.

### Sub-pages (`services/` & `blog/`)
-   Follow a consistent layout.
-   **Navigation**: Relative links updated to point back to root (e.g., `../index.html`).
-   **Sidebar/Related**: Often include "Related Services" or "Related Articles" sections.

## 5. Maintenance & Enhancement Recommendations

### Immediate Maintenance
-   **Code Duplication**: The Navbar and Footer are repeated in every HTML file. Any change to these requires updating every file.
    -   *Recommendation*: Use a Static Site Generator (Jekyll, Hugo, 11ty) or a simple server-side include (PHP, Express) to modularize headers and footers.
-   **Path Management**: Relative paths (e.g., `../style.css`) are manually managed. Moving files breaks links.
    -   *Recommendation*: Absolute paths or base URL configuration via a build tool.

### Future Enhancements
1.  **SEO Optimization**:
    -   Ensure unique `meta description` and `title` for every blog post and service page.
    -   Add Open Graph (OG) tags for better social sharing.
    -   Add `sitemap.xml` and `robots.txt`.
2.  **Performance**:
    -   Optimize images (WebP format).
    -   Lazy load images and iframes (Maps, Videos).
    -   Minify CSS and JS.
3.  **Accessibility**:
    -   Ensure all images have `alt` text.
    -   Check color contrast ratios.
    -   Ensure keyboard navigability for forms and carousels.
4.  **Dynamic Content**:
    -   If the blog grows, manually creating HTML files will be tedious. Consider a CMS (Content Management System) or a Headless CMS with a static generator.

## 6. How to Run Locally

Since this is a static site, you can serve it with any static file server.

**Using Python:**
```bash
python3 -m http.server 8000
```
Then visit `http://localhost:8000`.

**Using Node.js (http-server):**
```bash
npx http-server .
```
