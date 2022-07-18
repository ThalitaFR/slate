---
title: Exemplo API Doc

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Me siga no Github!</a>
  - <a href='https://github.com/ThalitaFR'>Mesmo ociosa, as vezes apareço ;D </a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Exemplo de documentação de API
---

# Introdução

Sejam bem-vindos ao meu site! 
Meu nome é Thalita Freire Rodrigues, sou Technical Writer a 3 anos e irei apresentar um exemplo de documentação de API.
A API fictícia **Needles** possui um método chamado **findNeedles**, o qual será usado no exemplo a seguir.

## Método findNeedles

`
public static void findNeedles(String haystack, String [] needles){
  if(needles.length>5){
    System.err.println("Too many words!");
  }else{
    int[] countArray = new int[needles.length];
    for(int i = 0; i< needles.length; i++){
      String [] words = haystack.split("[\"\'\t\n\b\f\r]", 0);
        for (int j=0; j < words.length; j++){
          if(words[j].compareTo(needles[i]) == 0){
            countArray[i]++;
          }
        }
    }
    for (int j = 0; j < needles.length; j++){
      System.out.println(needles[j] + ":" + countArray[j]);
    }
  }
}
`

# Autenticação

> Para se autenticar na API, use os seguintes códigos:

```ruby
require 'needles'

api = needles::APIClient.authorize!('chave-do-usuario')
```

```python
import needles

api = needles.authorize('chave-do-usuario')
```

```shell
# No shell, passe como parâmetros o endpoint e a chave do usuário para a autorização
curl "endpoint-da-api" \
  -H "Authorization: chave-do-usuario"
```

```javascript
const needles = require('needles');

let api = needles.authorize('chave-do-usuario');
```

> Não se esqueça de inserir sua chave no usuário onde está o texto 'chave-do-usuario'.

A API needles usa a chave do usuário para permitir o acesso à API. Se você não possui a chave, faça seu cadastro no [site da nossa API](). 

A chave da API deve ser inserida em todas as requisições em um header para que as operações sejam bem sucedidas. Veja a seguir um exemplo do header preenchido:

`Authorization: KJBR-087235`

<aside class="notice">
<code>KJBR</code> são as siglas que ditam as iniciais do usuário e sua região. A sequência númerica é o registro numérico do usuário.
</aside>

# Needles

## Find Needles

```ruby
require 'haystack'
require 'needles'

api = needles::APIClient.authorize!('chave-do-usuario')
api.needles.post(haystack, needles)
```

```python
import needles

api = needles.authorize('chave-do-usuario')
api.kittens.post(haystack, needles)
```

```shell
curl "endpoint-da-api\findNeedles\${haystack},${needles}" \
  -H "Authorization: chave-do-usuario"
```

```javascript
const needles = require('haystack', 'needles');

let api = needles.authorize('chave-do-usuario');
let needles = api.needles.post(haystack, needles);
```

> Veja a seguir um exemplo da resposta para a requisição acima:

```json
[
  {
    "id": 1,
    "response": " 2:4 "
  },
]
```

Esse endpoint retorna a quantidade de agulhas, representadas por letras ou palavras, encontradas em um palheiro.

## HTTP Request

`Post http://needles.com/api/findNeedles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
haystack | '' | String com frase que representa o palheiro onde as agulhas (palavras) serão procuradas.
needles | [''] | String array que deve conter as palavras que serão procuradas no palheiro.

<aside class="success">
Nota: caça-palavra ou caça-agulha? ;D
</aside>

