[params]
  paginate = {{ .Site.Params.itemsPerPage }}

  {{- $itemsPerPage := .Site.Params.itemsPerPage -}}
{{- $currentPage := .Paginator.PageNumber -}}
{{- $start := multiply (subtract $currentPage 1) $itemsPerPage -}}
{{- $end := add $start $itemsPerPage -}}
{{- $totalItems := len .Data.rankings -}}

<head>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/5.0.0-alpha1/css/bootstrap.min.css">
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/5.0.0-alpha1/js/bootstrap.bundle.min.js"></script>
</head>

<body>
  {{ range $ranking := .Paginator.Pages }}
  <h1>{{ $ranking.Params.titulo }}</h1>
  <h1>{{ $ranking.Params.canal }}</h1>
  {{ end }}

  <div class="pagination-container d-flex flex-row align-items-center">
    <span class="mr-2">Itens por página:</span>
    <div class="dropdown">
      <button class="btn btn-primary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown"
        aria-haspopup="true" aria-expanded="false">
        {{ $itemsPerPage }}
      </button>
      <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
        <a class="dropdown-item" href="{{ .Permalink }}">{{ $itemsPerPage }}</a>
        <a class="dropdown-item" href="{{ .Permalink }}?itemsPerPage=20">20</a>
        <a class="dropdown-item" href="{{ .Permalink }}?itemsPerPage=30">30</a>
        <!-- Add other options for items per page here -->
      </div>
    </div>
    <span class="mx-2">|</span>
    <span class="mr-2">{{ $start }}-{{ $end }} of {{ $totalItems }} items</span>
    <span class="mx-2">|</span>
    {{ if gt $currentPage 1 }}
    <a class="btn btn-primary mr-2" href="{{ .Paginator.Prev.URL }}">Previous</a>
    {{ end }}
    {{ if lt $currentPage .Paginator.TotalPages }}
    <a class="btn btn-primary" href="{{ .Paginator.Next.URL }}">Next</a>
    {{ end }}
  </div>
</body>
