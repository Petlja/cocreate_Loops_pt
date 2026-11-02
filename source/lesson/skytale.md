# Escítala

A Escítala (skytale) é uma das ferramentas de criptografia mais antigas conhecidas, datada da Grécia antiga, por volta de 400 a.C. Era um dispositivo cilíndrico simples usado pelos espartanos para enviar mensagens secretas durante campanhas militares.

Uma tira de pergaminho ou couro era enrolada em uma haste de madeira (*skytale*) de determinado diâmetro. A mensagem era então escrita ao longo da tira enrolada. Para descriptografar, o destinatário enrolava a tira em uma haste do mesmo diâmetro e lia a mensagem ao longo dela, da mesma forma que havia sido escrita.

Se quiser criptografar a mensagem:

```text
attackatdawn
```

e você escolher uma haste que permita **3 letras por volta**, a tira passa ao redor dela 4 vezes. Você escreve a mensagem ao longo da haste, linha por linha, com 4 letras por linha (uma em cada volta), formando uma tabela:

```text
a t t a
c k a t
d a w n
```

O texto criptografado é então obtido fazendo a leitura coluna por coluna (esta é a ordem das letras na tira desenrolada):

```text
acdtkatawatn
```

Para descriptografar a mensagem, o destinatário enrola a tira em uma haste do mesmo diâmetro e lê linha por linha novamente para reconstruir a mensagem original.

## Primeira tarefa

Crie um aplicativo de console em qualquer linguagem de programação para criptografar e descriptografar mensagens usando a cifra de Escítala.

O alfabeto permitido para mensagens contém apenas letras minúsculas do alfabeto inglês:

```text
Σ = { a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z }
```

Espaços, letras maiúsculas, números e outros caracteres não são permitidos!

Na primeira linha da entrada, há uma mensagem `m` com no máximo cem caracteres. Na segunda linha, há um número inteiro `k` (o número de colunas da tabela usada na criptografia). Na terceira linha, há um número inteiro `s` (1 para criptografia, 2 para descriptografia).

### Exemplo de teste 1

Se a entrada for:

```text
attackatdawn
4
1
```

a saída deve ser:

```text
acdtkatawatn
```

### Exemplo de teste 2

Se a entrada for:

```text
acdtkatawatn
4
2
```

a saída deve ser:

```text
attackatdawn
```

## Dicas de solução

Para a **criptografia**, escreva o texto simples linha por linha em uma tabela com `k` colunas. Leia a tabela coluna por coluna para obter o texto cifrado.

Para a **descriptografia**, escreva o texto cifrado coluna por coluna em uma tabela com `k` colunas (cada coluna contém o comprimento da mensagem dividido por `k` letras), depois leia a tabela linha por linha para reconstruir o texto simples.

## Exercícios mais complexos com a Escítala (opcional)

### Expandir o alfabeto permitido

Inclua letras maiúsculas, espaços, números e sinais de pontuação.

### Usar funções

Crie as funções `encrypt()` e `decrypt()` para tornar o código modular.

### Criar uma classe

Implemente uma classe `SkytaleCipher` que armazene `k` e forneça métodos para criptografia e descriptografia.

### Criptografar e descriptografar arquivos

Modifique o programa para que ele leia texto simples ou texto cifrado de um arquivo e escreva o resultado em outro arquivo.

### Lidar com linhas incompletas

Modifique o programa para que, caso a última linha seja mais curta que `k`, ele ainda consiga criptografar e descriptografar corretamente, tratando adequadamente as linhas incompletas.
