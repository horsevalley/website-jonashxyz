---
title : 'Create Your Own Website With HUGO'
date : 2024-03-14T14:42:54+01:00
tags:
  - HUGO
  - Website
  - Web development
  - Article
---

## What is HUGO?
It's a framework written in [Go](https://go.dev/), designed to convert code and content into static websites. [HUGO](https://gohugo.io/) is exceptionally fast at compiling websites, even those with thousands of pages. It is an excellent choice for projects where speed, security, and simplicity are prioritized.


## Here's how it works

HUGO takes your content, which you can write in [Markdown](https://en.wikipedia.org/wiki/Markdown) (a lightweight markup language), and your templates, which define the structure and design of your site, and combines them to generate a complete, static website. These websites are made up of prebuilt HTML files, making them very fast to load and easy to host.

Unlike dynamic site generators that require databases to store your site's content, HUGO works with files only. This means your website's content and layout are defined through text files, templates, and configurations without needing a database. This simplicity leads to increased security and ease of maintenance.

HUGO is highly customizable, allowing you to create websites that range from blogs and portfolios to documentation and company websites, all while providing a wide range of themes and plugins to enhance functionality and appearance.

It offers a live reload feature, which means you can see the changes you make in real-time as you develop your site. This makes the development process more intuitive and faster.

Since HUGO generates static websites, these sites are inherently secure, fast, and reliable. They can be hosted on any web server or services like GitHub Pages, Netlify, and Vercel, often with little to no cost for hosting.

## Let's (hu)GO!
### Step 1: Install HUGO
Here is the [installation guide](https://gohugo.io/installation/) from the official documentation.

### Step 2: Create a New Site
- Open a terminal or command prompt.
- Navigate to the directory where you want your site.
- Run the following command:
```bash 
hugo new site mywebsite -f "yaml"
```
(replacing `mywebsite` with your desired site name)

### Step 3: Add a Theme
- Find a theme you like from [HUGO Themes](https://themes.gohugo.io/).
- Clone the theme into your project: e.g. 

```bash
git clone https://github.com/reorx/hugo-PaperModX themes/PaperModX --depth=1
```
- Add the theme to your site's config file: `echo 'theme : nameOfYourTheme' >> config.yml`
    - e.g. `echo 'theme: PaperModX' >> config.yml`
    - you can remove the `hugo.toml` file, since we are using yaml config instead

### Step 4: Add Content
- cd into the `archetypes` folder and replace the contents of `defaults.md` with the following code:
```yaml
---
title : '{{ replace .File.ContentBaseName "-" " " | title }}'
date : {{ .Date }}
draft : false
---
```
- Create a new post: 

```bash
hugo new posts/my-first-post.md
```
- Open the file in a text editor ([neovim btw](https://github.com/neovim/neovim))
- You'll see some front matter at the top (the dashed lines) 
- Add your content below the front matter 
    - It's important that you write your content in [markdown](https://www.markdownguide.org/basic-syntax/) format

### Step 5: Start the HUGO Server
- Run `hugo server ` in your site directory.
- Open a web browser and go to `http://localhost:1313` to see your site.

### Step 6: Build Your Site
- When ready to publish, run `hugo` to build your static site.
- The output will be in the `public` directory, ready to be deployed to your hosting provider.
- I have added an alias, to my .zshrc file, to update my website after building with the `hugo` command, with the help of rsync:

```bash
  update_website="rsync -vrP --delete-after /home/jonash/dotfiles/website/website/jonashxyz/public/ root@jonash.xyz:/var/www/jonashxyz/" \
```
- I got the alias from [Luke Smith](https://lukesmith.xyz/)

- I then made the following alias to automate the building and deploying:

```bash
alias hugo="hugo && update_website" \
```
- It's amazing.

### Congratulations!
You've just created a website with HUGO. 

For more detailed instructions, visit the [official HUGO documentation](https://gohugo.io/documentation/).

Also, read the documentation of your chosen theme, e.g. [PaperModX](https://reorx.github.io/hugo-PaperModX/).

Good luck!

Links:

202403081313

https://go.dev/

https://gohugo.io/

https://en.wikipedia.org/wiki/Markdown
