---
permalink: /publications/
---

# Publications
{% capture numJournalPapers %}
{% bibliography_count --group_by year --group_order descending --query @article %}
{% endcapture %}
<h2 class="bibliography" style="counter-reset:bibarticleitem {{numJournalPapers|plus:1}}">Journal Papers</h2>
{% for year in (2000..2030) reversed %}  
  {% capture bib_entries %}{% bibliography --query @article[year = {{year}}] %}{% endcapture %}
  {% if  bib_entries.size > 90  %}
  <div class="bibarticle"> {{ bib_entries | replace first: 'h2', 'h4'}} </div>
  {% endif %}
{% endfor %}

<!-- {% bibliography --group_by year --group_order descending %} -->
{% capture numProceedings %}
{% bibliography_count --group_by year --group_order descending --query @inproceedings %}
{% endcapture %}
{% capture letterBib %} P {% endcapture %}
<h2 class="bibliography" style="counter-reset:bibcontitem {{numProceedings|plus:1}}">Conference proceedings</h2>

{% for year in (2000..2030) reversed %}  
  {% capture bib_entries %}{% bibliography --query @inproceedings[year = {{year}}] %}{% endcapture %}
  {% if  bib_entries.size > 90  %}
  <div class="bibconference"> {{ bib_entries | replace first: 'h2', 'h4'}} </div>
  {% endif %}
{% endfor %}
