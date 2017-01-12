# DockerMonitor
===============
Monitorando Docker Host e container com [Prometheus](https://prometheus.io/), [Grafana](http://grafana.org/), [cAdvisor](https://github.com/google/cadvisor) 

Original Project BY: [Stefan Prodan](https://github.com/stefanprodan).. Thanks man, you're awesome.

Como disse acima o projeto se baseia no [dockprom](https://github.com/stefanprodan/dockprom), porém com algumas diferenças, atualmente fiz a parte de monitoramente , retirando toda a parte de Services Alert (porque não era o objetivo).

Subindo o container
-------------------
```Shell
$git clone https://github.com/gcalcettebr/dockermonitor
$cd dockermonitor
$sudo docker-compose up
```
Clone o repositorio , e rode o docker-compose.
----------------------------------------------

Subiu a parada ai?

saidinha marota \/
```Shell
grafana    | t=2017-01-12T17:30:08+0000 lvl=info msg="Initializing Alerting" logger=alerting.engine
grafana    | t=2017-01-12T17:30:08+0000 lvl=info msg="Initializing CleanUpService" logger=cleanup
grafana    | t=2017-01-12T17:30:08+0000 lvl=info msg="Initializing HTTP Server" logger=server address=0.0.0.0:3000 protocol=http subUrl=
```
Checando o docker ps 
```Shell
CONTAINER ID        IMAGE                     COMMAND                  CREATED             STATUS              PORTS                    NAMES
fb70ec6d7807        grafana/grafana           "/run.sh"                8 minutes ago       Up 8 minutes        0.0.0.0:3000->3000/tcp   grafana
b91475cc2aa9        google/cadvisor:v0.24.1   "/usr/bin/cadvisor -l"   11 minutes ago      Up 11 minutes       8080/tcp                 cadvisor
76d84c512bd8        prom/prometheus           "/bin/prometheus -con"   12 minutes ago      Up 12 minutes       0.0.0.0:9090->9090/tcp   prometheus
``` 
Subiu ae tudo bonitinho? três containers.

Bora configrar o Grafana.
Cofigurando Grafana
-------------------

Acessando [Web](http://127.0.0.1:3000/login) 127.0.0.1:3000


User: admin  pass:  changeme

![alt tag](https://github.com/gcalcettebr/dockerizando/blob/master/jpg/iniciografana.png)

Adicionando [Data Source](http://127.0.0.1:3000/datasources) do Prometheus, clica ali na "engrenagem" depois em [Data Source](http://127.0.0.1:3000/datasources).

![alt tag](https://github.com/gcalcettebr/dockerizando/blob/master/jpg/adddashboar.png)

Add Data Source
![alt tag](https://github.com/gcalcettebr/dockerizando/blob/master/jpg/adddatadource.png)

Insira a configuração do Prometheus.
OBS: Em URL troque para o Ip do seu Host.
OKAY, 
Save & Test!

![alt tag](https://github.com/gcalcettebr/dockerizando/blob/master/jpg/configdatasource.png)
Sucesso
-------

Configurando as DashBoards
--------------------------
OBS: As DashBoars são de minha autoria 0/

Bora lá!
Adicionando Dash Board, clica ali na "engrenagem" depois em [Dashboards](http://127.0.0.1:3000/dashboard/new?editview=import) e em import.

Faça o Uploado dos arquivos .json localizados na pasta [dashboard](https://github.com/gcalcettebr/dockermonitor/tree/master/dashboard)

Selecione a Data Source do Prometheus e importa a parada.
![alt tag](https://github.com/gcalcettebr/dockerizando/blob/master/jpg/dashboard2.png)
OKAY

![alt tag](https://github.com/gcalcettebr/dockerizando/blob/master/jpg/dashboardcontainers.png)
![alt tag](https://github.com/gcalcettebr/dockerizando/blob/master/jpg/hostdashboard.png)


Agora é navegar pelas DashBoards e customizá-las ainda mais =)

Vlws flws abraços.
