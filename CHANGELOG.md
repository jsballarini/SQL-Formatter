# Changelog

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/),
e este projeto adere ao [Semantic Versioning](https://semver.org/lang/pt-BR/).

## [1.0.4] - 2026-08-20

### Adicionado

- Destaque da linha inteira ao posicionar o cursor sobre uma keyword SQL (entrada e resultado), similar ao realce de parênteses/colchetes

## [1.0.3] - 2026-08-20

### Corrigido

- Cláusulas `JOIN` passam a colocar `ON` em linha separada, com `AND` de condição alinhado abaixo do `ON`

## [1.0.2] - 2026-08-20

### Corrigido

- Indentação procedural T-SQL restaurada após formatação (`BEGIN`/`END`, `IF`/`ELSE`, `WHILE`)
- Corpo de `IF` sem `BEGIN` (ex.: `DROP TABLE` após `IF OBJECT_ID`) volta a ser indentado
- Linhas procedurais fundidas pelo formatador (`END CLOSE`, `WHILE ... BEGIN`, `SET` quebrado) são separadas e reindentadas

## [1.0.1] - 2026-08-20

### Corrigido

- Linhas em branco extras entre `DECLARE` consecutivos (`linesBetweenQueries` ajustado para `0`)
- Cabeçalho de `CREATE OR ALTER PROCEDURE` preservado ao formatar T-SQL (proteção com `sql-formatter-disable`)
- `SET NOCOUNT ON` deixando de ser quebrado em duas linhas após formatação
- Colapso de linhas em branco excessivas (3+ consecutivas) no pós-processamento

## [1.0.0] - 2026-08-20

### Adicionado

#### Aplicação principal

- Aplicação web completa em arquivo único `index.html` (HTML, CSS e JavaScript)
- Interface inspirada no Visual Studio Code com tema claro e escuro
- Dois painéis redimensionáveis com Monaco Editor (entrada e resultado)
- Barra de ferramentas: Formatar, Compactar, Validar, Copiar, Keywords maiúsculas, Remover comentários, Exemplo e Limpar
- Barra de status com validade, linhas, caracteres, tamanho, tempo de operação, posição de erro e modo do resultado
- Painel de configurações com persistência em `localStorage`
- Integração i18n (pt, en, es) via landing Juliano Ballarini

#### Editor (Monaco)

- Monaco Editor 0.45.0 com syntax highlight SQL/PostgreSQL
- Numeração de linhas, folding, bracket pair colorization e guias de indentação
- Busca (`Ctrl+F`), substituição (`Ctrl+H`) nativas do Monaco
- Minimap e word wrap configuráveis
- Painel de resultado somente leitura com opção de habilitar edição

#### Operações SQL

- Formatação via [sql-formatter](https://github.com/sql-formatter-org/sql-formatter) 15.8.2
- Suporte a dialetos: SQL, PostgreSQL, MySQL, MariaDB, SQLite, Transact-SQL, PL/SQL, Snowflake, BigQuery, Spark, Trino, Redshift
- Compactação para linha única
- Validação sintática com mensagens amigáveis e destaque de linha/coluna
- Keywords em maiúsculas, minúsculas ou preservadas
- Remoção de comentários `--` e `/* */` respeitando strings SQL

#### Arquivos

- Upload de `.sql` por clique ou drag-and-drop
- Download do resultado como `formatted-sql.sql`
- Validação de extensão, tipo MIME e tamanho (limite 5 MB)

#### Performance

- Formatação automática com debounce (500 ms)
- Limite configurável para auto-formatação (padrão 512 KB)
- Web Worker com importScripts para arquivos grandes (> 256 KB)

#### UX e acessibilidade

- Notificações toast, modal de confirmação e atalhos (`F1`)
- Layout responsivo, ARIA e foco visível
- Seção SEO traduzível para landing page

#### Distribuição offline

- Monaco Editor e sql-formatter incluídos localmente em `min/`
- Funcionamento sem dependência de CDN em runtime

#### Créditos

- Desenvolvido por Juliano Ballarini
- Licença MIT
