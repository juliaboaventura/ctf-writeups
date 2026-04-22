Desafio Busca por Regex

Categoria: Regex / PowerShell

Ferramenta principal: Where-Object com -match

Flag: Jesus

Descrição do desafio
-
"O arquivo users.txt contém 1098 usuários cadastrados. O objetivo era encontrar os usuários cujo nome possui a vogal e como segunda letra e a vogal u como quarta letra, utilizando REGEX no terminal."

Raciocínio
-
O desafio exigia filtrar nomes com posições específicas de caracteres — esse é um caso clássico de uso de expressões regulares. Montei o padrão REGEX pensando posição a posição: a primeira letra poderia ser qualquer caractere, a segunda deveria ser e, a terceira qualquer uma, e a quarta deveria ser u. O ^ ancora o padrão no início do texto, garantindo que as posições sejam contadas a partir da primeira letra do nome.

Comandos utilizados
-
Visualizar o conteúdo do arquivo:
-
Get-Content users.txt

Filtrar com REGEX — segunda letra e e quarta letra u:
-
Get-Content users.txt | Where-Object { $_ -match '^.e.u' }

Explicação do padrão ^.e.u:

^ ancora no início do texto

. primeira letra pode ser qualquer caractere

e segunda letra obrigatoriamente e

. terceira letra pode ser qualquer caractere

u quarta letra obrigatoriamente u

Resultado
-
O filtro retornou os nomes que respeitam o padrão, e o nome encontrado foi utilizado como flag.
Flag: Jesus
