# Guia de Contribuição

Obrigado por considerar contribuir com o **SQL Formatter**! Este documento descreve como participar do projeto.

## Índice

- [Código de conduta](#código-de-conduta)
- [Como posso contribuir?](#como-posso-contribuir)
- [Reportar bugs](#reportar-bugs)
- [Sugerir melhorias](#sugerir-melhorias)
- [Pull requests](#pull-requests)
- [Padrões de código](#padrões-de-código)
- [Commits](#commits)
- [Testes manuais](#testes-manuais)

---

## Código de conduta

Seja respeitoso e construtivo. Discussões técnicas são bem-vindas; ataques pessoais não são tolerados.

---

## Como posso contribuir?

Existem várias formas de ajudar, mesmo sem escrever código:

- ⭐ Dar uma **estrela** no repositório
- 🐛 Reportar **bugs** com passos para reproduzir
- 💡 Sugerir **melhorias** ou novas funcionalidades
- 📖 Melhorar a **documentação**
- 🔧 Enviar **pull requests** com correções ou features
- 📢 Compartilhar o projeto com colegas que trabalham com APIs

---

## Reportar bugs

Antes de abrir uma issue, verifique se já não existe uma issue similar.

### Informações necessárias

1. **Descrição clara** do problema
2. **Passos para reproduzir**
3. **Comportamento esperado** vs **comportamento atual**
4. **Navegador e versão** (ex.: Chrome 120, Firefox 121)
5. **Sistema operacional** (ex.: Windows 11, macOS 14)
6. **SQL de exemplo** (sem dados sensíveis) que reproduz o problema
7. **Screenshot** (se aplicável)

### Template sugerido

```markdown
## Descrição
[Descreva o bug]

## Passos para reproduzir
1. Abra index.html
2. Cole o SQL abaixo
3. Clique em "Validar"
4. Observe o erro

## Comportamento esperado
[O que deveria acontecer]

## Comportamento atual
[O que acontece]

## Ambiente
- Navegador: Chrome 120
- SO: Windows 11
- Versão: 1.0.0

## SQL de exemplo
```json
{ "exemplo": true }
```
```

---

## Sugerir melhorias

Abra uma issue com a tag `enhancement` descrevendo:

- **Problema** que a melhoria resolve
- **Solução proposta**
- **Alternativas** consideradas
- **Impacto** na experiência do usuário

---

## Pull requests

### Fluxo

1. Faça um **fork** do repositório
2. Crie uma **branch** a partir de `main`:
   ```bash
   git checkout -b feat/minha-melhoria
   ```
3. Implemente a mudança seguindo os [padrões de código](#padrões-de-código)
4. Teste manualmente (veja [testes manuais](#testes-manuais))
5. Atualize `CHANGELOG.md` na seção `[Não publicado]`
6. Abra o **pull request** com descrição clara

### Checklist do PR

- [ ] Código segue os padrões do projeto
- [ ] Funcionalidade testada manualmente no navegador
- [ ] `CHANGELOG.md` atualizado
- [ ] Sem regressões em funcionalidades existentes
- [ ] Sem dados sensíveis ou credenciais no código
- [ ] Descrição do PR explica o **porquê** da mudança

---

## Padrões de código

O projeto é um **arquivo único** (`index.html`). Mantenha essa filosofia:

### Estrutura

- HTML, CSS e JavaScript dentro de `index.html`
- JavaScript organizado em módulos lógicos (objetos/IIFEs)
- Constantes centralizadas em `CONSTANTS`
- Funções pequenas, coesas e reutilizáveis
- Evitar variáveis globais desnecessárias

### Estilo

- JavaScript moderno (ES6+)
- `const` e `let` em vez de `var`
- Nomes claros e descritivos em inglês para código, português para UI
- Comentários apenas onde a lógica não é óbvia
- Sem `eval`
- Sem `innerHTML` com conteúdo SQL — usar `textContent` ou APIs seguras
- Sem frameworks (React, Vue, Angular, Svelte)
- Sem arquivos CSS ou JS externos (exceto Monaco em `min/vs/`)

### Princípios

- **Minimize o escopo** — mudanças focadas, sem refatorações desnecessárias
- **Reutilize** funções existentes antes de criar novas
- **Trate erros** com mensagens amigáveis ao usuário
- **Acessibilidade** — ARIA, foco visível, suporte a teclado

---

## Commits

Utilize [Conventional Commits](https://www.conventionalcommits.org/):

| Tipo | Uso |
|---|---|
| `feat` | Nova funcionalidade |
| `fix` | Correção de bug |
| `docs` | Documentação |
| `style` | Formatação (sem mudança de lógica) |
| `refactor` | Refatoração sem mudança de comportamento |
| `perf` | Melhoria de performance |
| `test` | Testes |
| `chore` | Tarefas de manutenção |

### Exemplos

```
feat: add support for SQL5 trailing commas
fix: preserve escaped quotes in comment stripper
docs: update keyboard shortcuts table in README
refactor: extract statusBar update into single function
```

---

## Testes manuais

Antes de enviar um PR, valide no navegador:

### Casos obrigatórios

1. **Formatar** SQL compacto:
   ```json
   {"nome":"Juliano","ativo":true,"tecnologias":["C#","Node.js"]}
   ```

2. **Validar** SQL com vírgula trailing (deve falhar):
   ```json
   {
     "nome": "Juliano",
     "tecnologias": [
       "C#",
       "Node.js",
     ]
   }
   ```

3. **Remover comentários** preservando URLs:
   ```json
   {
     "url": "https://api.exemplo.com/v1",
     "texto": "Não remover // deste texto"
   }
   ```

4. **Ordenar propriedades** em objeto aninhado

5. **Upload** de arquivo `.json` válido

6. **Download** do resultado formatado

7. **Tema** claro e escuro

8. **Configurações** persistem após recarregar a página

9. **Atalhos** de teclado funcionam

10. **Limpar** com e sem conteúdo nos editores

### Casos adicionais (se aplicável)

- SQL grande (> 256 KB) com Web Worker
- Auto-formatação com debounce
- Raiz primitiva (`"hello"`, `42`, `true`, `null`)
- Abrir via `file://` e via servidor local

---

## Dúvidas?

Abra uma issue com a tag `question` ou entre em contato pelo [GitHub](https://github.com/jsballarini).

Obrigado por contribuir! 🚀
