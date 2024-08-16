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

<h2 class="bibliography" style="counter-reset:bibarticleitem {{numJournalPapers|plus:1}}"><i class="ai ai-google-scholar-square ai"></i> Statistics</h2>

<table style="border-collapse: collapse; border: none; border: 0; border-spacing: 0; padding: 0; font-size:80%;">
    <tr style="border: 0; padding: 0;">
        <td style="border: 0; padding: 0;">
        <b>Citations&nbsp;&nbsp;&nbsp;&nbsp;</b>
        </td>
        <td style="border: 0; padding: 0;">
        {{ site.data.scholar.citations }}
        </td>
    </tr><tr style="border: 0; padding: 0;">
        <td style="border: 0; padding: 0;">
        <b>h-index&nbsp;&nbsp;&nbsp;&nbsp;</b>
        </td>
        <td style="border: 0; padding: 0;">
        {{ site.data.scholar.h_index }}
        </td>
    </tr><tr style="border: 0; padding: 0;">
        <td style="border: 0; padding: 0;">
        <b>i10-index&nbsp;&nbsp;&nbsp;&nbsp;</b>
        </td>
        <td style="border: 0; padding: 0;">
        {{ site.data.scholar.i10_index }}
        </td>
    </tr>
    <tr style="border: 0; padding: 0;"><td style="border: 0; padding: 0;" colspan="2"> <small>(Updated on {{ "now" | date: "%a %b %d, %Y" }})</small></td></tr>
</table>
