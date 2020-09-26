---
layout: post
title:  "How to read JSON data in an HTTP POST request in Django"
<!-- date:   2016-11-24 21:47:04 +0530 -->
categories: django
comments: true
---
If you are working with Django, you might have faced this issue.
We use `request.GET` to get the data in a GET request. But if you
try to do the same with `request.POST` it would return an empty `<QueryDict: {}>`.

Where did the POST data go? Why is it empty?
It is because `request.POST` contains only the data sent from a HTML
`<form>` element. So if need to read JSON data from the POST request you need to
use `json.loads(request.body)`.

`request.body` gives you a raw HTTP request body as a bytestring. You can convert
into a dictionary using `json.loads()`.
{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = 'https://s-surineni.github.io/django/2017/05/14/django_post.html';  // Replace PAGE_URL with your page's canonical URL variable
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
