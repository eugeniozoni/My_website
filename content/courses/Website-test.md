---
title: My personal website
linktitle: My personal website
toc: true
type: docs
date: "2020-04-12T00:00:00+01:00"
draft: false
menu:
  example:
    parent: This website
    weight: 4

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 
---

In this page, I will illustrate some steps which brought me to generate my personal website, completely for free and in relatively small time.

<img src="/courses/my_website/computer.jpg" alt="my_website" width="600"/>

## **Step 1. Define a strategy**

If you want to build a personal website, these are the questions that you first need to answer:

* **What kind of website do you need or want?**
In my case, I wanted to have a personal website as a tool to illustrate my skills to people looking for my professional profile. My aim in this project was to build something simple, easy to read through and with a clean graphics.

* **What content do you want to showcase?**
I wanted to show that I can build a website, that I can use certain tools to generate content for my website and that I have a specific scientific record of publiction and work experience in my professional field.

* **What information are people searching in your field of work?**
My website needed to include my complete list of publications and my career path, since in my field, these are the information that people are looking for. 

## **Step 2. Choose the tools**

I decided to use [**Rstudio**](https://rstudio.com/) in combination with the [**Rblogdown**](https://bookdown.org/yihui/blogdown/) framework since I am familiar with the R language. Plus, this allowed me to build my website completely for free!

I choose the [**Academic theme**](https://sourcethemes.com/academic/) for [**HUGO**](https://gohugo.io/) as this is completely compatible with Rblogdown and was fully customizable for my needs.

With these tools you can have your template website up and running in few minutes, simply by following these 5 steps:

* Install the **blogdown** R package
```
install.packages('blogdown')
```

* Load the **blogdown** library
```
library(blogdown)
```

* Create a new project by clicking on File **>** New Project **>** New directory **>** Website using blogdown **>** change Hugo theme by typing **gcushen/hugo-academic**

* Build the template website using the Hugo theme that you just selected 
```
blogdown::build_site()
```

* Serve the site and have it rendered
```
blogdown::serve_site()
```

With these 5 steps, your new website will be generated. By copying the *http://IP-address* in your web browser, you will be able to visualize the desktop version of your website, while the mobile version will be automatically rendered in the R stution *Viewer* panel.

## **Step 3. Customize your website**

To edit the content of your website and add new content you can navigate throught the structure of your website by using the R studio file panel. By editing the content and structure of the *index.md* files you will be able to fully customize the content of the existing web pages. 

The main folder to customize the information that you want to include in your website is the *content* folder. Here is how I decided to customize mine:

* **Personal section**: I wanted to have a personal section with my interest and educational infos.
* **Skills sections**: I included a *Skill widget* to have an overview of my skills at a glance.
* **Experience section**: in this widget I included in details my research experience.
* **Publications**: I customized this section by having a separate widget with only few featured publications that I want to showcase.
* **Fun facts**: I included a *fun facts* section to make my website really personal, by reporting some fun facts related to my professional career.
* **Projects**: in this section, I illustrate some personal projects to showcase my skills with R. This is the section which will require more customization and a periodic updated in order to keep each project up to date.

## **Credits**

Credits for the feasibility of this project should be given to the author of the  [**Academic theme**](https://sourcethemes.com/academic/) for [**HUGO**](https://gohugo.io/) and [**Rblogdown**](https://bookdown.org/yihui/blogdown/). This website was developed within [**Rstudio**](https://rstudio.com/).

Photo by <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px" href="https://unsplash.com/@clemhlrdt?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Clément H"><span style="display:inline-block;padding:2px 3px"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-2px;fill:white" viewBox="0 0 32 32"><title>unsplash-logo</title><path d="M10 9V0h12v9H10zm12 5h10v18H0V14h10v9h12v-9z"></path></svg></span><span style="display:inline-block;padding:2px 3px">Clément H</span></a> on [**Unsplash**](https://unsplash.com/photos/95YRwf6CNw8).


