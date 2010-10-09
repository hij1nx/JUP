
![Alt text](http://29.media.tumblr.com/tumblr_l2xo55ndbA1qbo0zio1_r1_400.png)

* JUP Style JSON is now a STANDARD. *
The spec can be found at http://jsonml.org/ which is managed by Stephen

** JUP: Javascript IN, markup OUT. **
JUP processes a format now called jsonML which attempts to be the most concise mapping of JSON to MARKUP.
The purpose of this is to promote the Separation of Concerns principle, and keep markup out of javascript. 
JUP generates markup elements which are declared using nested arrays, for instance:

    ["div", { "class": "foo" }, "some text", ["br"]]

Args can come in any order as long as the first is a tag name. Any arbitrary string can become an element, no registering templates you can simply assign the jup-array to a variable and reuse it. If an object literal is provided in your jup-array, it's directly mapped to attributes of the element. Also, since all values in the JUP structure are strings, they can be stubbed out with mustache style {{tokens}}, they'll get filled in each time you use your jup-array, for instance: 

    ["{{tag}}", { "class": "foo" }, "some {{value}}", ["br"]]

This allows jup-arrays be data driven. No special keys or cryptic symbols like "cls" for class. Works great for SSJS and CSJS. JUP weighs in currently with most functionality done at about less than 100 lines of code, its really simple.

There are so many of '<%=these_template_engines%>' out there!! Theres a number of micro-templating and markup generation solutions, but very few address Separation Of Concerns. Designers should never need to confront script code, and markup strings look awful in JS. JUP attempts to take the simplest approach to mapping javascript and data to markup production. Here are some examples (more on the wiki page)...

    ["div"] // Renders: <div></div>

    ["div", { "class": "foo" }] // Renders: <div class="foo"></div>

    ["div", { "class": "foo" }, "content"] // Renders: <div class="foo">content</div>

    ["div", { "class": "{{someclass}}" }, ["div"], "content"] // Renders: <div class="foo"><div></div>content</div>

    ["{{namespace}}:{{tag}}", { "{{somekey}}": "foo" }, "content", ["div"]] // Renders: <ns:tag bar="foo">content<div></div></div>
