# Notes

Answer scratch: 

Maybe a bit of grouping could work like you want it to? Say, 
`/config.yaml`
```yaml
taxonomies:
    tag: "tags" # This is the default anyway
```
`/content/posts/mypost.md`
```yaml
---
tags: ["Rock"]
subtags: ["Metal"] # Not a taxonomy, just a param
---
```
`/layouts/tags/list.html`
```html
<ol>
    {{ range .Pages }}
    <li> {{ .Title }}
        <ol> 
            {{ range .Pages.GroupByParam "subtag" }}
                <li>{{.Key}}
                    <ol>
                        {{ range .Pages }}
                        <li><a href="{{.Permalink}}">😎{{.Title}}</a></li>
                        {{ end }}
                    </ol>
                    </li>
            {{ end }}
        </ol>
    </li>
    {{ end }}
</ol>
```