# Script loading strategies

There are a number of issues involved with getting scripts to load at the right time. Nothing is as simple as it seems!
A common problem is that all the HTML on a page is loaded in the order in which it appears.

If you are using JavaScript to manipulate elements on the page (or more accurately, the Document Object Model), your
code won't work if the JavaScript is loaded and parsed before the HTML you are trying to do something to.

In the above code examples, in the internal and external examples the JavaScript is loaded and run in the head of the
document, before the HTML body is parsed. This could cause an error, so we've used some constructs to get around it.

In the internal example, you can see this structure around the code:

`document.addEventListener("DOMContentLoaded", function() { ... });`

This is an event listener, which listens for the browser's "DOMContentLoaded" event, which signifies that the HTML body
is completely loaded and parsed. The JavaScript inside this block will not run until after that event is fired,
therefore the error is avoided (you'll [learn about events]() later in the course).

In the external example, we use a more modern JavaScript feature to solve the problem, the defer attribute, which tells
the browser to continue downloading the HTML content once the `<script>` tag element has been reached.

`<script src="script.js" defer></script> `

In this case both the script, and the HTML will load simultaneously, and the code will work.

Note: In the external case, we did not need to use the DOMContentLoaded event because the defer attribute solved the
problem for us. We didn't use the defer solution for the internal JavaScript example because defer only works for
external scripts.

An old-fashioned solution to this problem used to be to put your script element right at the bottom of the body (e.g.
just before the </body> tag), so that it would load after all the HTML has been parsed. The problem with this solution
is that loading/parsing of the script is completely blocked until the HTML DOM has been loaded. On larger sites with
lots of (JavaScript), this can cause a major performance issue, slowing down your site.

## `async` and `defer`

There are actually two modern features we can use to bypass the problem of the blocking script — `async and defer` (
which we saw above). Let's look at the difference between these two.

### `async`

Scripts loaded using the `async` attribute (see below) will

- <span style="color: #009988">Download the script without blocking rendering the page</span> and will execute it as
  soon as the script finishes downloading.
- You get <span style="color: #009988">no guarantee that scripts will run in any specific order</span>, only that they
  will not stop the rest of the page from displaying.
- It is <span style="color: #009988">best to use async when the scripts in the page run independently of each
  other</span> and depend on no other script on the page.

*For example*, if you have the following script elements:

```html

<script async src="js/vendor/jquery.js"></script>

<script async src="js/script2.js"></script>

<script async src="js/script3.js"></script> 
```

You can't rely on the order the scripts will load in.

`jquery.js` may load before or after `script2.js` and `script3.js` and if this is the case, any functions in those
scripts depending on jquery will produce an error because jquery will not be defined at the time the script runs.

async should be used when you have a bunch of background scripts to load in, and you just want to get them in place as
soon as possible. *For example*, maybe you have some game data files to load, which will be needed when the game
actually begins, but for now you just want to get on with showing the game intro, titles, and lobby, without them being
blocked by script loading.

### `defer`

Scripts loaded using the `defer` attribute (see below) will run in the order they appear in the page and execute them as
soon as the script and content are downloaded:

```html

<script defer src="js/vendor/jquery.js"></script>

<script defer src="js/script2.js"></script>

<script defer src="js/script3.js"></script>
```

All the scripts with the defer attribute will load in the order they appear on the page.

So in the second example,

- we can be sure that `jquery.js` will load before `script2.js` and `script3.js` and that `script2.js` will load
  before `script3.js`.
- They won't run until the page content has all loaded, which is useful if your scripts depend on the DOM being in
  place (*e.g. they modify one of more elements on the page*).

### To summarize:

`async` and `defer` both instruct the browser to download the script(s) in a separate thread, while the rest of the
page (
the DOM, etc.) is downloading, so the page loading is not blocked by the scripts.

#### <span style="color: #009988">If your scripts should be run immediately, and they don't have any dependencies, then use async.

If your scripts need to wait for parsing and depend on other scripts and/or the DOM being in place, load them using
defer and put their corresponding `<script>` elements in the order you want the browser to execute them. 
