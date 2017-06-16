---
layout: page
title: Blog
header: Blog
group: navigation
---
{% include JB/setup %}

{% for post in site.posts %}
<div class="panel">
    <div class="panel-body">
		<div class="row"> 
		<br>
			<div class="col-md-2 col-sm-3 text-center">
              <a class="story-img" href="{{ post.url }}"><img src="{{ post.thumbnail }}" style="width:100px;height:100px" class="img-thumbnail"></a>
            </div>
			<div class="col-md-10 col-sm-9">
              <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
				<div class="row">
					<div class="col-xs-9">
						<p>{{ post.excerpt }}</p>
						<a class="btn btn-default" href="{{ post.url }}">See full post</a>
						<a class="pull-right"> <div> <ul>{% assign tags_list = site.tags %} {% include JB/tags_list %}</ul></div></a>
						<ul class="list-inline"><li>{{ post.date | date_to_string }}</li><li><a href="#"><i class="glyphicon glyphicon-share"></i><!-- 12 --></a></li></ul>	
					</div>
                <div class="col-xs-3"></div>
              </div>
              <br><br>
            </div>	
		</div>
	</div>
</div>
{% endfor %}

{% include JB/tags_list %}
