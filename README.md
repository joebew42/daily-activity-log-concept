# Daily Activity Log Concept

The aim of this project is to produce a standard that gives to people an easy way to share and aggregates personal activity log around the Internet. You can think it such a sort of decentralized microblog platform without a platform: _"A microblog platform-less"_

## WTF!? Platform-less!

_Platform-less_ because you do not need a proprietary format platform in order to create, manage and share your daily activity log (like [_Wordpress_](https://wordpress.org/), [_Ghost_](https://github.com/tryghost/Ghost), [_Jekyll_](http://jekyllrb.com/) or others). You can manage your daily activity log through an XML (or JSON?) file that have to respect a format that is more human readable as possible, style it with CSS/XSLT rules and push your daily updates to your github pages repository.

A typical directory structure of your *platform-less microblog* could be:

```
/
/events.xml
/events.xsl
/events.css
```

You have to push your regular updates in `events.xml` and then everyone could access them by surfing your [_github page_](https://pages.github.com/) (`http://username.github.io/events.xml`) or aggregates contents with a custom made client.

## Data format

We are going to define a structured format that can be used to easily describe an activity. The candidates are XML (with an optional XSLT support for content representation formatting), JSON or RDF.

The basic idea is that each activity must describe a the action that we perform on a object. In addition we will give some useful (but optional) information such as references about the activity (such as URL, notes or whatever).

### XML

The XML format is the first candidate for a real application usage. If you want to give it a try, checkout the ready-to-go project [**daily-activity-log**](http://github.com/joebew42/daily-activity-log/), fork it to your github page repository and start push updates on `events.xml` file, improve the `css` or try different layout by modifying the `xsl`.

```
<events>
    <event date="YYYY-MM-DD">
        <action type="reading">My first book ever !</action>
        <references>
            <reference src="http://somewhere.local/resource.html" type="source" />
            <reference src="http://somewhere.local/resource.html" type="note" />
        </references>
    </event>
</events>
```

### JSON

```
[
    {
        "date" : "YYYY-MM-DD", "action" : "reading", "on" : "My first book ever !",
        "references" : [
            { "src" : "http://somewhere.local/resource.html", "type" : "source" },
            { "src" : "http://somewhere.local/resource.html", "type" : "note" }
        ]
    }
]
```

### RDF

Here I need help. The event should be expressed with the proper [Action type](http://schema.org/Action). Sadly, the action itself is not sufficient to describe the Event. We have to express references too:

```
<"Joe":Person> <ReadingAction:Predicate> <"My first book ever !":Book>
Other relations that link the Book with References ???
```

Anyway, the RDF format is not designed to be Human Readable. If we want to make event semantically valid we should translate it from XML or JSON to RDF. This could be optional.

If you are reading this section and know about RDF, I'll appreciate to see an example of an event expressed in RDF format. Maybe an action on schema.org already exist but I found nothing about.

### How to contribute

If you want to talk about this format, please open an issue. You are welcome!
