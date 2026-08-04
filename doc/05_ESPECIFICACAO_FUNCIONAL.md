# 5 — ESPECIFICAÇÃO FUNCIONAL
## Portal Cláudia Guerra

**Versão:** 1.0 (Consolidada)  
**Documento:** 05_ESPECIFICACAO_FUNCIONAL.md

---

# Finalidade deste documento

Este documento define o funcionamento do Portal Cláudia Guerra sob a perspectiva do usuário e da administração da plataforma.

Não trata de tecnologias, linguagens de programação, banco de dados ou infraestrutura. Essas definições pertencem à Missão 6.

O objetivo desta missão é responder à seguinte pergunta:

> **O que cada parte do Portal faz?**

Toda decisão aqui documentada foi aprovada durante a concepção do Portal e servirá como referência para a geração dos prompts do Freebuff e para o desenvolvimento do sistema.

---

# Filosofia funcional

O Portal não é um conjunto de páginas.

O Portal é uma plataforma orientada por conteúdo.

As pessoas não administram páginas.

Administram informações.

O sistema é responsável por organizar essas informações, relacioná-las e apresentá-las automaticamente ao visitante.

Quanto menos o Editor precisar se preocupar com aspectos técnicos ou estruturais, mais consistente será o Portal ao longo do tempo.

---

# Princípios funcionais

Toda funcionalidade do Portal deve respeitar os seguintes princípios:

- simplicidade operacional;
- organização automática dos conteúdos;
- reutilização de informações;
- preservação do contexto de navegação;
- crescimento contínuo sem perda de organização;
- integração com sistemas externos quando fizer sentido;
- evitar duplicação de cadastros e processos.

---

# Perfis de usuários

O Portal possuirá apenas três perfis de utilização.

## Visitante

Não necessita autenticação.

Pode:

- navegar livremente;
- utilizar a busca;
- acessar conteúdos;
- visualizar documentos;
- assistir vídeos incorporados;
- compartilhar conteúdos;
- entrar em contato;
- participar das ações propostas pelo Portal.

O visitante representa o público geral.

---

## Editor

Responsável pela operação diária do Portal.

Possui autenticação.

Pode:

- criar conteúdos;
- editar conteúdos;
- publicar;
- retirar conteúdos do ar;
- agendar publicações;
- anexar imagens;
- anexar documentos;
- incorporar vídeos;
- destacar conteúdos;
- organizar conteúdos em destaque.

O Editor administra conteúdos.

O Editor não administra páginas.

---

## Administrador

Responsável pela administração completa da plataforma.

Pode:

- gerenciar usuários;
- controlar permissões;
- alterar configurações gerais;
- administrar menus;
- configurar campanhas sazonais;
- controlar parâmetros do sistema;
- realizar manutenção administrativa.

---

# Princípio da administração

A administração do Portal é orientada por conteúdo.

Nenhum usuário edita manualmente a estrutura das páginas.

O Portal é responsável por construir automaticamente sua própria apresentação a partir das informações cadastradas.

Esse princípio garante:

- padronização visual;
- redução de erros;
- facilidade de manutenção;
- crescimento sustentável do acervo.

---

# Ciclo de vida do conteúdo

Todo conteúdo segue um ciclo simples.

```text
Criar
    ↓
Salvar
    ↓
Publicar
    ↓
Atualizar
    ↓
Arquivar
```

Conteúdos não são excluídos como procedimento padrão.

Quando deixam de ser relevantes permanecem arquivados, preservando o histórico institucional da Cláudia Guerra.

---

# Estados do conteúdo

Cada conteúdo poderá possuir um dos seguintes estados:

- Rascunho
- Publicado
- Agendado
- Arquivado

Esses estados são suficientes para o MVP.

---

# Conteúdo relacionado

Uma única publicação poderá alimentar diversos locais do Portal.

Exemplo:

Uma notícia publicada poderá estar relacionada simultaneamente a:

- História;
- Ações;
- Território;
- Minas que Cuida;
- determinado Projeto;
- determinado Eixo;
- Busca;
- Conteúdos relacionados.

O Editor informa apenas os relacionamentos.

O Portal realiza automaticamente toda a distribuição.

Este é um dos pilares arquitetônicos da plataforma.

---

# Conteúdo em destaque

Qualquer conteúdo poderá receber prioridade de exibição.

Exemplos:

- destaque do Hero;
- destaque da Home;
- destaque de uma seção específica.

O conteúdo continua sendo único.

Apenas sua prioridade visual muda.

---

# Busca

A busca é global.

O visitante poderá localizar conteúdos por:

- título;
- texto;
- tema;
- território;
- projeto;
- proposta;
- documentos;
- palavras-chave.

A busca representa uma das principais formas de navegação do Portal.

---

# Biblioteca de mídias

Toda mídia pertence a algum conteúdo.

Não existirão imagens soltas.

Cada conteúdo poderá possuir:

- imagem principal;
- galeria de imagens;
- vídeos incorporados;
- documentos;
- links externos.

A mesma mídia poderá ser utilizada em diversos locais sem duplicação.

---

# Imagem principal

Cada conteúdo poderá definir uma imagem de destaque.

Essa imagem será utilizada automaticamente em:

- cards;
- listagens;
- resultados de busca;
- conteúdos relacionados;
- destaques.

---

# Hero

O Hero não possui conteúdo próprio.

Ele utiliza conteúdos já existentes.

O Editor apenas indica quando um conteúdo poderá ser utilizado pelo Hero.

Isso garante atualização constante sem necessidade de reconstruir a página inicial.

---

# Documentos

Todo documento pertence a um conteúdo.

Exemplos:

Projeto → PDF.

Emenda → PDF.

Edital → PDF.

Plano → PDF.

Nenhum documento fica isolado na plataforma.

---

# Vídeos

O Portal não hospedará vídeos.

Os vídeos serão incorporados de plataformas externas, como:

- YouTube;
- Instagram;
- Facebook;
- Vimeo;
- outras plataformas compatíveis.

Essa decisão reduz consumo de armazenamento, processamento e banda da hospedagem.

---

# Interações

O Portal não pretende competir com redes sociais.

Ele organiza conteúdo.

As interações acontecem nas plataformas onde o conteúdo foi originalmente publicado.

---

## Compartilhamento

Todos os conteúdos poderão ser compartilhados.

Prioridade para:

- WhatsApp;
- Facebook;
- Instagram (compartilhamento de link);
- copiar link.

---

## Curtidas e comentários

Não existirão sistemas próprios de curtidas ou comentários no MVP.

Quando um conteúdo incorporado permitir interação, o Portal apresentará opções como:

- Curtir
- Comentar
- Assistir na plataforma original

Ao selecionar essas ações, o usuário será informado de que será redirecionado para a publicação original.

A abertura ocorrerá sempre em uma nova aba do navegador.

O Portal permanece aberto exatamente no ponto onde o visitante estava.

---

# Princípio das redes sociais

O Portal concentra o conteúdo.

As redes sociais concentram a conversa.

Essa separação elimina:

- moderação de comentários;
- combate a spam;
- duplicação de comunidades;
- complexidade desnecessária.

Ao mesmo tempo fortalece o alcance das próprias redes sociais da Cláudia Guerra.

---

# Navegação externa

Nenhum acesso externo interrompe a experiência do visitante.

Todo conteúdo externo será aberto em nova aba.

Exemplos:

- vídeos;
- redes sociais;
- documentos;
- links institucionais.

Esse princípio preserva a continuidade da navegação.

---

# Sistema de Contato Contextual

O Portal não possuirá dezenas de formulários independentes.

Existirá um único mecanismo de contato.

Cada botão do Portal abrirá esse mecanismo já contextualizado.

Exemplos:

## Denúncia

Assunto preenchido automaticamente:

```
Denúncia de maus-tratos aos animais
```

---

## Solicitação

```
Solicitação de palestra
```

---

## Escutatória

```
Agendamento de Escutatória
```

---

## Participação

```
Contribuição ao Plano Minas que Cuida
```

O visitante apenas complementa as informações necessárias.

---

# Integração com o Método Kóller (MK)

Sempre que o objetivo for cadastrar pessoas, o Portal não criará cadastros próprios.

Utilizará diretamente os processos oficiais já existentes no Método Kóller.

Exemplo:

```
Portal
      ↓
Google Forms incorporado
      ↓
STG
      ↓
Processamento MK
      ↓
Base Oficial de Pessoas
```

Essa decisão evita duplicação de cadastros e mantém uma única fonte oficial de informações.

O Portal integra processos.

Não cria sistemas paralelos.

---

# Busca e descoberta

A busca não serve apenas para responder perguntas.

Ela ajuda o visitante a descobrir novos conteúdos.

Cada publicação poderá gerar conexões automáticas com:

- territórios;
- projetos;
- organizações;
- campanhas;
- propostas;
- documentos;
- conteúdos relacionados.

O próprio conteúdo cria novos caminhos de navegação.

---

# Descoberta contextual

Ao acessar uma notícia, o visitante poderá continuar navegando por:

- projeto relacionado;
- território;
- eixo correspondente;
- proposta relacionada;
- organização envolvida.

O Portal funciona como uma rede de conhecimento.

---

# Objetivo funcional

Cada informação deve ser cadastrada apenas uma vez.

A partir desse único cadastro, o Portal organiza automaticamente:

- onde o conteúdo aparece;
- como aparece;
- com quais conteúdos se relaciona;
- quais caminhos de navegação serão oferecidos ao visitante.

Essa decisão reduz manutenção, elimina redundâncias e permite crescimento contínuo do Portal.

---

# Conceito oficial da Missão 5

O Portal Cláudia Guerra é uma plataforma orientada por conteúdo.

Seu funcionamento privilegia simplicidade operacional, organização automática, reutilização de informações e integração entre conteúdos, permitindo que o Editor concentre seus esforços na produção e atualização das informações, enquanto o próprio Portal organiza, relaciona e apresenta esse conhecimento ao visitante de forma consistente, intuitiva e escalável.

Cada funcionalidade existe para aproximar pessoas, preservar a trajetória de Cláudia Guerra, fortalecer sua atuação pública e facilitar a participação da sociedade, mantendo uma experiência contínua, organizada e preparada para evoluir sem perda de identidade.
````
