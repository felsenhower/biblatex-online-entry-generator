# BibLaTeX @online entry generator (Bookmarklet)

This is a simple bookmarklet that generates a BibLaTeX entry with type @online of the site that you're currently on.

This bookmarklet is optimized for BibLaTeX which features the @online type. If you're using BibTeX, it will also work, but it will probably get styled like an @misc entry.

I also did put no effort in handling any LaTeX control characters, please do so yourself.

## How to use

1. Simply copy the following code snippet

```javascript
javascript:(function(){t=document.title;u=document.URL;d=new Date().toISOString().split("T")[0];id=btoa((u+t+d).split('').reduce((a,b)=>{a=((a<<5)-a)+b.charCodeAt(0);return a&a;},0)).replace(/\W/g,'').substring(0,8);alert("@online{" +id+ ",\n  title = {" +t+ "},\n  url = {" +u+ "},\n  urldate = {" +d+ "}\n}");})();
```

2. Create a new bookmark by right-clicking your browser's bookmark bar
3. Paste the snippet into the address field and choose an arbitrary title, e.g. "Generate BibLaTeX"
4. Visit the page you want to cite
5. Click on the bookmark
6. An alert will pop up which contains your BibTeX entry
7. Copy the content of the alert and paste it into your BIB file
8. Fix broken control characters, if present

E.g. for `github.com`, the entry will look like this:

```bibtex
@online{aHR0cHM6,
  title = {GitHub},
  url = {https://github.com/},
  urldate = {2020-09-20}
}
```

## Disclaimer

I have only tested this with Firefox.

## Code

The unminified code of the function is below:

```javascript
function(){
  t = document.title;
  u = document.URL;
  d = new Date().toISOString().split("T")[0];
  id = btoa((u + t + d).split('').reduce((a,b) => {
    a = (( a << 5 ) - a ) + b.charCodeAt(0);
    return a & a;
  }, 0)).replace(/\W/g, '').substring(0,8);
  alert("@online{" + id + ",\n  title = {" + t + "},\n  url = {" + u + "},\n  urldate = {" + d + "}\n}");
}
```
