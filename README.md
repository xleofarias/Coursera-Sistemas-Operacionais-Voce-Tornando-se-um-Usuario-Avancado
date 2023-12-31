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

  -------------------

  Semana 3

- Distribuição de Softwares
  - Existem diferentes formas de empacotar software usando ferramentas de compilação. No Windows, o software costuma ser empacotado como ".exe", ou arquivo executável. Conceito de arquivo executável não é exclusivo do Windows, mas o Windows tem sua própria implementação, na forma de "exe". Eles são criados de acordo com o formato executável portátil, ou PE, da Microsoft. Os arquivos ".exe" não só contêm instruções para o computador executar. Eles também têm texto, código de computador, imagens que o programa pode usar e possivelmente algo chamado de arquivo "msi". Um pacote de instalação da Microsoft, ou msi, é usado para guiar um programa chamado Windows Installer na instalação, manutenção e remoção de programas do sistema operacional Windows. Além de usar o assistente de configuração da GUI para guiar o usuário na instalação do programa, o instalador do Windows usa o arquivo msi para criar instruções sobre como remover o programa se o usuário quiser desinstalá-lo. Normalmente, os arquivos executáveis do Windows são pontos de partida para ativar o Windows Installer. Nesse caso, eles costumam conter só um arquivo msi e algumas instruções para iniciar o Windows Installer e ler o arquivo. Existem alternativas que são usar os executáveis como independentes, instaladores personalizados, sem arquivo msi ou sem o Windows Installer. Se estiverem empacotados assim, o arquivo ".exe" tem que conter todas as instruções de que o sistema operacional precisa para instalar o programa.
  
  - No linux, um pacote Debian é empacotado como um arquivo ".deb" para o Debian. Para instalar um pacote Debian, você terá que usar o comando "dpkg", ou pacote Debian. Exemplo sudo dpkg -i(instalar) [nome do pacote]. Para remover é sudo dpkg -r [nome do pacote].
  - Para listar os pacotes instalados usamos comando dpkg -l.

  - Alguns formatos de arquivo compactado comuns são .tar, .zip e .rar.
    
  - Arquivos compactados no Windows
    - O Windows tem ferramentas para compactar e descompactar diferentes tipos de arquivo, como ".rar", ".zip" e ".tar". Esta é a ferramenta de código aberto 7-zip.
    - Com o comando Compress-Archive -path você pode compactar um arquivo. Exemplo Compress-Archive -path  aqui é algo arquivo ou diretório é para compactar [C:\Users\leonardo\teste.txt] e aonde caso queira mandar para outro lugar ou só nomear o zip mesmo [C:\Users\leonardo\Documentos\Teste].
   
  
  - No Linux
    - O 7-Zip também está disponível para Linux. Para extrair um arquivo usando o 7-Zip, use o comando "7z" e a sinalização "e" seguidos do arquivo que você quer extrair. 7z e [arquivo]
    - O comando tar e para criar um zipado é tar -cf file.tar file1 file2 file3 o -c significa criar e o -f indica o nome que será o zip. Existe também o -v que é para mostrar o output de forma detalhada -cvf.
    - Com esse link tem tudo sobre o tar http://www.linfo.org/tar.html.
   
  - Explicação sobre o que é uma biblioteca, é uma forma de empacotar um monte de código útil que alguém escreveu. No Windows, essas bibliotecas compartilhadas são chamadas de bibliotecas de vínculo dinâmico, ou DLL. Uma grande vantagem da DLL é que a mesma DLL pode ser usada por muitos programas diferentes. Isso significa que não é preciso carregar todo esse código compartilhado na memória para cada aplicativo que deseja usá-lo, portanto, há menos consumo de memória.
  - Hoje em dia não existem mais problemas com os DLLs por causa que a maioria das bibliotecas compartilhadas e recursos do Windows são gerenciados por algo chamado assemblies lado a lado ou SxS. A maioria das bibliotecas compartilhadas fica em uma pasta em C:\Windows\WinSxS. Se um aplicativo precisar usar uma biblioteca compartilhada para executar uma tarefa, essa biblioteca será especificada em algo chamado Manifesto. Ele instrui o Windows a carregar a biblioteca da pasta SxS. O sistema SxS também suporta o acesso automático a várias versões da mesma biblioteca compartilhada. Assim, quando você instala um software, não puxa o cobertor e descobre o pé dos programas que você já tem. Além do manifesto, o sistema SSX e os instaladores agrupam dependências em seu pacote de instalação. Você pode usar um gerenciador de pacotes Windows para ajudar a instalar e reter as bibliotecas e outras dependências que seu software instalado precisa usar.
  - Usando um cmdlet de gerenciamento de pacotes do Windows chamado "Find-Package", você encontra softwares e suas dependências direto pela linha de comando. Um cmdlet é o nome que damos aos comandos do Windows PowerShell que usam o formato verbo-substantivo. Já usamos muitos cmdlets, como "get-help", "select-string" e outros. Caso tentamos localizar o pacote "sysinternals" executando o seguinte comando. Find-Package sysinternals -IncludeDependencies, dará um erro já que a fonte padrão dos pacotes no PowerShell é a galeria do PowerShell, que não contém o pacote Sysinternals. Para resolver isso precisamos falar para o PowerShell onde encontrar o sysinternals. Vamos utilizar o repositório de pacotes, o chocolatey, mas antes instalarmos qualquer pacote, precisamos adicionar uma fonte de pacotes informe ao computador onde encontrar os pacotes que queremos instalar. Como queremos usar o Chocolatey para encontrar nossos pacotes, precisamos adicioná-lo como uma fonte de pacotes. Vamos fazer isso com o comando "Register-PackageSource" do PowerShell. Digitamos "Register-PackageSource -Name chocolatey -ProviderName Chocolatey -Location http://chocolatey.org/api/v2.
  - Podemos ver se as duas fontes de software estão prontas com o comando "Get-PackageSource". Depois, tente localizar nosso pacote e suas dependências de novo com o "Find-Package, sysinternals -includeDependencies". Agora que sabemos que esse é o pacote que queremos podemos usar um cmdlet chamado "Install-Package" para instalar o Sysinternals e suas respectivas dependências.

- Gerenciadores de Pacotes

  - Um gerenciador de pacotes garante que o processo de instalação, remoção, atualização e gerenciamento de dependências de software seja o mais fácil e automático possível. Pense em como você normalmente instala um programa no computador Windows. Você deve procurar o programa em um site de buscas, acessar o site do programa e baixar e executar o instalador. Quando quer atualizar o software, você abre o programa e usa o mecanismo que ele fornece para instalar a nova versão. Muitos programas podem executar atualizações automáticas, e a Microsoft atualiza os gravados por ela através da atualização do Windows. O Chocolatey é um gerenciador de pacotes de terceiro para o Windows. Ou seja, não foi desenvolvido pela Microsoft. Ele permite instalar aplicativos Windows pela linha de comando. O Chocolatey usa a estrutura de algumas tecnologias do Windows, como o PowerShell, e permite instalar qualquer pacote ou software presente no seu repositório público.  Você pode até criar seu próprio repositório privado se precisar empacotar algo como um aplicativo interno da empresa. Ferramentas de gerenciamento de configuração, como SCCM e Puppet, até se integram ao Choclatey. Isso faz o gerenciamento de implementações de software em computadores Windows ser automático e simples. Para instalar um pacote usamos o comando "Install-Package" -Name [nome do pacote] e caso queira verificar se o pacote está tudo certo usamos o comando "Get-Package" -name [nome do pacote]. Você ainda pode desinstalar um pacote usando Uninstall-Package -Name [nome do pacote]".

  - Agora no Linux
    - O gerenciador de pacotes usado no Ubuntu, chamado "APT" ou Advanced Packaging Tool. O gerenciador de pacotes APT é usado para ampliar os recursos do pacote. Ele facilita muito a instalação de pacotes. Ele instala dependências de pacote, facilita a busca dos pacotes que podemos instalar, apaga pacotes de que não precisamos e muito mais. Para instalar um pacote usamos o sudo apt install [nome do pacote]. Para remover "sudo APT remove [nome do pacote]".
    - Com os repositório de pacotes não precisamos procurar on-line nós mesmos todos os softwares que desejamos. Os repositórios são servidores que agem como armazenamento central de pacotes. Muitos desenvolvedores de software e organizações hospedam seus softwares na internet e geram um link para o local da hospedagem. Você pode adicionar esse link à sua própria máquina para ele referenciar esse pacote ou uma lista de pacotes. Você já viu isso com o cmdlet "Register-PackageSource", com o qual adicionamos esse local do repositório do Chocolatey. O arquivo-fonte do repositório no Ubuntu é /etc/APT/sources.list. Seu computador não saberá onde procurar softwares se você não adicionar explicitamente o link desse arquivo nos pacotes ou no repositório. na pasta sources.list há links. Se você entrar nesses links, verá um diretório com diversos pacotes. O Ubuntu já contém várias fontes de repositório aqui para ajudar na instalação dos pacotes-base do sistema operacional e outras ferramentas. Se você trabalha em um ambiente Linux, existem também repositórios especiais chamados PPA, ou arquivos de pacote pessoais.
   
    - Os PPAs são hospedados nos servidores do Launchpad. O Launchpad é um site de propriedade da Canonical Limited. Ele permite que desenvolvedores de software de código aberto desenvolvam, gerenciem e distribuam softwares. Você pode adicionar PPAs como se fossem um link de repositório convencional, mas tenha um pouco de cuidado ao usá-los no lugar dos repositórios do desenvolvedor original. O software de PPA não é tão seguro quanto repositórios de fontes confiáveis como o Ubuntu. Em alguns casos, ele pode ter software defeituoso ou até malicioso. Um outro ponto importante dos repositórios é que os gerenciadores de repositório são atualizados regularmente. Se você quer ter as atualizações de pacote mais recentes, atualize seus repositórios de pacote com o comando "APT update" seguido de "APT upgrade". O comando "APT update" atualiza a lista de pacotes nos seus repositórios para você ter o software mais recente disponível, Mas não instala nem atualiza os pacotes. Para fazer isso, depois de ter uma lista atualizada de pacotes, você pode usar o "APT upgrade" para instalar todos os pacotes desatualizados automaticamente. Antes de instalar o novo software, o ideal é executar "APT update" para garantir que você receba o software mais atual para os repositórios.
    - Mais sobre PPA: https://help.launchpad.net/Packaging/PPA.
   
  - Coisas básicas de Armazenamento no Linux
    - Execute o comando **lsblk** para ver os dispositivos de transferência por blocos e sistemas de arquivos conectados ao sistema. Esse comando reúne informações sobre todos os dispositivos conectados ao sistema e exibe o resultado em uma estrutura em árvore.
   
    - <img src=>Imagem do comando lsblk</img>
   
    - Dois dispositivos de transferência por blocos (sda ou sdb) vão estar conectados à sua instância (discos). Cada um deles tem 10 GB. A coluna MOUNTPOINT mostra onde o dispositivo de transferência por blocos está montado. É um local de arquivos no disco onde os arquivos podem ser acessados pelo sistema de arquivos Linux. Nesse caso, o MOUNTPOINT (/etc/hosts) é exibido em sdb, ou seja, o segundo disco (sdb) está montado na raiz da árvore de sistemas de arquivos Linux. Sendo assim, os arquivos que você está vendo agora no sistema são desse disco.
   - O primeiro disco, sda, também está disponível, mas está desmontado (UNMOUNT). Vamos dividi-lo em duas partições. Você vai montar uma delas no sistema de arquivos para poder acessar os documentos.
   - Antes de partir para partição existe o comando **df** para conferir os discos montados no sistema. Normalmente, esse comando é usado para mostrar o espaço disponível no sistema de arquivos. Ele gera uma lista de todos os dispositivos de transferência por blocos e o espaço disponível neles. Use a opção -h para mostrar os tamanhos de arquivo em um formato legível.
   - Em vez de usar um bloco de armazenamento como um todo, é comum dividir esse bloco em partições. Elas podem ter tamanhos diferentes e ser formatadas de acordo com diversos sistemas de arquivos. Isso permite usar um único dispositivo de armazenamento para vários fins.
   - Para exibir as informações de partição, use o comando fdisk. Você também pode usar a opção -l para listar as partições do bloco. Indique o nome de um dispositivo no comando fdisk para listar as partições dele. Não esqueça do **sudo**. Para listar todas as partições contidas em /dev/sdb, adicione /dev/sdb ao comando fdisk. No meu caso sudo fdisk -l /dev/sdb.
   - Quando o comando fdisk é usado sem opções, ele oferece um ambiente com menus para criar e excluir partições.
   - **ATENÇÃO**
     - modificar partições é destrutivo e pode levar à perda de dados. Isso não é bom! Sempre faça backup dos dados antes de modificar as partições de um sistema ativo.
   - Montar e desmontar significa deixar o disponível ou indisponível em um sistema de arquivos Linux. Isso é feito com os comandos mount e umount. Antes de modificar um disco, primeiro é preciso desmontar ou seja, desconectá-lo do sistema com o comando umount. Quando as modificações estiverem concluídas, será necessário montar esse disco novamente.
   - Inicie fdisk em modo interativo e adicione o nome do disco que você quer particionar. Neste laboratório, vamos particionar /dev/sda como um disco desconectado. sudo fdisk /dev/[UNMOUNTED DRIVE].
     -  O comando fdisk será iniciado em modo interativo. Use m para receber a ajuda do comando.
     -   Você também pode usar p para exibir detalhes sobre as partições no disco.
  # Criando partição
    - sudo fdisk /dev/[UNMOUNTED DRIVE]
    - Para criar uma partição, use o controle de comando n. No entanto, como todo o espaço no disco já está alocado, será necessário liberar espaço primeiro com a exclusão das partições padrão.

    - Use o controle de comando d para excluir as partições padrão. Ao emitir o controle de comando d, o comando fdisk solicita que você digite o número de partições a excluir. Como são 12 partições, o comando fdisk seleciona automaticamente a última por padrão. Pressione Enter para excluí-la. Repita o processo até excluir todas as 12 partições. Agora você já pode criar as novas partições. Para isso, digite o controle de comando n. Indique onde você que alocar o setor de início (local da memória) da nova partição. Neste caso, pressione Enter para selecionar o valor padrão 2048. Indique o último setor para definir até onde você quer alocar a partição. O tamanho total da partição é a diferença entre o primeiro e o último setor. "Setor de disco" se refere às unidades usadas para medir o tamanho em disco. Cada setor armazena um volume fixo de dados. Em muitos discos rígidos, um setor armazena 512 bytes. Para criar a primeira partição de 1 GB, digite 2097200 (divida a partição original por 10).
    - Antes de confirmar as mudanças, mude o tipo da partição. Altere o tipo da primeira partição para Linux swap. Digite o controle de comando t para mudar o tipo e selecione a primeira partição. É possível usar o controle de comando L para ver uma lista de todos os tipos de partição.
    - Até agora, você editou a tabela de partições na memória. Use o comando q para sair do fdisk sem confirmar mudanças no disco. Você também pode usar os comandos d e n para remover e adicionar novas partições.
    - Use o comando v se quiser verificar as alterações antes de continuar.
    - Se as mudanças feitas até o momento estiverem corretas, use o comando w para fazer a confirmação no disco.

  # Formatar partições com o comando mkfs
    - Agora, você vai criar diferentes sistemas de arquivos nas novas partições. Para isso, use o comando mkfs no Linux. Existem diferentes tipos de sistemas de arquivo, e é importante conhecer todos eles, além de saber para qual função eles são adequados. Para fazer isso, use o comando lsblk novamente para localizar o disco onde você quer criar o tipo de sistema de arquivos. Formate a segunda partição de sua unidade desconectada (sdb2 ou sda2) com ext4. Para isso, execute o seguinte comando: sudo mkfs -t ext4 /dev/[UNMOUNTED DRIVE]2.
    - Agora, você pode montar /dev/[UNMOUNTED DRIVE]2 em um local no sistema de arquivos para começar a acessar os arquivos locais. Monte no diretório /home/my_drive. sudo mount /dev/[UNMOUNTED DRIVE]2 /home/my_drive
