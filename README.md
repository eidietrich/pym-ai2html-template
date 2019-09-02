# ai2html + Pym.js responsive graphic template

Simple template for producing [ai2html](http://ai2html.org) graphics with Adobe Illustrator suitable for embedding via [Pym.js](http://blog.apps.npr.org/pym.js/), e.g in a Wordpress site via the [Pym.js Embeds plugin](https://wordpress.org/plugins/pym-shortcode/).

Produced for use with [Montana Free Press](https://montanafreepress.org/) data journalism projects. Documentation here is a work in progress.

Initial setup:
- Install ai2html plugin for Adobe Illustrator [per instructions here](http://ai2html.org/#how-to-install-ai2html)
- If using Wordpress website, install [Pym.js Embeds plugin](https://wordpress.org/plugins/pym-shortcode/).

Project workflow:
1. Clone this repository: `git clone https://github.com/eidietrich/pym-ai2html-template.git <project-name>`
2. Open `project-artboards.ai` in Adobe Illustrator, save as `project-name.ai`, create graphics
3. Export via ai2html script
    - In ai2html-settings text block, adjust `demo-output` in `html_output_path: ./demo-output/` to desired output folder name
    - Adjust `headline`, `ledein`, etc. text as desired
    - Export via `File >> Scripts >> ai2html`
    - Check export by booting up a local webserver (e.g. [serve](https://www.npmjs.com/package/serve)) and navigating to `/project-slug/project-name.preview.html` (NOT `/project-slug/project-name.html`, which doesn't pull in HTML/CSS/JS from `template.html` — see note below)
4. In output folder, delete `project-name.html` and rename `project-name.preview.html` to `index.html`
5. Upload project file to public server (e.g. Amazon S3 or, via FTP, to something like `domain.com//wp-content/uploads/graphics/` on your Wordpress site). This should produce a publicly accessible URL where the graphic is visible.
6. Link graphic URL to parent page via Pym.js (Pym.js embed plugin on Wordpress site)

Notes:
- This workflow uses something of a hack with `template.html` and the `local_preview_template` setting, which per the ai2html docs is designed to let you easily preview what your ai2html output looks like in a mock up of your web site's CMS. However, including Pym.js in that template gives us a way to shoehorn the script for making the graphic available as a responsive embed into a self-contained collection of files we can easily upload to a public web server.

References:
- Responsivity script included in template.html - see 'Multiple artboards for responsive web pages' section [here](http://ai2html.org/examples.html))
- Pym.js child snipped included in template.html - see [Pym.js documentation](http://blog.apps.npr.org/pym.js/)