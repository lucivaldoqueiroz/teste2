<div class="table-responsive">
  <table class="table">
    <thead>
      <tr>
        <th>Header 1</th>
        <th>Header 2</th>
        <th>Header 3</th>
        <th>Header 4</th>
        <th>Header 5</th>
        <th>
          <button class="btn btn-link" data-toggle="collapse" data-target="#tableCollapse" aria-expanded="false" aria-controls="tableCollapse">
            <i class="fa fa-chevron-down"></i>
          </button>
        </th>
      </tr>
    </thead>
    <tbody id="tableCollapse" class="collapse">
      <tr>
        <td>Item 1</td>
        <td>Item 2</td>
        <td>Item 3</td>
        <td>Item 4</td>
        <td>Item 5</td>
        <td>
          <button class="btn btn-link" data-toggle="collapse" data-target="#tableCollapse" aria-expanded="true" aria-controls="tableCollapse">
            <i class="fa fa-chevron-up"></i>
          </button>
        </td>
      </tr>
      <tr>
        <td colspan="6" class="bg-primary text-center">Header 2</td>
      </tr>
      <tr>
        <td>Item 6</td>
        <td>Item 7</td>
        <td>Item 8</td>
        <td>Item 9</td>
        <td>Item 10</td>
        <td></td>
      </tr>
      <tr>
        <td>Item 11</td>
        <td>Item 12</td>
        <td>Item 13</td>
        <td>Item 14</td>
        <td>Item 15</td>
        <td></td>
      </tr>
    </tbody>
  </table>
</div>

<table class="table">
  <thead>
    <tr>
      <th>Nome</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
    {{ range .data }}
    <tr>
      <td>
        <a data-toggle="collapse" href="#collapse{{ .id }}" role="button" aria-expanded="false" aria-controls="collapse{{ .id }}">
          {{ .nome }}
        </a>
      </td>
      <td>{{ .descricao }}</td>
    </tr>
    <tr class="collapse" id="collapse{{ .id }}">
      <td colspan="2">
        <!-- Conteúdo expandido para o item -->
        Conteúdo expandido para {{ .nome }}
      </td>
    </tr>
    {{ end }}
  </tbody>
</table>
