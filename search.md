---
layout: page
title: Search
header: Blog
---
{% include JB/setup %}

<h2>Search Page</h2>

<div class="col-xs-6">
	<form class="form-search" role="search" action="search.html">
		<div class="input-group add-on">
				<input class="form-control" placeholder="Search" name="q" id="tipue_search_input" type="text" pattern=".{3,}" title="At least 3 characters" required>
					<span class="input-group-btn">
						<button class="btn btn-success" type="button">
							<span class="glyphicon glyphicon-search"></span>
						</button>
					</span>
			<div style="clear: both;"></div>
		</div>
	</form>
</div>
<br>
<div id="tipue_search_content"></div>




<!-- Html Elements for Search -->
<div id="search-container">
<input type="text" id="search-input" placeholder="search...">
<ul id="results-container"></ul>
</div>

<!-- Configuration -->
<script>
SimpleJekyllSearch({
  searchInput: document.getElementById('search-input'),
  resultsContainer: document.getElementById('results-container'),
  json: '/search.json'
})
</script>
