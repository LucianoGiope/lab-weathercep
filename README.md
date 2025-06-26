## PRIMEIRO DESAFIO DO LABORATÓRIO proposto pelo curso.

## Texto descritivo do desafio
 Objetivo: Desenvolver um sistema em Go que receba um CEP, identifica a cidade e retorna o clima atual (temperatura em graus celsius, fahrenheit e kelvin). Esse sistema deverá ser publicado no Google Cloud Run.

Requisitos:

O sistema deve receber um CEP válido de 8 digitos  

O sistema deve realizar a pesquisa do CEP e encontrar o nome da localização, a partir disso, deverá retornar as temperaturas e formata-lás em: Celsius, Fahrenheit, Kelvin.
O sistema deve responder adequadamente nos seguintes cenários:
Em caso de sucesso:

Código HTTP: 200

Response Body: { "temp_C": 28.5, "temp_F": 28.5, "temp_K": 28.5 }

Em caso de falha, caso o CEP não seja válido (com formato correto):

Código HTTP: 422

Mensagem: invalid zipcode

​​​Em caso de falha, caso o CEP não seja encontrado:

Código HTTP: 404

Mensagem: can not find zipcode

Deverá ser realizado o deploy no Google Cloud Run.


Dicas:
Utilize a API viaCEP (ou similar) para encontrar a localização que deseja consultar a temperatura: https://viacep.com.br/

Utilize a API WeatherAPI (ou similar) para consultar as temperaturas desejadas: https://www.weatherapi.com/

Para realizar a conversão de Celsius para Fahrenheit, utilize a seguinte fórmula: F = C * 1,8 + 32

Para realizar a conversão de Celsius para Kelvin, utilize a seguinte fórmula: K = C + 273

Sendo F = Fahrenheit
Sendo C = Celsius
Sendo K = Kelvin

Entrega:

O código-fonte completo da implementação.

Testes automatizados demonstrando o funcionamento.

Utilize docker/docker-compose para que possamos realizar os testes de sua aplicação.

Deploy realizado no Google Cloud Run (free tier) e endereço ativo para ser acessado.


### Como utilizar a API

## Passo 1- Configurar as variáveis
- Adicionar seus dados validação e acessos à Api
- Acesse o arquivo .env na pasta server/cmd e altere a variável:
- - APIKEYWEATHER={SEU TOKEN PARA A API WEATHER}

## Passo 2- Deve-se subir o server
- [Modo1] Acesse a pasta: server/cmd
- Execute o comando 
- - go run main.go
-
- [Modo2] Suba o container docker
- Entre na pasta root do projeto
- docker-compose up --build weather-cep
- 

## Com servidor ativado, executar a consulta
- Utilizando o cliente em Go
- - Acesse a pasta client/cmd e rode o comando abaixo
- - go run main.go {NÚMERO DO CEP}
-
- Utilizando serviço http
- - Abra o arquivo consulta.http na pasta api
- - Informe um cep válido e execute.
-
- Utilizando o navegador
- - http://localhost:8080/weatherByCep/{NÚMERO DO CEP}

## Acessando via CloudRun
- https://cloudrun-weather-cep-e36gm7yrra-rj.a.run.app/weatherByCep/{NÚMERO DO CEP}

