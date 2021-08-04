
# Try Some SVG

Question is: will GitHub (and friends) render this recursive SVG image? 

![](recursion.svg)

The answer: no! 

You should see the content of the "parent" SVG image - a red circle.  
There is a "child" SVG image embedded within which you (as of publication time) can't see.  
Depending on your browser it'll either look like: 
* Nothing (Safari), or 
* The "no image found" logo (Chrome) 

[Open that file](recursion.svg) - or even better the [raw.githubusercontent.com](https://raw.githubusercontent.com/dan-fritchman/TrySomeSvg/main/child.svg) version with the dev-tools open, and you'll see some errors like: 

```
Refused to load the image 'https://raw.githubusercontent.com/dan-fritchman/TrySomeSvg/main/child.svg' because it violates the following Content Security Policy directive: "default-src 'none'". Note that 'img-src' was not explicitly set, so 'default-src' is used as a fallback.
```

So it seems that: 

* SVGs get rendered by the `raw.githubusercontent` mechanism (or similar) 
* That mechanism blocks loading *any* internal content via the [Content Security Policy (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) `default-src: none`

Sad! 

