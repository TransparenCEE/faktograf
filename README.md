# [Faktograf](https://faktograf.hr/)

Faktograf is based on sage theme, more about sage below.

## Installation

```
# Create DB
mysql -p -e "CREATE DATABASE fg; CREATE USER 'fg'@'localhost' IDENTIFIED BY 'fg'; GRANT ALL PRIVILEGES ON fg.* TO 'fg'@'localhost'; FLUSH PRIVILEGES;"

# Install code
wget https://wordpress.org/wordpress-4.6.1.tar.gz
tar -xzf wordpress-4.6.1.tar.gz
mv wordpress faktograf
cd faktograf
git clone https://github.com/TransparenCEE/faktograf wp-content/themes/faktograf

echo "Edit db connection params and set $table_prefix  = 'fg_';"
cp wp-config-sample.php wp-config.php
vim wp-config.php

# change site URL to one of your server and load database
# wp-content/themes/faktograf/initialize/sampledata.sql
cat sampledata.sql | sed 's/http:\/\/faktograf\.hr\/site/localhost:82/g' | sed 's/http:\/\/faktograf\.hr/localhost:82/g' | sed 's/home\/faktograf\/public_html\/site/home\/www\/faktograf/g' | mysql fg -u fg -pfg

tar -xvf wp-content/themes/faktograf/initialize/uploads.tar.gz -C wp-content 

# Go to your website /wp-admin and login using credentials admin@faktograf.hr Password1
# Go to your website, it should work! if not you may need a .htaccess file in root of the WP: See http://localhost:82/wp-admin/options-permalink.php

```

## Required plugins:

These required plugins are covered by installation procedure specified above
* [Google Analytics by MonsterInsights](https://www.monsterinsights.com/)
* [Monarch](https://www.elegantthemes.com/plugins/monarch/)
* [Yoast SEO](https://yoast.com/)
* [Wodrfence](https://www.wordfence.com/)
* [WP-Polls](https://wordpress.org/plugins/wp-polls/)

## Know more

Sage is a WordPress starter theme based on HTML5 Boilerplate, gulp, Bower, and Bootstrap Sass, that will help you make better themes.

* Source: [https://github.com/roots/sage](https://github.com/roots/sage)
* Homepage: [https://roots.io/sage/](https://roots.io/sage/)
* Documentation: [https://roots.io/sage/docs/](https://roots.io/sage/docs/)
* Twitter: [@rootswp](https://twitter.com/rootswp)
* Newsletter: [Subscribe](http://roots.io/subscribe/)
* Forum: [https://discourse.roots.io/](https://discourse.roots.io/)

## Theme development

Sage uses [gulp](http://gulpjs.com/) as its build system and [Bower](http://bower.io/) to manage front-end packages.

### Install gulp and Bower

Building the theme requires [node.js](http://nodejs.org/download/). We recommend you update to the latest version of npm: `npm install -g npm@latest`.

From the command line:

1. Install [gulp](http://gulpjs.com) and [Bower](http://bower.io/) globally with `npm install -g gulp bower`
2. Navigate to the theme directory, then run `npm install`
3. Run `bower install`

You now have all the necessary dependencies to run the build process.

### Available gulp commands

* `gulp` — Compile and optimize the files in your assets directory
* `gulp watch` — Compile assets when file changes are made
* `gulp --production` — Compile assets for production (no source maps).

### Using BrowserSync

To use BrowserSync during `gulp watch` you need to update `devUrl` at the bottom of `assets/manifest.json` to reflect your local development hostname.

For example, if your local development URL is `http://project-name.dev` you would update the file to read:
```json
...
  "config": {
    "devUrl": "http://project-name.dev"
  }
...
```
If your local development URL looks like `http://localhost:8888/project-name/` you would update the file to read:
```json
...
  "config": {
    "devUrl": "http://localhost:8888/project-name/"
  }
...
```

### Documentation

Sage documentation is available at [https://roots.io/sage/docs/](https://roots.io/sage/docs/).

## Requirements

| Prerequisite    | How to check | How to install
| --------------- | ------------ | ------------- |
| PHP >= 5.4.x    | `php -v`     | [php.net](http://php.net/manual/en/install.php) |
| Node.js 0.12.x  | `node -v`    | [nodejs.org](http://nodejs.org/) |
| gulp >= 3.8.10  | `gulp -v`    | `npm install -g gulp` |
| Bower >= 1.3.12 | `bower -v`   | `npm install -g bower` |
