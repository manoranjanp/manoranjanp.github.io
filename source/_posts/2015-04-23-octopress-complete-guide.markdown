---
layout: post
title: "Octopress:Complete Guide"
date: 2015-04-23 12:24:12 +0530
comments: true
categories: Octopress
---


{% img center /images/octopress.png 710 280 Octopress %}

So, in this article we will be looking into how to blog with **Octopress** also known as the **Blogging Framework for Hackers** and host the page on GitHub. So, what is Octopress ? _**Well, the answer to this question is Octopress is a static blogging framework built on top of Jekyll, It uses scripts to build static files to be deployed to a server**_

### Why Use Octopress?

* It uses Jekyll

  Octopress is based on top of Jekyll which also happens to be the site generator for GitHub Pages. Now here the 
  thing to be kept care of is the word **Generator**. Once you build the blog locally using Octopress and you run
  the command from your terminal `rake generate` a HTML Template of your blog will be generated which is later
  deployed on to GitHub.

* Markdown Language

  Unlike other CMS **Octopress** uses _Markdown_ to write posts which also in the language of nerds is refered as
  **_Plain Text_**. So, after spending 10 to 15 minutes you can easily learn Markdown if you don't know it yet.

* User Friendly

  Unlike other CMS you can write the code in your favourite IDE. Being a static page you can also host it for free on GitHub. One of the most biggest advantage I consider is not to worry about Data Loss. Being a static hosted website you always have your repository safe locally as well as on GitHub.

### How to Setup Octopress?

In order to setup Octopress you need to install the latest version of Ruby in your machine which in our case is 2.2.2. So, let's start with installing Ruby first of all. 

{% highlight html %}
1 rvm install 2.2.2 #It will install Ruby and other necessary things if required to support it.
2 rvm gemset create octopress #This will create a gemset for the Octopress Blog.
3 rvm 2.2.2@octopress #To convey RVM to use the newly created gemset.
{% endhighlight %}

Now, after Ruby is installed we need to pull down Octopress locally. To do that I will advice to fork the [Octopress](https://github.com/octopress/octopress) Repository to your Git and then clone the repository to your local machine.

{% highlight html %}
git clone 'Link of your forked Octopress Repository'
cd octopress
{% endhighlight %}

Now once you enter the octopress repository after cloning it we need to install [Bundles](http://bundler.io/) so that we can install required dependencies.

{% highlight html %}
gem install bundler
bundle install
{% endhighlight %}

So, after the above steps we have succesfully installed Octopress. Now, we will install theme for out blogs, to install default theme follow the below instructions and to install [3rd Party Themes](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes) follow the instructions given on its page.

{% highlight html %}
rake install
{% endhighlight %}

If you get an error while following `rake install` then you can follow another command i.e.

{% highlight html %}
bundle exec rake install
{% endhighlight %}

Now, your Octopress as well as desire theme is installed locally in your machine!

### How to configure Octopress?

In order to configure the Octopress Blog `cd` inside the Octopress folder and open the **_config.yml** file, it consists of all the possible configurations you may need to edit. Below is an example of a part of the **_config.yml** before and after editing.

**Before Edit**

{% highlight html %}
url: http://yoursite.com
title: My Octopress Blog
subtitle: A blogging framework for hackers.
author: Your Name
simple_search: https://www.google.com/search
{% endhighlight %}


**After Edit**
{% highlight html %}
url: http://manoranjanp.github.io
title: Blog | Manoranjan Padhy
subtitle: Let the Code Fly!
author: Manoranjan Padhy
simple_search: https://www.google.com/search
{% endhighlight %}


Thus this will configure your blog as per your needs. Also, when you scroll to the bottom of the page you can add your social links accordingly.


###How to write?

As mentioned earlier Octopress uses Markdown to write text. So, you need to first of all clear about various features as well as few syntax before you start writting. Now, in order to add **New Post** or **New Page** follow,

{% highlight html %}
rake new_post["Your Post Name"]    #This will add a new Post
rake new_page["Your Page Name"]    #This will add a new Page
{% endhighlight %}

Once the post or page has been added go inside your theme folder and inside that into _posts folder and you will find the newly added post there. Now, open it in your favourite editor and start writting the text in Markdown.


Once you are done with writting your page you need to generate the HTML file of your blog so that you can view it in the browser. This can be done by

{% highlight html %}
rake generate #This will generate the blog
rake preview  #This will run the blog on localhost. To view go to localhost:4000 in your browser.
{% endhighlight %}


###How to Host on GitHub.

GitHub provides free hosting for static websites/blogs. To start using the service sign in your account and create a new repository by the name `yourname.github.io` and copy its SSH url for cloning purpose.

Now open your terminal and `cd` into your Octopress installation and run the following,

{% highlight html %}
rake setup_github_pages[##Copy Your SSH Clone Link Here##]
rake deploy
{% endhighlight %}

After you completing this whenever you log on to `www.yourusername.github.io` you will be able to see your blog up and running. Now, once you complete the above you need to commit your changes which can be done by,

{% highlight html %}
git add .  
git commit -am 'Your Message'  
git push origin source
{% endhighlight %}

Now, your Blog is fully functional as well as hosted on GitHub. One more great feature you get here is to point a **Custom Domain Name** to your blog. So, how to do it?


###How to Point a Custom Domain / Sub Domain ?

This is one of the easiest part you need to do here in order to add a custom domain point to your GitHub hosted blog.

* **[Step-1]** Go to your Domain Name provider and add a `CNAME` record to point to yourusername.github.io
* **[Step-2]** `cd` into your Octopress directory and write `echo 'yourdomain.com' >> source/CNAME`

Now, you are done with pointing the custom domain towards your blog. Now you should again push the changed repository to see the changes online. Within 4 - 5 hours you will find the changes visible.

> I hope this guide really helps you in getting to know **Octopress** more. Still, if you have any issues you can comment below!
>Happy Blogging!

>May The Force be With You!
