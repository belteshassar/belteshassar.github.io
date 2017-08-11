---
layout: post
title: "Visualizing the Global Network of Sister Cities"
---

<a href="https://i.redd.it/2zkz9k798yez.png" title="Click to view higher resolution">
<img src="/assets/sister-cities-low-res.png" width="100%" /></a>

The concept of twin towns or [sister cities](https://en.wikipedia.org/wiki/Sister_city) fascinated me when I was growing up in a small industrial town in Sweden. What did my little municipality have in common with [Lapua](https://en.wikipedia.org/wiki/Lapua) in Finland or [Kjellerup](https://en.wikipedia.org/wiki/Kjellerup) in Denmark? Other examples include the Scottish town of Dull, which paired up with Boring, Oregon and Bland (Australia), much to the [Internet's amusement](http://www.scotsman.com/news/odd/scots-town-dull-joins-forces-with-bland-and-boring-1-3185215). I noticed that the pairings seemed to follow cultural connections; Scandinavian towns often have Scandinavian sister cities and occasionally one in Minnesota. Surely, there must be similar patterns elsewhere in the world?

I started searching for a dataset that could help me visualize this data. I found a [paper](https://arxiv.org/abs/1301.6900) that had visualized sister city relations, but the map was low resolution and the colors not optimal. An improved version has been [uploaded to Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Connections_between_sister_cities_visualised_on_a_world_map_(hotlog).svg).

To get my data, I [queried Wikidata](https://query.wikidata.org/), which is general knowledge database maintained by the Wikimedia Foundation. I found 20,108 distinct pairs of sister cities with the query

```
SELECT DISTINCT ?c1 ?c2 WHERE {
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
  ?city wdt:P190 ?sister_city.
  ?city wdt:P625 ?c1.
  ?sister_city wdt:P625 ?c2.
  FILTER ( STR(?c1) < STR(?c2) ).
}
```

There could be duplicates if the relationship is specified on multiple administrative levels and the coordinates for those entities differ, but duplicates aren't really a problem for the kind of visual I'm making.

I used the haversine formula to compute the distance between the two cities and mapped the quantiles of distance to line color with the _plasma_ color map included in matplotlib. For example, if two sister cities were closer than 75% of the pairs in my dataset, I would color the arc connecting them with 75% intensity. To connect the pair, I drew a great circle arc between them. I also made sure to set the drawing order such that the shortest lines would be drawn on top. I used Python with matplotlib and cartopy to make the visualization.

I find the result quite pleasing. I like how the borders of Europe are highlighted; even the former border between East and West Germany is clearly visible.
