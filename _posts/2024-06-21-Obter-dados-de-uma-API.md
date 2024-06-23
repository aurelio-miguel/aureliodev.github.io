---
layout: post
title:  "Obter dados de uma API"
date:   2024-06-21 21:00:00 -0300
categories: programação, c#, .net
---

## Introdução
A obtenção de dados de uma API é um processo muito importante e muito comum. Esse processo tem como objetivo obter dados através de um endpoint de uma API.

A ideia é acessar um endereço/endpoint através de uma request(requisição) e obter uma reposta(response).

## Realizando uma requisição
Para realizar requisições, utilizaremos a class **HttpClient** para nos auxiliar nessa tarefa. Essa classe possui uma base para a realização de requisições HTTP e receber respostas HTTP através de um enpoint. 

Primeiramente vamos inicializar um novo objeto da classe **HttpClient**, segue abaixo um trecho exemplificando esse processo:
```
HttpClient client = new HttpClient();
```

O próximo passo vai ser utilizar o método assíncrono **GetStringAsync()** para obter os dados do response e armazenar em uma variável essa resposta, conforme o exemplo abaixo:

```
HttpClient client = new HttpClient();

string resposta = await client.GetStringAsync("endpoint");
```
No exemplo acima nós armazenamos a response da nossa requisição na variável **resposta**. A partir desse momento podemos utilizar esse resultado para exibir no console, serializar para um novo objeto, etc.

No exemplo acima antes de chamar a função **GetStringAsync()** utilizamos o termo await pois a função em questão é uma função assíncrona.

No trecho abaixo vamos realizar uma requisição e vamos imprimir a resposta no console:
```
HttpClient client = new HttpClient();

string resposta = await client.GetStringAsync("https://www.deckofcardsapi.com/api/deck/new/draw/?count=1");

Console.WriteLine(resposta);

Output:
{"success": true, "deck_id": "t35toq4l97xh", "cards": [{"code": "QS", "image": "https://deckofcardsapi.com/static/img/QS.png", "images": {"svg": "https://deckofcardsapi.com/static/img/QS.svg", "png": "https://deckofcardsapi.com/static/img/QS.png"}, "value": "QUEEN", "suit": "SPADES"}], "remaining": 51}
```
Para o exemplo acima eu utilizei uma API que tem diversos endpoints para retornar dados de cartas de baralho e a requisição do exemplo acima foi para retornar uma carta aleatória de um novo baralho, incluindo todos os dados da carta e as imagens em png e svg da nossa carta.

Para conhecer mais essa API [Clique aqui](https://www.deckofcardsapi.com/)

## Tratando exceções
Durante o processo de obtenção de dados de uma API, inúmeros problemas podem ocorrer. O simples fato de inserir um endpoint inválido já é um problema e se ele não for tratado e identificado, esse problema pode interromper inesperadamente o nosso programa.

Sempre que vamos desenvolver devemos sempre imaginar que problemas vão ocorrer, dessa forma iremos programar de forma ativa em relação aos erros e não de forma passível. Com base nisso, utilizaremos o **Try** e **Catch** para identificar problemas e trata-los.

### Try e Catch
Imagina que o nosso programa é executado linha a linha, desde a linha 1 até a última linha de código. Com o Try e Catch podemos inserir no meio do nosso programa algo do tipo "Tente executar esse trecho, se não der certo faça isso aqui".

O **Try** vai ser exatamente o escopo que vai conter essa tentativa, se algum erro ocorrer vamos utilizar o escopo do **Catch** para identificar o erro e prosseguir da forma que desejarmos sem que o programa seja finalizado inesperadamente.

Para o nosso contexto de obtenção de dados de uma API, os principais problemas vão estar localizados no método que vai obter os dados da API. Dessa forma vamos inserir dentro do contexto do **Try** a nossa requisição, conforme o trecho abaixo:
```
HttpClient client = new HttpClient();

try{
    var resposta = await client.GetStringAsync(endpoint);
}

```
Caso ocorra algum erro durante a execução do **Try**, o sistema vai retornar uma exceção, e poderemos capturar essa exeção diretamente no **Catch**, confome o exemplo abaixo:
```
HttpClient client = new HttpClient();

try
{
    var resposta = await client.GetStringAsync(endpoint);
}
catch (Exception ex)
{
    Console.WriteLine($"Ocorreu um erro na requisição: {ex}");
}
```
Conforme consta no código acima, o **Catch** possui um parâmetro que recebe a exceção, caso tenha ocorrido. Dessa forma podemos tratar e exibir de forma personalizada a exceção.

Dessa forma o nosso programa não será finalizado de forma inesperada e podemos previnir e tratar erros sem que os erros "quebrem" o nosso programa como um todo.

## Conclusão
Neste artigo foi possível entender entender como funciona a obtenção de dados através de uma API. O assunto desse artigo é apenas uma pedrinha de gelo de um iceberg sobre como os programas e sistema se comunicam. Existem vários outros assunstos importantes para esgotar esse tema, como serialização e desserialização que é algo que irei escrever sobre posteriormente.

Até mais.