---
layout: post
title:  "Conhecendo e manipulando listas no C#"
date:   2024-06-21 20:43:00 -0300
categories: welcome
---

## O que são listas
A lista é uma coleção de objetos que possui a capacidade de armazenar informações de um tipo específico sem a necessidade de determinar na sua definição um limite máximo de objetos que podem ser inseridos em uma lista, a lista possui um tamanho dinâmico, diferente do array que possui um tamanho fixo e pré-determinado. Os objetos são organizados em uma lista de forma linear e podem ser acessados através do seu índice que representa a sua posição na lista.

Conforme novos objetos são inseridos e removidos da lista, o seu tamanho é alterado.

## Trabalhando com as listas no C#
Para trabalhar com as listas no C# utilizamos a classe List. Através da classe List poderemos realiar a criação da nossa lista e realizar diversos procedimentos através dos métodos dessa classe.

## Inicializando uma lista
Para inicializar uma lista utilizaremos a estrutura do trecho de código abaixo:
```
List<int> nomeLista = new List<int>();
```
Conforme consta no trecho acima, o tipo de dados que serão inseridos na nossa lista deve ser informado durante a inicialização da lista. No exemplo em questão foi criado uma lista de inteiros que poderá ser acessada através da variável com o nome "nomeLista".

## Principais propriedades da classe List
Dentre as principais propriedades da classe List podemos destacar a propriedade **Items** para obter ou gravar o elemtno em uma posição de índice específica, uma outra propriedade muito utilizada é a **Count** que retorna o número total de elementos que existe na lista.

## Principais métodos da classe List
Dentre os principais métodos, podemos destacar os métodos abaixo:
- **Add** - Adiciona um elemento no final da lista.
- **Remove** - Remove a primeira ocorrência de um determinado elemento.
- **Clear** - Remove todos os elementos da lista.
- **Contains** - Verifica se um elemento especificado existe ou não na lista.
- **Insert** - Insere um novo elemento em um índice específico da lista.
- **RemoveAt** - Remove o elemento em uma posição específica na lista.
- **Sort** - Orgena os elementos da lista.

## Inserindo itens em uma lista
Após a inicialização da lista podemos inserir os novos elementos na lista utilizando o método **Add()**, conforme o trecho abaixo:
```
List<int> valores = new List<int>();
valores.Add(3);
valores.Add(14);
valores.Add(20);
```

## Removendo um elemento específico da lista
Podemos utilizar o método **Remove()** para remover a primeira ocorrência de um elemento específico da lista. Podemos fazer isso passando como parâmetro do método **Remove** o valor que queremos remover:
```
List<int> lista = new List<int>();
lista.Add(3);
lista.Add(19);
lista.Add(11);

lista.Remove(3);
```
Dessa forma o elemento que possui o valor 3 será removido da nossa lista. Caso tenha algum elemento 3 após o elemento do item do índice zero, esse não será removido pois a função **Remove** remove a primeira ocorrência.

## Verificando a quantidade de itens na lista
Para verificar a quantidade de itens em uma lista podemos utilizar a propriedade **Count** do nosso objeto inicianlizado, conforme o trecho abaixo:
```
List<int> lista = new List<int>();
lista.Add(3);
lista.Add(19);
lista.Add(11);
lista.Add(3);

Console.WriteLine(lista.Count);

Output:
4
```