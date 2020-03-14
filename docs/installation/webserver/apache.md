---
title: Apache Configuration
---


Bolt requires the use of a `.htaccess` file to make sure requests like `page
/about-this- website` get routed to `index.php`, so it can be handled by Bolt.
By default, the file looks like this:

```apache
# Set the default handler.
DirectoryIndex index.php index.html index.htm

# Prevent directory listing
Options -Indexes

# Make sure MultiViews is disabled if available.
<IfModule mod_negotiation.c>
  Options -MultiViews
</IfModule>

<FilesMatch "\.(dist|db|markdown|md|twig|yaml|yml)|(bower|composer|jsdoc|package)\.json$">
  <IfModule mod_authz_core.c>
    Require all denied
  </IfModule>
  <IfModule !mod_authz_core.c>
    Order deny,allow
    Deny from all
  </IfModule>
</FilesMatch>

<IfModule mod_rewrite.c>
  RewriteEngine on

  RewriteRule cache/ - [F]

  # Some servers require the RewriteBase to be set. If so, set to the correct folder.
  # RewriteBase /

  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_URI} !=/favicon.ico
  RewriteRule ^ ./index.php [L]

</IfModule>


# set the correct mime type for woff2 font type
# =============================================
# if you don't set your own mimetypes or you aren't using
# HTML5 Boilerplate Server Configs https://github.com/h5bp/server-configs-apache
# then you can uncomment (delete the hash/pound/octothorpe/number symbol)
# the section below:

#<IfModule mod_mime.c>
#  AddType application/font-woff2    woff2
#</IfModule>

# Block access to all hidden files and directories. These types of files 
# usually contain user preferences and can include private information like, 
# for example, the `.git` or `.svn` directories.
<IfModule mod_rewrite.c>
   RewriteEngine On
   RewriteCond %{REQUEST_URI} "!(^|/)\.well-known/([^./]+./?)+$" [NC]
   RewriteCond %{SCRIPT_FILENAME} -d [OR]
   RewriteCond %{SCRIPT_FILENAME} -f
   RewriteRule "(^|/)\." - [F]
</IfModule>
```

In some cases it won't work without the `RewriteBase` line, and in some cases
it won't work _with_ it, depending on how your Apache is configured and the
location on your site on the server.

Anyway, if your site does not work, try uncommenting the `RewriteBase` line and
set it to the correct folder. For instance, if your Bolt site is located at
`example.org/test/`, set it to `RewriteBase /test/`.

Alternatively, if your server is running Apache 2.2.16 or higher, you might be
able to replace the entire `mod_rewrite` block from lines 22-35 with this
single line:

```apache
FallbackResource /index.php
```

If you have misplaced your `.htaccess` file, you can get a
<a href="https://bolt.cm/distribution/default.htaccess"> new one here</a>, from
our <a href="https://bolt.cm/distribution/">files distribution page</a>. Be sure
to rename it to `.htaccess`, though.

