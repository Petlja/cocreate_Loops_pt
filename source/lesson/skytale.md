# Skytale

Após concluir esta lição, você será capaz de:

* Explicar como funciona a cifra Skytale.
* Implementar criptografia e descriptografia usando operações simples de array ou string.
* Entender como dispositivos físicos de criptografia podem ser modelados digitalmente.

A Skytale é uma das ferramentas mais antigas conhecidas para criptografia, datando da Grécia Antiga por volta de 400 a.C. Era um dispositivo cilíndrico simples usado pelos espartanos para enviar mensagens secretas durante campanhas militares.

Uma tira de pergaminho ou couro era enrolada em torno de uma haste de madeira (a *skytale*) de um diâmetro específico. A mensagem era então escrita ao longo da haste. Uma vez desenrolada, as letras pareciam embaralhadas e sem sentido. O destinatário precisava de uma haste do **exato mesmo diâmetro** para enrolar a tira e ler a mensagem original.

Se você quiser criptografar a mensagem:

```text
attackatdawn
```

e escolher uma haste que permita **4 letras por volta**, você primeiro escreve a mensagem verticalmente em colunas, formando linhas de comprimento 4:

```text
a t t a
c k a t
d a w n
```

O texto cifrado é então criado lendo linha por linha:

```text
acdtkatawatn
```

Para descriptografar, o receptor enrola novamente a tira em uma haste do mesmo diâmetro e lê verticalmente novamente para reconstruir a mensagem original.

## Tarefa simples

Crie um aplicativo de console em qualquer linguagem de programação para criptografar e descriptografar mensagens usando a cifra Skytale.

O alfabeto permitido para mensagens inclui apenas as letras minúsculas do alfabeto inglês:

```text
Σ = { a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z }
```

Espaços, letras maiúsculas, números e outros caracteres não são permitidos.

Na primeira linha da entrada do usuário haverá uma mensagem `m` com no máximo cem caracteres. Na segunda linha haverá um inteiro `k` (o número de colunas – circunferência da haste). Na terceira linha haverá um inteiro `s`, que representa a operação. Se $s=1$, então `m` deve ser criptografada. Se $s=2$, então `m` deve ser descriptografada.

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

## Inicie a tarefa

[Implemente a cifra aqui ](https://arena.petlja.org/sr-Latn-RS/competition/123-co-create#tab_142946)

## Dicas de solução

Para **criptografar**, escreva o texto simples verticalmente em uma tabela com `k` colunas. Leia a tabela linha por linha para formar o texto cifrado. Para **descriptografar**, escreva o texto cifrado linha por linha em uma tabela com `k` colunas e leia a tabela verticalmente para reconstruir o texto simples.

## Tarefas avançadas de Skytale (opcional)

### Expanda o alfabeto permitido

Inclua letras maiúsculas, espaços, números e pontuação.

### Use funções

Crie funções `encrypt()` e `decrypt()` para manter o código modular.

### Crie uma Classe

Implemente uma classe `SkytaleCipher` que armazene `k` e forneça métodos para criptografia e descriptografia.

### Criptografe e Descriptografe Arquivos

Modifique o programa para ler o texto simples ou cifrado de um arquivo e escrever os resultados em outro arquivo.

### Trate linhas incompletas

Modifique seu programa para que, se a última linha for mais curta que `k`, ainda criptografe e descriptografe corretamente, tratando caracteres ausentes ou preenchendo com padding.
