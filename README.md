# Serveless-framework-desafio

Certo! Para dar os primeiros passos com Serverless e Infraestrutura como Código (IaC) utilizando o **Serverless Framework na AWS, vamos seguir um guia básico. Aqui estão os passos que você pode seguir para replicar uma solução simples:

# 1. Pré-requisitos

- Node.js: Certifique-se de ter o Node.js instalado em sua máquina.
- AWS CLI: Instale e configure a AWS Command Line Interface.
- Serverless Framework: Instale o Serverless Framework globalmente:
  ```bash
  npm install -g serverless
  ```

# 2. Criar um Novo Servidor Serverless

1. Criar um novo projeto:
   ```bash
   serverless create --template aws-nodejs --path my-service
   cd my-service
   ```

2. *Instalar dependências (se necessário):
   - Por exemplo, se você for usar o Express.js:
     ```bash
     npm init -y
     npm install express serverless-http
     ```

# 3. Configurar `serverless.yml`

Abra o arquivo `serverless.yml` e configure a função que sua aplicação vai usar. Um exemplo básico poderia ser:

```yaml
service: my-service

provider:
  name: aws
  runtime: nodejs14.x

functions:
  hello:
    handler: handler.hello
    events:
      - http:
          path: hello
          method: get
```

# 4. Criar o Manipulador

Edite o arquivo `handler.js` para incluir a função que será chamada:

```javascript
'use strict';

module.exports.hello = async (event) => {
  return {
    statusCode: 200,
    body: JSON.stringify({
      message: 'Hello from Serverless!',
      input: event,
    }),
  };
};
```

# 5. Implantar no AWS

Para implantar seu serviço na AWS, use o seguinte comando:

```bash
serverless deploy
```

# 6. Testar a Função

Após a implantação, você verá a URL de endpoint da função em sua saída. Você pode testá-la usando um navegador ou ferramentas como Postman ou Curl:

```bash
curl https://your-api-id.execute-api.region.amazonaws.com/dev/hello
```

# 7. Limpeza

Para remover o serviço que você criou e não ter custos em sua conta da AWS:

```bash
serverless remove
```

# Conclusão

Com isso, você deve ter uma implementação básica de uma função Serverless na AWS. Você pode expandir essa solução adicionando mais funções, integrações com bancos de dados, autenticações, etc. 
