# Estrutura de um projeto Laravel

### 1. Estrutura de Diretórios Principais

- **`app/`**: Contém o código principal da aplicação, incluindo Models, Controllers, e outros serviços.
- **`resources/`**: Armazena as Views (usando Blade), arquivos de linguagem, e ativos front-end como CSS e JavaScript.
- **`routes/`**: Define todas as rotas da aplicação, divididas em arquivos como `web.php` para rotas web e `api.php` para APIs.
- **`database/`**: Inclui migrações, factories e seeders para gerenciar o banco de dados.
- **`config/`**: Configurações diversas da aplicação.

### 2. Models e Eloquent ORM

- **Models**: Representam as tabelas do banco de dados e são responsáveis pela interação com os dados. Cada model geralmente corresponde a uma tabela específica.
  
  ```php
  namespace App\Models;

  use Illuminate\Database\Eloquent\Model;

  class Produto extends Model
  {
      protected $fillable = ['nome', 'preco', 'descricao'];
  }
  ```

- **Eloquent ORM**: É o Object-Relational Mapper do Laravel que facilita operações de banco de dados, permitindo interações intuitivas como criar, ler, atualizar e deletar registros sem escrever SQL diretamente.

  ```php
  // Recuperar todos os produtos
  $produtos = Produto::all();

  // Criar um novo produto
  Produto::create(['nome' => 'Produto A', 'preco' => 100, 'descricao' => 'Descrição']);
  ```

### 3. Importância da Nomenclatura Padrão

Usar a nomenclatura padrão do Laravel segue o princípio de "convenção sobre configuração", o que reduz a necessidade de configurações adicionais e facilita a manutenção e colaboração no projeto. Por exemplo, um model chamado `Produto` automaticamente se relaciona com a tabela `produtos` no banco de dados.

### 4. Controllers

Os **Controllers** contêm a lógica de negócios da aplicação, manipulando as requisições recebidas, interagindo com os Models e retornando respostas apropriadas (como Views ou JSON).

```php
namespace App\Http\Controllers;

use App\Models\Produto;
use Illuminate\Http\Request;

class ProdutoController extends Controller
{
    public function index()
    {
        $produtos = Produto::all();
        return view('produtos.index', compact('produtos'));
    }

    public function store(Request $request)
    {
        Produto::create($request->all());
        return redirect()->route('produtos.index');
    }
}
```

### 5. Rotas

As **Rotas** definem os endpoints da aplicação e mapeiam as URLs para os métodos dos Controllers.

```php
// routes/web.php

use App\Http\Controllers\ProdutoController;

Route::get('/produtos', [ProdutoController::class, 'index'])->name('produtos.index');
Route::post('/produtos', [ProdutoController::class, 'store'])->name('produtos.store');
```

### 6. Views e Blade Template Engine

As **Views** são responsáveis pela camada de apresentação da aplicação. O Laravel utiliza o **Blade**, um motor de templates poderoso e flexível que permite criar layouts reutilizáveis e incorporar lógica PHP de forma simplificada.

```blade
<!-- resources/views/produtos/index.blade.php -->

@extends('layouts.app')

@section('content')
    <h1>Lista de Produtos</h1>
    <ul>
        @foreach($produtos as $produto)
            <li>{{ $produto->nome }} - R$ {{ $produto->preco }}</li>
        @endforeach
    </ul>
@endsection
```

### 7. Fluxo de Funcionamento de um Projeto Laravel

1. **Requisição HTTP**: O usuário faz uma requisição para uma URL específica.
2. **Roteamento**: O Laravel verifica o arquivo de rotas (`routes/web.php` ou `routes/api.php`) para determinar qual Controller e método devem tratar a requisição.
3. **Controller**: O método do Controller correspondente é executado. Ele pode interagir com Models para acessar ou manipular dados.
4. **Eloquent ORM**: O Model utiliza o Eloquent para interagir com o banco de dados, realizando operações como consultas ou inserções.
5. **View**: Após processar os dados, o Controller retorna uma View Blade, passando os dados necessários para a apresentação.
6. **Resposta ao Usuário**: A View é renderizada e enviada de volta ao navegador do usuário como uma resposta HTML.

### 8. Vantagens de Seguir a Estrutura e Convenções do Laravel

- **Organização**: Facilita a manutenção e escalabilidade do projeto.
- **Produtividade**: Convenções padrão reduzem o tempo gasto em configurações e aumentam a eficiência no desenvolvimento.
- **Comunidade e Suporte**: Seguir as práticas comuns facilita o trabalho em equipe e o aproveitamento de recursos e pacotes da comunidade Laravel.
