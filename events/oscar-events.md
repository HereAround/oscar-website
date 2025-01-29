---
layout: page
title: OSCAR Meetings
meeting: true
---

## Upcoming Meetings

{% assign events = site.data.events | where: "satellite", "No" | group-by: "start-date" | sort: "end-date" | reverse %}
{% assign today = "now" | date: "%Y-%m-%d" %}
{% assign has_upcoming_events = false %}

<ul>
{% for event in events %}
  {% if event.end-date >= today %}
    {% assign has_upcoming_events = true %}
    <li>
      <strong>{{ event.title }}</strong><br>
      <em>{{ event.start-date }} – {{ event.end-date }}</em><br>
      Location: {{ event.location }}<br>
      <a href="{{ event.website }}" target="_blank">More information</a>
    </li>
  {% endif %}
{% endfor %}
</ul>

{% unless has_upcoming_events %}
Currently no upcoming events.
{% endunless %}


## Past Meetings

<ul>
{% for event in events %}
  {% if event.end-date < today %}
    <li>
      <strong>{{ event.title }}</strong><br>
      <em>{{ event.start-date }} – {{ event.end-date }}</em><br>
      Location: {{ event.location }}<br>
      <a href="{{ event.website }}" target="_blank">More information</a>
    </li>
  {% endif %}
{% endfor %}
</ul>
