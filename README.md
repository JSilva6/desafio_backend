## Contextualização
Nossa plataforma é responsável por armazenar e preencher formulários, mantendo os resultados num banco de dados.

## Definição
### Checklist
- Um checlist é a entidade que representa um modelo de formulário
- Um exemplo de checklist seria:
```json
{
  "id": "411594b5-c996-4756-a719-408dd4517161",
  "name": "Inspeção",
  "created_at": 1634083200000,
  "items": {
    "1e31c245-c2ea-4f26-8db8-c8f468ed8a4f": {
      "subject": "Situação de Limpeza"
    },
    "57882cad-7612-4e21-a62b-bd155c0b1d75": {
      "subject": "Necessidade de Manutenção?"
    },
    "1acfc695-e2c9-4586-b104-b870ba3c9b53": {
      "subject": "Estado dos Procedimentos"
    }
  }
}
```
Onde:
- `id` é um UUID v4;
- `name` é o nome do checklist;
- `created_at` é um timestamp em milissegundos;
- `items` é um conjunto de objetos, onde esses objetos devem conter apenas o atributo `subject` com o enunciado da pergunta e sua key deve ser um UUID v4 próprio;
### Histórico
- Um histórico é a entidade que representa o preenchimento de um checklist
- Um exemplo de histórico seria:
```json
{
  "id": "511594b8-c322-4732-a712-438dd4517938",
  "checklist": "411594b5-c996-4756-a719-408dd4517161",
  "created_at": 1634169600000,
  "data": {
    "1e31c245-c2ea-4f26-8db8-c8f468ed8a4f": {
      "answer": "Limpo"
    },
    "57882cad-7612-4e21-a62b-bd155c0b1d75": {
      "answer": "Não"
    },
    "1acfc695-e2c9-4586-b104-b870ba3c9b53": {
      "answer": "Normal"
    }
  }
}
```
Onde:
- `id` é um UUID v4;
- `created_at` é um timestamp em milissegundos;
- `checklist` é o UUID referente ao checklist ao qual foi respondido;
- `data` é um conjunto de objetos, onde esses objetos devem conter apenas o atributi `answer`, que deve conter a resposta da pergunta com a mesma key.

## Desafios
### Criar um endpoint para cadastrar novos Formulários
Neste desafio, será necessário criar um endpoint para cadastro de novos formulários, e eles não podem ser substituidos ou alterados.

Requisição: POST `/register_checklist`

### Criar um endpoint para responder Formulários
Neste desafio, será necessário criar um endpoint para resposta de formulários, contendo apenas os dados das respostas.

Requisição: POST `/answer/{checklist_id}`

### Criar um endpoint para listar Históricos
Nessa parte do desafio, será necessário criar um endpoint para listar respostas de formulários. Será retornado os respostas realizadas entre um período, definido pelos parametros `start_date` e `end_date`, que devem ser timestamps em milissegundos, e devem dizer respeito apenas a um tipo de formulário.

Requisição: GET `/history/{checklist_id}`

### Criar um endpoint para deletar Checklists
Nessa parte do desafio, será necessário criar um endpoint para marcar um formulário como deletado. Formulários deletados não devem ser apagados do banco, mas sim receber o atributo `deleted_at` que deve ser um timestamp em milissegundos. Note que formulários deletados não podem receber novas respostas.

Requisição: DELETE `/remove`

## Requisitos
- TypeScript;
- Node.js;
- Banco de dados não-relacional, preferencialmente firebase;
## Diferenciais
- ORM;
## Entre os critérios de avaliação estão:
- Código limpo e organização;
- Documentação do projeto (readme);
- Performance;
- Detalhamento;
## Como devo entregar o desafio?
- Clone o repositório (não forke);
- Suba o projeto para seu repositório
- Nos envie o link do repositório.
- Envie um e-mail para [juliano.silva@systemsmobile.com.br](mailto:juliano.silva@systemsmobile.com.br), com o assunto '\[Teste Dev\] Desafio';
## Dúvida
Se tiver qualquer dúvida sobre esse teste, envie um e-mail com o título '\[Teste Dev\] Dúvida' para [juliano.silva@systemsmobile.com.br](mailto:juliano.silva@systemsmobile.com.br)
Boa sorte! 🍀
