# astro-new-coll-api

Example project to demonstrate Astro v0.18.0-next.4 not building collection routes with a dot (.).

## Steps to reproduce

```bash
mkdir -p astro-new-coll-api/src/pages
cd astro-new-coll-api
npm init -y
npm install astro@next
# Add scripts in package.json
# Create src/pages/$site.astro
npm run build
```

## Result

### Expected

Three pages get rendered.

* /site/example-a.com/index.html
* /site/example-b-com/index.html
* /site/example-c-com/index.html


```
npm run build

> astro-new-coll-api@1.0.0 build
> astro build

[config] Set "buildOptions.site" to generate correct canonical URLs and sitemap
[16:60:27] [snowpack] Hint: run "snowpack init" to create a project config file. Using defaults...
[16:60:28] [snowpack] Ready!
[build] ! building pages...
[build] ✔ pages built.
[build] ! optimizing css...
[build] ✔ css optimized.
[build] ! bundling...

   Pages                                                     Page Weight (GZip)
 ┌ /site/example-a.com/index.html                            0.00 kB
 ├ /site/example-b-com/index.html                            0.00 kB
 └ /site/example-c-com/index.html                            0.00 kB
[build] ▶ Build Complete!
```

### Actual

The page for example-a.com is not rendered while example-b-com and example-c-com are.

```
npm run build

> astro-new-coll-api@1.0.0 build
> astro build

[config] Set "buildOptions.site" to generate correct canonical URLs and sitemap
[16:59:10] [snowpack] Hint: run "snowpack init" to create a project config file. Using defaults...
[16:59:10] [snowpack] Ready!
[build] ! building pages...
[build] ✔ pages built.
[build] ! optimizing css...
[build] ✔ css optimized.
[build] ! bundling...

   Pages                                                     Page Weight (GZip)
 ┌ /site/example-b-com/index.html                            0.00 kB
 └ /site/example-c-com/index.html                            0.00 kB
[build] ▶ Build Complete!
```

Tested with both Node.js v16.5.0 and v14.17.3 on Linux.
