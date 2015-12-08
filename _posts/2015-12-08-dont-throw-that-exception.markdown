---
layout: post
title:  "Don't throw THAT exception"
date:   2015-12-08 20:55:00
categories: legacy-code gravatar
---

There are many reasons for throwing an exception in your code, but 
please take a second to think about what you are doing. 
En exception is something you do not want occuring. You should always try and 
code in a manner that does not throw exception. It called an 'exception' FFS.

I found this code today (rewritten as abstract):

{% highlight java %}

public Answer fetchAnswer(String nr) {
        try {
            return logic.fetch(nr);
        } catch(Exception e) {
            // Removed several else if (e instanceof Type)
            if(e instanceof WaitingForFetchExternalException){
                return someService.fetchFromExternal(nr);
            }
        }
}

{% endhighlight %}

{% highlight java %}
//An implementation of _logic_
public Ansver fetch(String nr) {
    //Removed some logic that check if external fetch should be used. 
    throw new WaitingForFetchExternalException("Is being fetched from external");
}
{% endhighlight %}

This code uses polymorphism on the service named _logic_, and, depending on environment the 
application is deployed in, different implementations of _logic_ is used. One of which (!)
throws the exception _WaitingForFetchExternalException_. The problem is of course 
that it is not an exception at all, it is the expected behavior of this particular implementation
of _logic_. This is an exceptionally bad way to use exceptions and is probably introduced in the 
code base because it is convenient (ie. easier in untested code) to use the glorified GOTO 
statement an exception can be. This code should be refactored. 
 
Some say this is pragmatism. I call it just bad code.

[Here is a good read on the same topic with more examples](http://c2.com/cgi/wiki?DontUseExceptionsForFlowControl)