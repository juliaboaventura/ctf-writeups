Descrição do desafio
-
"Você recebeu um conjunto de arquivos com capturas de pacotes de rede de um administrador que reportou ter sido noticiado, em alguns momentos, sobre a necessidade de atualizar um serviço Microsoft a fim de mitigar uma falha de Buffer Overflow, capaz de causar desligamento inesperado do sistema, infecção por vírus e execução remota de código."

Raciocínio
-
Como o enunciado informa que a URL foi indicada pelo fabricante, parti da hipótese de que essa informação estaria em alguma comunicação da Microsoft. 

Inicialmente, procurei por tráfegos HTTP e SMTP que contivessem referências à Microsoft ou algum link relacionado a atualizações, mas não encontrei nenhuma evidência relevante.

Em seguida, utilizei o recurso Statistics → Protocol Hierarchy do Wireshark para analisar os protocolos presentes em cada captura. O objetivo era identificar algum protocolo incomum que pudesse conter mensagens relacionadas ao aviso.

Na captura The_Miner_6.pcap, encontrei o protocolo Microsoft Message Service, identificado no Wireshark como Messenger.

Ao abrir cada conversa utilizando Follow → UDP Stream, foi possível visualizar diversas mensagens contendo URLs, entre elas:

http://www.fixwinreg.com

http://SwipeSpy.com

http://WWW.WUPDATE.NET

A última mensagem fazia referência direta ao download de um patch de atualização, sendo essa a URL indicada na captura.


Descrição do desafio
-
"Em um dos PCAPs consta um tráfego TCP de um protocolo usado para transferência de arquivos que trafega as informações em texto claro (sem criptografia), tornando visível a senha do usuário anonymous."

Raciocínio
-
Como o enunciado menciona um protocolo de transferência de arquivos que transmite credenciais em texto claro, concentrei a análise no protocolo FTP.

Percorri os arquivos PCAP aplicando o filtro ftp

Na captura The_Miner_13.pcap, foi possível identificar uma tentativa de autenticação FTP. Como o protocolo não utiliza criptografia, os comandos de login aparecem em texto claro, incluindo as credenciais enviadas pelo cliente.

A sequência de autenticação revelou o usuário anonymous e a senha utilizada.

