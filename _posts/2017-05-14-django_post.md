---
layout: post
title:  "Why Django's request.POST returns nothing"
<!-- date:   2016-11-24 21:47:04 +0530 -->
categories: django
comments: true
---
If you are working with Django, you must have come across this issue.
We use `request.GET` to get all the parameters sent in GET request. But if you
try to do the same with `request.POST` it would return `<QueryDict: {}>`.

Where did your POST data go? Why is it empty? Let me start
by telling you how to get your POST data first. `json.loads(request.read())`
returns the data in a POST request.

Now let's discuss why `request.POST` returned an empty QueryDict.
It is because `request.POST` contains only the data sent from a HTML
`<form>` element. But if you prepare the request data from JavaScript
`request.POST` would be empty. In such cases you can get data from
HttpRequest by reading it like a file using `HttpRequest.read()`.
The returned data is of type string which you can convert to a dictionay by
passing it to `json.loads()`
{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = 'https://codersam8.github.io/django/2017/05/14/django_post.html';  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = '//codersam8.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-89599401-1', 'auto');
  ga('send', 'pageview');

</script>
