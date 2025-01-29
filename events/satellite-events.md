---
layout: page
title: Satellite Events
meeting: true
---

The [SFB-TRR 195](https://www.computeralgebra.de/sfb/events/), a transregional collaborative research center funded by the German Research Foundation (DFG), focuses on **symbolic tools in mathematics and their applications**. One of its research projects is **OSCAR**. For a list of events organized by the SFB-TRR 195, click [here](https://www.computeralgebra.de/sfb/events/).

In addition, the following events may also be of interest:

{% assign events = site.data.events | where: "satellite", "Yes" | group-by: "start-date" | sort: "end-date" | reverse %}

<ul>
  {% for event in events %}
    <li>
      <strong>{{ event.title }}</strong><br>
      <em>{{ event.start-date }} – {{ event.end-date }}</em><br>
      Location: {{ event.location }}<br>
      <a href="{{ event.website }}" target="_blank">More information</a>
    </li>
  {% endfor %}
</ul>
