# Comandos de analise basicos

### Caminhos com logs importantes
/var/log/auth.log (Procure Accepted e Failed)


### Comandos digitados
history (Não confiavel)

# Usuarios criados na maquina
cat /etc/passwd | grep -v nologin | grep -v false



### Grupos
cat /etc/group | grep sudo



### Sudoers possui informação dos usuários que podem rodar comandos como sudo
/etc/sudoers, ou usar o comando visudo



### analise de processos rodando
htop 
(F6 opções de organização)
(F3 search)
(t tree)

### para matar um processo use os comandos abaixo

kill -9 PID
killall PROCESS_NAME


### outra forma eficiente de saber mais detalhes de um processo é olhar a pasta /proc, ali é possível com o PID identificar detalhes do processo, abaixo alguns arquivos genéricos de processos



### FILE ANALISY
Busca de todos os arquivos alterados em janela de tempo (com exceção de .log) e ordenados

find /etc /var /usr/bin /usr/sbin /root /tmp /var/tmp -type f ! -name "*.log" -newermt "2025-01-13" ! -newermt "2025-01-16" -exec stat --format='%y %n' {} \; | sort


#Busca de scripts ordenados (Caso precise inclua a sentença -o -iname "*.py")

find / -type f \( -iname "*.php" -o -iname "*.php7" -o -iname "*.sh" -o -iname "*.elf" -o -iname "*.py" \) -exec stat --format='%y %n' {} \; | sort



### find por arquivos de usuários 

find /home -user online 




#detalhes sobre o arquivo

stat FILENAME




### VERIFICAR CONEXÕES 

### netstat

netstat -antup (-a all, -n sem resolução, -t TCP, -u UDP, -p processo)

netstat -l (portas como listen)

### verificar iptables 

iptables -L

### Verificar ultimos usuarios logados

last

last | grep logged




### VERIFICAR SERVIÇOS

### todos os serviços rodando

service --status-all

systemctl list-units --type=service

systemctl | grep running 

systemctl list-unit-files --state=enabled

systemctl list-unit-files --state=disabled

systemctl list-units --type=service --state=inactive | grep dead



### Outra forma de verificar os processos

/etc/init.d/





### Verificar processos rodando no sistema

pstree

### Analizar arquivos e conexões geradas por um processo

lsof -p 53811


### Utilizando o comando abaixo é possivel ver detalhes dos processos rodando em cada sessão

ps aux --forest

[ + ]: O serviço está ativo e em execução.

[ - ]: O serviço está inativo ou parado.

[ ? ]: O status do serviço é desconhecido ou o sistema não consegue determinar se ele está ativo ou inativo. Isso pode acontecer com serviços que não seguem a estrutura de



### servico específico rodando

service SERVICE_NAME status

systemctl status SERVICE_NAME


### history de serviços

journalctl --since "2021-05-07 00:00" --until "2021-05-07 23:59"

journalctl -u cron --since "2021-05-07 00:00" --until "2021-05-07 23:59"


### procurar o campo load nos comandos acima, após isso executar comando abaixo para mais detalhes

cat /lib/systemd/system/cron.service




### Verificar logs do serviço 

journalctl -u service-name.service


### Erradicacao, após identificar o serviço suspeito, desative-o e remova

sudo systemctl stop SERVICE_NAME

Sudo service SERVICE_NAME stop

sudo systemctl disable SERVICE_NAME

rm  FILE_NAME

sudo systemctl daemon-reload


### CRON
### listar crontabs

cat /etc/crontab

cat /etc/cron.d/*

### cada usuário pode ter sua própria crontab, use o comando abaixo 

cat /var/spool/cron/crontabs/*

cat /var/spool/cron/*


### caso exista suspeita de alguma cron ter sido excluída, é possível verificar o histórico de execução com o comando abaixo 

cat /var/log/syslog | grep CRON

### check cron jobs running

journalctl -u cron


### execucao durante uma janela 

journalctl -u cron --since "2021-05-07 00:00" --until "2021-05-07 23:59"


### Apos identificar a cron suspeita, basta excluí-la no abrindo o arquivo abaixo

crontab -e

### Caso esteja em outro usuário, utilize o comando abaixo 

 crontab -u USERNAME -e

