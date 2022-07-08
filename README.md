# ![Docker - Logo](https://www.docker.com/wp-content/uploads/2022/03/horizontal-logo-monochromatic-white.png)


## Como Docker funciona? por que tão leve?
 Ele cria uma espécie de "Máquina Virtual", porém mais leve e rápida. Basea-se em uma série de camadas formando uma imagem.

![Docker Explaining - Docker vs Lot of Virtual Machines](https://www.docker.com/wp-content/uploads/2021/11/docker-containerized-and-vm-transparent-bg.png)

Básicamente ele está em uma camada acima do Sistema operacional que contém uma aplicação específica...

Isso torna a manutenção mais simples e barata.

<br> 

### O que é um Continer?


<div style="display: flex;">
    <img 
    src="https://miro.medium.com/max/1400/0*44tYQBGpceB8sxjf.png"   height="200px">
    <div style="align-self: center;">
        <p>Primeiramente Imagem é um conjunto de camadas de instruções. É um arquivo comparado a uma snapshot em uma máquina virtual, um template.
        </p>
        <p>
        Agora, por sua vez Container é a junção de uma imagem com uma camada que salva suas alterações.
        </p>
    </div>
</div>


<br> 

### Por que tão leve?

O SO manda apenas uma certa quantidade de recursos especificados para os containers


### Como o isolamento é garantido ?

Uma palavra única:

#### Namespaces

![Explicação sobre namespaces](https://platform9.com/wp-content/uploads/2017/01/container_namespaces.png)

> Garante o isolamento do docker com a aplicação e com o SO

##### Tipos:

- PID:
    - Providencia isolamento de processos rodando em um container
- NET
    - Providencia isolamento de rede 
- IPC
    - Gerência o acesso a recursos IPC 

- MNT

    - Forece comunicação isolada do processo de memória compartilhada
- UTS
    - Garante isolamento do kernel. Age como um host separado

<br> 


### Como ele funciona sem a necessidade de instalar um novo SO
Graças ao namespace UTS, o sistema possuí um pedaço do kernel pai, porém isolado



#### Cgroups

Controlador de processos, pode ser definido manualmente e também automaticamente por cada container

---

<br> 

## Definições

Com tudo em mente vamos apronfundar mais nos conceitos!


<br> 

### O que são imagens?

Conjunto de camadas independentes.



<br> 

### O que são containers?

Uma camada superficial que guarda as informaçõe de uma imagem.


## Onde conseguir imagens?  

<a id="homeButton" class="styles__headerLogo___2ZFL4 styles__logoLink___1D6_2" href="https://hub.docker.com/" target="_blank" ><svg xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid meet" class="dicon   " style="width: 138px; height: 26px;" viewBox="0 0 138 26" data-testid="svg_DockerHubIcon"><g><g fill="#FFF" fill-rule="evenodd"><path d="M63.12 14.601c.292-.29.633-.519 1.023-.687.389-.168.806-.252 1.25-.252.402 0 .773.067 1.114.202.341.134.667.333.977.595.183.147.39.22.62.22.275 0 .501-.091.68-.275a.943.943 0 0 0 .27-.687.932.932 0 0 0-.329-.724c-.937-.83-2.048-1.245-3.332-1.245-1.412 0-2.617.5-3.615 1.502-.998 1.002-1.497 2.211-1.497 3.628 0 1.417.499 2.626 1.497 3.628.998 1.001 2.203 1.502 3.615 1.502 1.278 0 2.39-.415 3.332-1.245a.968.968 0 0 0 .302-.706.92.92 0 0 0-.95-.953 1.021 1.021 0 0 0-.602.202c-.305.263-.627.46-.968.591-.34.131-.712.197-1.114.197-.444 0-.861-.084-1.25-.252a3.199 3.199 0 0 1-1.963-2.964 3.194 3.194 0 0 1 .94-2.277zm15.771-2.267a1.055 1.055 0 0 0-.205-.307.893.893 0 0 0-.301-.206.951.951 0 0 0-.374-.073.926.926 0 0 0-.512.146l-5.46 3.564V8.312a.93.93 0 0 0-.278-.683.913.913 0 0 0-.67-.279.924.924 0 0 0-.68.28.929.929 0 0 0-.28.682v12.735c0 .262.093.488.28.678.185.189.412.283.68.283a.906.906 0 0 0 .67-.283.935.935 0 0 0 .279-.678v-3.308l1.114-.733 4.218 4.755a.88.88 0 0 0 .639.247.951.951 0 0 0 .374-.073.902.902 0 0 0 .301-.206c.085-.088.154-.19.205-.307a.885.885 0 0 0 .078-.367.97.97 0 0 0-.265-.668l-3.925-4.434 3.825-2.492c.244-.165.365-.418.365-.76a.887.887 0 0 0-.078-.367zm-21.838 5.785a3.255 3.255 0 0 1-1.702 1.718 3.08 3.08 0 0 1-1.251.257c-.45 0-.87-.086-1.26-.257a3.225 3.225 0 0 1-1.013-.691 3.284 3.284 0 0 1-.68-1.022 3.128 3.128 0 0 1-.252-1.246c0-.44.084-.855.251-1.246.168-.39.395-.731.68-1.022.286-.29.624-.52 1.014-.691.39-.171.81-.257 1.26-.257.444 0 .86.086 1.25.257a3.257 3.257 0 0 1 1.703 1.717c.168.388.251.802.251 1.242 0 .44-.083.854-.251 1.241zm.662-4.869c-1.01-1.002-2.215-1.502-3.615-1.502-1.412 0-2.617.5-3.615 1.502-.998 1.002-1.498 2.211-1.498 3.628 0 1.417.5 2.626 1.498 3.628.998 1.001 2.203 1.502 3.615 1.502 1.4 0 2.605-.5 3.615-1.502.998-.99 1.497-2.199 1.497-3.628a5.3 5.3 0 0 0-.379-1.97 5.031 5.031 0 0 0-1.118-1.658zm41.03-.861a1.797 1.797 0 0 0-.644-.39 3.775 3.775 0 0 0-.85-.197 7.268 7.268 0 0 0-.862-.054 4.97 4.97 0 0 0-1.716.293 5.234 5.234 0 0 0-1.489.842V12.7a.92.92 0 0 0-.278-.673.913.913 0 0 0-.671-.28.923.923 0 0 0-.68.28.92.92 0 0 0-.279.673v8.355a.92.92 0 0 0 .279.674c.185.186.412.28.68.28a.914.914 0 0 0 .671-.28.92.92 0 0 0 .278-.674v-4.177a3.232 3.232 0 0 1 .936-2.277c.29-.29.629-.519 1.018-.687.39-.168.807-.252 1.25-.252.451 0 .868.077 1.252.23.152.067.286.1.401.1a.95.95 0 0 0 .375-.073.89.89 0 0 0 .3-.207c.086-.088.154-.19.206-.306A.913.913 0 0 0 99 13.03a.853.853 0 0 0-.256-.641zm-16.708 3.536c.097-.336.247-.643.448-.92.2-.278.438-.516.711-.715.274-.199.576-.353.904-.463a3.175 3.175 0 0 1 2.023 0 3.279 3.279 0 0 1 1.606 1.177c.204.278.358.585.461.921h-6.153zm6.692-2.675c-1.01-1.002-2.216-1.502-3.615-1.502-1.412 0-2.618.5-3.616 1.502-.998 1.002-1.497 2.211-1.497 3.628 0 1.417.5 2.626 1.497 3.628.998 1.001 2.204 1.502 3.616 1.502 1.284 0 2.398-.415 3.341-1.245a.954.954 0 0 0 .274-.688.927.927 0 0 0-.27-.682.918.918 0 0 0-.68-.27.995.995 0 0 0-.63.238 3.011 3.011 0 0 1-.93.55 3.202 3.202 0 0 1-1.105.183c-.353 0-.693-.055-1.018-.165a3.28 3.28 0 0 1-.895-.463 3.197 3.197 0 0 1-1.164-1.635h7.23a.94.94 0 0 0 .959-.953c0-.708-.125-1.367-.374-1.974a4.991 4.991 0 0 0-1.123-1.654zm-42.988 4.87a3.245 3.245 0 0 1-1.703 1.718c-.389.17-.806.256-1.25.256-.45 0-.87-.086-1.26-.257a3.227 3.227 0 0 1-1.013-.691 3.272 3.272 0 0 1-.68-1.022 3.134 3.134 0 0 1-.251-1.246c0-.44.083-.855.25-1.246.168-.39.395-.731.68-1.022.287-.29.624-.52 1.014-.691.39-.171.81-.257 1.26-.257.444 0 .861.086 1.25.257a3.246 3.246 0 0 1 1.703 1.717c.168.388.251.802.251 1.242a3.1 3.1 0 0 1-.25 1.241zm1.2-10.77a.922.922 0 0 0-.949.953v4.571c-.925-.751-1.993-1.126-3.204-1.126-1.412 0-2.617.5-3.615 1.502-.999 1.002-1.497 2.211-1.497 3.628 0 1.417.498 2.626 1.497 3.628.998 1.001 2.203 1.502 3.615 1.502 1.4 0 2.605-.5 3.615-1.502.999-.99 1.498-2.199 1.498-3.628V8.303a.94.94 0 0 0-.959-.953zm-26.46 4.136h3.74V8.108h-3.74v3.378zm-4.419 0h3.74V8.108h-3.74v3.378zm-4.418 0h3.739V8.108h-3.74v3.378zm-4.42 0h3.74V8.108h-3.74v3.378zm-4.418 0h3.739V8.108H2.806v3.378zm4.419-4.054h3.739V4.054h-3.74v3.378zm4.419 0h3.739V4.054h-3.74v3.378zm4.418 0h3.74V4.054h-3.74v3.378zm0-4.054h3.74V0h-3.74v3.378zM31.32 9.046c-.186-1.352-.944-2.524-2.323-3.584l-.792-.525-.53.789C27 6.74 26.66 8.146 26.772 9.495c.05.474.207 1.323.698 2.069-.49.262-1.456.623-2.739.598H.14l-.049.282c-.23 1.355-.226 5.583 2.537 8.833C4.727 23.747 7.875 25 11.984 25c8.906 0 15.495-4.075 18.58-11.482 1.213.024 3.827.007 5.17-2.541.034-.058.115-.212.349-.695l.129-.264-.755-.501c-.817-.543-2.693-.742-4.137-.471z"></path><g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" opacity="0.5" font-family="Comfortaa" font-size="18" font-weight="bold"><text id="hub" fill="#FFFFFF"><tspan x="101" y="22">hub</tspan></text></g></g></g></svg></a>

O [Docker Hub](https://hub.docker.com) tem desde imagens como [Hello World](https://hub.docker.com/_/hello-world) até [A imagem oficial do Ubuntu!](https://hub.docker.com/_/ubuntu)

É o equivalente ao GitHub, só que mais aberto e útil, podendo, por exemplo baixar imagens de outros autores e ir complementando como necessitar.


### Como baixar imagens

O comando ```  docker run ``` procura a imagem selecionada nos arquivos de sua máquina, caso não encontrar ele irá baixá-la do `Docker Hub` e executará a imagem.

Sua sintaxe e retorno:
```ssh
$ docker run hello-world

Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete 
Digest: sha256:13e367d31ae85359f42d637adf6da428f76d75dc9afeb3c21faea0d976f5c651
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```    

OBS.: Com a tecnologia de camadas do Docker é possível que várias camadas sejam reutilizadas por outras imagens. Dessa forma o espaço em disco utilizando o Docker é maximizado!


Caso apenas desejar baixar a imagem é possível usar o comando `docker pull`

```ssh
$ docker pull debian

Using default tag: latest
latest: Pulling from library/debian
1339eaac5b67: Pull complete 
Digest: sha256:859ea45db307402ee024b153c7a63ad4888eb4751921abbef68679fc73c4c739
Status: Downloaded newer image for debian:latest
docker.io/library/debian:latest

``` 

"Ok, mas não retornou nada..."

Esse é o ponto, a maior parte dos containers tem a necessidade de, ao menos, inicia-los iterativamente. Eles geralmente `executam o comando inical e param`.

Para que um container fique em execução é necessário, no mínimo, ter um processo ocorrendo dentro dele.

```ssh
$ docker run -it ubuntu

root@e376259a4242:/# # Agora é possível entrar qualquer comando linux nesse terminal! 

root@e376259a4242:/# ls
bin   dev  home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  etc  lib   lib64  media   opt  root  sbin  sys  usr

root@e376259a4242:/# exit # saindo
```

### Listar Containers

O comando `docker ps ` ou `docker container ls ` lista todos os containers em execução:

```ssh
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

"Não retornou nada... e agora?"

Simples, não teve retorno pois não há nenhum container em execução!




O parâmetro `-a ` adiciona a lista todos os container que um dia foram executados. 

```ssh
CONTAINER ID   IMAGE   COMMAND   CREATED         STATUS  ...   
e376259a4242   ubuntu   "bash"   12 minutes ago  Exited (130) 8 minutes ago
```

### Parando a execução de containers

Para iniciar este teste

docker run ubuntu sleep 1d

docker ps

docker stop id

<!--
```ssh
```
-->
