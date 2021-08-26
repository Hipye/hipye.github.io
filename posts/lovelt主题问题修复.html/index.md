# Lovelt主题问题修复


## loveitbug修复

```
Start building sites …
ERROR 2020/10/05 23:28:46 render of "page" failed: execute of template failed: template: _default/single.html:18:124: executing "content" at <partial "function/content.html">: error calling partial: "/Users/peterlu/Documents/Dev/blog/themes/LoveIt/layouts/partials/function/content.html:4:19": execute of template failed: template: partials/function/content.html:4:19: executing "partials/function/content.html" at <partial "function/ruby.html" $content>: error calling partial: partial that returns a value needs a non-zero argument.
ERROR 2020/10/05 23:28:46 render of "page" failed: execute of template failed: template: _default/single.html:18:124: executing "content" at <partial "function/content.html">: error calling partial: "/Users/peterlu/Documents/Dev/blog/themes/LoveIt/layouts/partials/function/content.html:4:19": execute of template failed: template: partials/function/content.html:4:19: executing "partials/function/content.html" at <partial "function/ruby.html" $content>: error calling partial: partial that returns a value needs a non-zero argument.
Total in 418 ms
Error: Error building site: failed to render pages: render of "page" failed: execute of template failed: template: _default/single.html:18:124: executing "content" at <partial "function/content.html">: error calling partial: "/Users/peterlu/Documents/Dev/blog/themes/LoveIt/layouts/partials/function/content.html:4:19": execute of template failed: template: partials/function/content.html:4:19: executing "partials/function/content.html" at <partial "function/ruby.html" $content>: error calling partial: partial that returns a value needs a non-zero argument.
```
layouts/partials/function/content.html 源文件第一行后面和最后一行之前加入相应內容

```
{{- $content := .Content -}}

{{- if ne "" $content -}} #加入的代码

{{- if .Ruby -}}
    {{- $content = partial "function/ruby.html" $content -}}
{{- end -}}
@@ -16,4 +18,6 @@

{{- $content = partial "function/escape.html" $content -}}

{{- end -}} #加入的代码

{{- return $content -}}
```
## 修复网页上的的icin不显示
到这个网页上[https://realfavicongenerator.net](Favicon Generator) 处理自己的网站图标，最后会下载一个压缩包，包括生成的图标和 browserconfig.xml 、 site.webmanifest 等文件，将这些文件放到 blog\themes\LoveIt\static 中即可

[hugo](https://www.bahuangshanren.tech/hugo-loveit优化记/)

