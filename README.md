<h1 align="center"> Zabbix_Khomp </h1>

Template e configração do servidor para monitorar o status do link E1 utilizando equipamentos Khomp.



<h2> Importando template Zabbix Server </h2>

Importe a template  <b>zbx_templates_Khomp.xml</b> através do Menu <b>Configurações > Templates > Import </b>


<img src="https://monops.cloud/wp-content/uploads/2021/05/PASSO-5-Importar-Templates-no-Zabbix.png">



<h2> Configurando Zabbix_agent </h2>


Inicialmente você precisa dar permissão para o Zabbix realizar consultas no asterisk como root.
Para isso, adicione as linhas abaixo no arquivo ```/etc/sudoers ``` :

```
zabbix ALL=(ALL) NOPASSWD: /usr/sbin/rasterisk
zabbix ALL=(ALL) NOPASSWD: /usr/sbin/asterisk
```
Agora, tendo permissão de root, adicione as linhas abaixo no arquivo de configuração do zabbix ```/etc/zabbiz/zabbiz_agentd.conf  ```:

```

UserParameter=khomp.link[*],sudo asterisk -rx 'khomp links show concise'|grep "B00L0$1"|cut -c 11- |grep "Ok" | wc -l

```

Basicamente este comando recebe uma variável <b>"0"</b> ou <b>"1"</b> referente ao link0 e link1, os quais desejamos receber o <b>status</b>. O zabbix_agent faz uma consulta filtrando o recebimento da resposta <b>"OK"</b>.
Caso o resultado da consulta no Asterisk seja "OK", retornará ao Zabbix o valor <b>"1"</b>, senão retornará <b>"0"</b>.

Dessa forma, o template interpretará a resposta e mostrará o status <b>"up"</b> ou <b>"down"</b>.


<img width="728" alt="Captura de tela 2022-12-08 175804" src="https://user-images.githubusercontent.com/120132737/206566891-0d6f96bb-b619-4bc1-88f0-fd8472bd10c8.png">


Siga nossas redes sociais:

# Autores

| [<img src="https://avatars.githubusercontent.com/u/120132737?v=4" width=115><br><sub>TimedoutBr(GitHub)</sub>](https://github.com/TimedoutBr) | [<img src="[https://avatars.githubusercontent.com/u/120132737?v=4](https://instagram.ffln14-1.fna.fbcdn.net/v/t51.2885-15/305575465_419970000225685_1715275509275302889_n.jpg?stp=dst-jpg_e35&_nc_ht=instagram.ffln14-1.fna.fbcdn.net&_nc_cat=101&_nc_ohc=0yYsDJwgGHoAX9sEHHc&edm=ALQROFkBAAAA&ccb=7-5&ig_cache_key=MjkyMjE0ODc5OTM5MzM0NzIwNw%3D%3D.2-ccb7-5&oh=00_AfAFp9qvLXNBP0f_g3KdvNqOx4jcmyiU6QSut4g4wiqDvw&oe=639764B4&_nc_sid=30a2ef)" width=115><br><sub>@timedout.br (Instagram)</sub>](https://www.instagram.com/timedout.br/) |  [<img src="https://media-exp1.licdn.com/dms/image/C5603AQHJIJwnDoB59g/profile-displayphoto-shrink_400_400/0/1517232864658?e=1675900800&v=beta&t=q4-0_HHTwoai450ehOCIZgsM9VhrzGni23coIk0GjDM" width=115><br><sub>Vinicius J Tavares</sub>](https://www.linkedin.com/in/vinicius-jose-tavares/) 
| :---: | :---: | :---: |
