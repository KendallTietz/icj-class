# Data and loops

We're going to update our index page to look more like blog landing page, and we'll use a loop of data to create links to our Ship's Log entries.

Open up the `src/njk/index.njk` and take a look at it.

- The first line _extends_ the "base" layout. This is fine, since this is the only page we'll have like this.
- The next bit is _block page\_title_, which allows us to replace the default title, which we should do. Update the contents of that block with "The Ship's Log".
- Next, we have the _block content_, which is the guts of our page.

Now, look in the code for the bit about `data.books`, which prints out a series of books from a data file:

```html
<ul> 
  {% for book in data.books %}
    <li>{{ book.title }}, {{ book.author }}</li>
  {% else %}
    <li>This would display if the 'books' collection were empty</li>
  {% endfor %}
</ul>
```

A "for loop" in programming will repeat a series of code for as long as the condition is true. In our case Nunjucks will repeat the code for each new "book" in the "books" collection. This is a prime example of [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) programming, or DON'T REPEAT YOURSELF.

If there are no "books", then our _else_ condition is used, which is text noting the collection is empty. (Else conditions are optional depending on your logic needs).

Where is this "books" collection coming from? This project-template is set up so you can store data collections as JSON files in the `src/njk/_data/` folder. Look there and you'll find a file called `data.json`. Open that up and you'll see something similar to this:

```json
{
  "books": [
    {
      "title": "The Clown",
      "author": "Heinrich Böll"
    },
    {
      "title": "The Shipping News",
      "author": "Annie Proulx"
    },
    {
      "title": "The Hearing Trumpet",
      "author": "Leonora Carrington"
    }
  ]
}
```

This is a typical example of JSON, the data format for JavaScript. Here we define the "books" collection first, then set it to an **array** of key-value pairs ... "title" and "author". Think of each of those sets as a row of data in a spreadsheet.

Nunjucks can access the data from the current row through the key: `{{ book.title }}` gets the value "The Clown" on it's first pass through the data.

When we started Gulp, this "books" data collection was loaded into the Nunjucks "context", meaning it was made available to it. This was all set up in the Gulp tasks by the developer (me). To add new data for the templates, define it in `data.json` and restart Gulp.

## Add our blog entries to the data

On our index, we want to print out a list of all our blog entries. Let's add data about our entries into `data.json` so we can loop through it.

- In the `src/njk/data/data.json` file, add a comma after the last `]`.
- Add the following code:

```json
"entries": [
  {
    "date": "October 18, 2018",
    "url": "2018-10-18.html",
    "title": "It was a dark and stormy night"
  },
  {
    "date": "October 19, 2018",
    "url": "2018-10-19.html",
    "title": "Fear the Kraken"
  },
  {
    "date": "October 20, 2018",
    "url": "2018-10-20.html",
    "title": "Call me Ishmael"
  }
]
```

- Kill your BrowserSync server and restart it with `gulp dev`. Data is imported during the Gulp startup sequence, so we have to restart that each time we add or edit data.
- Now replace the entire for loop structure (including the `ul` tags) with this:

```html
{% for entry in data.entries %}
  <p>{{ entry.title }}, {{ entry.date }}, {{ entry.url}}</p>
{% endfor %}
```

We changed what the loop was looking for: `for entry in data.entries`. The "data.entries" part of that is important, because that is the name file first ( the "data" in `data.json`), then the name of our array in that file ("entries").  The "entry" term is what we call a single instance of the data within the loop. We can use whatever term we want there as long as we are consistent, but it is good practice to use variable names that make sense.

Now, in our `<p>` tag we are accessing the values in the data through their keys: `{{ entry.title }}`. The "entry" part of that term comes from what we defined it in the loop (for _entry_ in data.entries). And "title" is the "key" that matches the "value" we want from that row of the data.

This might seem like overkill for just three lines of data, but you can imagine how powerful this can be with lots of data, or how we can add new rows to data without editing our pages.

### Tools to make JSON data

If you have a spreadsheet of data that you need in JSON format, [CSVJSON](https://www.csvjson.com/) is a tool that can help with that. With [CSV to JSON](https://www.csvjson.com/csv2json) you can copy/paste from a spreadsheet and then get JSON in return.

## Rewrite our loop code to be more awesome

Now that we know how to access the data in our templates, we can change up our HTML/Bootstrap markup to make them look a little nicer.

Instead of a list, let's use headlines and such:

```html
{% for entry in data.entries %}
  <h3 class="entry-headline"><a href="{{ entry.url }}">{{ entry.title }}</a></h3>
  <p class="entry-date">{{ entry.date }}</p>
  <hr>
{% endfor %}
```

## Make it pretty and publish

### Index updates

- On the index, add an H1 headline and replace our ipsum text with something creative you write that introduces this blog about a ship's travel.
- When viewed on a desktop, the display of the index is really wide and not very readable. Play with the column [grid](https://getbootstrap.com/docs/4.3/layout/grid/) on the index so that the content uses full width on mobile, but fewer columns at the `sm` and higher breakpoints. The content should be centered on the page, though, which you can do by applying an [offset](https://getbootstrap.com/docs/4.3/layout/grid/#offsetting-columns) to move the column over to the right.

### Detail page updates

- Add some content to all three detail pages so you can easily tell them apart when you view those pages. Like new headlines. The text can just be different lorem ipsum text. Add a different Kraken photo to each page, with an img-fluid class.
- Now that you know a little about Nunjucks blocks, note that the `base.njk` template has a block for "page_title". On your detail pages, override the default page_title with one appropriate for each page, perhaps using your blog entry headline.

### Publish and check

- Publish this using Github Pages using the `docs` directory.

---

You're done!