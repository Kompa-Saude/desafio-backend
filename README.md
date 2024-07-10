### Desafio Técnico: Implementação de API de Cadastros de Pacientes

Prezado Candidato,

Estamos entusiasmados por tê-lo no nosso processo seletivo para a vaga de Programador Backend Python. Como parte da avaliação técnica, solicitamos que você implemente uma API de cadastros de pacientes utilizando Python, SQLAlchemy e PostgreSQL. A seguir estão os detalhes e requisitos do desafio.

#### Objetivo:
Implementar uma API RESTful para gerenciar cadastros de pacientes com funcionalidades de listagem, criação e edição. Além disso, será necessário manipular e formatar informações para exibição na API de forma diferente das quais estão sendo salvas no banco de dados.

#### Requisitos:

##### Tecnologias:
- **Linguagem:** Python
- **ORM:** SQLAlchemy
- **Banco de Dados:** PostgreSQL
- **Framework:** Flask

##### Funcionalidades da API:
1. **Listar Pacientes**
2. **Criar Paciente**
3. **Editar Paciente**

##### Especificações da API:

###### Entidade Paciente:
- `id` (Integer, Primary Key)
- `name` (String, até 100 caracteres)
- `birth_date` (Date)
- `address` (String, até 200 caracteres)
- `phone` (String, até 15 caracteres)
- `email` (String, até 100 caracteres)
- `medical_history` (Text)

###### Endpoints:
1. **Listar Pacientes**
   - **Endpoint:** `GET /patients`
   - **Descrição:** Retorna uma lista de todos os pacientes cadastrados.
   - **Resposta:** 
     ```json
     [
       {
         "id": 1,
         "name": "John Doe",
         "age": 30,
         "phone": "(11) 98765-4321",
         "email": "john.doe@example.com",
         "last_visit_summary": "Visit on 2023-01-15: General check-up, blood pressure 120/80"
       },
       ...
     ]
     ```
   - **Nota:** 
     - A idade deve ser calculada com base na `birth_date`.
     - O resumo da última visita deve ser construído a partir de um histórico de visitas médicas, contendo a data da última visita e uma breve descrição (assumindo que o histórico de visitas está armazenado em outra tabela).

2. **Criar Paciente**
   - **Endpoint:** `POST /patients`
   - **Descrição:** Cria um novo cadastro de paciente.
   - **Requisição:** 
     ```json
     {
       "name": "Jane Smith",
       "birth_date": "1990-05-15",
       "address": "123 Flower Street",
       "phone": "(11) 91234-5678",
       "email": "jane.smith@example.com",
       "medical_history": "Patient with a history of hypertension."
     }
     ```
   - **Resposta:** 
     ```json
     {
       "id": 2,
       "name": "Jane Smith",
       "birth_date": "1990-05-15",
       "address": "123 Flower Street",
       "phone": "(11) 91234-5678",
       "email": "jane.smith@example.com",
       "medical_history": "Patient with a history of hypertension."
     }
     ```

3. **Editar Paciente**
   - **Endpoint:** `PUT /patients/{id}`
   - **Descrição:** Edita as informações de um paciente existente.
   - **Requisição:** 
     ```json
     {
       "name": "Jane Smith",
       "birth_date": "1990-05-15",
       "address": "456 Rose Street",
       "phone": "(11) 91234-5678",
       "email": "jane.smith@example.com",
       "medical_history": "Patient with a history of hypertension and diabetes."
     }
     ```
   - **Resposta:** 
     ```json
     {
       "id": 2,
       "name": "Jane Smith",
       "birth_date": "1990-05-15",
       "address": "456 Rose Street",
       "phone": "(11) 91234-5678",
       "email": "jane.smith@example.com",
       "medical_history": "Patient with a history of hypertension and diabetes."
     }
     ```

###### Tabela de Visitas Médicas:
- **Entidade Visita:**
  - `id` (Integer, Primary Key)
  - `patient_id` (Integer, Foreign Key para `patients.id`)
  - `visit_date` (Date)
  - `summary` (Text)

- **Exemplo de Registro:**
  ```json
  {
    "id": 1,
    "patient_id": 1,
    "visit_date": "2023-01-15",
    "summary": "General check-up, blood pressure 120/80"
  }
  ```

##### Requisitos Adicionais:
- **Formatação de Dados:** Na listagem de pacientes, exibir a idade calculada a partir da data de nascimento.
- **Manipulação de Dados:** Na listagem de pacientes, incluir um resumo da última visita médica, composto pela data da última visita e uma breve descrição.
- **Organização do Projeto:** O projeto deve ser organizado de maneira clara, seguindo boas práticas de desenvolvimento e estrutura de diretórios.
- **Documentação:** Fornecer um README com instruções sobre como configurar e executar o projeto, bem como exemplos de uso da API.

#### Critérios de Avaliação:
- **Corretude e Funcionalidade:** A API deve atender a todos os requisitos funcionais descritos.
- **Qualidade do Código:** O código deve ser limpo, bem documentado e seguir boas práticas de desenvolvimento.
- **Estrutura do Projeto:** A organização do projeto deve ser clara e modular.
- **Tratamento de Erros:** A API deve lidar adequadamente com possíveis erros e exceções.
- **Performance:** A API deve ser eficiente no processamento das requisições.

#### Submissão:
- Envie o link para o repositório do GitHub com o código do projeto.
- Inclua instruções claras sobre como configurar e executar a aplicação.

Estamos ansiosos para ver sua solução e discutir os resultados na próxima etapa.
