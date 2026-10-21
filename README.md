# Trabalho-front-end — ServiceTech

Repositório do projeto acadêmico **ServiceTech**, um sistema web para assistência técnica especializada na manutenção e reparo de notebooks, celulares, computadores e outros dispositivos eletrônicos.

---

## Sobre o Projeto ServiceTech

O **ServiceTech** foi desenvolvido em equipe como projeto acadêmico de Desenvolvimento Front-End, com o objetivo de oferecer uma interface limpa, intuitiva e padronizada para o gerenciamento de chamados técnicos. O sistema adota uma identidade visual unificada em tons de roxo (`#543295` e `#3d296a`) e amarelo (`#f4c24c`).

---

## Página de Acompanhamento de Atendimentos

### Objetivo da Página
A página **Acompanhamento de Atendimentos** atua como o painel de controle operacional do sistema, permitindo visualizar todos os clientes que abriram solicitações de assistência técnica, identificar o aparelho e o serviço requerido, filtrar chamados por situação e pesquisar clientes pelo nome.

### Tecnologias Utilizadas
Na implementação atual, a página utiliza:
- **HTML5:** Estruturação semântica do layout (cabeçalho, barra lateral, controles de filtro e tabela de dados) e ícones vetoriais em SVG.
- **CSS3:** Estilização visual alinhada à identidade do projeto, layout com Flexbox, filtragem por status via seletor `:checked` e adaptação responsiva (`@media`).
- **JavaScript (ES6+ nativo):** Carregamento assíncrono dos registros com `fetch()` e filtragem em tempo real pelo nome do cliente na barra de pesquisa.
- **JSON:** Armazenamento estruturado dos dados mockados de atendimento (`atendimentos.json`).

---

## Estrutura do projeto

## Principais Áreas da Interface

1. **Cabeçalho Superior (`.cabecalho`):**
   Barra superior na cor roxa principal (`#543295`), composta pelo ícone de perfil do usuário à esquerda, o logotipo oficial `ServiceTech` centralizado e os botões de busca e notificações à direita.
2. **Barra Lateral de Navegação (`.barra-lateral`):**
   Menu vertical compacto à esquerda contendo 6 atalhos de navegação em SVG (Início, Novo Atendimento, Atendimentos, Pesquisar, Relatórios e Configurações), com destaque visual no item ativo.
3. **Cabeçalho da Seção (`.topo-secao`):**
   Apresenta o ícone circular de assistência técnica (chave inglesa sobre fundo lilás `#ebe2fe`) ao lado do título **"Acompanhamento de Atendimentos"**.
4. **Barra de Controles — Filtros e Pesquisa (`.barra-controles`):**
   Agrupa os 5 botões de filtro por status à esquerda e o campo de pesquisa pelo nome do cliente à direita.
5. **Tabela de Atendimentos (`.tabela`):**
   Tabela com cabeçalho destacado (`#f2edfc`) e corpo (`<tbody id="lista-atendimentos">`) alimentado dinamicamente a partir do arquivo `atendimentos.json`.

---

## Funcionalidades Implementadas

### 1. Carregamento de Dados via JSON (`atendimentos.json`)
Os registros de atendimento ficam separados do código HTML dentro do arquivo `pagina6/atendimentos.json`. Ao abrir a página, um script utiliza `fetch('atendimentos.json')` para ler os objetos JSON e gerar automaticamente as linhas (`<tr>`) dentro do `<tbody id="lista-atendimentos">`.

Exemplo de estrutura de um registro em `atendimentos.json`:
```json
{
  "id": "#001",
  "cliente": "Mariana",
  "aparelho": "Notebook Dell",
  "servico": "Diagnóstico",
  "status": "Recebido",
  "classe": "recebido",
  "data": "21/09/2026"
}
```

### 2. Filtro por Status (HTML + CSS)
Acima da tabela, os botões **Todos**, **Recebido**, **Em análise**, **Em manutenção** e **Pronto** filtram instantaneamente os chamados exibidos. Essa funcionalidade utiliza botões de rádio ocultos (`<input type="radio" name="filtro">`) combinados com os seletores `:checked` e `:not()` no CSS:
- Quando um status é selecionado, o botão correspondente recebe destaque roxo (`#543295`) e as linhas da tabela que não pertencem àquela classe (`tr:not(.item-...)`) são ocultadas.

### 3. Pesquisa Dinâmica pelo Nome do Cliente
O campo `<input type="search" class="pesquisa">` filtra as linhas da tabela em tempo real à medida que o usuário digita, comparando o texto digitado com a segunda coluna da tabela (**Cliente**).

### 4. Colunas da Tabela e Identificação Visual de Status
A tabela exibe 7 colunas padronizadas:

| Coluna | Descrição | Exemplo |
| :--- | :--- | :--- |
| **1. ID** | Identificador único do chamado técnico. | `#001`, `#002`, `#003` |
| **2. Cliente** | Nome do cliente que abriu a solicitação. | Mariana, Ana, Gabriel |
| **3. Aparelho** | Equipamento entregue para assistência. | Notebook Dell, Galaxy A52, MacBook Air |
| **4. Serviço** | Tipo de serviço solicitado. | Diagnóstico, Troca de tela, Formatação, Limpeza, Upgrade |
| **5. Status** | Situação atual do atendimento destacada pela cor da fonte. | `Recebido`, `Em análise`, `Em manutenção`, `Pronto` |
| **6. Data de criação** | Data em que o chamado foi registrado. | `21/09/2026`, `22/09/2026`, `23/09/2026` |
| **7. Ações** | Espaço reservado para ações sobre o chamado. | `Editar \| ...` |

Os quatro status são diferenciados de forma limpa e direta pela cor do texto em negrito:
- **Recebido (`.recebido`):** Amarelo (`#f4c24c`)
- **Em análise (`.analise`):** Roxo (`#543295`)
- **Em manutenção (`.manutencao`):** Laranja (`#fe7f28`)
- **Pronto (`.pronto`):** Verde (`#12bc59`)

---

## Dados Fictícios e Funcionalidades Pendentes

- **Dados de demonstração (Mock):** Os 9 atendimentos presentes em `pagina6/atendimentos.json` são dados fictícios criados para demonstrar o funcionamento da interface.
- **Integração futura com fonte definitiva:** A arquitetura já está preparada para substituir o caminho `'atendimentos.json'` no `fetch()` pelo endereço de uma futura API ou backend quando a origem definitiva dos dados for definida pela equipe.
- **Funcionalidades ainda apenas visuais:**
  - Controles da coluna **Ações** (`Editar | ...`), que aguardam definição das telas/modais de edição de chamado.
  - Botões de busca global e notificações no cabeçalho superior.
  - Links da barra lateral referentes às telas que ainda serão integradas pelas demais branches do grupo.

---

## Relação com a Página Inicial do Projeto

Esta página integra-se diretamente com a **Página Inicial** desenvolvida na branch `LiviaFreixo-pagina-inicial` (`pagina_inicial/index.html` e `pagina_inicial/style.css`):
- Reaproveita a tipografia (`Arial, sans-serif`), a paleta de cores oficial e o logotipo `logo.jpg`.
- Conecta-se ao fluxo de navegação principal do site (botões *"Acompanhe seu atendimento"* e menu *"Meus Atendimentos"* da página inicial).

---

## Como Executar e Visualizar Localmente

Como a página carrega os dados de um arquivo externo (`atendimentos.json`) via `fetch()`, é necessário abri-la por meio de um servidor local HTTP (os navegadores bloqueiam requisições `fetch` quando o arquivo é aberto diretamente via protocolo `file://`).

### Opção 1 — Usando a extensão Live Server no VS Code (Recomendado)
1. Abra a pasta do projeto no **Visual Studio Code**.
2. Clique com o botão direito sobre o arquivo `pagina6/pagina6.html` (ou `index.html`).
3. Selecione **"Open with Live Server"**.

### Opção 2 — Usando Python no terminal
Na pasta raiz do projeto, execute:
```bash
python -m http.server 5500
```
Em seguida, acesse no navegador: `http://localhost:5500/pagina6/pagina6.html`

---

## Próximas Etapas de Desenvolvimento

1. Unificar (*merge*) as branches de todas as telas do sistema na branch `main` e atualizar os links definitivos da barra lateral.
2. Implementar as ações de edição e alteração de status na coluna **Ações**.
3. Conectar o `fetch()` à fonte definitiva de dados (API ou banco de dados) quando definida pelo grupo.