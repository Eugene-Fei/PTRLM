# PetRealm (PTRLM) Static Website

This folder contains a complete five-page static B2B website. It can be hosted on EdgeOne Pages, Cloudflare Pages, Netlify, GitHub Pages, a conventional web server, or opened locally.

## Pages

- `index.html` — Home
- `products.html` — Wholesale product range
- `oem.html` — OEM and custom service
- `about.html` — Company profile
- `contact.html` — Contact details and inquiry form

## Replace images

All visual assets are stored in `images/`. Replace the placeholder SVG files with your photographs while keeping the same filenames, or change the `src="images/..."` value in the HTML files. Recommended dimensions:

- Product images: portrait 4:5, at least 1200 × 1500 px
- Factory/team images: landscape, at least 1600 × 1100 px
- Hero video: MP4 (H.264), 1920 × 1080 or higher, preferably under 20–30 MB for faster loading

The supplied hero video is saved as `images/hero-dog-raincoat.mp4`.

## Connect Getform / Forminit

Open `contact.html` and locate:

```html
action="https://getform.io/f/YOUR_FORM_ENDPOINT"
```

Replace it with the form endpoint supplied by Getform or Forminit. In the provider dashboard, configure `sales@ptrlm.com` as the notification recipient. File uploads require a provider plan that supports multipart attachments. The static site itself cannot send email without a form service.

## Change colors

Open `css/style.css` and edit the variables at the beginning:

```css
:root {
  --ink: #20211f;
  --paper: #f4f2eb;
  --white: #fbfaf6;
  --khaki: #c8c0aa;
  --line: #d8d5cc;
  --muted: #6e706b;
}
```

## Edit text and languages

Default English text is written directly in the HTML. Language translations are stored in `js/main.js` inside the `translations` object. The selector supports English, Chinese, Spanish, French, German and Japanese. The selected language is remembered in the visitor's browser.

## Publish

Upload the entire `petrealm-website` folder without changing its internal structure. The hosting service should use `index.html` as the entry file. Test the Getform endpoint after publishing.

## EdgeOne CMS

See `EDGEONE-CMS-PLAN.md` for the recommended GitHub + EdgeOne Pages + Decap CMS architecture. CMS authentication requires a GitHub OAuth gateway and should be configured only after the GitHub repository and final domain are confirmed.
