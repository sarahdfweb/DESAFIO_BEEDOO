# DESAFIO_BEEDOO

## Desafio Beedoo QA


<details><summary><b> 📒 User Story Cadastrar Cursos </b></summary>
    
<br>

**Título**: Cadastrar Cursos  

<br>
Como um administrador do sistema, eu quero cadastrar cursos, para que eu possa gerenciar os cursos disponíveis para os alunos.

**Critérios de Aceitação**:
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

```gherkin
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

**Título**: Lista de Cursos Cadastrados

Como um aluno interessado, eu quero visualizar a lista de cursos disponíveis, para que eu possa escolher e me inscrever em um curso de meu interesse.

Critérios de Aceitação:

A lista de cursos deve exibir todos os cursos disponíveis.
Cada curso deve exibir as seguintes informações: Nome do Curso, Descrição do Curso, Instrutor, Tipo de Curso (Online ou Presencial).
Os cursos devem ser ordenados alfabeticamente pelo Nome do Curso.
Deve ser possível filtrar os cursos pelo Tipo (Online ou Presencial).
Ao clicar no nome do curso, o usuário deve ser redirecionado para a página de detalhes do curso.
Caso de Teste para Tela de Lista de Cursos
Identificador: TC002
Título: Visualizar Lista de Cursos
Descrição: Verificar se a lista de cursos é exibida corretamente com todas as informações necessárias e funcionalidades de filtro.
Pré-condições: O usuário deve estar logado e na página de lista de cursos.
Passos:

Navegar até a página de lista de cursos.
Verificar se todos os cursos disponíveis são exibidos.
Verificar se cada curso exibe Nome do Curso, Descrição do Curso, Instrutor e Tipo de Curso.
Verificar se os cursos estão ordenados alfabeticamente pelo Nome do Curso.
Selecionar o filtro "Online" e verificar se apenas os cursos online são exibidos.
Selecionar o filtro "Presencial" e verificar se apenas os cursos presenciais são exibidos.
Clicar no nome de um curso e verificar se o usuário é redirecionado para a página de detalhes do curso.
Dados de Teste:

Tipos de cursos disponíveis: Online, Presencial
Nome de um curso específico para verificação de redirecionamento: "Python"
Resultado Esperado:

A lista de cursos deve exibir todos os cursos disponíveis com as informações corretas.
Os cursos devem estar ordenados alfabeticamente pelo Nome do Curso.
Os filtros devem funcionar corretamente, exibindo apenas os cursos do tipo selecionado.
O usuário deve ser redirecionado corretamente para a página de detalhes do curso ao clicar no nome do curso.
Resultado Real: (A ser preenchido durante a execução do teste)
Status: (Passou/Falhou)
Notas/Comentários: (Qualquer observação adicional)

</details>
</details>

<details><summary><b>📋 Caso de Teste Listas de Cursos Cadastrados</b></summary>

<br>

</details>

<details><summary><b>🎯 Cenário de Teste em BDD Listas de Cursos Cadastrados </b></summary>

```gherkin






