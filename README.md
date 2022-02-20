[![Build Status](https://travis-ci.org/wifiphisher/wifiphisher.svg?branch=master)](https://travis-ci.org/wifiphisher/wifiphisher)
[![Documentation Status](https://readthedocs.org/projects/wifiphisher/badge/?version=latest)](http://wifiphisher.readthedocs.io/en/latest/?badge=latest)
![Python Version](https://img.shields.io/badge/python-3.7-blue.svg)
![License](https://img.shields.io/badge/license-GPL-blue.svg)

<p align="center"><img src="https://wifiphisher.github.io/wifiphisher/wifiphisher.png" /></p>

## Sobre a Tradução
Esse projeto não é de minha autoria, apenas traduzi os arquivos html para português. Qualquer erro de tradução, ortografia, acentuação ou concordância percebido e/ou sugestões são bem-vindas.

O projeto original e todo o crédito de programação pode ser conferido no repositório oficial do GitHub:

https://github.com/wifiphisher/wifiphisher

## Sobre
<a href="https://wifiphisher.org">Wifiphisher</a> é um framework que utiliza um Ponto de Acesso falso para conduzir testes de segurança em redes Wi-Fi. Usando Wifiphisher, profissionais de segurança da informação podem facilmente se colocar na posição man-in-the-middle, testando clientes vulneráveis por ataques de associação a uma rede Wi-Fi. Wifiphisher pode ser também utilizado para atuar de forma customizada para entregar ataques com páginas de phishing para clientes com o intuito de capturar credenciais (ex.: desde login em páginas de terceiros ou senhas WPA/WPA2 compartilhadas) ou infectar o cliente com malwares.

Wifiphisher é...

* ...poderoso. Wifiphisher pode rodar por horas em um Raspberry Pi (funciona perfeitamente no Raspberry 4B e Raspberry 400 com o Kali Linux)
executando todas as técnicas modernas de associação Wi-Fi (incluindo "Evil Twin", "KARMA" e "Known Beacons"). 

* ...flexivel. Tem suporte de vários argumentos e vem com um conjunto de
páginas de phishing oriundas da comunidade para a entrega de vários cenários de ataque.  

* ...modular. Usuários podem <a href="http://wifiphisher.readthedocs.io/en/latest/extensions.html">escrever módulos simples ou complicados</a> em Python para expandir a funcionalidade da ferramenta ou <a href="http://wifiphisher.readthedocs.io/en/latest/custom_phishing_scenario.html">customizar cenários de phishing</a> para entrergar ataques a alvos específicos de forma inteiramente personalizada. 

* ...fácil de usar. Usuários avançados podem utilizar um rico conjunto de recursos oferecidos pelo Wifiphisher. Iniciantes podem começar de forma simples, executando "./bin/wifiphisher". A interface de texto interativa facilita a execução do ataque. 

* ...recursos de uma pesquisa extensiva. Ataque do tipo "Known Beacons" e "Lure10" assim como a arte da técnicas de phishing, foram encerrados por desenvolvedores, e o Wifiphisher foi a primeira ferramenta a incorporá-los. 

* ...apoiado com uma ótima comunidade de desenvolvedores e usuários.

* ...gratuito. Wifiphisher está disponível para download gratuitamente, e vem com o código-fonte completo
para que você possa estudar, modificar ou distribuir, sob os termos de licensa GPLv3.

## Patrocinadores 

Wifiphisher é gratuito e sempre será. O desenvolvimento contínuo desse projeto não seria possível sem a participação dos patrocinadores e apoiadores dos desenvolvedores:

<a href="https://www.tines.com/?utm_source=oss&utm_medium=sponsorship&utm_campaign=wifiphisher"><p align="center"><img src="https://wifiphisher.github.io/wifiphisher/tines_logo.png" /></p></a>

## Como funciona?

Phishing de Wi-Fi é dividido em duas etapas:

1. O primeiro passo envolve o processo de associação com clientes Wi-Fi inadvertidamente, 
em outras palavras obtendo a posição de man-in-the-middle (MITM). Wifiphisher usa um variado número de técnicas para alcançar esse objetivo, incluindo:
    * Evil Twin, onde Wifiphisher cria um ponto de acesso falso que se assemelha à rede Wi-Fi de maneira legítima.
    * KARMA, onde Wifiphisher se disfarça de uma rede pública procurada por clientes Wi-Fi no seu entorno.
    * Known Beacons, onde Wifiphisher transmite um dicionario de ESSIDs, que os clientes Wi-Fi se conectaram em algum momento.

    Ao mesmo tempo, Wifiphisher manda pacotes “Deauthenticate” ou “Disassociate” para interromper uma associação existente e eventualmente enganar a vítima utilizando as tecnicas descritas.

<p align="center"><img width="70%" src="https://wifiphisher.github.io/wifiphisher/diagram.jpg" /><br /><i>Executando um ataque man-in-the-middle</i></p>

2. (Opcional) Existem diferentes ataque que podem ser feitos em seguida 
uma vez que o Wifiphisher coloca o atacante na posição de man-in-the-middle.
Por exemplo, o atacante pode capturar pacotes de dados ou escanear os clientes da rede por vulnerabilidades. 

    Usando Wifiphisher, técnicas de phishing são possíveis atraves da coleta de informação
do ambiente do alvo e do usuário vítima. Por exemplo, em um dos
cenarios, Wifiphisher vai extrair informações das transmissões de frames e o cabeçalho HTTP User-Agent para dispor uma imitação de uma aplicação web de acesso
para capturar uma senha pré-compartilhada.

<p align="center"><img src="https://wifiphisher.github.io/wifiphisher/ss-webphishing.png" /><br /><i>Gerenciador de Rede baseado em interface web <a href="https://wifiphisher.org/ps/wifi_connect/">falsa</a></i></p>

## Requisitos
Para extrair o máximo de proveito do Wifiphisher são necessários os seguintes requisitos:

  - Um sistema Linux funcional. Apesar de várias pessoas fazerem a portabilidade em outras distribuições, o Kali Linux é a distribuição oficial da qual é dado suporte, já que os novos recursos são testados primeiramente nessa distribuição.
  - Um adaptador de rede que suporte AP & Monitor mode e capazes de injetar pacotes. Drivers pode suportar netlink.
  
Nota do tradutor: Apesar de o Kali Linux ser a distribuição oficial, nem todas as suas versões vêm com todas as bibliotecas para que esse programa funcione adequadamente, como distribuições mais antigas, Kali Live ISO 2021/2, Kali lite e distribuições Kali para Raspberry Pi por exemplo. O próprio processo de compilação é auto explicativo e vai orientar as bibliotecas necessárias. Para poupar trabalho foram acrescentadas duas linhas de commando que instalam  tais bibliotecas. Caso sua distribuição já tenha eles instalados esse passo simplesmente será ignorado durante o processo de instalação.

## Instalação

Para instalar essa versão traduzida siga os seguintes passos no terminal:

```bash
sudo apt-get update
sudo apt-get install libnl-3-dev libnl-genl-3-dev libssl-dev
git clone https://github.com/arm-ARMY/wifiphisher.git
cd wifiphisher 
sudo python3 setup.py install
```

Para instalar a última versão em desenvolvimento com código original (em inglês) digite os seguintes commandos:

```bash
git clone https://github.com/wifiphisher/wifiphisher.git # Download the latest revision
cd wifiphisher # Switch to tool's directory
sudo python3 setup.py install # Install any dependencies
```

Alternativamente, você pode baixar a última versão estável (em inglês) a partir do link <a href="https://github.com/wifiphisher/wifiphisher/releases">Página de versões</a>.

## Uso

Execute a ferramenta digitando `wifiphisher` ou `python bin/wifiphisher` (estando no diretorio onde a ferramenta foi instalada).

Ao executar o comando sem nenhum parâmetro, Wifiphisher vai procurar as interfaces de rede corretas e perguntar interativamente ao usuário para selecionar um ESSID alvo (de uma lista com todas as ESSIDs encontradas ao redor) assim como o cenário de phishing a executar. Por padrão, a ferramenta vai executar tanto o Evil Twin como o KARMA attacks.

***

```shell
wifiphisher -aI wlan0 -jI wlan4 -p firmware-upgrade --handshake-capture handshake.pcap
```

Use wlan0 para lançar um ponto de acesso falso e wlan4 para os ataques DOS. Selecione da lista manualmente uma rede e execute o cenário "Firmware Upgrade". Verifique que a senha compartilhada está correta checando ela no handshake, no arquivo handshake.pcap.

Útil para selecionar um adaptador de rede manualmente. O <a href="https://wifiphisher.org/ps/firmware-upgrade/">"Firmware Upgrade"</a> cenário é a maneira mais fácil de se obter a senha de uma rede protegida por senha.

***

```shell
wifiphisher --essid CONFERENCE_WIFI -p plugin_update -pK s3cr3tp4ssw0rd
```

Automaticamente selecione a interface correta. Tenha como alvo o Wi-Fi com ESSID "CONFERENCE_WIFI" e execute o cenário "Plugin Update". O Evil Twin será protegido por senha "s3cr3tp4ssw0rd".

Útil contra redes com senhas já compartilhadas (ex.: em conferências). O cenário <a href="https://wifiphisher.org/ps/plugin_update/">"Plugin Update"</a> é uma maneira fácil de entregar executáveis maliciosos (ex.: malwares contendo um reverse shell payload).

***

```shell
wifiphisher --essid "FREE WI-FI" -p oauth-login -kB
```

Lance uma rede Wi-Fi aberta com o ESSID "FREE WI-FI" e execute o cenário "OAuth Login". Além disso, use a técnica de associação Wi-Fi automática "Known Beacons". 

Útil contra vítimas em áreas públicas. O cenário <a href="https://wifiphisher.org/ps/oauth-login/">"OAuth Login"</a> é uma forma simples de capturar credenciais de redes sociais, como o FaceBook.

Obs.: esse exemplo usado ainda tem uma página phishing muito diferente da original. Se você é programador e em tem conhecimento de html sua ajuda é muito bem vinda.

A seguir estão todas as opções com suas descrições, em inglês, já que esse fork se limitou a traduzir apenas as páginas html (também disponível com 'wifiphisher -h'):


| Forma curta | Forma longa | Explicação |
| :----------: | :---------: | :-----------: |
|-h | --help| show this help message and exit |
|-i INTERFACE| --interface INTERFACE| Manually choose an interface that supports both AP and monitor modes for spawning the rogue AP as well as mounting additional Wi-Fi attacks from Extensions (i.e. deauth). Example: -i wlan1 |
|-eI EXTENSIONSINTERFACE| --extensionsinterface EXTENSIONSINTERFACE|	Manually choose an interface that supports monitor mode for running the extensions. Example: -eI wlan1|
|-aI APINTERFACE| --apinterface APINTERFACE|	Manually choose an interface that supports AP mode for spawning an AP. Example: -aI wlan0|
|-pI INTERFACE| --protectinterface INTERFACE| Specify one or more interfaces that will have their connection protected from being managed by NetworkManager.|
|-kN| --keepnetworkmanager| Do not kill NetworkManager.|
|-nE| --noextensions|	Do not load any extensions.|
|-e ESSID| --essid ESSID|	Enter the ESSID of the rogue Access Point. This option will skip Access Point selection phase. Example: --essid 'Free WiFi'|
|-pPD PHISHING_PAGES_DIRECTORY|--phishing-pages-directory PHISHING_PAGES_DIRECTORY| Search for phishing pages in this location|
|-p PHISHINGSCENARIO| --phishingscenario PHISHINGSCENARIO	|Choose the phishing scenario to run.This option will skip the scenario selection phase. Example: -p firmware_upgrade|
|-pK PRESHAREDKEY| --presharedkey PRESHAREDKEY|	Add WPA/WPA2 protection on the rogue Access Point. Example: -pK s3cr3tp4ssw0rd|
|-qS| --quitonsuccess|	Stop the script after successfully retrieving one pair of credentials.|
|-lC| --lure10-capture| Capture the BSSIDs of the APs that are discovered during AP selection phase. This option is part of Lure10 attack.
|-lE LURE10_EXPLOIT |--lure10-exploit LURE10_EXPLOIT| Fool the Windows Location Service of nearby Windows users to believe it is within an area that was previously captured with --lure10-capture. Part of the Lure10 attack.|
|-iAM| --mac-ap-interface| Specify the MAC address of the AP interface. Example: -iAM 38:EC:11:00:00:00|
|-iEM| --mac-extensions-interface| Specify the MAC address of the extensions interface. Example: -iEM E8:2A:EA:00:00:00|
|-iNM| --no-mac-randomization| Do not change any MAC address.|
|-hC|--handshake-capture|Capture of the WPA/WPA2 handshakes for verifying passphrase. Requires cowpatty. Example: -hC capture.pcap|
|-dE ESSID|--deauth-essid ESSID|Deauth all the BSSIDs in the WLAN with that ESSID.|
|-dC CHANNELS| --deauth-channels CHANNELS|Channels to deauth. Example: --deauth-channels 1,3,7|
||--logging| Enable logging. Output will be saved to wifiphisher.log file.|
|-lP LOGPATH| --logpath LOGPATH| Determine the full path of the logfile.|
|-cP CREDENTIAL_LOG_PATH|--credential-log-path CREDENTIAL_LOG_PATH|Determine the full path of the file that will store any captured credentials|
|-cM|--channel-monitor|Monitor if the target access point changes the channel.|
||--payload-path| Enable the payload path. Intended for use with scenarios that serve payloads.|
|-wP|--wps-pbc|Monitor if the button on a WPS-PBC Registrar side is pressed.|
|-wAI|--wpspbc-assoc-interface|The WLAN interface used for associating to the WPS AccessPoint.|
|-kB|--known-beacons|Perform the known beacons Wi-Fi automatic association technique.|
|-fH|--force-hostapd|Force the usage of hostapd installed in the system.|
||--dnsmasq-conf DNSMASQ_CONF|Determine the full path of dnmasq.conf file.|
|-dK|--disable-karma|Disables KARMA attack.|
|-pE|--phishing-essid|Determine the ESSID you want to use for the phishing page.|


## Screenshots

<p align="center"><img src="https://wifiphisher.github.io/wifiphisher/ss5.png" /><br /><i>Um ponto de acesso como alvo</i></p>
<p align="center"><img src="https://wifiphisher.github.io/wifiphisher/ss2.png" /><br /><i>Um ataque bem sucedido</i></p>
<p align="center"><img src="https://wifiphisher.github.io/wifiphisher/ss7.png" /><br /><i>Página falsa de <a href="https://wifiphisher.org/ps/firmware-upgrade/">router configuration page</a></i></p>
<p align="center"><img src="https://wifiphisher.github.io/wifiphisher/ss6.png" /><br /><i>Página falsa de <a href="https://wifiphisher.org/ps/oauth-login/">OAuth Login Page</a></i></p>
<p align="center"><img src="https://wifiphisher.github.io/wifiphisher/ss4.png" /><br /><i>Página falsa de <a href="https://wifiphisher.org/ps/wifi_connect/">web-based network manager</a></i></p>


## Ajuda requerida
Se você é desenvolvedor em Python ou web designer você pode ajudar os desenvovedores do projeto Wifiphisher a melhorar a ferramenta. Sinta-se livre para dar uma olhada no rastreador de bugs <a href="https://github.com/wifiphisher/wifiphisher/issues">bug tracker</a> e verá que ainda há muito o que melhorar.

Se você sabe programar, você pode ajudar os desenvolvedores do projeto <a href="https://github.com/wifiphisher/wifiphisher/issues">propondo melhorias ou relatando bugs</a>. Por favor, dê uma olhada no Guia para Relatar Bugs em <a href="https://wifiphisher.readthedocs.io/en/latest/faq.html">FAQ document</a> antes de relatar um bug já relatado. Essa ferramenta não é destinada a ser amigável com iniciantes. Certifique-se de compreender como a ferramenta funciona antes de relatar um erro.

## Créditos dos desenvolvedores
O script foi baseado em uma ideia de <a
href="https://github.com/DanMcInerney">Dan McInerney</a> ainda em 2015.

A lista completa de colaboradores pode ser vista <a href="https://github.com/wifiphisher/wifiphisher/graphs/contributors">aqui</a>.

## Licença
Wifiphisher é licenciado sob a licensa GPLv3. Veja [LICENSE](LICENSE) para mais informações.

## Status do Projeto
Wifiphisher está atualmente na versão **1.4**. Você pode baixar a versão mais recente <a href="https://github.com/wifiphisher/wifiphisher/releases/tag/v1.4">aqui</a>. Entretanto você pode clonar a esse repositório, que é  a última versão em desenvolvimento.

## Status dessa tradução (W.I.P)
Atualmente a versão usada nessa tradução foi a última versão em desenvolvimento (**1.4**). Essa tradução tambem encontra-se em fase de desenvolvimento. A pasta phishing-pages teve seus respectivos html's traduzidos. Necessita de revisão ainda. 

## AVISO
* O uso do Wifiphisher para atacar infraestruturas sem o consentimento mútuo pode ser considerado uma atividade ilegal. É responsabilidade do usuário final obedecer todas as leis aplicáveis, sejam locais, estaduais ou federais. Os autores nao assumem nenhuma responsabilidade por uso indevido ou causado por esse programa.

<b>Nota dos desenvolvedores</b>: Cuidado com sites fingindo estar relacionadas ao Wifiphisher Project. Elas podem conter malwares.

<b>Nota do tradutor</b>: Esse fork não altera o código fonte da ferramenta, nem a programação envolvida para o seu funcionamento. 
É apenas uma tradução dos links em html.

Para novidades Wifiphisher, siga os desenvolvedores em <a href="https://www.twitter.com/wifiphisher">Twitter</a> ou apoiem eles no <a href="https://www.facebook.com/Wifiphisher-129914317622032/">Facebook</a>.
