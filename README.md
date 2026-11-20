# Angela Ding — personal site

A static, three-page site (Home, Experience, Contact). Plain HTML, CSS and JavaScript with no build step.

## Structure

```
index.html          Home / About
experience.html     Timeline, skills, certifications, education
contact.html        Email, LinkedIn, GitHub, résumé download
css/styles.css      All styles (colors and fonts are variables at the top)
js/main.js          Mobile menu, active nav link, footer year, scroll fade-in
assets/             Headshot, résumé PDF, favicon
```

`headshot.png` and `Resume_Angela_Ding_2026.pdf` in the root folder are the originals. The site uses the copies in `assets/`.

## Editing

- **Text:** edit the HTML files directly. The header and footer are repeated in each page, so a change to the nav or social links must be made in all three files.
- **Colors and fonts:** change the variables in the `:root` block at the top of `css/styles.css`.
- **New résumé:** replace `assets/Resume_Angela_Ding_2026.pdf`. If the file name changes, update the two download links in `experience.html` and `contact.html`.
- **New headshot:** save it as `assets/headshot.jpg`, square, about 640×640. To compress on a Mac:
  `sips -s format jpeg -s formatOptions 70 -Z 640 photo.png --out assets/headshot.jpg`

## Preview locally

Open `index.html` in a browser, or run a local server:

```sh
cd /path/to/this/folder
ruby -run -e httpd . -p 8000
```

Then open http://localhost:8000. To test on your phone, connect it to the same Wi-Fi and open `http://<your-mac's-ip>:8000` (find the IP under System Settings → Wi-Fi → Details).

## Deploy to GitHub Pages

1. Create a GitHub repository named `kodingrobo.github.io` (gives the URL `https://kodingrobo.github.io`). Any other name works too and is served at `https://kodingrobo.github.io/<repo-name>/`.
2. From this folder:
   ```sh
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/kodingrobo/<repo-name>.git
   git push -u origin main
   ```
3. In the repo on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, choose `main` and `/ (root)`, then save.
4. After a minute or two the site is live. Re-run `git add . && git commit && git push` to publish changes.

**Note:** the résumé PDF includes a phone number. It becomes public once the site is deployed. Replace the PDF with a version without it if you'd prefer.
