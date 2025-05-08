# Web Application Document - Projeto Individual - Módulo 2 - Inteli

## Nome do Projeto

#### Autora: [Nicolli Venino Santana](https://www.linkedin.com/in/nicolli-venino-santana-b84341254/)

## Sumário

1. [Introdução](#c1)  
2. [Visão Geral da Aplicação Web](#c2)  
3. [Projeto Técnico da Aplicação Web](#c3)  
4. [Desenvolvimento da Aplicação Web](#c4)  
5. [Referências](#c5)  

<br>

## <a name="c1"></a>1. Introdução 

O (nome) é uma plataforma WEB de gerenciamento de tarefas para organização e produtividade dos usuários. Nesse sentido, o objetivo é concentrar as mais embasadas técnicas de ordenamento e de administração de atividades em um único sistema WEB tecnológico, personalizado e gratuito. 

Dentre as metodologias que a aplicação contempla, pode-se citar:

- Kanban;

- Mapa Mental;

- Model Canvas. <div>

Além disso, é válido destacar a personalização como elemento imprescindível à plataforma. Acerca disso, entende-se que a preferência de organização do usuário é prioritária em relação às técnicas intrínsecas no sistema, de forma que é possível escolher o modo de visualização das tarefas e, ainda, utilizar templates disponíveis para facilitar a usabilidade.

Diante disso, é notório que a aplicação caracteriza-se como uma alternativa ao tradicional “papel e caneta”, de modo que mitiga as seguintes duas problemáticas desse modelo: a complexidade de organização e gerenciamento dos papéis e o dispêndio abusivo dos recursos naturais. Sob essa ótica, no que tange à supracitada primeira falha do modo convencional de organizar tarefas, é fato que, não raro, a pilha de folhas ou o amontoado de cadernos se perdem em meio aos demais utensílios do dia a dia, assim como é dificultoso desenhar alinhadamente uma metodologia de gerenciamento no papel. Por isso, a aplicação erradica o problema de perda das anotações - haja vista que guarda as informações do usuário em pastas seguras na nuvem - e, por intermédio dos templates e das ferramentas de visualização, ameniza a imprecisão do design. Já em relação à segunda deficiência, uma vez que o programa não é concreto no meio físico, a aplicação permite que não haja gastos nem com papéis nem com tintas para que os usuários possam gerenciar suas tarefas com maestria, suavizando, portanto, o impacto ambiental consequente.

---

## <a name="c2"></a>2. Visão Geral da Aplicação Web

### 2.1. Personas 

<p align = "center">Figura 1: Persona</p>

![Persona](https://github.com/user-attachments/assets/214d0ac2-f0ad-4755-9e8c-1e0c6b9d099a)

<p align = "center">Fonte: material produzido pela autora com o CANVAS (2025).</p> <br>

### 2.2. User Stories 

- <strong>US01:</strong> Eu, como usuário, gostaria de visualizar minhas tarefas diárias, semanais e mensais em uma única plataforma digital para evitar gasto de tempo e de materiais físicos, assim como amenizar problemas de desorganização e perda de informações. <div>

  <strong>I:</strong> a ação que diz respeito ao usuário inserir suas tarefas é a mais fundamental funcionalidade do programa, de modo que é implementada sem depedência de derivações de outras user stories.<div>
  
  <strong>N:</strong> a user storie supracitada é negociável, ou seja, o desejo de inserir tarefas diárias, semanais e mensais pode ser adaptada, se necessário, por intermédio de conversas com o usuário.<div>
  
  <strong>V:</strong> a user storie é valiosa, pois descreve, notoriamente, o impacto na vida do usuário, destacando como será importante para suprir suas necessidades e amenizar suas dores.<div>
  
  <strong>E:</strong> é possível elaborar estimativas apartir da user storie, pois o desejo do usuário foi bem específico.<div>
  
  <strong>S:</strong> no que tange ao tamanho da funcionalidade descrita na user storie, pode-se afirmar que é possível executá-la dentro do prazo estabelecido e com os recursos dispostos. <div>
  
  <strong>T:</strong> a user storie expressa clareza o suficiente para que seja possível validá-la por meio de testes.<div>

- <strong>US02:</strong> Eu, como usuário, gostaria de usar técnicas fundamentadas de gerenciamento de tarefas - como Kanban e Mapa mentais - para tornar meu processo de administração de atividades mais eficiente.

- <strong>US03:</strong> Eu, como usuário, gostaria de ser lembrado de visualizar e cumprir minhas tarefas diárias para permanecer motivado ao longo do dia.

- <strong>US04:</strong> Eu, como usuário, gostaria de personalizar minhas visualizações e as funcionalidades da plataforma para tornar minha organização coerente com as minhas preferências e facilidades individuais.

- <strong>US05:</strong> Eu, como usuário, gostaria de monitorar o tempo que gasto com cada tarefa, assim como organizar esses tempos em pastas de áreas personalizadas, para conseguir gerenciar minhas prioridades com mais precisão.  
---

## <a name="c3"></a>3. Projeto da Aplicação Web

### 3.1. Modelagem do banco de dados 

#### 3.1.1. Modelagem Conceitual do banco de dados

<p align = "center">Figura 2: Modelagem Conceitual</p>

<p align="center"> <img src="https://github.com/user-attachments/assets/41af7b94-f344-4228-8d12-22509f936f7e" alt="Modelagem Conceitual"> </p>

<p align = "center">Fonte: material produzido pela autora com o DRAW.io (2025).</p> <br>

#### 3.1.2. Modelagem Relacional do banco de dados

<p align = "center">Figura 3: Modelagem Relacional</p>

<p align="center"> <img src="https://github.com/user-attachments/assets/c9ebc789-acc2-4974-95be-01fb5b2b10fd" alt="Modelagem Conceitual"> </p>

<p align = "center">Fonte: material produzido pela autora com o CANVAS (2025).</p> <br>

#### 3.1.3. Modelagem física com o Schema do banco de dados

```sql
CREATE TABLE usuários (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  usuário TEXT NOT NULL,
  email TEXT NOT NULL,
  senha TEXT NOT NULL,
  telefone INT,
  foto TEXT NOT NULL
);

CREATE TABLE áreas (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  descrição TEXT NOT NULL,
  id_usuário INT REFERENCES usuários(id) ON DELETE CASCADE
);

CREATE TABLE objetivos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  descrição TEXT NOT NULL,
  id_usuário INT REFERENCES usuários(id) ON DELETE CASCADE
);

CREATE TABLE tarefas (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  descrição TEXT NOT NULL,
  tamanho TEXT NOT NULL,
  prioridade TEXT NOT NULL,
  status TEXT NOT NULL,
  data_inicio DATE,
  data_conclusao DATE,
  id_área INT REFERENCES áreas(id) ON DELETE CASCADE,
  id_objetivo INT REFERENCES objetivos(id) ON DELETE CASCADE
);

CREATE TABLE tarefas_objetivos (
  id SERIAL PRIMARY KEY,
  id_tarefa INT REFERENCES tarefas(id) ON DELETE CASCADE,
  id_objetivo INT REFERENCES objetivos(id) ON DELETE CASCADE
);

CREATE TABLE tarefas_áreas (
  id SERIAL PRIMARY KEY,
  id_tarefa INT REFERENCES tarefas(id) ON DELETE CASCADE,
  id_área INT REFERENCES áreas(id) ON DELETE CASCADE
);

CREATE TABLE objetivos_áreas (
  id SERIAL PRIMARY KEY,
  id_área INT REFERENCES áreas(id) ON DELETE CASCADE,
  id_objetivo INT REFERENCES objetivos(id) ON DELETE CASCADE
);
```

#### 3.1.4 BD e Models (Semana 5)
*Descreva aqui os Models implementados no sistema web*

### 3.2. Arquitetura (Semana 5)

*Posicione aqui o diagrama de arquitetura da sua solução de aplicação web. Atualize sempre que necessário.*

**Instruções para criação do diagrama de arquitetura**  
- **Model**: A camada que lida com a lógica de negócios e interage com o banco de dados.
- **View**: A camada responsável pela interface de usuário.
- **Controller**: A camada que recebe as requisições, processa as ações e atualiza o modelo e a visualização.
  
*Adicione as setas e explicações sobre como os dados fluem entre o Model, Controller e View.*

### 3.3. Wireframes (Semana 03 - opcional)

*Posicione aqui as imagens do wireframe construído para sua solução e, opcionalmente, o link para acesso (mantenha o link sempre público para visualização).*

### 3.4. Guia de estilos (Semana 05 - opcional)

*Descreva aqui orientações gerais para o leitor sobre como utilizar os componentes do guia de estilos de sua solução.*


### 3.5. Protótipo de alta fidelidade (Semana 05 - opcional)

*Posicione aqui algumas imagens demonstrativas de seu protótipo de alta fidelidade e o link para acesso ao protótipo completo (mantenha o link sempre público para visualização).*

### 3.6. WebAPI e endpoints (Semana 05)

*Utilize um link para outra página de documentação contendo a descrição completa de cada endpoint. Ou descreva aqui cada endpoint criado para seu sistema.*  

### 3.7 Interface e Navegação (Semana 07)

*Descreva e ilustre aqui o desenvolvimento do frontend do sistema web, explicando brevemente o que foi entregue em termos de código e sistema. Utilize prints de tela para ilustrar.*

---

## <a name="c4"></a>4. Desenvolvimento da Aplicação Web (Semana 8)

### 4.1 Demonstração do Sistema Web (Semana 8)

*VIDEO: Insira o link do vídeo demonstrativo nesta seção*
*Descreva e ilustre aqui o desenvolvimento do sistema web completo, explicando brevemente o que foi entregue em termos de código e sistema. Utilize prints de tela para ilustrar.*

### 4.2 Conclusões e Trabalhos Futuros (Semana 8)

*Indique pontos fortes e pontos a melhorar de maneira geral.*
*Relacione também quaisquer outras ideias que você tenha para melhorias futuras.*



## <a name="c5"></a>5. Referências

_Incluir as principais referências de seu projeto, para que o leitor possa consultar caso ele se interessar em aprofundar._<br>

---
---
