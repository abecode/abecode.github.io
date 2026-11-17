# WordPress archive import

Imported all 24 published posts returned by the public WordPress.com API for
https://abewrites.wordpress.com/, covering May 3, 2011 through July 9, 2015.

Each post's Quarto `date` uses its original publication day, matching the date in
the WordPress permalink. `wordpress.json` records the original publication
timestamp, source URL, destination file, and source HTML checksum for each post.

The 56 referenced images and PDFs are stored in `assets/wordpress/`, with source
URLs and checksums recorded in the manifest. Four embedded GitHub gists were
converted to static code blocks, and a Jetpack slideshow to a static gallery.
Links between imported articles point to their new Quarto pages. Each article
also links to its original WordPress post.

The dated aliases provide the original paths on this site's domain. They do not
redirect visitors from the WordPress domain, which remains unchanged. Comments
and the WordPress About page were not imported.

The import used Beautiful Soup in a temporary uv virtual environment and
Quarto's bundled Pandoc. Rendering the site requires only Quarto.
