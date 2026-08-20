# Política de Segurança

## Versões suportadas

| Versão | Suportada          |
| ------ | ------------------ |
| 1.0.x  | :white_check_mark: |

## Modelo de segurança

O SQL Formatter é uma aplicação **100% client-side**:

- Todo o processamento ocorre no navegador do usuário
- Nenhum dado JSON é enviado para servidores externos
- O Monaco Editor é carregado localmente (`min/vs/`)
- Preferências são armazenadas apenas em `localStorage` do navegador

Isso significa que o risco principal está no **código executado localmente** e em como o usuário interage com a ferramenta.

## Reportar uma vulnerabilidade

Se você encontrou uma vulnerabilidade de segurança, **não abra uma issue pública**.

Envie um reporte privado para:

- **GitHub:** [Abrir security advisory](https://github.com/jsballarini/json-formatter/security/advisories/new) (quando o repositório estiver publicado)
- **E-mail:** Contato disponível no [perfil GitHub](https://github.com/jsballarini)

### O que incluir no reporte

1. Descrição da vulnerabilidade
2. Passos para reproduzir
3. Impacto potencial
4. Sugestão de correção (se houver)
5. Navegador e versão utilizados

### O que esperar

- **Confirmação** em até 5 dias úteis
- **Avaliação** da gravidade e impacto
- **Correção** priorizada para vulnerabilidades confirmadas
- **Crédito** ao reportador (se desejado) após a correção

## Escopo

### Dentro do escopo

- Execução de código arbitrário via processamento de JSON
- XSS através de manipulação do DOM
- Vazamento de dados via `localStorage`
- Bypass de validação de arquivos no upload
- Problemas no Web Worker inline (Blob)

### Fora do escopo

- Ataques que exigem acesso físico ao computador do usuário
- Problemas em navegadores não suportados (versões muito antigas)
- Engenharia social
- Vulnerabilidades no Monaco Editor upstream (reportar diretamente ao [microsoft/monaco-editor](https://github.com/microsoft/monaco-editor))

## Boas práticas para usuários

- Use a ferramenta para processar JSON de fontes confiáveis
- Evite colar payloads de origem desconhecida em qualquer ferramenta
- Mantenha o navegador atualizado
- Para dados altamente sensíveis, prefira servir a aplicação em ambiente controlado

## Licença de dependências

O Monaco Editor é licenciado sob a [MIT License](https://github.com/microsoft/monaco-editor/blob/main/LICENSE.md) pela Microsoft Corporation. Consulte `min/vs/` para os arquivos distribuídos localmente.
