Cocar
===============

Descrição: Symfony2 + Cocar

Pré-requisitos:
===============
	* Protocolo de gerência SNMP
	* Sistema de Banco de dados RRDTool
	* Agendador de tarefas cron

	- Instalação: apt-get install snmp rrdtool php5-snmp php5-json php-gd libicu-dev

Instalação (Somente o Bundle):
===============
	1 – Clone o projeto do github.
		Comando: git clone https://github.com/urucumbrasil/cocar.git

	2 – Configure os dados de acesso ao banco de dados em (app/config/parameters.yml).

	3 – Crie um novo banco de dados.
		Comando: php app/console doctrine:database:create
	
	4 – Crie as tabelas do bundle.
		Comandos: php app/console doctrine:schema:create

	5 – Atualize e instale o composer.
		Comando: php composer.phar self-update
		Comando: php composer.phar install

	6 – Instale os assets.
		Comando: php app/console assetic:dump
		Comando: php app/console assets:install –symlink

	7 – Adicione os agendamentos ao cron.
		Comando: crontab -u {usuario} schedules.txt

Configuração:
===============
	1 – Cadastre uma nova entidade no menu (Entidades).

	2 – Cadastre um novo circuito no menu (Circuitos).

Atenção:
===============
		Inicialmente os relatórios (menu Relatórios) estarão em branco, pois são gerados automaticamente 
	pelo sistema (através do cron). Geralmente este processo é executado entre 5 e 6:30 da manhã. 
		Isto é necessário por se tratar de um processo pesado, onde na parte do dia os dados são coletados, 
	e a noite são gerados os demais relatórios.

