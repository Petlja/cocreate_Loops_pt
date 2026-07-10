
# Condições e laços

Para dominar com sucesso o material sobre criptografia, é necessário conhecer os fatos básicos sobre o trabalho com condições e laços. Condições e laços são mecanismos fundamentais que permitem aos programas de computador tomar decisões e repetir determinadas ações. Graças às condições, um programa pode reagir de forma diferente dependendo dos dados recebidos, enquanto os laços permitem a repetição eficiente dos mesmos passos várias vezes. Esses conceitos são essenciais na criptografia, pois os algoritmos de proteção de dados baseiam-se em um conjunto de regras, verificações e procedimentos repetitivos que garantem a segurança das informações.

Vamos relembrar os fundamentos básicos! Se esta área ainda não estiver clara para você, consulte a lição dedicada a este tema na Petlja.

Link para a lição da Petlja sobre laços: [aqui](https://petlja.org/en/biblioteka/r/lekcije/python-za-svakog/01_karel_eng_02_for)
<!--Link for Serbian versions of the course https://www.petlja.org/sr-Latn-RS/kurs/477/12/5844 -->

```{learnmorenote} Para os professores

Link para a lição da Petlja em sérvio: https://www.petlja.org/sr-Latn-RS/kurs/477/12/5844
Link para versões do curso que não são em sérvio: https://petlja.org/en/biblioteka/r/lekcije/python-za-svakog/01_karel_eng_02_for
```

## Condições

Na maioria das linguagens de programação modernas, as instruções condicionais são usadas para tomar
decisões e controlar o fluxo de um programa. As construções mais comuns são:

* if
* if-else
* switch-case

Embora a sintaxe varie entre as linguagens, a lógica central é a mesma.

### O comando `if`

O comando `if` executa um bloco de código apenas se uma condição especificada for
verdadeira.

```text
if condition then
    statement(s)
```

Por exemplo, em C, C++, C# e Java, se você quiser verificar se `x` é maior que
`0`, a instrução condicional pode ser escrita assim:

```csharp
int x = 5;
if (x > 0) {
    // ...
}
```

### O comando `if-else`

O comando if-else executa um bloco de código se a condição for verdadeira e
outro bloco se for falsa.

```text
if condition then
    statement(s)
else
    statement(s)
```

Por exemplo, em C, C++, C# e Java, se você quiser verificar se `x` é maior que
`0` ou não, a instrução condicional pode ser escrita assim:

```csharp
int x = 5;
if (x > 0) {
    // ...
} else {
    // ...
}
```

### O comando `switch-case`

O comando `switch-case` é útil quando se compara a mesma variável com
muitos valores possíveis. Pode ser mais legível do que usar muitos comandos `if-else`.

```text
switch expression do
    case value1:
        statement(s)
    case value2:
        statement(s)
    ...
    default:
        statement(s)
```

Por exemplo, em C, C++, C# e Java, se você quiser determinar o nome do
dia com base no seu número ordinal na semana, a instrução condicional pode ser
escrita assim:

```csharp
int day = 3;
string name = "";
switch (day) {
    case 1:
        name = "Monday";
        break;
    case 2:
        name = "Tuesday";
        break;
    case 3:
        name = "Wednesday";
        break;
    // ...
    default:
        name = "";
        break;
}
```

### Aninhamento de condições

Instruções condicionais podem ser colocadas dentro de outras instruções condicionais — isso
é chamado de **aninhamento**. Condições aninhadas são úteis quando uma decisão depende do
resultado de uma decisão anterior. Por exemplo, você pode primeiro verificar se um usuário
está logado e, em seguida, dentro desse bloco, verificar se ele tem permissão para
realizar determinada ação.

## Laços

Na maioria das linguagens de programação modernas, os laços geralmente são implementados usando uma
das seguintes construções:

* `for`,
* `while` (ou `while-do`),
* `do-while` (ou `repeat-until`),
* `foreach` (ou `for-each`).

Embora a sintaxe varie entre as linguagens, a lógica central é a mesma.


### O laço `for`

O laço `for` é usado quando o número de iterações é finito e
pré-determinado.

```text
for variable ← start to end do
    statement(s)
```

Por exemplo, em C, C++, C# e Java, um laço `for` para iterar pelos números
de 0 a 9 pode ser escrito assim:

```csharp
for (int i = 0; i <= 9; i++) {
    // ...
}
```

### O laço `while`

O laço `while` (ou `while-do`) é usado quando o número de iterações é
desconhecido previamente. A condição é verificada antes de cada iteração, por isso
é chamado de **laço com pré-condição**.

```text
while condition do
    statement(s)
```

Por exemplo, em C, C++, C# e Java, um laço `while` para iterar pelos números
de 0 a 9 pode ser escrito assim:

```csharp
int i = 0;
while (i <= 9) {
    // ...
    i++;
}
```

### O laço `do-while`

O laço `do-while` (ou `repeat-until`) também suporta um número desconhecido de
iterações, mas a condição é verificada após cada iteração. Isso é chamado de
**laço com pós-condição**, e sempre executa pelo menos uma vez.

```text
repeat
    statement(s)
until condition
```

Por exemplo, em C, C++, C# e Java, um laço `do-while` para iterar pelos números
de 0 a 9 pode ser escrito assim:

```csharp
int i = 0;
do {
    // ...
    i++;
} while (i <= 9);
```

### O laço `foreach`

O laço `foreach` (ou `for-each`) é usado para iterar sobre todos os elementos de uma
coleção ou array. Ele simplifica a iteração quando você não precisa saber o
índice.

```text
for-each element in collection do
    statement(s)
```

Por exemplo, um laço `for-each` para iterar pelo array `nums` pode ser escrito
em C++ assim:

```cpp
int nums[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
for (int i : nums) {
    // ...
}
```

...ou em C# assim...

```csharp
int[] nums = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
foreach (int i in nums) {
    // ...
}  
```

...ou em Java assim:

```java
int[] nums = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
for (int i : nums) {
    // ...
}   
```

### Aninhamento de laços

Laços também podem ser aninhados, ou seja, um laço é colocado dentro de outro. Isso
é comum ao trabalhar com dados multidimensionais, como percorrer linhas e
colunas em uma matriz ou iterar sobre uma grade em um jogo. Além disso, laços e
condições podem ser combinados livremente — por exemplo, um laço pode conter uma instrução `if`
para processar apenas certos elementos, ou uma instrução `if` pode conter um laço para realizar ações repetidas quando uma condição for verdadeira. Essa capacidade de misturar
e aninhar laços e condições permite a criação de algoritmos complexos
mantendo a lógica subjacente estruturada.
