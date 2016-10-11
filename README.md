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

# change site URL to one of your server
sed 's/faktograf\.hr/localhost:82/g' faktograf_wp_fg_20161010_677.sql | sed 's/home\/faktograf\/public_html\/site/home\/www\/faktograf/g' > DB/konfliktiinteresa_me.sql | mysql ki -u ki -pki

# TODO: anonimization of dat
mysql ki -u ki -pki -e "UPDATE cdt_users SET user_pass=MD5('Password1')"


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

## Requirements

| Prerequisite    | How to check | How to install
| --------------- | ------------ | ------------- |
| PHP >= 5.4.x    | `php -v`     | [php.net](http://php.net/manual/en/install.php) |
| Node.js 0.12.x  | `node -v`    | [nodejs.org](http://nodejs.org/) |
| gulp >= 3.8.10  | `gulp -v`    | `npm install -g gulp` |
| Bower >= 1.3.12 | `bower -v`   | `npm install -g bower` |
