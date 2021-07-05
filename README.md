# openSUSE - Guia Básico Pós Instalação

Este breve guia pós instalação do openSUSE é voltado para iniciantes e irá ajudá-los a instalar alguns softwares e passar informações básicas sobre o sistema. As instruções que vamos ver a seguir são compatíveis com as duas versões oficiais do openSUSE: **Leap** (lançamentos periódicos) e **Tumbleweed** (lançamento contínuo).

## CONFIGURAÇÕES E APLICATIVOS BÁSICOS
### CODECS MULTIMÍDIA
A ação a seguir adiciona o repositório Packman e instala automaticamente os codecs necessários para reprodução de arquivo multimídia no openSUSE Leap e Tumbleweed.
Abra o terminal (CTRL+T) copie e cole o comando abaixo:
```sh
$ sudo zypper install opi && sudo opi codecs
```
Será perguntado algo como: 
“você quer rejeitar a chave, confiar temporariamente ou confiar sempre? [r/t/s/?]”
responda com a letra: ***s (sempre)***.

[OPI - OBS Package Installer](https://github.com/openSUSE/opi)

### NAVEGADORES DE INTERNET
As sugestões a seguir dos navegadores de internet são opcionais.

#### Chromium 
Copie e cole no terminal:

```sh
sudo zypper in chromium chromium-ffmpeg-extra
```
#### Google Chrome
Copie e cole no terminal:
1. Adicione o repositório
```sh
sudo zypper addrepo http://dl.google.com/linux/chrome/rpm/stable/x86_64 Google-Chrome
```  
2. Atualize os repositórios e instale a chave
```sh
sudo zypper ref && sudo rpm --import https://dl.google.com/linux/linux_signing_key.pub
```
3. Instale o Google Chrome
```sh
sudo zypper in google-chrome-stable
```
#### Opera
Instale o Opera pelo Gerenciador de Programa ou copie e cole no terminal:
sudo zypper in opera
#### Vivaldi
1. Baixe direto do site oficial do [Vivaldi](https://vivaldi.com/download/) e escolha “Linux RPM”. 
2. Para instalar, clique no botão direito sobre o .rpm baixado:
 Abra com > “YaST Software” e clique em “Aceitar” no botão do lado direito. 
Se aparecer um aviso “pacote corrompido”, clique em “Ignorar” para concluir a instalação.
#### Brave
Baixe direto do site oficial [Brave](https://brave.com/linux/#opensuse-15) e siga as instruções.

Obs.: Apesar do site se referir ao Leap openSUSE 15+, o Tumbleweed também foi compátivel nos meus testes.

#### FONTES MS TRUETYPE
Para trabalhos acadêmicos que exigem as normas ABNT, geralmente as fontes padronizadas são a Arial ou Times New Roman. Se precisar dessas fontes, instale:
```sh
sudo zypper install fetchmsttfonts
```
#### EXTRATORES DE ARQUIVOS
```sh
sudo zypper install rar unrar zip
```
#### JAVA JRE (OPENJDK)
```sh
sudo zypper in java-16-openjdk
```
#### SUÍTE DE ESCRITÓRIO
O LibreOffice já vem instalado no openSUSE e é uma suíte de escritório completa de código aberto compatível com o MS Office. Abaixo cito mais três excelentes alternativas gratuitas: 
* [**ONLYOFFICE**](https://www.onlyoffice.com/pt/download-desktop.aspx): ótima compatibilidade com os formatos do MS Office, é de código aberto e grátis.
* [**WPS Office**](https://www.wps.com/pt-BR/office/linux): tem uma boa compatibilidade com MS Office, é de código fechado e gratuito com anúncios.
* [**FreeOffice**](https://www.freeoffice.com/pt/baixar/aplicativos): também tem boa compatibilidade com MS Office, código fechado e é gratuito.
Caso queira instalar algum, baixe-o pelo Gerenciador de Programa ou pelo site oficial do aplicativo.

## SOFTWARES ADICIONAIS
Assim como a Play Store e a App Store são respectivamente a principal fonte confiável para instalar aplicativos no Android e do mac OS. No openSUSE, o lugar mais indicado e confiável para procurar por softwares é no próprio Gerenciador de Programa - seja pelo KDE Discover, GNOME Programa ou YaST Software.
### HABILITAR O FLATHUB
Habilitando o [Flathub](https://flatpak.org/setup/openSUSE/) teremos mais aplicativos disponíveis para instalação com formato Flatpak, como: Spotify, XMind, Zoom, Steam, Telegram, Discord, Microsoft Teams e muitos outros. Flatpak é um formato de empacotamento e distribuição de softwares em sandbox para Linux.
* Habilite para o openSUSE Plasma
1. Abra: Discover → Configuração → na parte superior “Adicionar Flathub”
* Habilite para o openSUSE GNOME
1.  Adicione o repositório
Copie e cole no terminal:
```sh
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
2. Reinicie a máquina para concluir.

### SOFTWARE DA COMUNIDADE OPENSUSE 
A segunda oção é procurar pelos pacotes mantidos pela comunidade - que são construídos no [OBS - openSUSE Build Service](https://en.opensuse.org/Portal:Build_Service). Ou claro, verificar no próprio site do aplicativo desejado.
1. Acesse: https://software.opensuse.org
2. Pesquise o software desejado, por ex.: **emacs** (editor)
3. Clique no software que procura
4. Role para baixo e verifique se tem o software para a sua versão do openSUSE
5. Encontrou? Pode clicar em **1 Click install**
6. Esta ação deve abrir o YaST Software, perguntando se você aceita instalar.

## CONHECENDO O CAMALEÃO
### DESTAQUES DO OPENSUSE
#### YaST 
É a ferramenta para administração do sistema e se destaca por sua facilidade de uso, possibilitando instalar e customizar rapidamente o sistema com alguns cliques.

Algumas funções:
* Gerenciar repositórios de software
* Adicionar impressora
* Formatar e particionar unidades
* Editar o boot/inicialização
* Configurar firewall
* Verificar os snapshots do BTRFS

#### ZYPPER
O zypper é um poderoso gerenciador de pacotes de linha de comando. Apenas para demonstração, veremos abaixo alguns comandos que podem ser executados no terminal:
```sh
comando | descrição
$ sudo zypper refresh | atualiza os repositórios
$ sudo zypper update | (execute no Leap) instala as atualizações 
$ sudo zypper dup | (execute no Tumbleweed) instala as atualizações
$ sudo zypper install nome-pacote | instala o pacote
$ sudo zypper remove nome-pacote | remove o pacote
$ sudo zypper repos | lista todos os repositórios
```
Não curtiu muito a linha de comando? Relaxa! Tudo que foi apresentado acima é perfeitamente realizado graficamente pelos gerenciadores de programas.

#### Snapper + BTRFS = rollback 😍 
No openSUSE você pode fazer um rollback (reverte mudanças do sistema para um estado anterior) caso alguma atualização quebre o sistema, por exemplo. Para a mágica acontecer, a partição raiz “/” deve ser criada em BTRFS com espaço acima de 16 GB durante a instalação do sistema. 
Caso você utilize EXT4 na raiz, por exemplo, não será possível usufruir do rollback com o Snapper. Isso não se aplica a partição “/home”, que poderá ser em XFS, BTRFS, EXT4 etc.

No link a seguir você poderá ver uma demonstração detalhada de como fazer um rollback: 
[Rollback | Btrfs no openSUSE - Fast OS](https://fastoslinux.com/2019/11/26/rollback-btrfs-no-opensuse/)

### “BEM-VINDO | WELCOME”
Assim que o sistema é iniciado aparece a tela de documentação e suporte.
Nela, você encontrará mais conteúdo de suporte, inclusive sobre drivers proprietários (como Nvidia).
Enfim, aproveite ao máximo o que o openSUSE tem a oferecer e se envolva!

### REFERÊNCIAS
* [Documentação](https://pt.opensuse.org/Portal:Documenta%C3%A7%C3%A3o)
* [Codecs do Packman](https://pt.opensuse.org/SDB:Instalar_codecs_do_Packman)
* [opi/openSUSE](https://github.com/openSUSE/opi)
* [Zypper](https://pt.opensuse.org/Zypper/Uso) 
* [Snapper](https://en.opensuse.org/openSUSE:Snapper_Tutorial)
* [Flathub](https://flathub.org/home)
* Telegram do [openSUSE Brasil](https://telegram.me/opensusebr)



