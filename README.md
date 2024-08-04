# DESAFIO_BEEDOO

## Desafio Beedoo QA


<details><summary><b> 📒 User Story Cadastrar Cursos </b></summary>
    
<br>

Título: Cadastrar Cursos  

<br>
Como um administrador do sistema, eu quero cadastrar cursos, para que eu possa gerenciar os cursos disponíveis para os alunos.


## Critérios de Aceitação:
<br>

1. O formulário de cadastro de curso deve incluir os seguintes campos obrigatórios: Nome do curso, Descrição do curso, Instrutor, URL da imagem de capa, Data de início, Data de fim, Número de vagas e Tipo de curso.
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
10. Clicar no botão "Cadastrar".

**Dados de Teste**:
- Nome do curso: "Python"
- Descrição do curso: "Seja um Desenvolvedor Web Profissional com Python e Django"
- Instrutor: "João Silva"
- URL da imagem de capa: "https://creative-sherbet-a51eac.netlify.app/"
- Data de início: "01/09/2024"
- Data de fim: "30/09/2024"
- Número de vagas: "100"
- Tipo de curso: "Online"

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

  Cenário 1: Cadastro de Curso com Sucesso
    Quando preencho todos os campos obrigatórios corretamente
      | Nome do curso        | Python                                                    |
      | Descrição do curso   | Seja um Desenvolvedor Web Profissional com Python e Django |
      | Instrutor            | João Silva                                                |
      | URL da imagem de capa| https://creative-sherbet-a51eac.netlify.app/              |
      | Data de início       | 01/09/2024                                                |
      | Data de fim          | 30/09/2024                                                |
      | Número de vagas      | 100                                                        |
      | Tipo de curso        | Online                                                    |
    E clico no botão "Cadastrar"
    Então o curso deve ser salvo
    E devo ser redirecionado para a página de listagem de cursos
    E uma mensagem de sucesso deve ser exibida

  Cenário 2: Falha no Cadastro por Campos Obrigatórios em Branco
    Quando deixo todos os campos em branco
    E clico no botão "Cadastrar"
    Então mensagens de erro indicando que os campos são obrigatórios devem ser exibidas

  Cenário 3: Falha no Cadastro por Limite de Caracteres no Nome do Curso
    Quando preencho o campo "Nome do curso" com um texto de mais de 100 caracteres
      | Nome do curso |
      | Curso com nome muito longo que excede o limite de cem caracteres permitido no campo nome do curso |
    E preencho os demais campos corretamente
    E clico no botão "Cadastrar"
    Então uma mensagem de erro indicando que o nome do curso não pode exceder 100 caracteres deve ser exibida

  Cenário 4: Falha no Cadastro por URL da Imagem de Capa Inválida
    Quando preencho o campo "URL da imagem de capa" com um texto não formatado como URL
      | https://creative-sherbet-a51eac.netlify.app/xxx   |
      | https://creative-sherbet-a51eac.netlify.app/yyyy |
    E preencho os demais campos corretamente
    E clico no botão "Cadastrar"
    Então uma mensagem de erro indicando que a URL da imagem de capa não é válida deve ser exibida

  Cenário 5: Falha no Cadastro por Datas Inválidas
    Quando preencho os campos "Data de início" e "Data de fim" com datas em formatos inválidos
      | Data de início | Data de fim |
      | 32/13/2024     | 45/09/2024  |
    E preencho os demais campos corretamente
    E clico no botão "Cadastrar"
    Então mensagens de erro indicando que as datas devem estar no formato dd/mm/aaaa devem ser exibidas

  Cenário 6: Falha no Cadastro por Número de Vagas Inválido
    Quando preencho o campo "Número de vagas" com um valor não numérico ou negativo
      | Número de vagas |
      | -10             |
    E preencho os demais campos corretamente
    E clico no botão "Cadastrar"
    Então uma mensagem de erro indicando que o número de vagas deve ser um número inteiro positivo deve ser exibida

  Cenário 7: Uso do Botão "Limpar" para Data de Início
    Quando preencho o campo "Data de início" e "Data fim" com "01/09/2024"
    E clico no botão "Limpar" no campo "Data de início" e "Data fim"
    Então o campo "Data de início" deve estar vazio

  Cenário 8: Uso do Botão "Hoje" para Data de Início
    Quando clico no botão "Hoje" no campo "Data de início" e "Data fim"
    Então o campo "Data de início" e "Data fim" deve ser preenchido com a data atual

  Cenário 9: Seleção do Tipo de Curso
    Quando seleciono "Online" no campo "Tipo de curso"
    Então o campo "Tipo de curso" deve estar preenchido com "Online"

  Cenário 10: Cadastro de Curso com Sucesso e Verificação na Listagem
    Quando preencho todos os campos obrigatórios corretamente
      | Nome do curso        | Python                                       |
      | Descrição do curso   | Curso para testar o cadastro                |
      | Instrutor            | João Silva                                  |
      | URL da imagem de capa| https://creative-sherbet-a51eac.netlify.app/|
      | Data de início       | 01/09/2024                                  |
      | Data de fim          | 30/09/2024                                  |
      | Número de vagas      | 100                                         |
      | Tipo de curso        | Online                                      |
    E clico no botão "Cadastrar"
    Então o curso deve ser salvo
    E devo ser redirecionado para a página de listagem de cursos
    E uma mensagem de sucesso deve ser exibida
    E o curso "Python" deve estar visível na listagem de cursos

```
</details>

<details><summary><b>📚 User Story Lista de  Cursos </b></summary>
    
<br>

Título: Visualização da Lista de Cursos
Como um aluno, eu quero visualizar a lista de cursos disponíveis, para que eu possa ver os cursos que estão disponíveis para matrícula e obter informações sobre cada um deles.

## Critérios de Aceitação:

A tela de lista de cursos deve exibir todos os cursos disponíveis.
Cada curso deve exibir as seguintes informações:
Nome do Curso
Descrição do Curso
Tipo de Curso (Online ou Presencial)
Data de Início
Data de Fim
Quantidade de Vagas
Deve haver um botão de inscrição ao lado de cada curso para permitir que o aluno se inscreva no curso.



</details>
</details>

<details><summary><b>📋 Caso de Teste Listas de Cursos Cadastrados</b></summary>

<br>

**Identificador**: TC002  
**Título**: Visualização da Lista de Cursos com Detalhes e Ordenação  
**Descrição**: Verificar se a lista de cursos é exibida corretamente com todas as informações necessárias. Também verificar a funcionalidade do botão de inscrição e a exibição dos detalhes do curso.  
**Pré-condições**: O usuário deve estar logado e na página de listagem de cursos.

**Passos**:
1. Navegar até a página de listagem de cursos.
2. Verificar se todos os cursos disponíveis são exibidos na lista.
3. Verificar se cada curso exibe as seguintes informações:
   - Nome do Curso
   - Descrição do Curso
   - Tipo de Curso (Online ou Presencial)
   - Data de Início
   - Data de Fim
   - Quantidade de Vagas
4. Clicar no botão de exclusão ao lado do "Curso B".
5. Confirmar a exclusão do curso.
6. Verificar se o curso "Curso B" foi removido da lista e uma mensagem de sucesso é exibida.
7. Clicar no botão de inscrição ao lado do "Curso A".
8. Verificar se a inscrição foi realizada com sucesso e a página foi atualizada.

**Dados de Teste**:
- Cursos Disponíveis:
  - Nome do Curso: "Curso A"
  - Descrição do Curso: "Descrição do Curso A"
  - Tipo de Curso: "Online"
  - Data de Início: "01/08/2024"
  - Data de Fim: "31/08/2024"
  - Quantidade de Vagas: 30
  - Nome do Curso: "Curso B"
  - Descrição do Curso: "Descrição do Curso B"
  - Tipo de Curso: "Presencial"
  - Data de Início: "01/09/2024"
  - Data de Fim: "30/09/2024"
  - Quantidade de Vagas: 25

**Resultado Esperado**:
- Todos os cursos disponíveis são exibidos na lista com as informações completas.
- O botão de inscrição ao lado do "Curso A" está funcionando corretamente.
- Após clicar no botão de inscrição, o usuário é inscrito no "Curso A" e a página é atualizada com uma mensagem de sucesso.
- Ao visualizar um curso, todos os detalhes do curso são exibidos corretamente.
- O botão de inscrição ao lado do "Curso A" está funcionando corretamente e a inscrição é realizada com sucesso.
- O botão de exclusão ao lado do "Curso B" está funcionando corretamente e o curso é removido da lista.
- Após a exclusão, a página é atualizada com uma mensagem de sucesso e o curso excluído não aparece mais na lista.

**Resultado Real**: ()  
**Status**: (Passou/Falhou)  
**Notas/Comentários**: (l)

</details>



</details>

<details><summary><b>🎯 Cenário de Teste em BDD Listas de Cursos Cadastrados </b></summary>

```
Funcionalidade: Visualização da Lista de Cursos
  Como um aluno
  Eu quero visualizar a lista de cursos disponíveis
  Para que eu possa ver os cursos que estão disponíveis para matrícula e obter informações sobre cada um deles

Contexto dos cenários: Dado que estou na página de listagem de cursos

  Cenário 1: Visualização e Ordenação dos Cursos

    Quando visualizo a lista de cursos
    Então devo ver todos os cursos disponíveis
    E cada curso deve exibir as seguintes informações:
      | Nome do Curso      | Descrição do Curso                          | Tipo de Curso | Data de Início | Data de Fim | Quantidade de Vagas    |
      | Curso Python       | Descrição do Curso A                        | Online        | 01/08/2024      | 31/08/2024   | 30                   |
      | Curso QA           | Descrição do Curso B                        | Presencial    | 01/09/2024      | 30/09/2024   | 25                   |
    E os cursos devem ser ordenados alfabeticamente pelo Nome do Curso

  Cenário 2: Inscrição em Curso
    Dado que existem cursos listados
    Quando clico no botão de inscrição ao lado do "Curso A"
    Então eu devo ser inscrito no "Curso A"
    E a página deve atualizar para mostrar que a inscrição foi realizada com sucesso

  Cenário 3: Visualização de Detalhes dos Cursos
    Quando visualizo um curso na lista
    Então devo ver os detalhes completos do curso
    E esses detalhes devem incluir:
      | Nome do Curso | Descrição do Curso | Tipo de Curso | Data de Início | Data de Fim | Quantidade de Vagas |

 Cenário 4: Exclusão de Curso com Sucesso
    Dado que existem cursos na lista
    Quando clico no botão de exclusão ao lado do "Curso B"
    E confirmo a exclusão do curso
    Então o curso "Curso B" deve ser removido da lista
    E uma mensagem de sucesso deve ser exibida
    E a lista de cursos deve ser atualizada sem o "Curso B"

```
</details>








