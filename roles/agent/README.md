### Ansible Roles: Agent
- Playbook para instalar e configurar o zabbix-agent em servidores Linux

## Sistema Operacional
- Familia Red Hat 7 x64

## Pre-requesitos
- Par de chaves keys entre as maquinas

```
$ ssh-keygen -t rsa -b 2048 -v -f keyname
```

## Role Variaveis
- As variáveis disponíveis estão listadas abaixo, juntamente com os valores padrão:
 * [grup_vars](inventory/all.yml)
 * [defaults](defaults/main.yml)

## Inventario
- Arquivo de inventario para adicionar novos hosts

```bash
[linux-hyperv]
#btu-ftp
btu-spark
btu-sg-smc
btu-nginx01
btu-nginx02
btu-appservers01
btu-appservers02
btu-docker01
btu-docker02
btu-docker03
btu-docker04
btu-gitlab
btu-jms-prd
btu-jenkins
btu-mysql1
btu-squid01
btu-squid02
```

## Playbook: deploy-user.yml
```yml
---
- name: Configurando zabbix-agent
  hosts: agentd
  gather_facts: true
  remote_user: root
  roles:
  - { role: agent }
```

## Executando playbook:
- O playbook é executado e agendado pelo propio gitlab em modo de ci/cd.

## Autor:
- [Fabio Coelho](http://gitlab.braspress.com.br/fabiocoelho-sao)
