# Coursera-Sistemas-Operacionais-Voce-Tornando-se-um-Usuario-Avancado

Fiz esse repositório para revisar o conteúdo do curso da Coursera.

----------------------

Semana 1

- GUI - Significa Graphical User Interface ou Interface Gráfica do Usuário.
- CLI - Significa Command-line interface ou Interface de linha de comandos.

- Manipulação de Arquivos e Textos
  - No PowerShell existe o comando 'cat' pode ser usado com parametros o '-Head' e '-Tail' acrescente no final quantas linhas quer visualizar. Já no bash usamos o comando head e tail sem precisar do cat.
  - Existe un comando que faz visualizar o conteúdo de forma interativa no PowerShell é o 'more' e no bash é 'less'. Algumas das teclas mais comuns que você pode usar para navegar pela ferramenta são as teclas para cima e para baixo, page up e page down. "g": move-se para o começo de um arquivo. Dá para ver agora que estamos no começo. "G": move-se para o final de um arquivo de texto. '/' mais a palavra a ser pesquisada. Serve para pesquisar uma palavra ou frase. Se eu digitar barra e depois a palavra que quero pesquisar, consigo navegar pelo arquivo de texto em busca de palavras que correspondem à minha pesquisa. "q": serve para sair do "less" e voltar para o shell, igual à tecla "q" do comando "more" no Windows.
  - No PowerShell, vamos usar o comando "sls", ou "Select-String", para encontrar palavras ou outras sequências de caracteres e arquivos. O comando "Select-String" serve para pesquisar um texto que corresponda a um padrão que você apresenta. Pode ser uma palavra, parte de uma palavra, uma frase ou padrões mais complicados descritos por meio de uma linguagem de correspondência de padrões chamada de "Expressões Regulares".
  - Todos os processos do Windows e todos os comandos do PowerShell podem receber informações e gerar informações. Para isso, usamos algo conhecido como fluxos de entrada e de saída (input/output streams - I/O Streams).
  - Cada processo no Windows tem três fluxos diferentes:
    - Entrada padrão;
    - Saída padrão;
    - Erro padrão.
  - Você insere informações em um processo adicionando coisas no fluxo de entrada padrão, que adentra o processo. Quando o processo gera informações, ele adiciona dados ao fluxo de saída padrão, que sai do processo. Na CLI, as informações de entrada que você insere pelo teclado vão para o fluxo de entrada padrão do processo com o qual você está interagindo. Isso acontece no PowerShell, no editor de texto ou qualquer outra coisa. Depois, o processo se comunica com você colocando dados no fluxo de saída padrão, que a CLI escreve na tela à sua frente.
  - Todos os fluxos de saída são numerados:
    -  "1" é a saída padrão, que é a saída que você normalmente vê;
    -  "2" é para erro padrão ou mensagens de erro.
  - No PowerShell, podemos fazer isso redirecionando o erro padrão para $null. Ele é basicamente um buraco negro de informações. No Linux também há um arquivo especial no Linux chamado "/dev/null".

----------------------

Semana 2

#- Usuários e Grupos

  - No Windows no GUI para se mais exato existe uma ferramenta chamada "**Gerenciamento do computador**" ela é responsavel por todo o gerenciamento do computador.
  - Existe alguns menus nessa ferramenta:
    - Agendador de Tarefas: permite agendar programas e tarefas para serem executados em determinados horários, como desligar automaticamente o computador todas as noites às 11h da noite.
    - Visualizador de Eventos: é onde o nosso sistema armazena seus logs do sistema.
    - Pastas compartilhadas: mostra as pastas que os diferentes usuários da máquina compartilham uns com os outros.
    - Usuários e Grupos Locais: é aqui que faremos nosso gerenciamento de usuários e grupos.
    -  Desempenho: mostra o monitoramento dos recursos da nossa máquina, como CPU e RAM.
    -  Gerenciador de Dispositivos: é aqui que vamos gerenciar dispositivos do nosso computador, como nossas placas de rede, placas de som, monitores e muito mais.
    -  No menu Repositório, temos um submenu chamado "Gerenciamento de disco".
    -  O menu "Serviços e aplicativos" nos mostra os programas e serviços que temos disponíveis no sistema. Aqui podemos optar por habilitar ou desabilitar serviços como o DNS.
  - Agora no CLI do Windows existe alguns comandos que podemos utilizar para ter informações necessaria para administrar o computador.
    - Alguns comandos para isso:
    - Com o comando "Get-LocalUser": você pode usar a CLI para ver rapidamente a lista de usuários do computador usando o comando.
    - Com o comando "Get-LocalGroup" listará os grupos da máquina local, são todos grupos internos.
    - Com o comando Get-LocalGroupMember podemos ver quem está nesse grupo e quero ver o grupo de administradores. Exempço Get-LocalGroupMember Administradores.
    - Para fazer a troca de senha de usuários ou outras coisas podemos utilizar o comando net. Como ele é um comando do antigo DOS podemos utilizar o /? para ter informações do comando. Caso queira que o usuário troque a senha no próximo login utlizamos o comando net user [nome do usuario] e o parametro [/logonpasswordchg:yes].
    - Para criar um novo usuário utilizamos o comando net user [nome do usuário] * /add, logo após da criação  não esqueça da boa prática do parametro [/logonpasswordchg:yes].
    - Para excluir um usuário net user [nome do usuário] /del ou Remove-LocalUser [nome do usuário].

  - Agora no Linux
    - Com o comando cat podemos visulizar as informçaões quais usuarios e grupos que existem como também quem faz parte.
    - Na pasta /etc/sudoers tem todas as informações do usuário sudo.
    - Na pasta /etc/groupfile dá para ver quem tem acesso à execução do sudo visualizando.É também assim que você visualiza os membros de todos os grupos.
    - Na pasta /etc/password contém as informações do usuário.
    - Para trocar a senha de um usuário utilizamos o comando passwrd. Logo após a troca ela ficará criptografada e guardada no /etc/shadow.
    - Caso queira que no próximo login o usuário troque de senha utilizamos o comando passwrd com a flag -e que sinifica "expirar". Exemplo sudo passwrd -e leonardo.
    - Para adicionar um novo usuário no Linux, você pode usar o comando "useradd". "sudo useradd [nome do usuário]". Pode combinar com o comando "passwd" para fazer o usuário alterar a senha dele ao efetuar login.
    - Para remover o usuário, você pode usar "sudo userdel [nome do usuário]".
  
 # - Permissões

# WINDOWS

  - **Para leitura sobre ACLs:** https://learn.microsoft.com/pt-br/windows/win32/secauthz/access-control-lists?redirectedfrom=MSDN.
  - No Windows, as permissões de arquivos e diretórios são dadas usando-se listas de controle de acesso, ou "ACLs".
  - De forma mais específica, vamos trabalhar com listas de controle de acesso discricionário, ou "DACLs".
  - Arquivos e pastas do Windows também podem receber lisistas de controle de acesso do sistema, ou "SACLs". As SACLs são usadas para informar ao Windows que ele deve usar um log de eventos para fazer uma anotação cada vez que alguém acessa determinado arquivo ou pasta.
  - Você pode pensar na DACL como uma anotação sobre quem pode usar determinado arquivo e o que essa pessoa fazer com ele. Cada arquivo ou pasta tem um proprietário e uma ou mais DACLs.
  - Vamos fazer um resumo dessas permissões:
    - Leitura(R): a permissão Leitura(R) permite que você veja que o arquivo existe e permite que você leia seu conteúdo. Também permite que você leia os arquivos e diretórios de um diretório.
    - Ler e executar: a permissão "Ler e executar" permite que você leia os arquivos e, se o arquivo for executável, que você o execute. "Ler e executar" inclui a permissão "Leitura", então, se você selecionar "Ler e executar", o item "Leitura" será selecionado automaticamente.
    - "Listar conteúdo da pasta": o item "Listar conteúdo da pasta" é um alias para "Ler e executar" em um diretório. A seleção de um marcará o outro. Isso significa que você pode ler e executar arquivos nesse diretório.
    - Gravar(W): a permissão "Gravar" permite fazer alterações em um arquivo. Pode ser uma novidade para você, mas você pode ter acesso para gravar um arquivo sem ter permissão de leitura para esse arquivo. A permissão "Gravar" também permite criar subdiretórios e gravar arquivos no diretório.
    -  Modificar: a permissão "Modificar" é uma permissão curinga que inclui leitura, execução e gravação.
    -  Controle total: o usuário ou grupo com controle total pode fazer o que quiser com o arquivo. Inclui todas as permissões do "Modificar" e adiciona a capacidade de tomar a propriedade de um arquivo e alterar suas ACLs.
    - Se quisermos ver quais ACLs estão atribuídas a um arquivo, podemos usar um utilitário criado para visualizar e alterar as ACLs chamado de "ICACLs", ou "ACLs de mudança aprimorada".
    - Com o comando icacls podemos ver no CLI quem tem permissão para tal pasta ou arquivo. Por exemplo icacls C:\Users\leofa\AdaTech\.
  - No PowerShell para fazer a troca de permissão precisamos utilizar o comando icacls '[o arquivo ou o caminho absoluto]' /grant e, com aspas simples, '[nome do grupo]: (OI)(CI)(R)'. No PowerShell utilizamos aspas simples.
  - No Prompt "[o arquivo ou o caminho absoluto]" /grant [nome do grupo]:(IO)(CI)(R). No Prompt precisamos utilizar as aspas duplas.
  - Para remover algum grupo das permissões  icacls 'C:\Vaction Pictures' /remove [nome do grupo].
  - Link para entender melhor sobre permissões: https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732880(v=ws.11)?redirectedfrom=MSDN

# LINUX

- Existem 3 permissões diferentes que você pode ter no Linux:
  -  Leitura: permite que alguém leia o conteúdo de um arquivo ou pasta.
  -  Escrita: permite que alguém grave informações em um arquivo ou pasta.
  -  Execução: permite que alguém execute um programa.
- "-rwxrw-r--". Há 10 bits aqui, cada um desses é um bit, se tiver com o "traço" é por causa que bit está desligado.
  - O primeiro é o tipo de arquivo. Neste exemplo, "-" significa que o arquivo que estamos vendo é apenas um arquivo normal. Às vezes você pode ver "d", que significa diretório. Os próximos nove bits são nossas permissões, que estão agrupadas em trios. O primeiro trio refere-se à permissão do proprietário do arquivo. O segundo trio refere-se à permissão do grupo ao qual este arquivo pertence. O último trio refere-se à permissão de todos os outros usuários. O "r" significa legível, "w" significa gravável e "x" significa executável.

- No Linux, mudamos as permissões usando o comando "chmod", que vem de "modo de alteração".
  - Primeiro, escolha qual conjunto de permissões você quer mudar:
    - O proprietário, que é representado por "u".
    - O grupo ao qual o arquivo pertence, que é representado por "g".
    - Os outros usuários, que são representados por "o".
    - Para adicionar ou remover permissões, basta usar um sinal de mais ou de menos para indicar quem a permissão afeta.
    - Exemplo: chmod u+x [nome do arquivo ou diretório].
  - O equivalente numérico de "rwx":
    - 4 para "ler" ou "r";
    - 2 para gravar ou "w";
    - 1 para executar ou "x".
    - Para definir permissões, adicionamos esses números para cada conjunto de permissões que queremos afetar. Vamos ver um exemplo.
    - chmod 7(aqui o arquivo ficará com o rwx, para isso somamos as permissões e assim por adiante). chmod 7(rwx)6(rw)1(x) [nome do arquivo ou diretório].
  - O comando "chown", que vem de "mudar proprietário", permite que você mude o dono de um arquivo. Exemplo chown [nome do novo proprietário] [nome do arquivo].
  - O comando "chgrp",  que vem de "mudar grupo". Exemplo chgrp [nome do grupo] [arquivo].
  -  Um bit de permissão especial conhecido como "setuid", podemos permitir que os arquivos sejam executados pela permissão do proprietário do arquivo. O "s" significa "setuid". Quando o "s" é colocado no lugar do que seria um bit irregular, ele nos permite executar o arquivo com as permissões do proprietário do arquivo. Para ativar o bit "setuid", você pode fazê-lo simbolicamente ou numericamente. O formato simbólico usa "s", enquanto o formato numérico usa um "4". Exemplo chmod 4755 [nome do arquivo].
  -  Você pode executar um arquivo usando permissões de grupo com "setgid", que vem de "definir ID de grupo". Isso permite que você execute um arquivo como membro do grupo desse arquivo. O bit "setgid" que significa que quando este programa é executado, ele é executado como o grupo que você escolher". Para ativar o bit "setgid", você pode fazer algo parecido com o "setuid". A única diferença é que o formato numérico usa "2". Então, chmod 2755 [nome do arquivo].
  -  Último bit de permissão especial que devemos apresentar, que é o "sticky bit". Este bit fixa um arquivo ou uma pasta. Ele faz com que qualquer um possa gravar em um arquivo ou pasta, mas não possa excluir nada. Apenas o dono ou o root podem excluir qualquer coisa. Ele é representado pelo 't'. Você também pode ativar o "sticky bit" usando o formato numérico ou simbólico. O bit simbólico é o "t", e o bit numérico é "1". Exemplo chmod 1755 [nome do arquivo].
