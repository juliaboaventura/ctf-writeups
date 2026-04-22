Desafio IP Suspeito no Apache

Categoria: Log Analysis

Ferramenta principal: awk, sort, uniq

Flag: 66.249.73.135

Descrição do desafio
-
"O servidor web estava recebendo uma quantidade expressiva de requisições. Com o arquivo logs.txt de um servidor Apache em mãos, o objetivo era descobrir qual IP fez o maior número de requisições — um indicativo clássico de varredura ou ataque."

Raciocínio
-
Em logs do Apache, cada linha representa uma requisição e começa com o IP de origem. Para descobrir qual IP aparece mais vezes, precisava extrair apenas a coluna de IPs, ordenar (o uniq só funciona em dados adjacentes), contar as ocorrências de cada IP e por fim reordenar pelo número de ocorrências para encontrar o maior.

Comandos utilizados
-
Visualizar o conteúdo do log:
-
cat logs.txt

Extrair apenas a primeira coluna (IPs):
-
awk '{print $1}' logs.txt

Ordenar os IPs:
-
awk '{print $1}' logs.txt | sort

Contar ocorrências de cada IP:
-
awk '{print $1}' logs.txt | sort | uniq -c

Ordenar pelo número de ocorrências e encontrar o mais frequente:
-
awk '{print $1}' logs.txt | sort | uniq -c | sort

awk divide cada linha por espaço e imprime só a 1ª coluna (o IP)

sort ordena as linhas — necessário antes do uniq

uniq -c conta quantas vezes cada linha consecutiva se repete

sort no final reordena pelo número de ocorrências, colocando o maior por último

Resultado
-
O IP com maior número de requisições apareceu com a contagem mais alta ao fim do pipeline.

Flag: 66.249.73.135
