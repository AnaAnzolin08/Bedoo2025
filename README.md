# # User Stories - Módulo de Cursos – (Estudante)
## US001: Visualizar Cursos Disponíveis
**Como** um estudante  
**Eu quero** visualizar uma lista de todos os cursos disponíveis  
**Para que** eu possa escolher qual curso me interessa
--
## US002: Detalhes do Curso
**Como** um estudante  
**Eu quero** ver os detalhes completos de um curso (descrição, módulos, pré-requisitos, etc.)  
**Para que** eu possa tomar uma decisão informada sobre a inscrição.
---

## US003: Inscrição em Curso
**Como** um estudante  
**Eu quero** me inscrever em um curso  
**Para que** eu possa iniciar meus estudos e acompanhar meu progresso.
## US004: Acompanhar Progresso do Curso
**Como** um estudante  
**Eu quero** acompanhar meu progresso em um curso  
**Para que** eu possa saber quais módulos já completei e quais ainda preciso fazer.
## US005: Concluir Módulo/Curso
**Como** um estudante  
**Eu quero** marcar um módulo ou curso como concluído  
**Para que** eu possa registrar meu avanço e obter certificação, se aplicável.

**Então a**

Como instrutor- Funcionalidade 
Quero cadastrar novos cursos
Para que eles fiquem disponíveis na lista de cursos

## US002-1- Cadastro de um novo curso
Dado que estou na página de cadastro de cursos
Quando eu preencho o campo "Título" com "Curso de Teste E2E"
E clico no botão "Salvar"
Então o curso "Curso de Teste E2E" deve aparecer na lista de cursos

## US002-3 Visualização da lista de cursos
Dado que existem cursos cadastrados
Quando eu acesso a página de listagem de cursos
Então devo ver os títulos e descrições dos cursos cadastrados


Instrutor - Funcionalidade de criar Cadastro 

Cenário 1: Cadastro de Curso com Sucesso 
Dado que eu sou um instrutor logado no sistema
E eu estou na página de "Cadastro de Novo Curso"
Quando eu preencho todos os campos obrigatórios com informações válidas:
| Campo | Valor |
| :---------------- | ----------------------------- |
| Nome do Curso | "Desenvolvimento Ágil com Scrum" |
| Descrição | "Aprenda Scrum na prática para projetos de sucesso." |
| Categoria | "Metodologias Ágeis" |
| Data de Início | "15/03/2025" |
| Data de Fim | "15/04/2025" |
| Número de Vagas | 30 |
E eu clico no botão "Salvar"
Então o sistema deve exibir a mensagem "Curso cadastrado com sucesso!"
E o curso "Desenvolvimento Ágil com Scrum" deve aparecer na minha lista de cursos
E o curso deve estar disponível para alunos visualizarem
________________________________________
Cenário 2: Tentativa de Cadastro com Campos Obrigatórios Ausentes
Dado que eu sou um instrutor logado no sistema
E eu estou na página de "Cadastro de Novo Curso"
Quando eu preencho apenas o "Nome do Curso" com "Curso sem Data"
E eu deixo os campos "Data de Início", "Data de Fim" e "Número de Vagas" vazios
E eu clico no botão "Salvar"
Então o sistema deve impedir o cadastro do curso
E o sistema deve exibir mensagens de erro para cada campo obrigatório não preenchido
E os campos "Data de Início", "Data de Fim" e "Número de Vagas" devem ser destacados visualmente como erro
________________________________________
Cenário 3: Validação de Datas (Data Fim anterior à Data Início)
Dado que eu sou um instrutor logado no sistema
E eu estou na página de "Cadastro de Novo Curso"
Quando eu preencho o "Nome do Curso" com "História Invertida"
E eu preencho a "Data de Início" com "01/06/2025"
E eu preencho a "Data de Fim" com "01/05/2025" (anterior à Data de Início)
E eu preencho o "Número de Vagas" com "20"
E eu clico no botão "Salvar"
Então o sistema deve impedir o cadastro do curso
E o sistema deve exibir a mensagem de erro "A Data de Fim não pode ser anterior à Data de Início."
E os campos "Data de Início" e "Data de Fim" devem ser destacados visualmente como erro
________________________________________
Cenário 4: Validação de Número de Vagas (Valor Inválido)
Dado que eu sou um instrutor logado no sistema
E eu estou na página de "Cadastro de Novo Curso"
Quando eu preencho todos os campos obrigatórios com informações válidas
E eu preencho o campo "Número de Vagas" com um valor inválido (ex: 100000" ou "1")
E eu clico no botão "Salvar"
Então o sistema deve impedir o cadastro do curso
E o sistema deve exibir uma mensagem de erro "O Número de Vagas deve ser um inteiro positivo." (ou similar)
E o campo "Número de Vagas" deve ser destacado visualmente como erro
________________________________________
Cenário 5 : Cadastro de curso com nome duplicado
Dado que já existe um curso cadastrado com o mesmo nome pelo instrutor
Quando o usuário tenta cadastrar outro curso com o mesmo nome
E clica em "Cadastrar"
Então o sistema deve exibir a mensagem "Já existe um curso com este nome"
E não deve permitir o cadastro duplicado

Funcionalidade: Gerenciar lista de cursos

Como um usuário do sistema QA 
Quero visualizar, editar e excluir cursos
Para que eu possa manter a lista de cursos atualizada
________________________________________
Contexto:
Dado que estou na página "Lista de cursos"
________________________________________
Cenário: Visualizar lista de cursos disponíveis
Quando a página é carregada
Então deve ser exibido o título "Lista de cursos"
E cada curso deve estar representado em um card
E cada card deve exibir os seguintes detalhes:
| Modalidade | Online |
| Nome | Quality assurance |
| Descrição | qualidade de teste de software |
| Início | 2025-11-03 |
| Fim | 2025-11-10 |
| Vagas | texto "10" |
E cada card deve possuir os seguintes botões:
| Botão  =Editar CURSO || EXCLUIR CURSO |
________________________________________
Cenário: Editar informações de um curso
Dado que há um curso exibido na lista (ex: "Quality assurance")
Quando clico no botão "EDITAR CURSO" do curso desejado
Então deve ser exibido um formulário de edição do curso
E o formulário deve conter os seguintes campos preenchidos com os dados atuais do curso:
| 
| Nome Quality assurence 
| Descrição |qualidade de software 
| Modalidade |online 
| Início |12-11-2025
| Fim |
| Vagas |
Quando atualizo as informações do curso (ex: "Vagas" para "25")
E clico no botão "Salvar"
Então as informações do curso devem ser atualizadas na lista (ex: "VAGAS"  do curso passa a ser "25")
E uma mensagem de sucesso "Curso atualizado com sucesso!" (ou similar) deve ser exibida
________________________________________
Cenário: Excluir um curso da lista
Dado que há um curso exibido na lista (ex: "Quality assurance")
Quando clico no botão "EXCLUIR CURSO"
Então o sistema deve solicitar confirmação da exclusão com uma caixa de diálogo
E ao confirmar (clicar em "Sim" ou "Confirmar" na caixa de diálogo), o curso deve ser removido da lista
E uma mensagem de sucesso "Curso excluído com sucesso!" (ou similar) deve ser exibida
E o curso "Quality assurance" não deve mais aparecer na lista de cursos
