---
layout: page
title: Events
---

<div class="float-right pb-1">
<a href="/calendar" class="float-right">
<button class="btn btn-outline-primary">
{% octicon calendar height:16 %} Calendar
</button>
</a>
</div>

<br/>

<ul class="list-unstyled">
  {% assign events = site.events | reverse %}
  {% for event in events %}
    <li>
      <h4><a href="{{ event.url }}">{{ event.title | escape }}</a></h4>
      <p class="text-muted text-info">
        <time datetime="{{ event.start_date | date_to_xmlschema }}">
                            {{ event.start_date | date: site.event_date_format }}
                        </time>
        {%- if event.end_date -%}
            - 
            <time datetime="{{ event.end_date | date_to_xmlschema }}">
                                        {{ event.end_date | date: site.event_date_format }}
                                    </time>
        {%- endif -%}     
        {%- if event.location -%}
            &nbsp;({{ event.location }})
        {%- endif -%}                   
      </p>      
    </li>
  {% endfor %}
</ul>