---
layout: post
title: Intro to Jekyll
categories:
  - Markup
  - Edge Case
tags:
  - Examples
---

# Overview

The RHNA website is built with jekyll - a blog-aware, static site generator written in ruby and hosted through github pages. Github is powered by Jekyll which makes deploying another jekyll website onto github pages really intuitive. All of the backend coding is handled through github.

The main power of jekyll is the use of themes to pragmatically convert simple text files (markdown) into beautifully and consistently designed webpages. I picked a theme called hydeout that seemed to fit nicely with the purpose of the website. This theme can be changed relatively easily since all of the data can be moved into a new project with a different theme.

An example "playground" version of the website has been created here: [https://regional-affordable-housing-study.github.io/hydeout/](https://regional-affordable-housing-study.github.io/hydeout/). I would recommend recommend opening it and playing around with the website before going through this.

This guide provides the fundamentals of updating the RHNA website with a new post and some other likely changes. Anything more complex and I turn you to the [jekyll documentation](https://jekyllrb.com/docs/) and the [hydeout](https://github.com/Regional-Affordable-Housing-Study/hydeout/tree/master) specific documentation. Pretty much anything can be customized and changed to fit the needs of the project.

# Markdown
A vast majority of the website can be written with markdown - a way of using rules to format text from a plaintext document - except for a few minor cases which require html, which for this purpose can be swapped pretty simply.

The example posts in the playground build of the website actually have some really good examples of how to use markdown [here](https://regional-affordable-housing-study.github.io/hydeout/) and there are multiple guides online on more advanced usage of markdown such as [this](https://www.markdownguide.org/) that can be found with a quick search.

There are multiple markdown editors (such as [Obsidian](https://obsidian.md/) which is also a great tool for the "second brain" technique of note taking - it is free and open source) that dynamically display how your markdown will actually be formatted as you type it. For example this tutorial is being written with obsidian markdown. This is highly recommended if you are doing anything complicated with the blog posts otherwise you will have to publish the changes to see how they look.

The bare fundamentals are here:

## Headers

Headers of difference levels are created with #'s
```
# Header Level One
## Header Level Two
### Header Level Three
```

And appear as follows
# Header Level One
## Header Level Two
### Header Level Three

## Text Formatting

Text can be formatted with either *'s or _'s

```
Single is Italics

_italics_

*also italics*

Double is bold

__bold__

**bold**
```

Rendering as:
Single is Italics

_italics_

*also italics*

Double is bold

__bold__

**also bold**

## Code

Inserting code (as with these examples) or anything that you want to show up raw as written uses triple backticks (usually top left of your computer sharing the tilda key)

```
\```
**code you want to display** - remove the backslashes for actu
\```
```

## Lists

Lists use a standard

```
- bullet 1
- bullet 2

1. numbered 1
2. numbered 2
```

- bullet 1
- bullet 2

1. numbered 1
2. numbered 2

format and nesting is done with tabs

## Images

Images can be imbedded into text by adding the file path to the image - note this needs to be the file path once in website form, not the file path stored locally on your computer. These image files can be hosted on github and then linked to from the markdown (see the raw markdown of this file for an example)

```
![alt text that describes the image - important for screen readers](file/path/to/image)

![An image showing distribution of Risk Values for Bay County](HARP_FSF_PreliminaryFindings/RiskHistogram.png)

```

![An image showing distribution of Risk Values for Bay County](https://raw.githubusercontent.com/Regional-Affordable-Housing-Study/hydeout/master/_screenshots/RiskHistogram.png?raw=true)
# Structure

The website is primarily composed of markdown documents in a simple folder structure.

![Image showing github file structure](https://raw.githubusercontent.com/Regional-Affordable-Housing-Study/hydeout/master/_screenshots/fileStruct.png?raw=true)

A majority of these files and folders control more advanced uses for the website. The most important ones are:

1. Primary Pages - these are the home pages of the website (index.html and about.md, but more can be added). Index.html is the home page of the website. About.md and any others you create will make up the first options on the sidebar.
2. Category Pages - contained within the category folder, these are the home pages for each category. These make up the last options on the sidebar. Go to [Edge Case](https://regional-affordable-housing-study.github.io/hydeout/category/edge-case.html) on the playground website to see how these pages show up.
3. Posts - contained within the ```_posts``` folder, these are the actual content of the website and are designed in a blog-style format (i.e. new posts get pushed to the top of the list and are organized by date). Posts show up both on the main page (index.html) as well as the home page of whatever category they are in.

# Format

All pages, whether written in markdown or html, are composed of a filename, then front matter followed by the visible page content.

## File Name

The homepage has to be called index.html, but all other pages from 1 and 2 can be named however you want.

Posts need to follow a specific format.

```
yyyy-mm-dd-here-is-the-title.md
```

year-month-day: this determines the ordering of the blog posts and should be the day that you are publishing the blog. This should be done in a standard yyy-mm-dd format to maintain consistency across the posts.

here-is-the-title part should line up with whatever you put in the title section of front matter (below) to make it easy to find and edit posts, but won't break the website if they don't. The actual page title is pulled from the front matter but this gives it a readable ID aside from the date.
## Front Matter

This is the content contained within the three dashes --- at the top of the page. The front matter contains metadata for the post.

The two required components for all pages are

```
layout: post
title: "Edge Case: Nested and Mixed Lists"
```

Layout will be whatever template you want to use. index.html uses ```
index```, home pages use ```page``` and posts use ```post```. You can create additional templates if you want to differentiate between post styles.

Title is just the title of the page.

Categories are automatically added to the sidebar as long as they are located in the categories folder. If you want to add another page to the sidebar - like the about page - you need to add this to the front matter.

```
sidebar_link: true
```

If you wanted to showcase a particular blog post for a month or two, you could add this so it shows up in the sidebar, and then remove it again once you are done showcasing it, for example.

Finally posts have more suggested options

```
categories:
  - Edge Case
tags:
  - content
  - css
  - edge case
  - lists
  - markup
```

If you want a post to show up in multiple categories (i.e. it is an interactive map and a new project) then you can list multiple pieces under categories and it will show up on the main page for each. Since categories are contained in the sidebar, it is recommended that these are kept relatively few and only for overarching or important categories. Tags provide a way to categorize even further and are searchable as well. These can be as detailed as you want and can be created on the fly - make sure formatting is the same though since 'data' and 'Data' will show up as two different tags.
## Content

Beneath the front matter goes the content of the page, either written in markdown or css.

# Creating a new post using github online

This will walk through how to create a new post online using github. I would recommend eventually setting up a test environment on your computer and deploying using git (documentation on jekylls page), but this is the easiest method and can be done by anyone with access to the organization.

1. When you first login you will likely be on your personal dashboard. Navigate to the organizational dashboard (click your username in the top left, then click Regional-Affordable...) then Browser Organizations Repositories.
	1. Alternatively just go to this link after logging in: https://github.com/orgs/Regional-Affordable-Housing-Study/repositories
2. Click on the repository: currently 'hydeout' for the playground version of the website, but eventually there will be one with the actual name
3. Click on the ```_posts``` folder
4. Click add file -> create new file in the top right
5. At the top you should see hydeout/posts/name your file
	1. Rename your file using the standard format
	2. 2023-09-05-my-first-file.md
6. In the text editor below that, add your front matter
```
   ---
   layout: post
   title: My First File (to comply with whatever you named the file)
   categories:
	  - Markup
   ---
```
7. Then add your content
```
   # Here is a header
   Followed by some glorious content
```
8. If you hit preview you can see what your markdown will look like - it will try to format the front matter as a table. Just ignore that as it will be fixed when you publish and make sure the content looks good
9. Hit commit changes - add a description if you want, this is more for troubleshooting purposes on the backend and wont effect the website content
10. Click <>Code at the top left
11. Near the bottom right you should see Deployments - click that. Updates do not happen immediately, but rather when you commit your changes you trigger an event on github that the content should be redeployed. Wait until you see a new deployment with a green checkmark next to it and a "1 minute ago" tag (if you don't see it wait, depending on server loads sometimes it can take a bit)
12. Once that shows up, you can hit the Square with the arrow to take you to the website. Alternatively, you can just refresh the website page https://regional-affordable-housing-study.github.io/hydeout/ for the playground
13. On the website you should see you new blog post at the top of the posts section on the home page, and at the top of the posts section on whatever category you put it in. If it is not there, go back and check what you did and make sure everything is a) in the correct folder, b) titled in the correct format, and c) has the proper front matter.
14. Celebrate yourself for a job well done.
