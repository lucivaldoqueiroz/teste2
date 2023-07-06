## Meu conteúdo

Aqui está o conteúdo da minha página.

{{ range .Paginator.Pages }}
  {{ range .Data.items }}
    - {{ .nome }}
  {{ end }}
{{ end }}

{{ partial "pagination.html" . }}

Passo 3 

{{ $paginator := .Paginator }}
{{ $currentPage := .Paginator.PageNumber }}
{{ $totalPages := .Paginator.TotalPages }}

<div class="pagination-container d-flex flex-row align-items-center">
  <span class="mr-2">Itens por página:</span>
  <div class="dropdown">
    <button class="btn btn-primary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown"
      aria-haspopup="true" aria-expanded="false">
      {{ $paginator.PageSize }}
    </button>
    <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
      {{ range .Site.Params.paginationOptions }}
        <a class="dropdown-item" href="{{ $paginator.PermalinkWithPageSize . }}">{{ . }}</a>
      {{ end }}
    </div>
  </div>
  <span class="mx-2">|</span>
  <span class="mr-2">{{ $paginator.FirstItemIndex }}-{{ $paginator.LastItemIndex }} de {{ $paginator.TotalCount }} itens</span>
  <span class="mx-2">|</span>
  {{ if gt $currentPage 1 }}
    <a href="{{ $paginator.Prev.URL }}" class="btn btn-primary mr-2">&lt;</a>
  {{ end }}
  {{ if lt $currentPage $totalPages }}
    <a href="{{ $paginator.Next.URL }}" class="btn btn-primary">&gt;</a>
  {{ end }}
</div>
Personalize o estilo e a aparência do HTML e do CSS de acordo com suas necessidades.
Ao executar o Hugo para gerar o site, a página personalizada mypage.md será processada e a paginação será gerada automaticamente com base nos parâmetros definidos. O conteúdo da página será exibido de acordo com a quantidade de itens por página, e os botões de página anterior e próxima permitirão navegar pelos itens paginados.






