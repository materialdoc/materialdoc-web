# How to contribute

* If you want to edit an article, at the top right corner of every page there is `Pencil` icon.
* If you want to write a new article.

    * Create `article-name.md` file based on [article-template](/article-template).
    * Put this file inside [/docs/components](https://github.com/materialdoc/materialdoc-web/tree/master/docs/components) or [/docs/patterns](https://github.com/materialdoc/materialdoc-web/tree/master/docs/patterns) folder.
    * Put images inside [/docs/images/](https://github.com/materialdoc/materialdoc-web/tree/master/docs/images) folder.
    * Add article reference to [mkdocs.ymld](https://github.com/materialdoc/materialdoc-web/blob/master/mkdocs.yml) file.
    * When ready send pull request to `master` branch.

### Preview

If you want to preview your article in browser, you have to install [mkdocs.js.org](http://www.mkdocs.org/) and run local server.

```
cd materialdoc
mkdocs serve
```
