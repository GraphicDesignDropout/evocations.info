---
title: "Hugo Theme Editing"
description: "Make your site function exactly the way you want it to"
date: 2020-01-30T23:17:40-08:00
draft: false
showpage: true
tags: ["Hugo","HTML","CSS","WebDev"]
---

Configuring your hugo theme to be exactly how you want it is complex, and will vary depending on the theme you're using.
In this tutorial, I'll go over how I reconfigured AmazingRise's [Diary](https://github.com/AmazingRise/hugo-theme-diary) theme.

## Hugo's Directory Structure
Hugo builds sites using the theme selected in `/config.toml`
which will select a theme from the `/themes/` directory. Inside will be the rules Hugo uses to build the site, written in HTML.

Download your theme to `/themes/` 

Change the theme paramater in `/config.toml` to `theme = "<your theme>"`

Maybe that theme is perfect for your use, or maybe there are a few things not quite right. Maybe you're just a tinkerer like me!

[More info here on Hugo's directory structure here](https://gohugo.io/getting-started/directory-structure/)

## The Tinkering Part

This will require a bit of HTML, CSS, and programming knowledge for you to get the most out of your tinkering.

