Configuração:
Certifique-se de ter configurado o parâmetro "paginate" no arquivo de configuração do seu site. Por exemplo, adicione a seguinte linha ao arquivo config.toml:

toml
Copy code
paginate = 10
Criação do arquivo content/docs/_index.md com o seguinte conteúdo:

markdown
Copy code
---
title: "Documentação"
---

{{< jsonshortcode >}}

{{ partial "pagination.html" . }}
Criação do arquivo layouts/partials/pagination.html com o seguinte conteúdo:

html
Copy code
{{ $paginator := .Paginator }}
{{ with $paginator.HasPrev }}
  <a href="{{ $paginator.Prev.URL }}">Anterior</a>
{{ end }}
{{ with $paginator.HasNext }}
  <a href="{{ $paginator.Next.URL }}">Próxima</a>
{{ end }}
Criação do arquivo layouts/shortcodes/jsonshortcode.html com o seguinte conteúdo:

html
Copy code
{{ $jsonData := readFile "data/docs.json" | parseJSON }}
{{ $currentPage := .PageNumber }}
{{ $pageSize := .Site.Params.paginate }}
{{ $start := mul $currentPage $pageSize }}
{{ $end := add $start $pageSize }}
{{ $data := slice $jsonData $start $end }}
{{ range $data }}
  <h2>{{ .title }}</h2>
  <p>{{ .summary }}</p>
{{ end }}
Criação do arquivo data/docs.json com o seguinte conteúdo:

json
Copy code
[
  {
    "title": "Título da Página 1",
    "summary": "Resumo da Página 1"
  },
  {
    "title": "Título da Página 2",
    "summary": "Resumo da Página 2"
  },
  {
    "title": "Título da Página 3",
    "summary": "Resumo da Página 3"
  },
  ...
]
