# 07_GUIA_DE_IMPLEMENTACAO_FREEBUFF

## Guia de Implementação utilizando FreeBuff Web

---

# 1. Objetivo do Documento

Este documento estabelece as diretrizes de utilização do **FreeBuff Web** como ferramenta de implementação, desenvolvimento e evolução do Portal Cláudia Guerra.

O objetivo é padronizar o uso da plataforma, otimizar o processo de criação, reduzir retrabalho, controlar o contexto fornecido à inteligência artificial e garantir que as alterações realizadas estejam alinhadas com a documentação oficial do projeto.

O FreeBuff atua como ferramenta de implementação visual e geração assistida de código, enquanto o GitHub permanece como repositório central do projeto.

---

# 2. Papel do FreeBuff na Arquitetura do Projeto

Dentro da arquitetura do Portal Cláudia Guerra:

```text
Documentação do Projeto
        │
        ▼
GitHub
        │
        ▼
FreeBuff Web
        │
        ▼
Código do Portal
        │
        ▼
Publicação
```

Responsabilidades:

## GitHub

Responsável por:

* armazenar a documentação oficial;
* controlar versões;
* registrar alterações;
* manter o histórico do projeto.

## FreeBuff Web

Responsável por:

* criação da interface;
* desenvolvimento visual;
* geração e edição de código;
* implementação das funcionalidades definidas.

## Documentação

Responsável por:

* orientar decisões;
* preservar o conceito;
* evitar alterações sem planejamento.

---

# 3. Organização do Repositório

A estrutura principal do projeto segue:

```text
portal-claudia-guerra/

├── README.md
│
├── docs/
│   ├── 01_CONCEITO_DO_PORTAL.md
│   ├── 02_ARQUITETURA_DA_INFORMACAO.md
│   ├── 03_ESTRATEGIA_DE_CONTEUDO.md
│   ├── 04_EXPERIÊNCIA_IDENTIDADE_VISUAL.md
│   ├── 05_ESPECIFICACAO_FUNCIONAL.md
│   ├── 06_ESPECIFICACAO_TECNICA.md
│   └── 07_GUIA_DE_IMPLEMENTACAO_FREEBUFF.md
│
├── site/
│   └── arquivos gerados pelo FreeBuff
│
└── assets/
    └── recursos visuais
```

Regra principal:

* `docs/` contém a inteligência documental do projeto.
* `site/` contém a implementação.
* `assets/` contém recursos visuais.

---

# 4. Fluxo Padrão de Desenvolvimento no FreeBuff

Toda alteração relevante deve seguir o fluxo:

```text
1. Consultar documentação existente

        ↓

2. Planejar alteração

        ↓

3. Aprovar abordagem

        ↓

4. Implementar no FreeBuff

        ↓

5. Revisar resultado

        ↓

6. Versionar no GitHub
```

Nenhuma alteração estrutural deve ser feita sem considerar os documentos:

* Conceito do Portal;
* Arquitetura da Informação;
* Especificação Funcional;
* Especificação Técnica.

---

# 5. Utilização dos Slash Commands

Os comandos de barra devem ser utilizados para orientar a inteligência artificial do FreeBuff.

## /interview

### Objetivo:

Alinhar requisitos antes da criação.

Utilizar quando:

* criar novas páginas;
* criar novas funcionalidades;
* modificar estruturas importantes.

---

## /plan

### Objetivo:

Criar um plano de implementação antes da alteração.

Utilizar antes de:

* mudanças estruturais;
* novas funcionalidades;
* alterações de arquitetura.

---

## /execute

### Objetivo:

Executar uma implementação previamente planejada.

Utilizar somente após aprovação do plano.

---

## /review

### Objetivo:

Realizar auditoria da implementação.

Avaliar:

* erros;
* inconsistências;
* problemas de interface;
* problemas de desempenho;
* compatibilidade.

---

## /clear

### Objetivo:

Limpar o contexto da sessão atual.

Utilizar quando:

* iniciar uma nova etapa;
* mudar completamente de assunto;
* evitar excesso de informações acumuladas.

---

# 6. Controle de Contexto da Inteligência Artificial

O FreeBuff trabalha melhor quando recebe apenas as informações necessárias para cada tarefa.

Evitar:

* carregar todo o projeto sem necessidade;
* enviar arquivos grandes sem objetivo;
* misturar documentos de diferentes etapas.

Preferir:

* referências diretas aos arquivos;
* solicitações específicas;
* alterações isoladas.

---

# 7. Referenciamento Direto de Arquivos

Sempre que possível utilizar referências específicas:

Exemplos:

```text
@01_CONCEITO_DO_PORTAL.md
```

para consultar o conceito geral.

```text
@02_ARQUITETURA_DA_INFORMACAO.md
```

para alterações estruturais.

```text
@05_ESPECIFICACAO_FUNCIONAL.md
```

para criação de funcionalidades.

Essa prática reduz ambiguidades e melhora a precisão das respostas.

---

# 8. Controle de Indexação com .codebuffignore

Quando necessário, utilizar o arquivo:

```text
.codebuffignore
```

para impedir que arquivos irrelevantes consumam contexto da IA.

Exemplo:

```text
# Arquivos temporários

*.log
*.tmp


# Dependências futuras

node_modules/
dist/
build/
.cache/


# Arquivos pesados

assets/**/*.png
assets/**/*.jpg
assets/**/*.jpeg
assets/**/*.mp4
```

Observação:

A pasta `docs/` não deve ser ignorada, pois contém a documentação fundamental do projeto.

---

# 9. Estratégia de Uso dos Modelos de IA

Utilizar modelos conforme a complexidade da tarefa.

## Modelo rápido

Indicado para:

* ajustes simples;
* HTML;
* CSS;
* textos;
* pequenas alterações visuais.

---

## Modelo de raciocínio profundo

Indicado para:

* decisões arquitetônicas;
* problemas complexos;
* revisão de código;
* otimização;
* análise de erros.

---

# 10. Processo de Revisão e Versionamento

Toda alteração significativa deve resultar em:

1. revisão da implementação;
2. verificação da documentação relacionada;
3. commit no GitHub;
4. registro da evolução do projeto.

Exemplo de mensagens de commit:

```text
estrutura: cria nova seção do portal

funcionalidade: adiciona formulário de participação

design: ajusta identidade visual da página inicial

correcao: resolve problema de navegação
```

---

# 11. Boas Práticas Específicas do Portal Cláudia Guerra

## Preservar o conceito antes do código

O Portal deve sempre evoluir a partir da documentação.

---

## Separar conteúdo, identidade e tecnologia

As decisões devem respeitar:

* conceito institucional;
* experiência do usuário;
* identidade visual;
* requisitos técnicos.

---

## Evitar alterações sem planejamento

O FreeBuff é uma ferramenta de execução, não de definição estratégica.

A estratégia permanece registrada na documentação.

---

# 12. Atualização do Documento

Este documento deve ser atualizado sempre que:

* o fluxo do FreeBuff mudar;
* novas funcionalidades forem incorporadas;
* novas práticas forem definidas;
* outra ferramenta substituir o FreeBuff.

Caso outra plataforma seja utilizada futuramente, este documento poderá ser substituído sem impacto na documentação principal do Portal.
