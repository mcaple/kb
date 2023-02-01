Publishes notes on your own server see [this](https://forum.obsidian.md/t/perlite-publish-your-notes-to-your-own-web-server/21712/13) for a discussion about Perlite

Or the full [github](https://github.com/secure-77/Perlite) page.

For setup on local machine:

**After asking on Discourse I was told this is the [way](https://blog.nihilism.network/servers/perlite/)**

I have set this up at http://localhost:4000

but I could change this to a url part using [this](https://stackoverflow.com/questions/19675839/mapping-a-url-path-to-a-server-in-nginx)

#### One time setup

```
cd ~/Data
git clone https://github.com/secure-77/Perlite.git
```

```
cd /var/www/html
mkdir perlite
# copy the contents of perlite github page to this folder 
cd perlite
cp -r ~/Data/Perlite/perlite/* .
```

-   Adjust the `$rootDir = 'Demo';` in the helper.php to you vault folder name
-   Install PHP module **mb_strings** for the parsedown (apt install php-mbstring)
-  Install PHP module **yaml_parse** for the metadata (apt install php-yaml)

For our first vault we will create kb so change Demo to kb and then

```
cd /var/www/html/perlite
# create a vault subfolder
mkdir kb
cd kb
# copy our vault into the subfolder
cp -r ~/Data/md/kb/* .
```

### Themes

For correct themes look at [this](https://github.com/secure-77/Perlite/wiki/Themes)

```
cd /var/www/html/perlite/kb
cp -r ~/Data/md/kb/.obsidian .
```