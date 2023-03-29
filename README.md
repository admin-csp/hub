
# Hub 

Esse projeto tem como objetivo fazer uma plataforma que possibilite os clientes fazer as integrações de forma automática para o nosso marketplace na VTEX. O projeto foi desenvolvido parcialmente e atualmente está rodando numa máquina virtual na AWS e consegue fazer compatibilidade com a Tray. Futuramente vai integrar demais ERPs, como Captare, Sankhya e outros.


## Funcionalidades
- Adicionar produto

- Pesquisar por produtos

- Integração de produtos com a VTEX

- Integração de pedidos com a VTEX

- Visualização das operações anteriores

- Sistema de notificação de novas vendas


## Stack utilizada

**Front-end:** Angular dentro do gerenciador de UI Vex.

**Back-end:** ASP.NET, JQuery, RabbitMQ.

**Database:** Postgress.

**Linguagem Principal:** C#.

**OS da instância:** Ubuntu.

No deploy na máquina virtual da AWS, foi utizado docker tanto para o banco de dados quanto para o RabbitMQ, mas o resto da aplicação está usando a VM como um todo como servidor.

## Demonstração

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

## Navegando dentro da instância da EC2

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

Dentro da pasta "src", você consegue encontrar as pastas com o backend da aplicação. Os códigos de ASP.NET, RabbitMQ e mais.

Se quiser ter mais informações sobre o frontend, digite o seguinte comando no terminal:

```bash
cd /var/www
# Ao dar um ls
ls
# Deve ter a seguinte saída: 
# cliente.compresuapeca.com.br  csp-idp  csp-web  dump_23-03-2023_02_59_32.sql
```

Se continuar investigando esse diretório, vai encontrar informações sobre o gerenciador de design Vex que utiliza Angular.JS. 

#### Containers Ativos

Existem dois containers ativos rodando na VM. Um deles contém o banco de dados postgres com o nome "postgres.rpaPecas". O segundo container contém uma instância do rabbitMQ com o nome "csp.rabbitmq". Logo:

```bash
# Quando rodamos o seguinte comando:
sudo docker ps -a

# Obtemos o seguinte output: 
#                                                                      NAMES
8bd518f6f905   postgres                "docker-entrypoint.s…"   7 weeks ago   Up 2 weeks   0.0.0.0:5935->5432/tcp, :::5935->5432/tcp                                                                                                             postgres.rpaPecas
fb0b5de4ac58   rabbitmq:3-management   "docker-entrypoint.s…"   7 weeks ago   Up 2 weeks   4369/tcp, 5671/tcp, 15671/tcp, 15691-15692/tcp, 25672/tcp, 0.0.0.0:5673->5672/tcp, :::5673->5672/tcp, 0.0.0.0:15673->15672/tcp, :::15673->15672/tcp   csp.rabbitmq
```
## Melhorias

- Corrigir falhar na integração com a Tray e VTEX

- Melhorar documentação do código

- Expandir para abarcar mais ERPs

- Repensar o UI/UX da plataforma(Tem informações como agenda e clima que não fazem sentido para a nossa aplicação)

- Corrigir o erro do lado do admin. Após logar, o site da o erro 502 Gateway

- Revisar a necessidade de uma VM talvez contanerizar a aplicação e rodar no modelo de microserviços seja melhor e mais escalável

