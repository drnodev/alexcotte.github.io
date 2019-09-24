---
layout: default
---

<!-- Html Elements for Search -->
<div id="search-container">
<input type="text" id="search-input" placeholder="search...">
    <div style="z-index:200" ><ul id="results-container"></ul></div>
</div>

<!-- Script pointing to search-script.js -->
<script src="./js/search.js" type="text/javascript"></script>

<!-- Configuration -->
<script>
SimpleJekyllSearch({
  searchInput: document.getElementById('search-input'),
  resultsContainer: document.getElementById('results-container'),
  json: '/search.json',
})
</script>

<!-- Posts -->
<div style="z-index:-1">
  <ul id="posts">
    {% for post in site.posts %}
      <li>
        <h2><a href="{% if site.baseurl == "/" %}{{ post.url }}{% else %}{{ post.url | prepend: site.baseurl }}{% endif %}">{{ post.title }}</a></h2>
      <time datetime="{{ post.date | date_to_xmlschema }}" class="by-line">{{ post.date | date_to_string }}</time>
        <p style="text-align:justify">{{ post.content | strip_html | truncatewords:50 }}</p>
      </li>
    {% endfor %}

  </ul>
</div>
