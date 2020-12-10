# Trabalho Individual - GCES - 2020/1

A Gestão de Configuração de Software é parte fundamental no curso de GCES, e dominar os conhecimentos de configuração de ambiente, containerização, virtualização, integração e deploy contínuo tem se tornado cada vez mais necessário para ingressar no mercado de trabalho.

Para exercitar estes conhecimentos, você deverá aplicar os conceitos estudados ao longo da disciplina no produto de software contido neste repositório.

O sistema se trata de uma aplicação Web, cuja funcionalidade consiste na pesquisa e exibição de perfis de usuários do GitHub, que é composta de:

- Front End escrito em Javascript, utilizando os frameworks Vue.JS e Quasar;
- Back End escrito em Ruby on Rails, utilizado em modo API;
- Banco de Dados PostgreSQL;

Para executar a aplicação na sua máquina, basta seguir o passo-a-passo descrito no arquivo [Descrição e Instruções](Descricao-e-Instrucoes.md).

## Critérios de avaliação

### 1. Containerização

A aplicação deverá ter seu ambiente completamente containerizado. Desta forma, cada subsistema (Front End, Back End e Banco de Dados) deverá ser isolado em um container individual.

Deverá ser utilizado um orquestrador para gerenciar comunicação entre os containers, o uso de credenciais, networks, volumes, entre outras configurações necessárias para a correta execução da aplicação.

Para realizar esta parte do trabalho, recomenda-se a utilização das ferramentas:

- Docker versão 17.04.0+
- Docker Compose com sintaxe na versão 3.2+

### 2. Integração contínua

Você deverá criar um 'Fork' deste repositório, onde será desenvolvida sua solução. Nele, cada commit submetido deverá passar por um sistema de integração contínua, realizando os seguintes estágios:

- Build: Construção completa do ambiente;
- Testes: Os testes automatizados da aplicação devem ser executados;
- Coleta de métricas: Deverá ser realizada a integração com algum serviço externo de coleta de métricas de qualidade;

O sistema de integração contínua deve exibir as informações de cada pipeline, e impedir que trechos de código que não passem corretamente por todo o processo sejam adicionados à 'branch default' do repositório.

Para esta parte do trabalho, poderá ser utilizada qualquer tecnologia ou ferramenta que o aluno desejar, como GitlabCI, TravisCI, CircleCI, Jenkins, CodeClimate, entre outras.

### 3. Deploy contínuo (Extra)

Caso cumpra todos os requisitos descritos acima, será atribuída uma pontuação extra para o aluno que configure sua pipeline de modo a publicar a aplicação automaticamente, sempre que um novo trecho de código seja integrado à branch default.

---
### Solução

Aluno: Youssef Muhamad | 17/0024334

#### Conteinerização:

- O projeto foi dividido em 3 containers(frontend, backend e banco de dados), para isso foi utilizado o Docker e o Docker Compose.

- A env `/docker/db_config.env` foi criada para facilitar a mudança nas variáveis do PostgreSQL.

### Como executar o projeto:

- `docker-compose up`

Após o comando terminar de executar, as aplicações estarão nas urls:

- Frontend : http://localhost:8080/
- Backend : http://localhost:3000

Para rodar os testes nos ambientes já dockerizados:
- Frontend: `docker-compose run frontend yarn run test:unit`
- Backend: `docker-compose run api bundle exec rails test`