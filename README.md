# Trabalho-front-end — ServiceTech

Repositório do projeto acadêmico **ServiceTech**, um sistema web para assistência técnica especializada no conserto e manutenção de notebooks, celulares, computadores e outros dispositivos eletrônicos.

---

## Sobre o Projeto ServiceTech

O **ServiceTech** tem como proposta oferecer uma interface clara, organizada e acessível para o gerenciamento e acompanhamento de serviços de assistência técnica. O sistema foi concebido em equipe como projeto acadêmico de Desenvolvimento Front-End, priorizando uma identidade visual consistente (em tons de roxo `#543295` / `#3d296a` e amarelo `#f4c24c`) e facilidade de navegação.

---

## Página de Acompanhamento de Atendimentos

### Objetivo da Página
A página **Acompanhamento de Atendimentos** funciona como um painel administrativo onde é possível visualizar os clientes que abriram chamados para assistência técnica, consultar o equipamento e o serviço solicitado e acompanhar a situação (status) de cada aparelho.

### Tecnologias Utilizadas
Nesta etapa do projeto, a página foi desenvolvida utilizando exclusivamente:
- **HTML5** (estruturação semântica da interface, filtros, campo de busca e tabela).
- **CSS3** (estilização visual, Flexbox, filtro funcional via seletor `:checked` e responsividade com Media Queries).

*(Nenhuma biblioteca externa, framework ou script JavaScript foi adicionado nesta etapa).*

---

## Localização e Estrutura dos Arquivos Relevantes

```text
Trabalho-dev-front-end/
├── index.html                   # Página raiz com atalho para a tela de Acompanhamento
├── README.md                    # Documentação geral do projeto (este arquivo)
└── pagina6/                     # Diretório da página de Acompanhamento de Atendimentos
    ├── pagina6.html             # Estrutura HTML principal da página de Acompanhamento
    ├── css6.css                 # Folha de estilos CSS da página de Acompanhamento
    ├── atendimentos.json        # Dados mockados dos atendimentos em formato JSON
    ├── img/
    │   └── logo.jpg             # Logotipo oficial compartilhado com a página inicial
    ├── pagina6model.html        # Modelo/esboço inicial de layout (preservado)
    ├── cssmodel.css             # Estilo do modelo inicial de layout (preservado)
    └── GUIA_DE_ESTUDO.md        # Guia detalhado de estudo e compreensão do código
```

---

## Principais Áreas da Interface

1. **Cabeçalho Superior (`.cabecalho`):**
   Apresenta a identidade visual do ServiceTech na cor roxa principal (`#543295`), contendo o ícone de perfil à esquerda, o logotipo oficial `ServiceTech` centralizado e os botões de busca e notificações à direita.
2. **Barra Lateral de Navegação (`.barra-lateral`):**
   Menu vertical compacto à esquerda com os 6 ícones de navegação.
3. **Cabeçalho da Seção (`.topo-secao`):**
   Apresenta o ícone circular de ferramenta (chave inglesa) e o título **"Acompanhamento de Atendimentos"**.
4. **Barra de Controles — Filtros e Pesquisa (`.barra-controles`):**
   Reúne os botões de filtro por status à esquerda e o campo de pesquisa pelo nome do cliente à direita.
5. **Tabela de Atendimentos (`.tabela`):**
   Lista estruturada com os chamados registrados e identificação visual por cor de texto em cada status.

---

## Funcionalidades Implementadas

### Filtros e Pesquisa
- **Filtros por Status (via HTML e CSS):** Ao clicar em **Todos**, **Recebido**, **Em análise**, **Em manutenção** ou **Pronto**, a tabela filtra automaticamente as linhas correspondentes usando `<input type="radio">` e o seletor `:checked` do CSS.
- **Barra de Pesquisa pelo Nome:** Campo `<input type="search">` que filtra os atendimentos da tabela conforme o nome do cliente digitado.

### Colunas da Tabela de Atendimentos
A tabela apresenta 7 colunas padronizadas:

| Coluna | Descrição | Exemplo |
| :--- | :--- | :--- |
| **1. ID** | Identificador único do chamado técnico. | `#001`, `#002`, `#003` |
| **2. Cliente** | Nome do cliente que abriu a solicitação. | Mariana, Ana, Gabriel |
| **3. Aparelho** | Equipamento entregue para assistência. | Notebook Dell, Galaxy A52, MacBook Air |
| **4. Serviço** | Tipo de serviço solicitado. | Diagnóstico, Troca de tela, Formatação, Limpeza, Upgrade |
| **5. Status** | Situação atual do atendimento destacada pela cor da fonte. | `Recebido`, `Em análise`, `Em manutenção`, `Pronto` |
| **6. Data de criação** | Data em que o chamado foi registrado. | `21/09/2026`, `22/09/2026` |
| **7. Ações** | Espaço reservado para ações sobre o chamado. | `Editar | ...` |

### Identificação Visual dos Status
Cada status é identificado diretamente pela cor da fonte em negrito, seguindo a paleta do projeto:
- **Recebido (`.recebido`):** amarelo (`#f4c24c`).
- **Em análise (`.analise`):** roxo (`#543295`).
- **Em manutenção (`.manutencao`):** laranja (`#fe7f28`).
- **Pronto (`.pronto`):** verde (`#12bc59`).

---

## Dados Fictícios e Funcionalidades Pendentes

> **Aviso sobre os dados atuais:** Todos os 9 registros exibidos atualmente na tabela de `pagina6/pagina6.html` são **dados fictícios de demonstração**, inseridos diretamente no `<tbody>` do HTML apenas para ilustrar a interface.
>
> **Origem real dos dados:** A fonte externa que alimentará os atendimentos **ainda será definida** em etapas futuras do projeto.

### Funcionalidades que ainda dependem de implementação futura (JavaScript / Dados Externos):
- **Busca dinâmica por ID:** digitar um identificador na barra de pesquisa ainda não filtra os registros em tempo real.
- **Ações do chamado:** os controles na coluna **Ações** são elementos visuais preparados para futura implementação.
- **Carregamento dinâmico de dados:** substituição das linhas estáticas do `<tbody>` por dados vindos da fonte externa quando esta for escolhida.

---

## Relação com a Página Inicial e Como Visualizar Localmente

Esta página integra-se diretamente com a **Página Inicial** desenvolvida na branch `LiviaFreixo-pagina-inicial` (`pagina_inicial/index.html` e `pagina_inicial/style.css`), compartilhando tipografia, paleta de cores e ícones.

Para visualizar localmente:
1. Abra o arquivo `pagina6/pagina6.html` diretamente no navegador, ou abra o arquivo `index.html` na raiz do projeto e clique em **"Ir para Acompanhamento de Atendimentos"**.