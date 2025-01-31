---
layout: page
title: Tutorials
main: true
---

This page contains jupyter notebooks that demonstrate the functionality of the OSCAR project.

For each topic, you can decide to open a static version of the jupyter notebook, powered by <a href="https://nbviewer.jupyter.org/">nbviewer</a>.
Alternatively, you can inspect the jupyter notebook directly on <a href="https://github.com/">github</a>.

<div class="oscar_detail" style="margin-bottom: 0em;">
  <details>
    <summary>
      How to interact with a "live" version
    </summary>
    Live interaction requires to download the notebook. Please select
    the notebook of your choice, and follow the instructions below.
    <ul>
      <li>Go to <em>nbviewer</em>.</li>
      <li>Find the download icon (top-right corner) and right-click on it (ctrl-click on macOS)
        to open the context menu. Choose <em>Save Link As...</em> to download the notebook
        (say <code>Tutorial.ipynb</code>) to a directory of your choice.
      </li>
      <li>Make sure that you have the <code>Oscar</code> package installed
        (cf. the <a href="{{ site.baseurl }}/getting-started/install">Installation Page</a>), including <code>IJulia</code>.
      </li>
      <li>  
        Run the following code in your Julia REPL: <code>using IJulia; notebook()</code>
      </li>
      <li> You should have landed on a page in your web browser, with <em>jupyter</em> written in the upper
        left corner. Below is a file explorer. Open the notebook file you downloaded (e.g. <code>Tutorial.ipynb</code>).
        You might see a pop-up with the message "Kernel not found", in which case you select a julia kernel from the
        drop-down menu.
      </li>
    </ul>
  </details>
</div>

<br/>


## OSCAR Tutorials

Click on one of the links below to filter notebooks (and re-click to disable filtering).

<div class="example_box">
  {%- for component in site.data.examples_components -%}
  {%- assign component_url = "/tutorials/" | append: component.name | replace: " ", "" | append: "/" %}
  <div class="example">
    <a style="display: block; text-align: center;"
       {% if page.url == component_url %}
           href="{{ site.baseurl }}/tutorials/"
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


## How to contribute Tutorials

1. Create a jupyter notebook with the desired content.
2. Place this notebook in a github repository of your choice.
3. Send the link to this jupyter notebook to [Martin Bies](https://martinbies.github.io/).

Note that **tutorial authors are expected to maintain their tutorial(s)**, so that their
tutorial notebooks function with the latest stable OSCAR release.


## Looking for more/other Notebook?

  - [polymake examples](https://github.com/micjoswig/oscar-notebooks)
  - [Hecke examples](https://github.com/thofma/HeckeTutorials.jl)
