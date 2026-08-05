# 06_ESPECIFICACAO_TECNICA

# Especificação Técnica do Portal Cláudia Guerra

**Versão:** 1.1 (MVP)  
**Status:** Aprovado

---

# 1. Objetivo

Esta especificação técnica define a arquitetura tecnológica do Portal Cláudia Guerra.

Seu objetivo é servir como documento oficial de referência para a implementação técnica do Portal, estabelecendo padrões tecnológicos, arquitetura do sistema, banco de dados, integrações, segurança, infraestrutura e requisitos de compatibilidade para o ambiente de produção.

Este documento não descreve aspectos visuais nem editoriais, tratados nas demais documentações do projeto. Seu foco é exclusivamente a estrutura técnica do Portal.

---

# 2. Princípios Arquitetônicos

Toda a arquitetura deverá seguir os seguintes princípios:

- simplicidade;
- baixo acoplamento;
- reutilização de componentes;
- escalabilidade;
- facilidade de manutenção;
- independência de frameworks proprietários;
- compatibilidade total com o ambiente de produção;
- portabilidade da solução.

O Portal deverá ser construído para crescer ao longo dos anos sem necessidade de reconstrução completa.

---

# 3. Arquitetura Geral

O Portal será desenvolvido como uma aplicação web própria.

Não utilizará WordPress como plataforma principal.

Não dependerá de plugins para funcionamento.

A arquitetura será composta por três camadas:

```text
Front-end
    ↓
Back-end (PHP)
    ↓
Banco de Dados (MySQL)
```

Cada camada possui responsabilidades específicas e independentes.

---

# 4. Ambiente Tecnológico

## Linguagem

PHP

---

## Banco de Dados

MySQL/MariaDB

---

## Front-end

- HTML
- CSS
- JavaScript

JavaScript será utilizado para as interações da interface no navegador.

Poderão ser utilizados frameworks modernos de frontend durante o desenvolvimento, desde que o resultado final permaneça compatível com os requisitos definidos para o ambiente de produção.

---

## Compatibilidade com o Ambiente de Produção

Toda a implementação deverá ser compatível com hospedagem compartilhada.

O ambiente de produção não deverá depender da execução contínua de Node.js.

Caso sejam utilizados frameworks como React ou similares, o resultado final deverá ser um **build estático**, compatível com HTML, CSS e JavaScript convencionais.

Não serão utilizados recursos que dependam da execução permanente de Node.js em produção, tais como:

- Server-Side Rendering (SSR);
- API Routes;
- Server Actions;
- servidores Node.js persistentes.

---

# 5. Compatibilidade

Toda a solução deverá funcionar integralmente no ambiente de produção previsto.

Características consideradas:

- hospedagem compartilhada;
- PHP nativo;
- MySQL/MariaDB;
- HTML;
- CSS;
- JavaScript;
- recursos limitados de CPU e memória;
- sem necessidade de Node.js em produção.

Toda decisão técnica deverá respeitar essas limitações.

---

# 6. Unidade Fundamental do Sistema

A arquitetura será baseada em um único conceito:

> **Tudo no Portal é um Conteúdo.**

Não existirão estruturas independentes para:

- notícias;
- artigos;
- eventos;
- páginas;
- projetos;
- documentos.

Todos serão registros de uma única entidade denominada **Conteúdo**.

O que diferencia cada registro é o seu tipo.

Exemplo:

```text
Conteúdo

├── História
├── Ação
├── Projeto
├── Proposta
├── Evento
├── Notícia
├── Documento
├── Vídeo
├── Campanha
└── Página Institucional
```

Esta decisão reduz complexidade, facilita buscas, relacionamentos e manutenção.

---

# 7. Banco de Dados

## Tabela Principal

### conteudos

Campos principais:

- id
- titulo
- subtitulo
- resumo
- conteudo
- imagem_capa
- tipo_conteudo
- status
- data_criacao
- data_publicacao
- data_atualizacao
- autor
- destaque

---

## Tipos de Conteúdo

Exemplos:

- historia
- acao
- projeto
- proposta
- evento
- noticia
- documento
- video
- campanha
- institucional

---

## Status

Cada conteúdo poderá possuir:

- rascunho;
- publicado;
- agendado;
- arquivado.

---

# 8. Tabelas Auxiliares

## usuarios

Controle de acesso ao painel administrativo.

Campos:

- id
- nome
- email
- senha
- perfil
- ativo

Perfis:

- administrador;
- editor.

---

## midias

Biblioteca central de arquivos.

Campos:

- id
- nome
- tipo
- caminho
- data_upload

---

## territorios

Cadastro territorial.

Exemplos:

- Uberlândia;
- Uberaba;
- Araguari;
- Triângulo Mineiro;
- Minas Gerais.

Um conteúdo poderá relacionar-se com diversos territórios.

---

## categorias

Organização temática.

Exemplos:

- Mulheres;
- Educação;
- Cultura;
- Direitos Humanos;
- Saúde;
- Proteção Animal.

---

## relacionamentos

Tabela responsável pelas conexões inteligentes entre conteúdos.

Estrutura:

- conteudo_origem;
- tipo_relacao;
- conteudo_destino.

Essa estrutura permitirá múltiplos caminhos de navegação sem duplicação de conteúdo.

---

# 9. Back-end

O Back-end será responsável por:

- autenticação;
- gerenciamento de conteúdos;
- relacionamento de dados;
- regras de negócio;
- comunicação com banco de dados.

Toda a lógica será implementada em PHP.

---

# 10. Área Administrativa

Endereço previsto:

```text
/admin
```

Acesso protegido.

Funcionalidades:

- criar conteúdos;
- editar conteúdos;
- publicar;
- arquivar;
- agendar publicações;
- enviar mídias;
- organizar arquivos;
- definir destaques;
- relacionar conteúdos.

---

# 11. Autenticação

Fluxo:

```text
Login

↓

PHP valida usuário

↓

Banco confirma

↓

Sessão criada

↓

Painel liberado
```

Segurança:

- senhas criptografadas;
- controle de sessões;
- proteção contra acesso direto;
- logout.

---

# 12. Organização de Arquivos

Estrutura conceitual:

```text
/public_html

index.php

admin/

includes/

assets/

uploads/
```

A organização poderá evoluir durante a implementação, mantendo separação entre:

- interface;
- regras de negócio;
- recursos;
- arquivos enviados.

---

# 13. Front-end

A interface será baseada em componentes reutilizáveis.

Exemplos:

- Hero Narrativo;
- Cards;
- Timeline;
- Galerias;
- Feed;
- Painéis de aprofundamento;
- Modais;
- Menu;
- Rodapé.

---

# 14. Responsividade

O Portal será desenvolvido seguindo o princípio **Mobile First**.

A experiência deverá adaptar-se para:

- Desktop;
- Tablet;
- Smartphones.

---

# 15. Performance

Prioridades:

- imagens otimizadas;
- carregamento progressivo;
- CSS organizado;
- JavaScript leve;
- mínimo de bibliotecas externas;
- cache sempre que possível.

---

# 16. Hero Narrativo

O Hero não será um banner.

Será um componente dinâmico composto por:

- imagens;
- textos;
- animações;
- camadas;
- chamadas.

As cenas poderão ser substituídas futuramente sem alterar a estrutura do Portal.

---

# 17. Integrações

## Ferramentas de Desenvolvimento

O Portal poderá utilizar ferramentas de desenvolvimento assistidas por Inteligência Artificial.

A ferramenta utilizada para geração do código não altera os requisitos desta especificação técnica.

Todo código produzido deverá respeitar integralmente este documento antes de sua publicação.

---

## Método Kóller

O Portal não manterá cadastro próprio de pessoas.

Sempre que necessário utilizará os processos oficiais do Método Kóller.

---

## Google Forms

Será incorporado quando necessário para coleta de informações.

---

## Redes Sociais

Integração com:

- Instagram;
- Facebook;
- X;
- YouTube.

As interações ocorrerão na plataforma original.

---

## Vídeos

Serão incorporados via YouTube.

Não serão armazenados no servidor.

---

## Mapas

Arquitetura preparada para futura integração com:

- Google Maps;
- OpenStreetMap.

Não faz parte do MVP.

---

## SMTP

O envio de e-mails utilizará SMTP.

---

## Analytics

Arquitetura preparada para integração com:

- Google Analytics;
- Google Search Console.

---

# 18. SEO

SEO fará parte da arquitetura desde sua construção.

Cada conteúdo poderá possuir:

- título SEO;
- descrição SEO;
- imagem de compartilhamento;
- URL amigável.

Também deverão existir:

- sitemap.xml;
- robots.txt;
- dados estruturados;
- otimização para compartilhamento em redes sociais.

---

# 19. Segurança

Boas práticas obrigatórias:

- consultas preparadas;
- validação de entrada;
- controle de uploads;
- criptografia de senhas;
- controle de sessões;
- permissões de acesso.

---

# 20. Backups

Deverão existir duas camadas:

- backup da hospedagem;
- backup independente do Portal.

Incluindo:

- banco de dados;
- imagens;
- documentos;
- arquivos enviados.

---

# 21. Publicação

Fluxo previsto:

```text
Desenvolvimento

↓

Versionamento (GitHub)

↓

Build (quando aplicável)

↓

Publicação

↓

Configuração do Ambiente

↓

Testes

↓

Portal Online
```

---

# 22. Evolução

Toda a arquitetura deverá permitir crescimento sem reconstrução.

Novos:

- tipos de conteúdo;
- categorias;
- territórios;
- componentes;
- integrações.

Deverão ser incorporados preservando a estrutura existente.

---

# 23. Princípios Técnicos Consolidados

O Portal deverá obedecer aos seguintes princípios:

- Tudo é Conteúdo.
- Componentes são reutilizáveis.
- O Portal organiza conhecimento.
- Integrações substituem retrabalho.
- A tecnologia deve permanecer invisível para o visitante.
- O Portal deve funcionar plenamente no ambiente de produção definido.
- O sistema deve crescer por evolução, nunca por reconstrução.
- SEO faz parte da arquitetura.
- Segurança e desempenho são requisitos estruturais.
- O Portal não multiplica sistemas: conecta pessoas aos processos corretos.

---

# Conclusão

A Especificação Técnica estabelece a base arquitetônica oficial do Portal Cláudia Guerra.

Toda implementação futura deverá respeitar este documento como referência técnica principal, garantindo coerência entre arquitetura, ambiente de produção, desempenho, segurança e evolução contínua do Portal.
