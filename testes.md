# Testes no Laravel
Os testes são uma prática essencial para garantir que uma aplicação funcione como esperado e para prevenir que mudanças no código introduzam erros. Em aplicações Laravel, os testes ajudam 
a verificar se cada componente do sistema, seja no backend ou frontend, está cumprindo seu papel corretamente. Eles aumentam a confiabilidade e a qualidade do software, proporcionando 
segurança para realizar atualizações e melhorias no código.

## Desenvolvimento Baseado em Testes (Test-Driven Development - TDD)
No desenvolvimento baseado em testes (TDD), os testes são escritos antes do código funcional. O ciclo do TDD inclui três etapas principais:

- **Escrever um Teste que Falhe**: Antes de implementar uma funcionalidade, o desenvolvedor cria um teste que define o comportamento esperado da função. Esse teste falha inicialmente, pois a 
funcionalidade ainda não foi implementada.
- **Escrever o Código para Passar no Teste**: O próximo passo é escrever o código mínimo necessário para que o teste passe.
- **Refatorar e Repetir**: Depois que o teste passa, o código pode ser otimizado ou refatorado, sempre garantindo que os testes continuam passando.
Essa abordagem ajuda a desenvolver um código mais limpo, testável e modular, e com alta cobertura de testes.

## Tipos de Testes no Laravel
Laravel oferece suporte a diferentes tipos de testes, cada um focando em aspectos específicos da aplicação:

- **Testes Unitários**: Avaliam partes isoladas do código, como funções e métodos específicos. Esses testes ajudam a verificar a lógica interna de classes e métodos, garantindo que cada
unidade funcione corretamente.

- **Testes de Integração**: Verificam se vários componentes do sistema funcionam bem juntos. No Laravel, testes de integração podem incluir interações entre modelos, controladores, e o
banco de dados, garantindo que os dados fluam corretamente entre eles.

- **Testes de Interface (Browser Testing)**: Laravel Dusk permite realizar testes no navegador, simulando interações de usuário, como preenchimento de formulários e navegação. Eles
verificam se o front-end da aplicação está funcionando conforme o esperado.

- **Testes de Requisição (Feature Tests)**: Avaliam funcionalidades completas da aplicação, simulando requisições HTTP. São úteis para verificar endpoints, lógica de autenticação e
regras de acesso.

## Principais Funções de Teste no Laravel e Suas Funções
Aqui estão algumas das principais funções e métodos usados em testes no Laravel e Dusk, com uma breve explicação de cada uma:

### Em Testes Unitários e de Integração
`assertEquals($expected, $actual)`: Verifica se dois valores são iguais. Útil para comparar resultados específicos.

`assertNotNull($value)`: Verifica se o valor não é null, útil para garantir que valores estão sendo salvos ou retornados corretamente.

`assertDatabaseHas($table, $data)`: Verifica se uma tabela no banco de dados contém o registro específico com os valores fornecidos. Esse método é útil para confirmar que uma operação de criação ou atualização foi bem-sucedida.

`assertDatabaseMissing($table, $data)`: Verifica que um determinado registro não existe na tabela, usado frequentemente em testes de exclusão.

### Em Testes de Requisição (Feature Tests)
`get($uri)`: Simula uma requisição HTTP GET para uma rota específica. Verifica se a rota responde como esperado.

`post($uri, $data)`: Simula uma requisição HTTP POST com dados. Útil para testar a criação de recursos.

`assertStatus($code)`: Verifica se a resposta HTTP tem o código de status esperado, como 200 para sucesso ou 404 para não encontrado.

`assertSee($text)`: Confirma que a resposta contém o texto especificado. Ideal para verificar se a página carrega o conteúdo correto.

### Em Testes de Interface (Laravel Dusk)
`visit($url`): Navega até uma URL específica no navegador de teste. É o ponto inicial para testes de navegação.

`assertSee($text)`: Verifica se um texto específico aparece na página, confirmando que o conteúdo foi carregado.

`type($field, $value)`: Insere texto em um campo de entrada (input), útil para simular o preenchimento de formulários.

`press($buttonText)`: Simula o clique em um botão com o texto especificado.

`assertPathIs($path)`: Verifica se o navegador está na URL especificada, usado para confirmar redirecionamentos.

`pause($milliseconds)`: Faz uma pausa no teste por um determinado número de milissegundos. Útil para depuração.

`assertVisible($selector)`: Confirma que um elemento específico está visível na página, útil para verificar se elementos estão carregados.

## Referências
[Documntação do Laravel](https://laravel.com/docs/11.x/http-tests)

[Leitura recomendada sobre testes](https://kinsta.com/pt/blog/testes-unidade-laravel/)

[Exemplos sobre teste no Laravel](https://github.com/framgia/laravel-test-examples/tree/master)
