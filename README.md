{{ $paginator := .Paginate (where .Site.Data.jsonData "featured" true) }}
{{ $paginatedPages := $paginator.Pagers }}

<nav>
    <ul class="pagination">
        {{ if gt $paginator.TotalPages 1 }}
            {{ if $paginator.HasPrev }}
                <li class="page-item">
                    <a class="page-link" href="{{ $paginatedPages.Prev.URL }}">Anterior</a>
                </li>
            {{ end }}
            {{ range $paginatedPages.Pages }}
                <li class="page-item{{ if eq $paginator.PageNumber .Paginator.PageNumber }} active{{ end }}">
                    <a class="page-link" href="{{ .URL }}">{{ .Paginator.PageNumber }}</a>
                </li>
            {{ end }}
            {{ if $paginator.HasNext }}
                <li class="page-item">
                    <a class="page-link" href="{{ $paginatedPages.Next.URL }}">Próxima</a>
                </li>
            {{ end }}
        {{ end }}
    </ul>
</nav>
