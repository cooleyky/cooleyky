---
title: Building a Website That Grows With Me
layout: default
date: 2023-01-31
---

I started building this website by learning new HTML commands whenever I thought of a new feature to add. It wasn't until I wanted to feature a sneak peak of my latest blog post on my homepage that I started to wonder if there was a way of automating things. Good news: There is! A very nice tutorial posted [here](https://jekyllrb.com/tutorials/convert-site-to-jekyll/) explains the process in detail. Bad news: My approach to the problem was backwards. I would have to make a bigger mess of my very detailed individual HTML pages before I could have the shiny, automated build of my site. If you also dream of an easy-to-update personal website but aren't a professional web designer, read on for my "Spark notes" on starting the process *in medias res*.

## My first test blog post disappeared when I added HTML pages :open_mouth:

**DISCLAIMER:** I will be mentioning a lot of different tools used in different types of code, but you don't need to understand most of them. I will explain anything that is important to understanding my experience. My goal in mentioning these terms is only full transparency.

To get started, I learned about how my website is built. This website is hosted by [GitHub Pages](https://pages.github.com/), a free website hosting service for GitHub users that runs on Jekyll. Okay, that sounds straightforward enough, but what does it mean to "run on Jekyll"? [Jekyll](https://jekyllrb.com/) is a code that takes all of the files that I have in my GitHub website repository and turns it into the website that you see. Jekyll is especially great with automating building blogs, so that must have been the problem with my site -- Jekyll wasn't inserting my blog posts anywhere on my site! I scrolled through the Jekyll [documentation](https://jekyllrb.com/docs/) for hours thinking only of my blog feed problem until I found my first clue.

That clue was a [template](https://jekyllrb.com/docs/posts/#post-excerpts) for exactly the type of automatically-updating blog excerpt that I wanted on my homepage. The default length of the excerpt is even set to the first paragraph of the post without any tinkering by me. This is how I learned that specific templates are transformed by Jekyll, but this would not happen if I only copied and pasted the templates into my regular HTML files. I was also missing a different file with the content and other settings that tell Jekyll how to plug things into the template.

## Mystery Solved!

Content for one page goes in a markdown file that has the same names as the HTML file that you want. The relevant page data that defines the page title, date (if a blog post), appearance, and more are variables in that file, too. The variables are defined at the top of the file in the "front matter block". Example:
~~~
    ---
    title: Home
    layout: index
    ---
~~~
The page template that I mentioned before is referenced by the `layout` variable. The layout templates live in a folder in my GitHub repository called "_layouts". The markdown file and the template are all you need! Here's the kicker: your template *is* the original HTML file that you started with.

## Using Jekyll when you already lost track of your content in the template

**DISCLAIMER:** These steps are best-suited for someone who already has some familiarity with using GitHub. If this is not you, please try these tutorials first and then come back if you get carried away with an HTML5 template and need to reorient yourself.
How-to GitHub: [Quickstart guide from GitHub Docs](https://docs.github.com/en/get-started/quickstart)
Launching your site with GitHub Pages: [skills/github-pages on Github](https://github.com/skills/github-pages)

I had to go through these steps tortoise-slow because I was afraid of losing all of the personalization I already made in the HTML files. Hopefully the following list speeds up the process for you.

1. Create folder called "_layouts" in your GitHub repository for this project.
2. Copy the an HTML that file you want to work with and paste a copy in the "_layouts" folder.
3. Very Important!! If you were working in the original HTML filed, *close it now*. Open the new HTML file in "_layouts". This is the only HTML file we will use going forward.
<!-- Ask MacKenzie if she can try out these steps and if they don't work, does she need to delete/move the old HTML file first? -->
4. Open another file from the "root" directory of your repository and name it "YourPageName.md". Naming the Markdown files (.md file-type) the same as the HTML files I'm replacing has worked well for me because I am trying to reduce the number of links I have to go back and change in the short term. When Jekyll builds the site, the Markdown file goes in, and an HTML file with the same name as the Markdown file comes out.
5. In .md file, write the frontmatter:
~~~
    ---
    title: YourPageTitle
    layout: templateName
    ---
~~~
Depending on the type of page, you might also include a date, a special series of symbols to end the excerpt manually, or any other settings.
6. Below this section, you can include your :sparkles: *content* :sparkles:. For example, I moved my bio from my homepage HTML template to the content section in my Markdown file. This way, I can find it and edit only my bio easily. Content can be formatted with Markdown or HTML commands, and with HTML nested inside Markdown, but not with Markdown inside HTML sections. 
7. Now, replace the content that you grabbed in the HTML template with `{{ content }}`.
<!-- Might need to add another step here about fixing absolute links (and href's) that link to assets and stylesheets -->
8. You can also add any other Markdown or Liquid (a different markdown-type language) to the HTML template at this point. Jekyll will recognize these parts and insert data from elsewhere in your repository depending on the commands. I added the template for blog excerpts I mentioned earlier, which you can find [here](https://jekyllrb.com/docs/posts/#post-excerpts).
9. If you haven't yet, save your changes and push them to the main branch of your GitHub repository. Then your page should start the deployment process, but this could take a minute or two to show your changes online. You can see when the deployment process starts and finishes from the "Actions" tab in your repository.

<center>Happy Coding!</center>