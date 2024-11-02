---- Uma apresentação de Pipeline utilizando tecnoligias Open Sources ----

- docker / jenkins / linux ubuntu

1 - step

Instala o jenkins em uma Intancia em cloud ou Vm na maquina

2 - step 

Instala o docker engine na maquina e add o user no grupo docker:

Como fazer:

    Identifique o seu usuário:
        No terminal: Use o comando ' whoami ' para descobrir o nome do seu usuário atual.

    Adicione o usuário ao grupo Docker:
        Comando:
        Bash

        sudo usermod -aG docker $USER

    Explicação:
        sudo: Executa o comando com privilégios de administrador.
        usermod: Comando para modificar as informações de um usuário.
        -a: Adiciona o usuário ao grupo.
        -G: Especifica o grupo a ser adicionado.
        docker: Nome do grupo Docker.
        $USER: Variável que representa o nome do seu usuário atual.

3 - Instale o jenkins na máquina e add ao grupo docker o jenkins:

Pré-requisitos:

    Um servidor Ubuntu: Você pode usar uma máquina virtual ou um servidor físico.
    Um usuário com privilégios sudo: Isso permite executar comandos com privilégios de root.
    Java Development Kit (JDK): O Jenkins requer o JDK para executar.

Passos para a instalação:

    Atualizar o sistema:
    Bash

    sudo apt update && sudo apt upgrade

    Use o código com cuidado.

Instalar o JDK:
Bash

sudo apt install default-jdk

Observação: Você pode precisar instalar uma versão específica do JDK, dependendo das suas necessidades. Para verificar a versão instalada, use:
Bash

java -version

Adicionar a chave GPG do repositório Jenkins:
Bash

wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -

Use o código com cuidado.
Adicionar o repositório Jenkins:
Bash

sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

Use o código com cuidado.
Instalar o Jenkins:
Bash

sudo apt update
sudo apt install jenkins

Iniciar o serviço Jenkins:
Bash

sudo systemctl start jenkins

Habilitar o serviço para iniciar na inicialização:
Bash

sudo systemctl enable jenkins

Acessar o Jenkins:

    Encontrar o endereço IP:
    Bash

    sudo netstat -tulnp | grep :8080

    Use o código com cuidado.

Acessar no navegador: Abra seu navegador e digite o endereço IP seguido da porta 8080 ou escolher uma porta de sua escolha, por exemplo: http://seu_ip:8080.
Identificando o Arquivo com Chave

A senha inicial do Jenkins é armazenada em um arquivo. Para encontrá-lo:
Bash

sudo cat /var/lib/jenkins/secrets/initialAdminPassword


Copie a senha exibida e cole-a na página do navegador.

4 - Crie um projeto com a função pipeline e baixe os plugins necessario:
- docker, docker-build-step, docker pipeline e cloudbees docker build and publish
- nodejs, OWASP Dependency-check

5 - Instala os Tools para configurar os plugin baixado conforme o a necessidade.
6 - Executa o job conforme o step apresentado no jenkinsfile
7 - Visualiza a aplicação na porta mapeada

Enjoy

------------------------------------------------------

MIT License

Copyright (c) 2022 vidushidocker

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
