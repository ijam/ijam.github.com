---
layout: post
title: "[fixed] Could not find rake-0.9.2 in any of the sources Run 'bundle install' to install"
date: 2012-03-12 23:00
comments: true
categories: fixed
---

When you key in 'rake install', then get this error:

    rake aborted!
    You have already activated rake 0.9.2.2, but your Gemfile requires rake 0.9.2. Using bundle exec may solve this.
    
The Solution:

    add gem 'rake', '0.9.2.2' in the Gemfile Document.
 
