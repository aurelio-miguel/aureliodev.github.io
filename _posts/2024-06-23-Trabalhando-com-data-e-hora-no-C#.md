---
layout: post
title:  "Trabalhando com data e hora no C#"
date:   2024-06-24 00:56:00 -0300
categories: programação, c#, .net
---

# Introdução
Variáveis e dados com data e hora são utilizados por praticamente todos os programas. Esses tipos de informações podem ser úteis para armazenar a data e hora de uma venda, armazenar informações de registros e até mesmo para validações de formulários. Saber trabalhar com essas informações é algo crucial e necessário para o bom funcionamento de um programa.

O objetivo desse arquivo é estressar esse assunto extremamente importante.

# Tipo DateTime
Para armazenar informações de data e hora utilizaremos o tipo **DateTime**. Segue abaixo o trecho de código que exemplifica a criação de uma variável do tipo DateTime:
```
DateTime data = new DateTime();
```
Por padrão as variáveis desse tipo não são nulas. Ao imprimir essa variávei será possível visualizar o valor indicando a estrutura do DateTime.

# Data e hora atual
Com o DateTime podemos capturar a data e horário atual do computador. Para fazer isso iremos acessar a propriedade **Now** do tipo **DateTime**, conforme o exemplo abaixo:
```
DateTime data = new DateTime();
data = DateTime.Now;

Console.WriteLine(data);

Output:
23/06/2024 22:35:02
```

# Pegando detalhes da data e hora
Após a inicialização de uma variável do tipo DateTime, poderemos acessar a sua propriedade para obter algumas informações específicas. Imagine que queremos obter apenas o ano de uma variável do tipo DateTime, podemos acessar a propriedade **Year** para ter acesso a essa informação.

Dessa forma podemos pegar cada um dos detalhes de uma data e hora e armazenar em uma variável para poder trabalhar separadamente, por exemplo.

Segue abaixo algumas das principais propriedades:
- **Year**: Obter o ano.
- **Month**: Obter o mês.
- **Day**: Obter o dia.
- **Hour**: Obter a hora.
- **Minute**: Obter os minutos.
- **Second**: Obter os segundos.
- **DayOfYear**: Obter o número do dia em questão no ano.
- **DayOfWeek**: Obter o dia da semana;

Segue abaixo um exemplo de como podemos capturar essas informações utilizando as propriedades do DateTime:
```
DateTime data = DateTime.Now;

int ano = data.Year;
int dia = data.Day;
int hora = data.Hour;

Console.WriteLine($"Ano: {ano} | Dia: {dia} | Hora: {hora}");

Output:
Ano: 2024 | Dia: 23 | Hora: 23
```

# Inserindo uma data e hora em uma variável DateTime
Nós podemos também inserir os valores que desejamos na variável DateTime passando por parâmetro essas informações, conforme o exemplo abaixo:
```
DateTime data = new DateTime(2024, 06, 23, 23, 18, 15);
Console.WriteLine(data);

Output:
23/06/2024 23:18:15
```
Por parâmetro são passados em sequência o ano, o mês, o dia, a hora, os minutos e por último os segundos.

Além disso, caso tenhamos o interesse em não específicar o horário, podemos passar por parâmetro apenas a data, o mês e a hora. Conforme o trecho abaixo:
```
DateTime data = new DateTime(2024, 06, 23);
Console.WriteLine(data);

Output:
23/06/2024 00:00:00
```

# Formatando a data e hora
Podemos também formatar a data e hora para que sejam exibidos no formato que tivermos interesse. Por exemplo podemos formatar a data para que seja exibida no formato brasileiro, contendo como primeira informação o dia, após isso o mês e por último o ano.

No trecho abaixo iremos formata a data para que ela seja exibida no formato brasileiro:
```
DateTime data = DateTime.Now;
string dataConvertida = data.ToString("dd/MM/yyyy");

Console.WriteLine(dataConvertida);

Output:
24/06/2024
```
No exemplo acima nós utilizamos o método **ToString** para formatar a data que estava na variárel **data** para o formado dia/mês/ano. Após isso a informação foi exibida no console.

No exemplo acima é possível visualizar que utilizamos a string **"dd/MM/yyyy"** para formatar a data. Esses caracteres específicos são utilizados para representar cada um das informações do DateTime, isso nos auxilia a descrever quais formatação devemos utilizar. 

Abaixo você pode ver a lista de caracteres e o que eles representam na formatação, lembrando que o C# faz a diferenciação entre as letras maiúsculas e letras minúsculas:
- **yyyy** - Para o ano descrito de forma completa.
- **yy** - Para o ano com apenas dois dígitos.
- **M** - Para o mês sem o zero.
- **MM** - Para o mês com o zero, por exemplo mês 06;
- **d** - Para o dia do mês sem o zero.
- **dd** - Para o dia do mês com o zero, por exemplo dia 05;
- **H** - Para a hora sem o zero.
- **HH** - Para a hora com o zero, por exemplo 07 horas;
- **m** - Para os minutos sem o zero.
- **mm** - Para os minutos com o zero, por exemplo 05 minutos;
- **s** - Para os segundos sem o zero.
- **ss** - Para os segundos com o zero, por exemplo 04 segundos.

Segue abaixo um trecho de código realizando uma formatação de data e hora conforme um modelo específico que iremos determinar utilizando o método **ToString()** e os caracteres indicados acima:
```
DateTime data = DateTime.Now;
string dataConvertida = data.ToString("dd/MM/yyyy HH:mm");

Console.WriteLine(dataConvertida);

Output:
24/06/2024 00:23
```

# Manipulação e cálculo de datas com o DateTime
Nós podemos também fazer manipulações de datas e cálculos utilizando variávies do tipo DateTime. Dentre as operações, podemos inserir datas ou remover datas, podemos também calcular a diferença entre duas datas, por exemplo.

Segue abaixo um exemplo onde podemos inserir 5 dias em uma determinada data utilizando o método **AddDays()**:
```
DateTime data = DateTime.Now;
DateTime novaData = data.AddDays(5);

Console.WriteLine(novaData);

Output:
29/06/2024 00:39:14
```
Podemos também realizar a operação de atribuição de valores inserindo anos com o método **AddYear()**, minutos com o método **AddMinutes**, horas com o método **AddHours()**, etc.

Além disso, podemos remover valores. Basta passar como parâmetro a quantidade que queremos remover, por exemlo `DateTime novaData = data.AddDays(-5)`. Dessa forma a variável **novaData** terá o valor da variável **data** decrescido de 5 dias.

Com indicado no ínicio desse tópico, podemos também realizar operações entre as datas. Imagine que temos um programa para calcular quantos dias você vai ficar de férias com base nada data de inicio das suas férias e data de retorno. Para isso utilizaremos também o tipo TimeSpan, esse tipo é utilizado para representar um período.

Podemos fazer isso utilizando as operações matemáticas entre duas variáveis do tipo DateTime, conforme o exemplo abaixo:
```
DateTime dataInicio = new DateTime(2024, 06, 24);
DateTime dataRetorno = new DateTime(2024, 07, 20);
TimeSpan periodoFerias = dataRetorno - dataInicio;

Console.WriteLine(periodoFerias.Days);

Output:
26
```
No exemplo acima utilizamos criamos uma nova variável do tipo TimeSpan para armazenar o período entre o retorno das férias - o inicio das férias. Dessa forma foi possível calcular o período de férias e depois acessamos a propriedade **Days** da variável do tipo TimeSpan para obter apenas a quantidade de dias.

# Conclusão
Esse tipo de dado utilizado por praticamente todos os programas, desde programas simples até mesmo sistema mais complexos. Por conta disso, é muito importante conhecer todas as particularidades desse tipo.

Em breve eu pretendo trazer um vídeo ou artigo para esgotar esse assunto através de um programa via console de lista de tarefas.

Até mais!