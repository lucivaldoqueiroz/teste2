<!-- Código para a páginação -->

<!DOCTYPE html>
<html>

<head>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/5.0.0-alpha1/css/bootstrap.min.css">
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/5.0.0-alpha1/js/bootstrap.bundle.min.js"></script>
</head>

<body>
  <div class="pagination-container d-flex flex-row align-items-center">
    <span class="mr-2">Itens por página:</span>
    <div class="dropdown">
      <button class="btn btn-primary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown"
        aria-haspopup="true" aria-expanded="false">
        10
      </button>
      <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
        <a class="dropdown-item" href="#">10</a>
        <a class="dropdown-item" href="#">20</a>
        <a class="dropdown-item" href="#">30</a>
        <!-- Adicione outras opções de quantidade de itens por página aqui -->
      </div>
    </div>
    <span class="mx-2">|</span>
    <span class="mr-2">1-10 de x itens</span>
    <span class="mx-2">|</span>
    <button class="btn btn-primary mr-2">
      <
    </button>
    <button class="btn btn-primary">
      >
    </button>
  </div>

  <div class="content-container">
    {{ $itemsPerPage := 10 }}
    {{ $currentPage := .Paginator.PageNumber }}
    {{ $start := multiply (subtract $currentPage 1) $itemsPerPage }}
    {{ $end := add $start $itemsPerPage }}
    {{ $data := .Site.Data.conteudo }}
    {{ range $index, $item := $data }}
    {{ if and (ge $index $start) (lt $index $end) }}
    <div class="item">
      <h2>{{ $item.title }}</h2>
      <p>{{ $item.content }}</p>
    </div>
    {{ end }}
    {{ end }}
  </div>
</body>

</html>

<!-- Código para a páginação -->
