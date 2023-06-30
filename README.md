# Coursera-Sistemas-Operacionais-Voce-Tornando-se-um-Usuario-Avancado

Fiz esse repositório para revisar o conteúdo do curso da Coursera.

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

Semana 2

  - Usuários e Grupos
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

    - Agora no Linux
      - Com o comando cat podemos visulizar as informçaões quais usuarios e grupos que existem como também quem faz parte.
      - Na pasta /etc/sudoers tem todas as informações do usuário sudo.
      - Na pasta /etc/groupfile dá para ver quem tem acesso à execução do sudo visualizando.É também assim que você visualiza os membros de todos os grupos.
      - Na pasta /etc/password contém as informações do usuário.
