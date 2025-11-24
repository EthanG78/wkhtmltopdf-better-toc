wkhtmltopdf and wkhtmltoimage
-----------------------------

wkhtmltopdf and wkhtmltoimage are command line tools to render HTML into PDF
and various image formats using the QT Webkit rendering engine. These run
entirely "headless" and do not require a display or display service.

See https://wkhtmltopdf.org for updated documentation.

## Building
wkhtmltopdf has its own dedicated repository for building and packaging.

See https://github.com/wkhtmltopdf/packaging


## better-toc forl
This fork provides more flexibility when creating a table of contents with wkhtmltopdf (basically a fix I needed). This fork adds the `data-toc-item`, `data-toc-level`, and `data-toc-title` attributes to any parsed outline items for table of content generation. Still, only header tags are parsed, but now if you don't want to include some header tags you can perform the following:
```html
<h1 data-toc-item="true">This will be included</h1>
<h1 data-toc-item="false">This will NOT be included</h1>
```

```toc.xsl
...
<xsl:if test="@data-toc-item!='false'">
...
</xsl:if>
```
Additionally, if you want to customize the text that appears in the generated TOC to not be the header tag's value but instead something custom, you can do the following:
```html
<h1 data-toc-item="true" data-toc-title="This will be rendered in the TOC!">This won't be the text rendered in the TOC</h1>
```
Overall, this provides more flexibility when it comes to customizing your TOCs with wkhtmltopdf. 
