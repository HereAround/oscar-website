---
layout: page
title: Tutorials
main: true
---

This page contains jupyter notebooks that demonstrate the functionality of the OSCAR project.

For each topic, you can decide to open a static version of the jupyter notebook, powered by <a href="https://nbviewer.jupyter.org/">nbviewer</a>.
Alternatively, you can inspect the jupyter notebook directly on <a href="https://github.com/">github</a>.

You can run and interact with each tutorial locally. To this end, select the tutorial of your interest below and go to <em>nbviewer</em>.
Find the download icon (top-right corner) and right-click on it (ctrl-click on macOS) to open the context menu. Choose <em>Save Link As...</em> to download the notebook to a directory of your choice. Now follow the instructions provided in the last step of the [installation instructions]({{site.baseurl }}/getting-started).

Click on one of the links below to filter notebooks (and re-click to disable filtering).

<div class="example_box">
  {%- for component in site.data.examples_components -%}
  {%- assign component_url = "/getting-started/tutorials/" | append: component.name | replace: " ", "" | append: "/" %}
  <div class="example">
    <a style="display: block; text-align: center;"
       {% if page.url == component_url %}
           href="{{ site.baseurl }}/getting-started/tutorials/"
           style="font-weight: bold;"
       {% else %}
           href="{{ site.baseurl }}{{component_url}}"
       {% endif %}
       >
      <img class="item_example-image-link"
           src="{{ site.baseurl }}/public/thumbnails/{{ component.logo }}">
      <div style="word-break: break-word;">
        {{ component.name }}
      </div>
    </a>
  </div>
  {%- endfor -%}
</div>

<div class="gallery_example_cards">
  {%- if page.main -%}
  {%-     assign someexamples = site.data.examples_with_updated_last_modified -%}
  {%- else -%}
  {%-     assign someexamples = site.data.examples_with_updated_last_modified | where:"thumbnail",page.component -%}
  {%- endif -%}
  {%- for post in someexamples  -%}

  <div class="item_example_card {{site.data.examples_status[post.filename]}}">
    <div class="item_example_left">
        <img class="item_example-image"
             src="{{ site.baseurl }}/public/thumbnails/{{ post.thumbnail }}">
    </div>
    <div class="item_example_right">
      <div class="item_example-title">
          {{ post.title }}
      </div>
      <div class="item_example-author">Author(s): {{ post.author }}</div>
      <div class="item_last_modified">Last modified: {{ post.date }} </div>
      <div><a href="https://nbviewer.jupyter.org/github/{{ post.repository }}/blob/{{ post.branch }}/{{ post.filename }}.ipynb">nbviewer</a> </div>
      <a href="https://github.com/{{ post.repository }}/blob/master/{{ post.filename }}.ipynb">Github</a>

    </div>
  </div>
  {% endfor %}
</div>

<details style="padding-top: 2em; padding-bottom: 2em;">
  <summary>Out of Date Tutorials</summary>
<div class="borked">
<div class="gallery_example_cards">
  {%- if page.main -%}
  {%-     assign someexamples = site.data.examples_with_updated_last_modified -%}
  {%- else -%}
  {%-     assign someexamples = site.data.examples_with_updated_last_modified | where:"thumbnail",page.component -%}
  {%- endif -%}
  {%- for post in someexamples  -%}
  <div class="item_example_card {{site.data.examples_status[post.filename]}}">
    <div class="item_example_left">
        <img class="item_example-image"
             src="{{ site.baseurl }}/public/thumbnails/{{ post.thumbnail }}">
    </div>
    <div class="item_example_right">
      <div class="item_example-title">
          {{ post.title }}
      </div>
      <div class="item_example-author">Author(s): {{ post.author }}</div>
      <div class="item_last_modified">Last modified: {{ post.date }} </div>
      <div><a href="https://nbviewer.jupyter.org/github/{{ post.repository }}/blob/{{ post.branch }}/{{ post.filename }}.ipynb">nbviewer</a> </div>
      <a href="https://github.com/{{ post.repository }}/blob/master/{{ post.filename }}.ipynb">Github</a>

    </div>
  </div>
  {% endfor %}
</div>
</div>
</details>
<span class="date">Last updated on {{ site.time | date: '%d-%m-%Y' }}</span>
