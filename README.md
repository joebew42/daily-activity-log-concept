# Events Stream Log

## Problem

I would like to have a mechanism that allows me to browse the history of my personal events stream.
What is an *Events Stream*? An Events Stream is an ordered list of events, in which each event can
describe an action that I've done during the day (e.g. Studying a paragraph of a book, Reading a book,
Writing a new blog post, Thinking about a specific topic, and so on). By querying my events stream log,
I (or other people) can stay updated about different kind of topic or activities. Better, I can go back
in time through my events stream to find useful information believed lost.

## Idea

The idea is that everyone can have a personal events stream log, in which (daily) can be feeded with
events. Is not about a centralized social network platform with proprietary format or lock-in logics.
Is something about a standard. What I have to do is to publish a file (in a Human Readable format) and
share the URL with who wants to follows my stream of events.

Example: http://joebew42.github.io/events.xml or simply http://joebew42.github.io

In this example I can maintain my events stream with a version control system.

## Example of data format

We are going to define a structured format that can be used to easily describe an activity.
The candidates are XML (with an optional XSLT support for content representation formatting),
JSON or RDF.

### XML

```
<stream>
    <event date="YYYY-MM-DD" action="reading" on="My first book ever !">
        <references>
            <reference src="http://somewhere.local/resource.html" type="source" />
            <reference src="http://somewhere.local/resource.html" type="note" />
        </references>
    </event>
</stream>
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

Here I need help. The event should be expressed with the proper [Action type](http://schema.org/Action).
Sadly, the action itself is not sufficient to describe the Event. We have to express
references too:

```
<"Joe":Person> <ReadingAction:Predicate> <"My first book ever !":Book>
Other relations that link the Book with References ???
```

Anyway, the RDF format is not designed to be Human Readable. If we want to make event
semantically valid we should translate it from XML or JSON to RDF. This could be optional.

If you are reading this section and know about RDF, I'll appreciate to see an example
of an event expressed in RDF format. Maybe an action on schema.org already exist but
I found nothing about.
