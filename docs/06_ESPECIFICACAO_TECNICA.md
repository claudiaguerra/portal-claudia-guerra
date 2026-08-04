# 6 — ESPECIFICAÇÃO TÉCNICA
## Portal Cláudia Guerra

**Versão:** 1.0 (MVP)  
**Status:** Aprovado

---

# 1. Objetivo

Esta especificação técnica define a arquitetura tecnológica do Portal Cláudia Guerra.

Seu objetivo é servir como documento oficial de referência para a implementação do Portal no Freebuff e posterior implantação na Hostinger, estabelecendo padrões técnicos, arquitetura do sistema, banco de dados, integrações, segurança e infraestrutura.

O documento não descreve aspectos visuais nem editoriais, tratados em outras missões. Seu foco é exclusivamente a estrutura técnica do Portal.

---

# 2. Princípios Arquitetônicos

Toda a arquitetura deverá seguir os seguintes princípios:

- simplicidade;
- baixo acoplamento;
- reutilização de componentes;
- escalabilidade;
- facilidade de manutenção;
- independência de frameworks proprietários;
- compatibilidade total com o ambiente de hospedagem disponível.

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

HTML

CSS

JavaScript

JavaScript será utilizado apenas no navegador para interações da interface.

Não haverá Node.js executando no servidor.

---

# 5. Compatibilidade

Toda a solução deverá funcionar integralmente no plano:

Hostinger Single Web Hosting.

Restrições consideradas:

- sem Node.js;
- sem aplicações persistentes;
- hospedagem compartilhada;
- PHP nativo;
- MySQL;
- recursos limitados de CPU e memória.

Toda decisão técnica deverá respeitar essas limitações.

---

# 6. Unidade Fundamental do Sistema

A arquitetura será baseada em um único conceito:

> Tudo no Portal é um Conteúdo.

Não existirão estruturas independentes para:

- notícias;
- artigos;
- eventos;
- páginas;
- projetos;
- documentos.

Todos serão registros de uma única entidade chamada Conteúdo.

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

## Tipo de Conteúdo

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

- rascunho
- publicado
- agendado
- arquivado

---

# 8. Tabelas Auxiliares

## usuarios

Controle de acesso ao painel.

Campos:

- id
- nome
- email
- senha
- perfil
- ativo

Perfis:

- administrador
- editor

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

- Uberlândia
- Uberaba
- Araguari
- Triângulo Mineiro
- Minas Gerais

Um conteúdo poderá relacionar-se com diversos territórios.

---

## categorias

Organização temática.

Exemplos:

- Mulheres
- Educação
- Cultura
- Direitos Humanos
- Saúde
- Proteção Animal

---

## relacionamentos

Tabela responsável pelas conexões inteligentes entre conteúdos.

Estrutura:

- conteudo_origem
- tipo_relacao
- conteudo_destino

Exemplos:

Uma notícia poderá relacionar-se com:

- projeto;
- território;
- proposta;
- eixo;
- campanha.

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

```
/admin
```

Acesso protegido.

---

## Funcionalidades

O Editor poderá:

- criar conteúdos;
- editar conteúdos;
- publicar;
- arquivar;
- agendar publicações.

Também poderá:

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

- senha criptografada;
- sessões;
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
- regras;
- recursos;
- arquivos enviados.

---

# 13. Front-end

A interface será baseada em componentes reutilizáveis.

Exemplos:

- Hero Narrativo
- Cards
- Timeline
- Galerias
- Feed
- Painéis de aprofundamento
- Modais
- Menu
- Rodapé

Cada componente deverá ser reutilizável em diferentes partes do Portal.

---

# 14. Responsividade

O Portal será desenvolvido seguindo o princípio:

**Mobile First.**

A experiência deverá adaptar-se para:

Desktop

Tablet

Smartphones

---

# 15. Performance

Considerando os recursos disponíveis da hospedagem:

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

Permitirá versões específicas para campanhas eleitorais.

---

# 17. Integrações

## Freebuff

Será utilizado para geração do sistema.

O resultado será código proprietário.

Fluxo:

```text
Freebuff

↓

Código

↓

Hostinger

↓

Portal
```

---

## Método Kóller

O Portal não manterá cadastro próprio de pessoas.

Sempre que necessário utilizará os processos oficiais do MK.

Exemplo:

Voluntário

↓

Google Forms

↓

MK

↓

Banco de Pessoas

O Portal será uma interface de acesso aos processos.

---

## Google Forms

Será incorporado em painéis internos quando necessário.

Não quebrará a experiência de navegação.

---

## Redes Sociais

Integração com:

- Instagram
- Facebook
- X
- YouTube

As interações ocorrerão na plataforma original.

O Portal organiza e apresenta o conteúdo.

---

## Vídeos

Não serão armazenados no servidor.

Serão incorporados via YouTube.

Curtidas e comentários abrirão nova aba.

---

## Mapas

Estrutura preparada para futura integração com:

- Google Maps
- OpenStreetMap

Não faz parte do MVP.

---

## SMTP

O envio de e-mails utilizará SMTP.

Não dependerá de mail() do PHP.

---

## Analytics

Estrutura preparada para:

- Google Analytics;
- Google Search Console.

---

# 18. SEO

SEO fará parte da arquitetura.

Não será tratado posteriormente.

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

A arquitetura deverá favorecer indexação orgânica desde sua construção.

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

- banco;
- imagens;
- documentos;
- arquivos enviados.

---

# 21. Publicação

Fluxo previsto:

```text
Código

↓

Upload

↓

Configuração PHP

↓

Banco

↓

Importação

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
- O Portal deve funcionar plenamente na infraestrutura disponível.
- O sistema deve crescer por evolução, nunca por reconstrução.
- SEO faz parte da arquitetura.
- Segurança e desempenho são requisitos estruturais.
- O Portal não multiplica sistemas: conecta pessoas aos processos corretos.

---

# Conclusão

A Especificação Técnica estabelece a base arquitetônica do Portal Cláudia Guerra.

Todas as implementações futuras, incluindo os prompts do Freebuff, deverão respeitar este documento como referência oficial, garantindo coerência entre a arquitetura planejada, o ambiente de hospedagem e a evolução contínua do Portal.