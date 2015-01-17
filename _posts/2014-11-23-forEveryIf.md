---
layout: post
title: For Every If...
---

##...There really should be an else.
Or an otherwise or a catch or something.


**I am learning through repeated ERROR that I need to take more care to cover my butt.**  

Today I spent a great deal of time staring at some code for a POST request, and wondering why the promise returned was falling straight through to the catch block.  I got a little mad at the repo for a while, and then I realized that this was a gift.

{% highlight javascript %}
var add = function(link) {
    return $http({
      method: 'POST',
      url: '/api/links',
      data: link
    })
    .then(function(){
      console.log('HeyThere!');
    })
    .catch(function(err){
      $window.location = '#/links';
      console.log(err, 'CAUGHTCAUGHT!');
    });
  };
{% endhighlight %}

Every time a promise didn't resolve the way I was expecting, I could immediately see where the error was caught, through a simple logging of "CAUGHTCAUGHT", or "YOUSANKMYBATTLESHIP".  Even though it took me a while to wade through this code, I never went down with the ship through the stack trace because I could see the error trail that I wrote myself.  

It occurred to me that I have never seen this before because in writing code I often write if statements without a corresponding else because I am just too lazy and those cases probably shouldn't really matter anyway because its fun to pretend to be a wizard.
    
##I realized that I should be taking measures to **CATCH** my own errors always.

And that it doesn't have to be anything too fancy.  I'll always write the path that I expect data to flow through, but if it doesn't work out as planned, I can set up blocks that will tell me exactly where things went awry.


{% highlight javascript %}
//for example:

if ( IsDefinedHere(data) ){
  passAlong(data)
} else {
  console.log("Your data is in the chocolate swamp.")
}

{% endhighlight %}
 
And I know where that chocolate's at.
 
Send me good vibes please world...
