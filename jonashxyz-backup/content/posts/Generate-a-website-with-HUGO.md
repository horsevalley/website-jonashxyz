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
HUGO is a framework, designed to convert code and content into static websites. It is written in Go, making it exceptionally fast at compiling websites, even those with thousands of pages. Here's how it works:

- **Fast and Efficient**: HUGO takes your content, which you can write in Markdown (a lightweight markup language), and your templates, which define the structure and design of your site, and combines them to generate a complete, static website. These websites are made up of prebuilt HTML files, making them very fast to load and easy to host.

- **No Database Required**: Unlike dynamic site generators that require databases to store your site's content, HUGO works with files only. This means your website's content and layout are defined through text files, templates, and configurations without needing a database. This simplicity leads to increased security and ease of maintenance.

- **Customizable**: HUGO is highly customizable, allowing you to create websites that range from blogs and portfolios to documentation and company websites, all while providing a wide range of themes and plugins to enhance functionality and appearance.

- **Live Reloading**: It offers a live reload feature, which means you can see the changes you make in real-time as you develop your site. This makes the development process more intuitive and faster.

- **Static Site Benefits**: Since HUGO generates static websites, these sites are inherently secure, fast, and reliable. They can be hosted on any web server or services like GitHub Pages, Netlify, and Vercel, often with little to no cost for hosting.

In essence, HUGO is a tool that helps developers and content creators build websites quickly and efficiently, without worrying about databases or server-side scripting, making it an excellent choice for projects where speed, security, and simplicity are prioritized.

## Step 1: Install HUGO
- **Windows:** Use Chocolatey: `choco install hugo -confirm`
- **macOS:** Use Homebrew: `brew install hugo`
- **Linux:** Use your distro's package manager, for example, `sudo apt-get install hugo` for Ubuntu.

## Step 2: Create a New Site
- Open a terminal or command prompt.
- Navigate to the directory where you want your site.
- Run `hugo new site mywebsite -f "yaml"` - replacing `mywebsite` with your desired site name.

## Step 3: Add a Theme
- Find a theme you like from [HUGO Themes](https://themes.gohugo.io/).
- Clone the theme into your project: e.g. 
```
git clone https://github.com/reorx/hugo-PaperModX themes/PaperModX --depth=1
```
- Add the theme to your site's config file: `echo 'theme : nameOfYourTheme' >> config.yml`
    - e.g. `echo 'theme: PaperModX' >> config.yml`
    - you can remove the `hugo.toml` file, since we are using yaml config instead

## Step 4: Add Content
- cd into the `archetypes` folder and replace the contents of `defaults.md` with the following code:
```
---
title : '{{ replace .File.ContentBaseName "-" " " | title }}'
date : {{ .Date }}
draft : false
---
```
- Create a new post: `hugo new posts/my-first-post.md`
- Open the file in a text editor, and you'll see some front matter at the top. Below this, add your content.

## Step 5: Start the HUGO Server
- Run `hugo server ` in your site directory.
- Open a web browser and go to `http://localhost:1313` to see your site.

## Step 6: Build Your Site
- When ready to publish, run `hugo` to build your static site.
- The output will be in the `public` directory, ready to be deployed to your hosting provider.
- I have added an alias, to my .zshrc file, to update my website after building with the `hugo` command, with the help of rsync:
```
  update_website="rsync -vrP --delete-after /home/jonash/dotfiles/website/website/jonashxyz/public/ root@jonash.xyz:/var/www/jonashxyz/" \
```
- I got the alias from [Luke Smith](https://lukesmith.xyz/)

## Done
Congratulations! You've just created a website with HUGO. For more detailed instructions, visit the [official HUGO documentation](https://gohugo.io/documentation/).

Also, read the documentation of your chosen theme, e.g. [PaperModX](https://reorx.github.io/hugo-PaperModX/).

Enjoy!

Links:

202403081313

