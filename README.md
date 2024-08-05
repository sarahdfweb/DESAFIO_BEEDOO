# DESAFIO_BEEDOO

## Desafio Beedoo QA


<details><summary><b> 📒 User Story Cadastrar Cursos </b></summary>
    
<br>

Título: Cadastrar Cursos  

<br>
Como um administrador do sistema, eu quero cadastrar cursos, para que eu possa gerenciar os cursos disponíveis para os alunos.


## Critérios de Aceitação:
<br>

1. O formulário de cadastro de curso deve incluir os seguintes campos obrigatórios: Nome do curso, Descrição do curso, Instrutor, URL da imagem de capa, Data de início, Data de fim, Número de vagas, Tipo de curso e Link de Inscrição.
2. O campo "Nome do curso" deve permitir a inserção de até 100 caracteres.
3. O campo "Descrição do curso" deve permitir a inserção de até 1000 caracteres.
4. O campo "Instrutor" deve permitir a inserção de até 100 caracteres.
5. O campo "URL da imagem de capa" deve validar se a URL inserida está no formato correto.
6. Os campos "Data de início" e "Data de fim" devem aceitar datas válidas no formato dd/mm/aaaa podendo o usuário selecionar a data desejada.
7. Os botões “Limpar” dos campos “Data de início” e “Data de fim” devem limpar o campo “Data”.
8. Os botões “Hoje” dos campos “Data de início” e “Data de fim” devem inserir a data do dia atual.
9. O campo "Número de vagas" deve aceitar apenas números inteiros positivos.
10. O campo "Tipo de curso" deve ser um dropdown com opções predefinidas (Presencial ou Online).
11. Ao clicar no botão "Cadastrar", se todos os campos forem preenchidos corretamente, o curso deve ser salvo e o usuário deve ser redirecionado para a página de listagem de cursos.
12. Se houver algum erro no preenchimento dos campos, mensagens de erro apropriadas devem ser exibidas ao usuário.

</details>

<details><summary><b>📋 Caso de Teste para Cadastro de Cursos</b></summary>

<br>

**Identificador**: TC001  
**Título**: Cadastro de Curso com Sucesso  
**Descrição**: Verificar se é possível cadastrar um novo curso com todos os campos preenchidos corretamente.  
**Pré-condições**: O usuário deve estar logado e na página de cadastro de curso.  

**Passos**:
1. Navegar até a página de cadastro de curso.
2. Preencher o campo "Nome do curso" com "Python".
3. Preencher o campo "Descrição do curso" com "Seja um Desenvolvedor Web Profissional com Python e Django".
4. Preencher o campo "Instrutor" com "João Silva".
5. Preencher o campo "URL da imagem de capa" com "https://creative-sherbet-a51eac.netlify.app/".
6. Preencher o campo "Data de início" com "01/09/2024".
7. Preencher o campo "Data de fim" com "30/09/2024".
8. Preencher o campo "Número de vagas" com "100".
9. Selecionar "Online" no campo "Tipo de curso".
10. Link de Inscrição.
11. Clicar no botão "Cadastrar".

**Dados de Teste**:
- Nome do curso: "Python"
- Descrição do curso: "Seja um Desenvolvedor Web Profissional com Python e Django"
- Instrutor: "João Silva"
- URL da imagem de capa: "https://creative-sherbet-a51eac.netlify.app/"
- Data de início: "01/09/2024"
- Data de fim: "30/09/2024"
- Número de vagas: "100"
- Tipo de curso: "Online"
- URl da inscrição: https://creative-sherbet-a51eac.netlify.app/python

**Resultado Esperado**: O curso é salvo com sucesso, o usuário é redirecionado para a página de listagem de cursos e uma mensagem de sucesso é exibida.  
**Resultado Real**: ()  
**Status**: (Passou/Falhou)  
**Notas/Comentários**: ()

</details>

<details><summary><b>🎯 Cenário de Teste em BDD Cadastro de Cursos</b></summary>

```
Funcionalidade: Cadastrar Cursos
  Como um administrador do sistema
  Eu quero cadastrar cursos
  Para que eu possa gerenciar os cursos disponíveis para os alunos

Contexto dos cenários: Dado que estou na página de cadastro de curso

  Cenário 001: Cadastro de Curso com Sucesso
    Quando preencho todos os campos obrigatórios corretamente
      | Nome do curso        | Python                                                    |
      | Descrição do curso   | Seja um Desenvolvedor Web Profissional com Python e Django|
      | Instrutor            | João Silva                                                |
      | URL da imagem de capa| https://creative-sherbet-a51eac.netlify.app/              |
      | Data de início       | 01/09/2024                                                |
      | Data de fim          | 30/09/2024                                                |
      | Número de vagas      | 100                                                       |
      | Tipo de curso        | Online                                                    |
      | link de inscrição    | https://creative-sherbet-a51eac.netlify.app/python        |
    E clico no botão "Cadastrar"
    Então o curso deve ser salvo
    E devo ser redirecionado para a página de listagem de cursos
    E uma mensagem de sucesso deve ser exibida

  Cenário 002: Falha no Cadastro por Campos Obrigatórios em Branco
    Quando deixo todos os campos em branco
    E clico no botão "Cadastrar"
    Então mensagens de erro indicando que os campos são obrigatórios devem ser exibidas

  Cenário 003: Falha no Cadastro por Limite de Caracteres no Nome do Curso
    Quando preencho o campo "Nome do curso" com um texto de mais de 100 caracteres
      | Nome do curso |
      | Curso com nome muito longo que excede o limite de cem caracteres permitido no campo nome do curso |
    E preencho os demais campos corretamente
    E clico no botão "Cadastrar"
    Então uma mensagem de erro indicando que o nome do curso não pode exceder 100 caracteres deve ser exibida

  Cenário 004: Falha no Cadastro por URL da Imagem de Capa Inválida
    Quando preencho o campo "URL da imagem de capa" com um texto não formatado como URL
      | https://creative-sherbet-a51eac.netlify.app/xxx   |
      | https://creative-sherbet-a51eac.netlify.app/yyyy |
    E preencho os demais campos corretamente
    E clico no botão "Cadastrar"
    Então uma mensagem de erro indicando que a URL da imagem de capa não é válida deve ser exibida

  Cenário 005: Falha no Cadastro por Datas Inválidas
    Quando preencho os campos "Data de início" e "Data de fim" com datas em formatos inválidos
      | Data de início | Data de fim |
      | 32/13/2024     | 45/09/2024  |
    E preencho os demais campos corretamente
    E clico no botão "Cadastrar"
    Então mensagens de erro indicando que as datas devem estar no formato dd/mm/aaaa devem ser exibidas

  Cenário 006: Falha no Cadastro por Número de Vagas Inválido
    Quando preencho o campo "Número de vagas" com um valor não numérico ou negativo
      | Número de vagas |
      | -10             |
    E preencho os demais campos corretamente
    E clico no botão "Cadastrar"
    Então uma mensagem de erro indicando que o número de vagas deve ser um número inteiro positivo deve ser exibida

  Cenário 007: Uso do Botão "Limpar" para Data de Início
    Quando preencho o campo "Data de início" e "Data fim" com "01/09/2024"
    E clico no botão "Limpar" no campo "Data de início" e "Data fim"
    Então o campo "Data de início" deve estar vazio

  Cenário 008: Uso do Botão "Hoje" para Data de Início
    Quando clico no botão "Hoje" no campo "Data de início" e "Data fim"
    Então o campo "Data de início" e "Data fim" deve ser preenchido com a data atual

  Cenário 009: Seleção do Tipo de Curso
    Quando seleciono "Online" no campo "Tipo de curso"
    Então o campo "Tipo de curso" deve estar preenchido com "Online"


Cenário 010: Link de inscrição
    Quando digito o  "Link de incrição" inválido
    Então deverá ser exibido uma mensagem de erro: "URL inválida"

  Cenário 011: Cadastro de Curso com Sucesso e Verificação na Listagem
    Quando preencho todos os campos obrigatórios corretamente
      | Nome do curso        | Python                                       |
      | Descrição do curso   | Curso para testar o cadastro                |
      | Instrutor            | João Silva                                  |
      | URL da imagem de capa| https://creative-sherbet-a51eac.netlify.app/|
      | Data de início       | 01/09/2024                                  |
      | Data de fim          | 30/09/2024                                  |
      | Número de vagas      | 100                                         |
      | Tipo de curso        | Online                                      |
      |link de inscrição     |https://creative-sherbet-a51eac.netlify.app/python|
    E clico no botão "Cadastrar"
    Então o curso deve ser salvo
    E devo ser redirecionado para a página de listagem de cursos
    E uma mensagem de sucesso deve ser exibida
    E o curso "Python" deve estar visível na listagem de cursos

```
</details>

<details><summary><b>📚 User Story Lista de  Cursos </b></summary>
    
<br>

Título: Visualizar e Gerenciar Lista de Cursos
Como um administrador do sistema
Eu quero visualizar e gerenciar a lista de cursos
Para que eu possa ver os detalhes dos cursos disponíveis e realizar ações administrativas

## Critérios de Aceitação:

1. A lista de cursos deve exibir todos os cursos disponíveis.
2. Cada curso deve exibir as seguintes informações:
3. Nome do Curso
4. Descrição do Curso
5. Tipo de Curso
6. Data de Início
7. Data de Fim
8. Quantidade de Vagas
9. Instrutor
10. Deve ser possível excluir um curso da lista.

</details>


<details><summary><b>📋 Caso de Teste Listas de Cursos Cadastrados</b></summary>

<br>

### Identificador: TC004
**Título**: Visualização dos Cursos  
**Descrição**: Verificar se a lista de cursos exibe todos os cursos disponíveis com os detalhes corretos.  
**Pré-condições**: O administrador deve estar logado e na página de listagem de cursos.

**Passos**:
1. Navegar até a página de listagem de cursos.
2. Verificar se todos os cursos estão sendo exibidos.
3. Verificar se cada curso exibe as seguintes informações:
    - Nome do Curso
    - Descrição do Curso
    - Tipo de Curso
    - Data de Início
    - Data de Fim
    - Quantidade de Vagas
    - Instrutor
    - Excluir

**Dados de Teste**:
- **Nome do Curso**: "Curso Python"
- **Descrição do Curso**: "Descrição do Curso A"
- **Tipo de Curso**: "Online"
- **Data de Início**: "01/08/2024"
- **Data de Fim**: "31/08/2024"
- **Quantidade de Vagas**: "30"
- **Instrutor**: "Denis"
- **Botão**: "Excluir"


**Resultado Esperado**:
- A lista de cursos é exibida corretamente com todas as informações.

**Resultado Real**: (A ser preenchido durante a execução do teste)  
**Status**: (Passou/Falhou)  
**Notas/Comentários**: (Qualquer observação adicional)

</details>

<details><summary><b>🎯 Cenário de Teste em BDD Listas de Cursos Cadastrados </b></summary>

```
Funcionalidade: Visualizar e Gerenciar Lista de Cursos
  Como um administrador do sistema
  Eu quero visualizar e gerenciar a lista de cursos
  Para que eu possa ver os detalhes dos cursos disponíveis e realizar ações administrativas

Contexto dos cenários: Dado que estou na página de listagem de cursos

  Cenário 012: Visualização e Ordenação dos Cursos

    Quando visualizo a lista de cursos
    Então devo ver todos os cursos disponíveis
    E cada curso deve exibir as seguintes informações:
      | Nome do Curso      | Descrição do Curso                          | Tipo de Curso | Data de Início | Data de Fim | Quantidade de Vagas    |Instrutor|
      | Curso Python       | Descrição do Curso A                        | Online        | 01/08/2024      | 31/08/2024   | 30                   |Denis    |
      | Curso QA           | Descrição do Curso B                        | Presencial    | 01/09/2024      | 30/09/2024   | 25                   |Sarah    |
  
 Cenário 013: Exclusão de Curso
  Quando clico no botão "Excluir" ao lado de um curso
  Então o curso deve ser removido da lista
  E eu não devo ver mais o curso na lista de cursos

```
</details>

<details><summary><b> 📒 User Story Trilha de Acesso </b></summary>
    
<br>

Título: Gerenciar Cursos

<br>

Como um administrador do sistema, eu quero listar e cadastrar cursos, para que eu possa gerenciar as opções disponíveis para os alunos de forma eficiente.
<br>

## Critérios de Aceitação:

1. O administrador deve ser capaz de acessar a página de acesso correspondente através da trilha de acesso.

</details>

</details>

<details><summary><b>📋 Caso de Teste Trilha de Acesso</b></summary>

### Identificador: TC008
**Título**: Navegação via Trilha de Acesso  
**Descrição**: Verificar se o administrador pode acessar as páginas de listagem e cadastro de cursos a partir das trilhas de acesso.  
**Pré-condições**: O administrador deve estar logado no sistema e pode estar na página de listagem ou na página de cadastro de cursos.

**Passos**:
1. **Se estiver na página de listagem de cursos:**
   - Clique na trilha de acesso "Cadastrar Cursos".
   - Verifique se o administrador é direcionado para a página de cadastro de cursos.

2. **Se estiver na página de cadastro de cursos:**
   - Clique na trilha de acesso "Listar Cursos".
   - Verifique se o administrador é direcionado para a página de listagem de cursos.

**Dados de Teste**:
- Não se aplica dados específicos para este caso de teste.

**Resultado Esperado**:
- Ao clicar na trilha de acesso "Listar Cursos" a partir da página de cadastro de cursos, o administrador deve ser direcionado para a página de listagem de cursos.
- Ao clicar na trilha de acesso "Cadastrar Cursos" a partir da página de listagem de cursos, o administrador deve ser direcionado para a página de cadastro de cursos.

**Resultado Real**: (A ser preenchido durante a execução do teste)  
**Status**: (Passou/Falhou)  
**Notas/Comentários**: (Qualquer observação adicional)


</details>

<details><summary><b>🎯 Cenário de Teste em BDD Trilha de Acesso </b></summary>
    
```
Funcionalidade: Acessar a Trilha de Acesso
  Como um administrador do sistema
  Eu quero acessar a tela de cadastro ou de listar cursos 
  Para que eu possa ver os detalhes dos cursos disponíveis e realizar ações administrativas

Contexto dos cenários: Dado que estou na página de listagem ou de cadastro de cursos

  Cenário 014: Navegação entre as Telas de Cadastro e Listagem de Cursos
    Quando clico na trilha de acesso "Listar Cursos"
    Então sou direcionado para a página de listagem de cursos

    Quando clico na trilha de acesso "Cadastrar Cursos"
    Então sou direcionado para a página de cadastro de cursos

```
</details>

<details><summary><b> 🚀 Planilha de Excel</b></summary>

📎 [Planilha de teste.xlsx](https://github.com/user-attachments/files/16489253/Planilha.de.teste.xlsx)

</details>

<details><summary><b>🐞 Bugs</b></summary>
    
### Erro de exclusão
 
Descrição do Erro
   
Código do Erro: 405 

Mensagem: Method Not Allowed
Contexto: Ocorreu ao tentar excluir um curso.
 
https://github.com/user-attachments/assets/21844cbc-f2ec-49c6-914a-ec57bd781f20


### Permitindo cadastrar cursos com todo campo em branco

Código do Erro: 404 

Mensagem: O recurso solicitado não foi encontrado no servidor.
Contexto: Ocorreu ao tentar cadastrar um curso com campos em branco



https://github.com/user-attachments/assets/27e2082a-bd87-493e-b0b6-2b25fd8af9c4



### Data inválida

Aceitando datas idênticas de iníco e fim e inválida

![image](https://github.com/user-attachments/assets/3254ad20-4c89-4e36-b0e6-bd0913fa4a53)


https://github.com/user-attachments/assets/6098fa2b-cbe8-439c-a4e4-0faa3a843968

### Relatório dos bugs

📎[Relatório_Beedoo.docx](https://github.com/user-attachments/files/16489457/Relatorio_Beedoo.docx)


</details>

<details><summary><b>🧐Vunerabilidades </b></summary>



## Vulnerabilidades Identificadas

Durante os testes da funcionalidade de criação de cursos, foram encontrados os seguintes problemas:

- **URLs Inválidas:** O sistema permite o cadastro de URLs inválidas, o que pode resultar em links quebrados.
- **Formulário em Branco:** É possível cadastrar um curso mesmo sem preencher todos os campos obrigatórios, o que pode levar a dados incompletos.
- **Validação de Dados:** O sistema não valida adequadamente os dados inseridos, permitindo informações incorretas.


## Situação hipotética

### Pontos Críticos a Esclarecer Antes dos Testes
Antes de começar a testar a nova funcionalidade de cadastro de cursos, preciso  esclarecer os seguintes pontos com a equipe:

1.Como os Dados Devem Ser Validados? Quais regras devem ser seguidas para garantir que as informações inseridas (como URLs e campos obrigatórios) estejam corretas?

2.Como Deve Ser a Navegação? O processo de cadastro de cursos será dividido em etapas ou abas? Qual deve ser o fluxo de navegação para tornar o processo claro e organizado?

3. O Que Fazer em Caso de Erros? Qual é o procedimento para lidar com erros durante o cadastro? Existe uma mensagem de erro padrão ou uma maneira específica de tratar falhas?

### Próximos Passos
* Conversar com a Equipe: Marcar uma reunião para discutir essas questões e garantir que todos os detalhes estejam claros.
* Atualizar Documentação: Certificar-se de que todas as regras e detalhes sobre o cadastro estejam bem documentados.
Preparar Testes: Criar e executar testes com base nas informações obtidas para garantir que tudo funcione conforme o esperado.

### Como Saber se um Erro é Causado pela Nova Funcionalidade


Reproduzir o Erro:

Testo a feature, executo os testes conforme os critérios definidos.
Documento o erro, registro o erro com detalhes sobre como e onde ele ocorre.

Verifico o Escopo da Feature:

Preciso entender a feature: Conheçer as funcionalidade que está sendo testada e quais áreas do sistema ela deve impactar.
Reviso a documentação: Confirindo a documentação da feature para entender como ela deve funcionar.

</details>







