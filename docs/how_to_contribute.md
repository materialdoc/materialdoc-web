# How to contribute

* At the bottom of every page there is **Edit this page on GitHub** button.
* If you want to write new article.
  * Create `article-name.md` file based on [article-template](/article-template).
  * Put this file inside [/content/components](https://github.com/materialdoc/materialdoc-web/tree/master/content/components) or [/content/patterns](https://github.com/materialdoc/materialdoc-web/tree/master/content/patterns) folder.
  * Put images inside [/content/images/](https://github.com/materialdoc/materialdoc-web/tree/master/content/images) folder.
  * Add article reference to [sidebar.md](https://github.com/materialdoc/materialdoc-web/blob/master/content/_sidebar.md) file.
  * When ready send pull request to `master` branch.

### Preview

If you want to preview your article in browser, you have to install [docsify.js.org](https://docsify.js.org/#/quickstart) and run local server.

* Install docsify-cli globally `npm i docsify-cli -g`
* Run the local server with docsify serve. To preview site in your browser open http://localhost:3000

```
cd materialdoc
docsify serve content
```
