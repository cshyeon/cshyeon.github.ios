<ul class="post">
{% for item in sorted %}
<li class="post-title">
  <a href="">
    {{ item.title }}
</li>
{% endfor %}
</ul>