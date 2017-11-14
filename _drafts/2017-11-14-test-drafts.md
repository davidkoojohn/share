---
layout: post
title:  "test---drafts"
date:   2017-11-14 10:20:37 +0800
categories: jekyll update
---

# hello world
![test](/share/assets/images/2011-12-31-new-years-eve-is-awesome/me.jpg)

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

******
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
      {{ post.excerpt | remove: '<p>' | remove: '</p>' }}
    </li>
  {% endfor %}
</ul>

{% highlight ruby linenos %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}

