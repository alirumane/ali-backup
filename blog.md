---
layout: page
title: Blog
header: Blog
group: navigation
---
{% include JB/setup %}
<div class="col-md-8">
<div class="row">
{% for post in site.posts %}
<div class="panel">
    <div class="panel-body">
		<div class="row"> 
		<br>
			<div class="col-md-4 text-center">
              <a class="story-img" href="{{ post.url }}"><img src="{{ post.thumbnail }}" style="width:200px;height:200px" class="img-thumbnail"></a>
            </div>
			<div class="col-md-8">
              <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
				<div class="row">
					<div class="col-xs-9">
						<p>{{ post.description | truncate: 150 }}</p>
						<a class="btn btn-default" href="{{ post.url }}">See full post</a>
						<a class="pull-right"> <div> <ul class="list-inline">{% assign tags_list = post.tags %} {% include JB/tags_list %}</ul></div></a>
						<ul class="list-inline"><li>{{ post.date | date_to_string }}</li><li><a href="#"><i class="glyphicon glyphicon-share"></i><!-- 12 --></a></li></ul>	
					</div>
              </div>
              <br><br>
            </div>	
		</div>
	</div>
</div>
{% endfor %}

</div>
<div class="col-md-4">
	<div class="well">
		<h3> <i class="fa fa-tags" aria-hidden="true"></i> Tags</h3>
		<ul>
		{% assign tags_list = site.tags %}  
		{% include JB/tags_list %}
		</ul>
	</div>
	<div class="well">
		<h3> <i class="fa fa-folder-open" aria-hidden="true"></i> Categories</h3>
		 <ul>
		{% assign categories_list = site.categories %}
		{% include JB/categories_list %}
		</ul>
	</div>
</div>
</div>
