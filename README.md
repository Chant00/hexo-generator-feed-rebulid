# hexo-generator-feed-rebulid
add css to support rss view better  

## Before  
- You are using node hexo  
- Your website(Wiki/Blog) are using hexo plugin - [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed)  
- You want to make your rss looking better  

## Resolve  
add css to the rss'xml    

## How to use
Ok, everybody.Let's begin.  
1. <pre><code>
cd ./your website dir/node-modules/hexo-generator-feed/lib/
vim generator.js
</code></pre>  
2. change code undiffent.Also you can directly clone, but it's not recommend...

## Undiffent code  
- css/rss.css in my gayhub is necessary!!
- add this code:  
<pre><code>
var rssCssSrc = pathFn.join(__dirname, '../css/rss.css');
var rssCssTmpl = nunjucks.compile(fs.readFileSync(rssCssSrc, 'utf8'), env);
</code></pre>  
- change this code on the end:  
<pre><code>
var rssCss = rssCssTmpl.render();
    return [
        {
            path: feedConfig.path,
            data: xml
        },
        {
            path: feedConfig.path.substr(0,feedConfig.path.length - 8) + "css/rss.css",
            data: rssCss
        }
    ];
</code></pre>
