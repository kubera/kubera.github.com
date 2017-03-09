---
title: "Groovy is awesome!"
tags: [groovy, grails, gradle]
---

In my last project, we used Grails 3 that uses _groovy_ as the main technology. With groovy you can really focus on your business problems. You have very little boilerplate code.

Here it is some cool stuff I really like in groovy.

Working with strings:
{% highlight groovy %}
def text = 'Groovy is awesome!'
assert text[10..16] == 'awesome'
assert text - ' is awesome!' == 'Groovy'
assert text[0].isLetter()
assert text[0].isUpperCase()
assert text[6].isWhitespace()
{% endhighlight %}


Working with lists and maps:
{% highlight groovy %}
List emptyList = []
def countries = ["England", "Switzerland", "France"]
assert countries[1] == "Switzerland"
countries << "Italy"
assert countries.contains("Italy")
Map emptyMap = [:]
def country = [name: "Switzerland", capital: "Bern", population: 8211700]
assert country.name == "Switzerland"
{% endhighlight %}

The elvis operator is very useful:
{% highlight groovy %}
def text
assert 'not null' == text ?: 'not null'
text = 'Hi!'
assert 'Hi!' == text ?: 'not null'
{% endhighlight %}

Avoid null pointer exception:
{% highlight groovy %}
class Country {
    Capital capital
}
class Capital {
    String name
}
def switzerland = new Country()
println switzerland?.capital?.name
{% endhighlight %}
