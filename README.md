# Projeto_A3_NoteNest_Main - Notenest: Planner Semanal
Projeto pronto

Descrição:

Esta aplicação React oferece uma interface simples para gerenciar tarefas diárias. Organize suas atividades por dia da semana, adicione lembretes e atribua categorias personalizadas a cada tarefa.

🔧 Funcionalidades:
- Criar Lembretes;
- Selecionar uma categoria para cada lembrete;
- Apagar lembretes;



Requisitos:
- Node.Js v20.9.0;
- npm v10.2.4;
- React;
- Axios;
- MYSQL;
- Docker;

🛠️ Passo a Passo para rodar o projeto

Front:
- Abra o terminal (ctrl+shift+T);
- Clone este repositório em seu ambiente local: https://github.com/Projeto-A3-NoteNest/Projeto_A3_NoteNest_Main.git;
- Acesse o diretório do projeto utilizando o comando cd [caminho-do-diretorio];
- Instale as dependências do projeto usando npm install;
- Após a instalação das dependências, você pode iniciar o servidor de desenvolvimento. No diretório do projeto, execute: "npm start";
- Isso iniciará o aplicativo em um servidor local e abrirá automaticamente uma nova janela do navegador. Se isso não acontecer, você pode acessar http://localhost:3001 em seu navegador;

Back:

1) No cmd, colocar o seguinte código: docker run -d -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3.12-management;
2) Verificar no package.json na parte de dependências, está: "amqplib": "0.10.3" para o funcionamento do barramento;
3) No terminal, é preciso dar um npm install, para instalar as dependências do projeto e depois um npm start para ele rodar;
4) Alterar, caso necessário a porta de conexão com o MYSQL, na configuração do banco de dados, para a porta necessária;
5) Para fazer um teste de rotas no Postman, se coloca a rota desejada, por exemplo no caso de criar um lembrete: "POST: localhost:3000/lembretes". (Sendo 3000 a porta de Lembretes e 5000 a porta de Observações);
6) No terminal da IDE, vai aparecer "publishing", singificando que a rota desejada foi colocada na fila do barramento, no seguinte endereço: localhost:15672;
7) Em relação ao MYSQL, utilize os seguintes códigos:
   
CREATE database notenest;

USE notenest;

CREATE TABLE lembretes ( id_lembrete BIGINT auto_increment PRIMARY KEY, nome_lembrete VARCHAR(255) NOT NULL, dia_semana VARCHAR(20) NOT NULL, concluido BOOLEAN DEFAULT FALSE, data_lembrete DATE, categoria VARCHAR(36) );

CREATE TABLE observacoes ( id_obs BIGINT auto_increment PRIMARY KEY, texto TEXT, id_lembrete BIGINT, FOREIGN KEY (id_lembrete) REFERENCES lembretes(id_lembrete) );






  


