# Guia de Introdução ao Projeto Laravel

Este guia tem como objetivo ajudar novos participantes a configurar e rodar o projeto Wegia desenvolvido com o Laravel em seus computadores. Siga as instruções abaixo para garantir que o ambiente de desenvolvimento esteja corretamente configurado.

[Vídeo com o passo a passos](https://youtu.be/sCqkYScIWI8)

## 1. Configurações Necessárias 
**Não é necessário para quem usar as maquinas virtuais**

Antes de começar, é necessário ter algumas ferramentas instaladas. Confira as versões mínimas recomendadas:

- **PHP** (versão 8.1 ou superior)
  - Laravel requer PHP 8.1 ou superior. Instale o PHP via [site oficial](https://www.php.net/downloads) ou por um gerenciador de pacotes.
  
- **Composer** (gerenciador de dependências para PHP)
  - Composer é usado para gerenciar as dependências do Laravel. Baixe e instale via [site oficial](https://getcomposer.org/).

- **MySQL** (banco de dados)
  - Laravel utiliza MySQL como padrão. Certifique-se de que o MySQL esteja configurado e rodando.

- **Git** (versão 2.x ou superior)
  - Para clonar o projeto do GitHub. Baixe e instale via [site oficial](https://git-scm.com/downloads).

- **Node.js** (versão 16.x ou superior)
  - Laravel utiliza Node.js para compilar assets (JavaScript e CSS). Instale via [site oficial](https://nodejs.org/en/).

## 2. Clonando o Projeto

1. **Clonar o Repositório**
   - Abra o terminal e execute o comando abaixo para clonar o projeto:
     ```bash
     git clone https://github.com/wegia/wegia2.git
     ```
   - Entre no diretório do projeto:
     ```bash
     cd wegia2
     ```

2. **Instalar Dependências PHP**
   - Instale as dependências PHP com o Composer:
     ```bash
     composer install
     ```

3. **Instalar Dependências JavaScript**
   - Instale as dependências front-end com o npm:
     ```bash
     npm install
     ```

4. **Configurar o Arquivo `.env`**
   - Copie o arquivo de exemplo `.env.example` para `.env`:
     ```bash
     cp .env.example .env
     ```
   - Edite o arquivo `.env` para ajustar as configurações do banco de dados, especialmente as variáveis:
     - `DB_CONNECTION`, `DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`.

5. **Gerar a Chave da Aplicação**
   - Gere a chave do Laravel:
     ```bash
     php artisan key:generate
     ```

6. **Configurar o Banco de Dados**
   - Certifique-se de que o MySQL esteja rodando e crie o banco de dados que será utilizado pelo projeto.
   - Rode as migrações para criar as tabelas:
     ```bash
     php artisan migrate
     ```

   - Depois rode o seguinte comando para popular as tabelas
     ```bash
     php artisan db:seed
     ```

7. **Rodar o Servidor de Desenvolvimento**
   - Inicie o servidor local do Laravel:
     ```bash
     php artisan serve
     ```
   - O servidor estará acessível em http://localhost:8000


