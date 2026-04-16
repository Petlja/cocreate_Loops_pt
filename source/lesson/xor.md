# XOR

XOR *(OU Exclusivo)* é uma operação lógica que retorna verdadeiro (1) apenas quando
as entradas são diferentes. É uma operação binária fundamental com aplicações importantes
em ciência da computação e criptografia.

| A | B | A XOR B |
| - | - | :-----: |
| 0 | 0 | 0       |
| 0 | 1 | 1       |
| 1 | 0 | 1       |
| 1 | 1 | 0       |

Por exemplo, para criptografar a palavra "HELLO" usando a chave "KEY", você deve primeiro
converter `HELLO` para binário...

| Caractere | ASCII | Binário   |
| ---- | ----- | -------- |
| H    | 72    | 01001000 |
| E    | 69    | 01000101 |
| L    | 76    | 01001100 |
| L    | 76    | 01001100 |
| O    | 79    | 01001111 |

...depois converter `KEY` para binário...

| Caractere | ASCII | Binário   |
| ---- | ----- | -------- |
| K    | 75    | 01001011 |
| E    | 69    | 01000101 |
| Y    | 89    | 01011001 |

...e finalmente fazer a criptografia — aplicar XOR em cada caractere com a chave, repetindo a
chave quantas vezes for necessário:

```text
H ⊕ K: 01001000 ⊕ 01001011 = 00000011 (ASCII 3)
E ⊕ E: 01000101 ⊕ 01000101 = 00000000 (ASCII 0)
L ⊕ Y: 01001100 ⊕ 01011001 = 00010101 (ASCII 21)
L ⊕ K: 01001100 ⊕ 01001011 = 00000111 (ASCII 7)
O ⊕ E: 01001111 ⊕ 01000101 = 00001010 (ASCII 10)
```

O texto cifrado resultante consiste em caracteres ASCII não imprimíveis com
valores decimais 3, 0, 21, 7 e 10. Se um atacante interceptasse essa mensagem,
ele veria apenas dados binários ilegíveis, já que os caracteres não são imprimíveis.

Para descriptografar o texto cifrado, basta aplicar XOR novamente com a mesma chave:

```text
3  ⊕ K: 00000011 ⊕ 01001011 = 01001000 (ASCII 72 → H)
0  ⊕ E: 00000000 ⊕ 01000101 = 01000101 (ASCII 69 → E)
21 ⊕ Y: 00010101 ⊕ 01011001 = 01001100 (ASCII 76 → L)
7  ⊕ K: 00000111 ⊕ 01001011 = 01001100 (ASCII 76 → L)
10 ⊕ E: 00001010 ⊕ 01000101 = 01001111 (ASCII 79 → O)
```

A operação XOR é auto-inversa — aplicar XOR duas vezes com a mesma chave
restaura os dados originais.

Em aplicações reais, reutilizar a mesma chave para várias mensagens torna a
criptografia XOR vulnerável à análise de frequência e a ataques de texto conhecido.
O XOR sozinho não fornece segurança forte, a menos que a chave seja gerenciada corretamente
e tenha pelo menos o mesmo tamanho da mensagem — como em uma one-time pad (chave descartável). No entanto, para fins educacionais e demonstrações básicas de princípios criptográficos, o XOR
é simples e ideal.

## Tarefa simples

Crie um aplicativo de console em qualquer linguagem de programação para criptografar e descriptografar
mensagens usando a operação XOR.

O alfabeto permitido para mensagens (tanto texto simples quanto chave) inclui apenas
letras minúsculas do inglês:

```text
Σ = { a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z }
```

Espaços, letras maiúsculas, números e outros caracteres não são permitidos.

Na primeira linha da entrada do usuário haverá uma mensagem `m` com no máximo
cem caracteres ASCII para texto simples ou 800 bits para texto cifrado, na segunda linha haverá uma chave `k` com no máximo cinco caracteres, e na terceira linha haverá um inteiro `s`, que representa a operação. Se $s=1$ então `m` é texto simples e deve ser criptografada, e se $s=2$, então `m` é texto cifrado em binário e deve ser descriptografada.

### Exemplo de teste 1

Se a entrada for:

```text
nikolatesla
ser
1
```

a saída deve ser:

```text
0001110100001100000110010001110000001001000100110000011100000000000000010001111100000100
```

### Exemplo de teste 2

Se a entrada for:

```text
0001110100001100000110010001110000001001000100110000011100000000000000010001111100000100
ser
2
```

a saída deve ser:

```text
nikolatesla
```

## Inicie a tarefa

[Implemente a cifra aqui ](https://arena.petlja.org/sr-Latn-RS/competition/123-co-create#tab_142947)

## Dicas de solução

Cada caractere é armazenado na memória como um valor ASCII de 8 bits (para letras minúsculas a–z, os códigos variam de 97 a 122). Para criptografar um caractere, pegue seu valor ASCII e o valor ASCII do caractere correspondente da chave (ciclando pela chave), aplique XOR (^) entre eles e exiba o resultado como um número binário de 8 bits.

Para descriptografar, siga o processo inverso: pegue cada bloco binário de 8 bits do texto cifrado, converta de volta para um inteiro (0–255), aplique XOR com o valor ASCII do caractere correspondente da chave e converta o resultado de volta para um caractere.

## Tarefas avançadas de XOR (opcional)

### Expanda o alfabeto permitido

Permita letras minúsculas e maiúsculas, espaços, números e pontuação.
Caracteres não-letras são criptografados com a chave da mesma forma.

## Use funções

Crie duas funções: `encrypt()` para criptografar mensagens e `decrypt()` para
descriptografar mensagens. Use as funções criadas em seu programa principal.

### Crie uma Classe

Crie uma classe `XorCipher` que:

* Armazene a chave,
* Forneça métodos `encrypt()` e `decrypt()`,
* Opcionalmente inclua um método auxiliar privado para repetir a chave ao longo do comprimento da mensagem.

Use a classe criada em seu programa principal.

### Aceite argumentos de linha de comando

Em vez de esperar pela entrada do usuário, crie um aplicativo de console que
aceite os seguintes argumentos de linha de comando:

1. argumento `m` para especificar a mensagem,
2. argumento `k` para especificar a chave, e
3. argumento `s` para especificar a operação (`1` para criptografar, `2` para descriptografar).

### Criptografe e Descriptografe Arquivos

Use o conhecimento adquirido até agora para criar um programa que possa:

* ler texto simples ou texto cifrado binário de um arquivo,
* criptografar ou descriptografar com uma chave fornecida, e
* escrever o resultado em um novo arquivo.
