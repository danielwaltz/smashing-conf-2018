# Day 1

## General Design

* Be itterative in the whiteboard - "version control" for design
* Get to the point - it's easy to over think a design
* Inspiration can come from design of simple tangible things
* Great design is a constant - apply it to everything

## CSS Grid

* Fixed units in relation to sizing in grid - understand why things are sized the way they are without percentages
* Three types of sizing - fixed, intrinsic, and flexible
* CSS grid is magic ???
* Spec is similar to flexbox - yay!
* Lets you force sizing of content in a grid item (like images)
* [Box alignment cheatsheet](https://rachelandrew.co.uk/css/cheatsheets/box-alignment)
* "Feature queries" might be an option for progressive enhancement

```
@supports (display: grid) {
    WOW HELL FUCKING YES
}
```

* `shape-outside` css prop is neat
* Don't worry about it looking the _same_ everywhere - make it look _good_ everywhere
* Why flexbox? It's more simple - use it for simple things
* Find content & articles that align with the solution you're looking for - not every solution works for you
* Flexbox and CSS grid isn't either/or - why not both?
* IE11 doesn't support feature queries - nuuuuu
* Code without grid to start and adapt to it with feature queries

## Web Design

* Care about states like `:focus` and `:active` - don't remove defaults, make them better
* [Localization tips](https://slack.engineering/localizing-slack-680c4bc7f45a)
* Using slack to access documentation via `/whatever` commands is a neat idea
* Don't get ahead of yourself - a strong foundation is important
* Markup first - clean html is the highest priority - use css for proper formatting

## User Experience

* Understand people and their lives - design better experiences
* Expect people to be distracted while using your interface - _VERY GOOD THOUGHT_
* People can be in less than ideal mindsets - maybe tired, disinterested, not motivated, etc
* Decision fatigue (cognitive load) is _so very real_ - reduce mental cost!
* Rough equation to help with this - compare the **time to respond** to the **number of options**
* Step driven design - lead into following actions
* Consider numonics (lefty loosey, righty tighty boyyy)
* People are bad at working with declaritive knowledge and good at procedural knowledge
* Don't be different for the sake of being different - people have expectations from years of using websites ([design axiom](https://www.designprinciplesftw.com/collections/design-axioms)) - take advantage of that!
* Introducing new prodecural designs is hard - it demands a mental retraining - largly unavoidable unforunately
* People work in models - consider how a person expects to order coffee? buy a movie tickets? order a product?
* So... how do you innovate then? You can't really...? Use it to guide people down new paths if you want, but you just can't change for the sake of change

## Script & Load Time Optimization

* 3rd party scripts can get out of hand fast
* If you notice the bloat, say something about it!
* Might be useful to consider `npm` packages as 3rd party and attributed to bloat
* Inspect http archive `.har` files with [har.tech](https://har.tech)
* Interesting stat - out of 46 sites, resources came from 213 other unique locations - the web branches like crazy
* News and shopping sites are the worst offenders
* Tag managers can make it too easy to add scripts without considering consquences (don't blame the tool tho)
* Would be a very good idea to define a performance budget (no more than 1MB network load for instance)
* ^ Could be nice to catagorize them (allot for images, 3rd party scripts, css, etc)
* Easy to convince other devs - harder to convince leadership - **SAD**
* Kinda obvious, but speed super matters - almost the most important aspect of UX
* Percieved perf can help - show _something_ until you can show what matters
* Lots of js is extra expensive because it's more than size - it's parse time
* It's important to test on real hardware - virtualized hardware is not representative for parse time
* Goes without saying, but only load what you need
* Server optimization can have yyyuge gains (cache headers, gzip/brotli, response times, etc)
* Code splitting is nice (can confirm)
* If you can, only import and use the pieces of a lib that you actually need
* Network panel in chrome lets you see priority!
* Import important scripts in html using `<link rel="preload || prefetch || prerender" type="script" link="file.js">`
* HTTP2 does cool things - look into http push (it might be too aggressive right now, it doesn't care about browser cache)
* In progress spec called "priority hints" - add `importance="low || high"` to html tags
* `font-display: optional;` can help with web font flashing or hidden text
* Define a preload for web fonts!
* Progressive web apps are hype - slack, twitter, and other big names are doing this shit - service workers are going to be very important soon
* [Very relevant article](https://medium.com/@paularmstrong/twitter-lite-and-high-performance-react-progressive-web-apps-at-scale-d28a00e780a3)
* Include optimization into the build tooling - maybe CI tests for perf? (thanks `create-react-app`)
* If you _have_ to focus on one metric, focus
  on "time to interactive"

# Day 2

## Design Systems

* The rate on change is different depending on the layers in your application or website
* Reusabliity & automation in this field is out of neccesity - there just aren't enough of us
* We're in an era of design systems :3
* MAKE. A. STRONG. FOUNDATION.
* Rate of change order for design systems: foundation > governance > documentation > people > patterns (like components) > tooling
* Care about what you name things
* Goes without saying, but design systesm are hard and demands many people and teams - not a good option even for some large companies

## _Beyond_ Media Queries

* Maybe don't rely only on media queries
* Using media queries is like a heatmap - you cater to break points sizes and the further you stray from the definiations the less the design properly fits the screen
* How can we design without breakpoints?
* Fluid typography - `calc()` with `vw` for font sizing - **AWESOME IDEA**
* Magic prop `font-size: calc(18px + 3vw);`
* Change the rate of scale with `font-size: calc(16px + (24 - 16) * (100vw - 400px) / (800 - 400));`
* SASS mixins available - neat!
* [Typescale](https://type-scale.com/) to generate module scale
* SVG can help too!
* Flex hack `flex-grow: 9999;`
* CSS custom proporties (variables) are dynamic - lots of fun options!
* Custom props are scoped but inherited
* Change the value, not the variable
* Use them - just do it - **progressive enhancement bruv**
* Element media queries...?
