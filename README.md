# Introdução

Este script firewall possui ação de proteção e já vem com grande opções para um rede doméstica. 
O instalador é para sistemas que usam SystemD, mais isso não lhe impede de usa-lo apenas colocar no diretório `/usr/sbin`.
O script é baseado nas regras de IPTables, se você deseja usa-lo, é importante ter um básico conhecimento sobre interfaces de rede através de bibliotecas/programas que lhe trás informações sobre quais são as interfaces de rede e suas configurações que possui em sua máquina, para poder preencher algumas variáveis que o script necessita.
Também é recomendado que se tenha uma base sobre as regras de IPTables, caso queira configurar algumas regras desse script ou inclementa-lo, mas caso não saiba, você também pode usá-lo desde que configure as variáveis corretamente.

# Configurações / Variáveis

O arquivo `src/firewall`, contem os seguintes conceitos para as variáveis:

## Rede Externa / Internet

A Rede Externa / Internet tem as seguintes variáveis nesse script:

* iface_externa_yesno
* iface_externa
* ip_externo

Se a máquina que você queira rodar este script, tem um acesso a internet diretamente, ou seja, não necessitando de outra maquina (Rede Local) para ter uma conexão, deixe a variável **iface_externa_yesno** com o valor de **yes**. 
Após isso, informe a interface da placa de rede externa, ou seja, a interface da placa de rede que é utilizada para acessar a internet na variável **iface_externa**. Informe também o seu IP de sua máquina.

## Rede Interna / Rede Local

A Rede Interna / Rede Local tem as seguintes variaveis nesse script:

* iface_interna_yesno
* iface_interna
* ip_interno

Se a máquina que você queira rodar este script, for uma máquina que acessa a internet através de outra máquina, ou seja, for uma máquina cliente,  deixe está variável a **iface_interna_yesno** com o valor de **yes** e a variável
**iface_externa_yesno** como **no** Após isso, informe a interface da placa de rede interna, ou seja, a interface da placa de rede que é utilizada para se conectar à máquina cliente, ou seja, a máquina servidor que tem o acesso a internet na variavel  **iface_interna**. Logo em seguida, na variável **ip_interno** , terás que colocar o IP de Rede Local,   

>  As demais variáveis são opcionais, você habilita o que você deseja usar no  
>  script, estão com explicações no próprio script.

# Pré requisitos

* 1 - Você terá que ter acesso de root.

* 2 - Após entrar como root, tenha certeza que sua máquina possua o IPTables instalado.

~~~shell
iptables --version
~~~

> Nota: Caso não tenha, instale!

* 3 - O script criará um serviço chamado "firewall.service", então, é importante sua maquina não ter nenhum serviço com esse nome, caso tenha, renomeia o arquivo `src/firewall` para um nome a gosto.

# Instalação

Faça um clone do projeto e entre na pasta:

~~~shell
git clone git@github.com:williamcanin/firewall-linux.git
cd "firewall-linux"
~~~

Logue-se como root (caso ainda não esteja logado):

~~~shell
$ su root
~~~

Execute o script **"init"** e opções serão mostradas:

~~~shell
Usage: init [ install [-i] | uninstall [-u] ]
~~~

Instale o Firewall:

~~~shell
bash init -i
~~~

# Usando o firewall no terminal (OPCIONAL).

* Crie um link simbólico do script "firewall" na pasta "/usr/sbin":

~~~shell
ln -s /usr/lib/systemd/scripts/firewall /usr/sbin/firewall
~~~

* Use o comando abaixo (com root) para obter a forma de uso:

~~~shell
bash firewall
~~~


# License

The MIT License (MIT)

Copyright (c) 2016 William C. Canin

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.




