# Edmonton Speed Skating Association website

The ESSA website, built with [Hugo](https://gohugo.io/) and published free on GitHub Pages.
Every change saved to the `main` branch rebuilds and republishes the site automatically, usually within two minutes.

You don't need to install anything to update the site. All the everyday edits below can be done in your web browser on GitHub.

## Where things live

| To change… | Edit this file |
|---|---|
| Season, IceReg link, "registration open", emails, social links | `hugo.toml` (the `[params]` section) |
| Program groups, times, locations and fees | `data/programs.yaml` |
| Coaches, volunteers and directors | `data/people.yaml` |
| Policy list | `data/policies.yaml` (PDFs go in `static/documents/policies/`) |
| Partner and sponsor logos | `data/partners.yaml` (logos go in `assets/images/partners/`) |
| Training locations and maps | `data/locations.yaml` |
| Page text (Programs intro, About, History, etc.) | `content/*.md` |
| Home page headline and the three feature panels | `content/_index.md` |
| Top menu order | `hugo.toml` (the `[menus]` section) |
| Photos | `assets/images/photos/` |

## Editing on GitHub

1. Open the file in the repository on github.com.
2. Click the pencil icon (**Edit this file**).
3. Make your change. Keep the indentation and the `- ` at the start of list items exactly as they are; YAML files are sensitive to spacing.
4. Click **Commit changes**, add a short note such as "Update Group 3 fees", and commit to `main`.
5. Check the **Actions** tab. A green tick means the site has been republished; a red cross means something in the file couldn't be read. Open the failed run to see which file and line, fix it, and commit again.

### Common yearly update: new season

1. In `hugo.toml`, change `season` and `registrationURL` to the new IceReg event link.
2. Set `registrationOpen = true` when registration opens, and `false` when it closes. This shows or hides the "Register now" buttons across the site.
3. Update `data/programs.yaml` with the new times and fees.
4. Update the season mentions in `content/programs.md`, `content/registration.md` and the "Get ready" panel in `content/_index.md`.

### Adding a policy

1. Upload the PDF into `static/documents/policies/` (**Add file › Upload files** on GitHub).
2. Add an entry to `data/policies.yaml` under the right section:

   ```yaml
       - title: New Policy Name
         file: New-Policy-File.pdf
   ```

   To mark a policy as suspended, add `status: Suspended` beneath it.

### Adding a partner

1. Upload a square logo (about 300 × 300 pixels) to `assets/images/partners/`.
2. Add an entry to `data/partners.yaml` with the name, website and logo file name.

### Writing page text

Page text uses [Markdown](https://www.markdownguide.org/basic-syntax/): `**bold**`, `*italic*`, `[link text](https://example.com)`, `## Heading`, and a blank line between paragraphs. The block between the `---` lines at the top of each page holds its title and settings.

## Optional: form-based editing with Pages CMS

For volunteers who'd rather not touch YAML, the repository includes a `.pages.yml` file for [Pages CMS](https://pagescms.org), a free editor that works with GitHub repositories. Sign in at pagescms.org with a GitHub account that has access to this repository, open it, and the programs, people, policies, partners and locations appear as simple forms. Page text and site settings are still edited on GitHub as described above.

## Working on the site locally (for developers)

Install Hugo extended, version 0.167.0 or later, then run:

```sh
hugo server
```

and open http://localhost:1313. Run `hugo --gc --minify` to produce the finished site in `public/`.

Layouts are in `layouts/`, the stylesheet is `assets/css/main.css`, and images in `assets/images/` are resized and converted to WebP automatically at build time.

## First-time publishing setup

1. Create a repository on GitHub and upload these files to the `main` branch.
2. In the repository, go to **Settings › Pages** and set **Source** to **GitHub Actions**.
3. The **Deploy to GitHub Pages** workflow runs on the next commit (or run it from the **Actions** tab). The site appears at `https://<account>.github.io/<repository>/`.
4. To use `edmontonspeedskating.ca`, add the domain under **Settings › Pages › Custom domain**, then update the domain's DNS records as GitHub describes. Do this when you're ready to retire the WordPress site.

## Old links

The old WordPress addresses `/registration-2/` and `/essa-partners-and-sponsors/` redirect to the new pages. Policy PDFs now live under `/documents/policies/`, so links to the old `/wp-content/uploads/...` PDF addresses will stop working once the domain moves.

Photos by Stephen Maunder, used with permission.
