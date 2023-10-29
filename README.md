CHAVE DE ACESSO:AKIAVZPFIW2JEQSNMYOJ

CHAVE SECRETA: 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


//INSTALAÇÃO:

1 - pip install requests

2 - pip install virtualenv

3 - pip install chalice

4 - pip install pytest


//COMANDOS NO TERMINAL:

1 - cd apis

2 - cd consumers

3 - Chalice new-project

4 - cd consumers

//DEPLOY NA AWS:

1 - cd apis

2 - cd consumers

3 - cd consumers

4 - chalice deploy

5 - após isso confira API no setor lambda do site AWS

6 - vá em configurações e após isso em gatilhos, cliquem em consumers

7 - Vá em monitor para conferir os logs

8 - Vá em CloudWatch

9 - Streams log

//CONFIGURAÇÃO DE ACESSO

1 - Na AWS acesse API gateway

2 - Clique em qualquer uma das APIs

3 - Clique em Resource Policy/ Políticas de Recurso

4 - Cole o seguinte código:

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "execute-api:Invoke",
            "Resource": "arn:aws:execute-api:us-east-1:506145668366:kif37v3am0/*/*/*"
        },
        {
            "Effect": "Deny",
            "Principal": "*",
            "Action": "execute-api:Invoke",
            "Resource": "arn:aws:execute-api:us-east-1:506145668366:kif37v3am0/*/*/*",
            "Condition": {
                "NotIpAddress": {
                    "aws:SourceIp": "MEU_IP"
                }
            }
        }
    ]
}

5 - Clique em Save

6 - Vá em recursos e em ações e faça o deploy novamente só que pela AWS 

7 - Selecione API na primeira caixa e clique em deploy

Observação: A região que tem “Meu_IP” pode ser substituída por uma lista com vários IPs

Link: https://repost.aws/knowledge-center/api-gateway-resource-policy-access

TOKEN DE ACESSO:

1 - Vá em API gateway e escolha sua api 

2 - Escolha o método como get por exemplo

3 - Vá em Editar

4 - Altere API key Required para True

5 - Depois vá em Deploy API

6 - Selecione API e depois deploy

7 - Depois vá em Chaves de API e criar chave de API

8 - Coloque um nome e clique em save

9 - volte para tela de API e clique na API que você requisitou uma chave obrigatória

10 - Vá em Usage Plans/ Planos de utilização

11 - Clique em criar plano de uso

12 - Coloque um nome e deixe o rate em 100 e burst em 200 e as cotas em 5000 e clique em Next

13 - Clique no plano e clique em adicionar estágio

14 - Selecione a API que você configurou como chave obrigatória e o estágio coloque api

15 - clique em adicionar

16 - depois vá em Chaves de API associadas e clique em adicionar chave

17 - Clique em Key

Link: https://docs.aws.amazon.com/pt_br/apigateway/latest/developerguide/api-gateway-setup-api-key-with-console.html#api-gateway-usage-plan-configure-apikey-on-method

Link: 

https://docs.aws.amazon.com/pt_br/apigateway/latest/developerguide/api-gateway-create-usage-plans-with-console.html

POSTMAN:

1 - Na AWS copie o valor da chave de API associada.

2 - Vá em headers do postman, em key adicionei x-api-key.

3 - em Value copie o valor copiado e digite send, perceba que agora funcionou.

DICAS:

1 - Documente sua API!

2 - Desenhe o fluxo antes de fazer o código!

3 - Teste seu código antes de colocar em produção!

4 - Crie Classes!

5 - Crie um processo de integração contínua!

6 - Quebra as ações em pequenos AWS Lambdas!

Documentação do projeto: https://docs.google.com/document/d/1vqZY7SxDAEfLKkabE9pgMBfAgQjYmcTp0AlqwCEGFt4/edit
