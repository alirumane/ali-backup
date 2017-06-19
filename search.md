---
layout: search
title: Search
header: Blog
---
{% include JB/setup %}

<h1>Search Page</h1>

<form action="search.html">
<div class="input-group">
<div class="tipue_search_left"><img src="tipuesearch/search.png" class="tipue_search_icon"></div>
<div class="tipue_search_right"><input type="text" name="q" id="tipue_search_input" pattern=".{3,}" title="At least 3 characters" required></div>
<div style="clear: both;"></div>
</div>
</form>
<div id="tipue_search_content"></div>
