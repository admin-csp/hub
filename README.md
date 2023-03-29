
# Hub

Esse projeto tem como objetivo fazer uma plataforma que possibilite os clientes fazer as integrações de forma automática para o nosso marketplace na VTEX. O projeto foi desenvolvido parcialmente e atualmente está rodando numa máquina virtual na AWS. Futuramente vai integrar demais ERPs, como Captare, Sankhya e outros.

A url para acessar o lado do cliente:

- https://cliente.compresuapeca.com.br/

Neste link, é possível ver a aplicação rodando.

Para acessar o admin, basta colocar o seguinte endereço no navegador:

- admin.compresuapeca.com.br

Atualmente a plataforma já consegue fazer uma integração com a Tray.
Aqui tem um snap do login da plataforma do lado do cliente: 

![login](https://github.com/compresuapeca/hub/blob/main/assets/Captura%20de%20tela%202023-03-29%20151551.png?raw=true)


Após logar, temos a seguinte tela com o menu lateral: 

![paginaInicial](https://github.com/compresuapeca/hub/blob/main/assets/Captura%20de%20tela%202023-03-29%20152318.png?raw=true)


Quando tocamos no menu de Cadastros -> Produtos chegamos numa tela com as informações dos produtos disponíveis: 


![paginaDeProdutos](https://github.com/compresuapeca/hub/blob/main/assets/Captura%20de%20tela%202023-03-29%20152828.png?raw=true)

Outras funcionalidades podem ser encontradas dentro da plataforma, mas as vezes dão erros na comunicação com a VTEX.
Para entrar na plataforma, solicite ao Iago, Leonardo ou Hanna o usuário e o login. 

Ainda não foi possível baixar e fazer o debug, pois não temos a chave SSH de acesso ao terminal da instância no EC2 e essa chave só existe na hora da criação.

Ao entrar na AWS EC2, a aplicação pode ser encontrada em diferentes lugares. Para acessar a instância, entre no AWS, busque pelo EC2. No dashboard, clique no "intances(running)". Quando aparecer as instâncias rodando, selecione a instância de nome "ubuntu_new". Já dentro da instância, clique no botão "connect" no canto superior direito. E depois clique em "connect" novamente. 


 Para encontrar os arquivos do backend: 

```bash
cd /home/dev/net7/Coja.IDP
```

Ao rodar o comando: 
```bash
ls
# Deve ter o seguinte resultado: 
# README.md  action  docker  docs  prods-ant.xml  prods.xml  sql  src
```

Dentro da pasta "src", você consegue encontrar as pastas com o backend da aplicação. Os códigos de ASP.NET e mais.

Se quiser ter mais informações sobre o frontend, digite o seguinte comando no terminal:

```bash
cd /var/www
# Ao dar um ls
ls
# Deve ter a seguinte saída: 
# cliente.compresuapeca.com.br  csp-idp  csp-web  dump_23-03-2023_02_59_32.sql
```

Se continuar investigando esse diretório, vai encontrar informações sobre o gerenciador de design Vex que utiliza Angular.JS. 


## Stack utilizada

**Front-end:** Angular dentro do gerenciador de UI Vex.

**Back-end:** ASP.NET, JQuery, RabbitMQ.

**Database:** Postgress.

**Linguagem Principal:** C#.

**OS da instância:** Ubuntu.

No deploy na máquina virtual da AWS, foi utizado docker tanto para o banco de dados quanto para o RabbitMQ, mas o resto da aplicação está usando a VM como um todo como servidor.
