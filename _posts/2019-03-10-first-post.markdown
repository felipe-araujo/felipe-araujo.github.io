---
layout: post
title:  "First post; initial setup for Github Pages"
date:   2019-03-10 08:09:53 -0300
categories: jekyll static-generator publishing site
---

It's been some time since I first had the impetus to write down a blog, and nowadays one fairly simple option would be to use some free service, like Medium, and avoid all the setup and hosting issues related to publishing something on the Web. But then I recalled the existence of a blog - [colah's blog](http://colah.github.io/){:target="_blank"} - which was hosted under a subdomain of Github.

The one thing that makes it possible is [Github pages](https://pages.github.com/){:target="_blank"}, a solution that allows anyone with a Github account to host a *static website*, for free. Being static means that you cannot rely on server side tools to deliver your content, so no databases, storage or use of dynamic content generated with a web framework. For a personal blog, this isn't that restrictive, so it may be worth give it a try.

To publish on Github pages, you first need to create a repository named `<your-github-username>.github.io`. With a free account it is mandatory for this repository to be **public**, but with paid accounts it can be kept private. The name of the repository is also the address for your website. To start publishig, you can simply create an index.html file, push it to the master branch, and the page is live:


{% highlight bash %}
echo "<pre>Welcome aboard!</pre>" > index.html
git add --all
git commit -m "Created first page"
git push -u origin master
{% endhighlight %}

## Jekyll

Of course, writing all pages like this, in pure plain html, is tedious, error prone, time consuming and may lead to inconsistent results. Luckly Github pages comes with a built in **static site generator**, a tool that allows you to write all of your content in a specific format, and generates the html files from it.
[Jekyll](https://jekyllrb.com/docs/home){:target="_blank"} is written in Ruby, so you need to install it. Managing Ruby versions is a something that can become tricky, and there are tools to make it easier, but for my purpose the default packages available in the Ubuntu repository were enough:

{% highlight bash %}
sudo apt-get install ruby ruby-all-dev
sudo gem install bundler jekyll
{% endhighlight %}


The only trouble I had was when trying to install gems with a normal user, without sudo. To solve this, add the following to your .bashrc file:

{% highlight bash %}
export GEM_HOME=$HOME/gems
export PATH=$HOME/gems/bin:$PATH
{% endhighlight %}

Now that you already have the repository for the site cloned on your machine, you can create a new Jekyll site, reusing the existing directory with the `--force` option:

{% highlight bash %}
jekyll new <your-github-username>.github.io --force
{% endhighlight %}

Push it to the master branch, and GitHub takes care of the rest.

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
