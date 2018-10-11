# Frankenstein

A Ghost blog theme for book reviews.

Based off of the default theme for [Ghost](http://github.com/tryghost/ghost/).

To download, visit the [GitHub page](https://github.com/max-nova/Frankenstein).

Demo [here](https://books.max-nova.com)

## Features

* Within a post, show the post cover image and the embedded book image nicely
* Shows post cover image (the book cover) alongside post in list
* Displays more of the review in list

### Post template
```
[GoodReads: XXX stars](GOODREADS_LINK)

<img src="XXX" class="post-book" />["TITLE"](AMZN_LINK) is a book about...
```

### Build a Ghost theme
```bash
cd ~/workspace/
zip -r /tmp/frankenstein.zip Frankenstein -x *.git/* -x *node_modules/*
# then upload the zip file to your Ghost blog
```

### Develop theme locally
```bash
cd ~/workspace
cp -r Frankenstein/assets/built/* ghost_local/content/themes/frankenstein/assets/built/
```

### Pull changes from Casper
```bash
# only needed the first time
git remote add upstream git://github.com/TryGhost/Casper.git

git fetch upstream
git rebase upstream/master

# handle any conflicts

# rebuild assets
yarn install
yarn dev

git rebase --continue
git push --force
```

### Creating swap space on your server
This assumes a DigitalOcean Ubuntu 16.04 droplet
```bash
dd if=/dev/zero of=/var/swap bs=1k count=1024k
mkswap /var/swap
swapon /var/swap
echo '/var/swap swap swap default 0 0' >> /etc/fstab
```
