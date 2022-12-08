<h1 align="center"> Zabbix_Khomp </h1>

Template e configração do servidor para monitorar o status do link E1 utilizando equipamentos Khomp.

Inicialmente você precisa dar permissão para o zabbix realizar consultas no asterisk com permissão de root.
Para isso, adicione as linhas abaixo no arquivo /etc/sudoers :

zabbix ALL=(ALL) NOPASSWD: /usr/sbin/rasterisk
zabbix ALL=(ALL) NOPASSWD: /usr/sbin/asterisk

# Autores

| [<img src="https://avatars.githubusercontent.com/u/120132737?v=4" width=115><br><sub>TimedoutBr</sub>](https://github.com/TimedoutBr) |  [<img src="https://media-exp1.licdn.com/dms/image/C5603AQHJIJwnDoB59g/profile-displayphoto-shrink_400_400/0/1517232864658?e=1675900800&v=beta&t=q4-0_HHTwoai450ehOCIZgsM9VhrzGni23coIk0GjDM" width=115><br><sub>Vinicius J Tavares</sub>](https://www.linkedin.com/in/vinicius-jose-tavares/) 
| :---: | :---: | 
