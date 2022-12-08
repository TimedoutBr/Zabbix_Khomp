<h1 align="center"> Zabbix_Khomp </h1>

Template e configração do servidor para monitorar o status do link E1 utilizando equipamentos Khomp.

<h2 align="center"> Zabbix Server </h2>


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




# Autores

| [<img src="https://avatars.githubusercontent.com/u/120132737?v=4" width=115><br><sub>TimedoutBr</sub>](https://github.com/TimedoutBr) |  [<img src="https://media-exp1.licdn.com/dms/image/C5603AQHJIJwnDoB59g/profile-displayphoto-shrink_400_400/0/1517232864658?e=1675900800&v=beta&t=q4-0_HHTwoai450ehOCIZgsM9VhrzGni23coIk0GjDM" width=115><br><sub>Vinicius J Tavares</sub>](https://www.linkedin.com/in/vinicius-jose-tavares/) 
| :---: | :---: | 
