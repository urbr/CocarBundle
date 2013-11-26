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
------------

1 – Adicione a seguinte linha ao seu composer.json
```js
//composer.json
{
    //...

    "require": {
        //...
        "gerenciador-redes/cocar-bundle": "dev-master"
    }

    //...
}
```
	
2 – Atualize e instale o composer.

        php composer.phar self-update
        php composer.phar install

3 - Adicione o CocarBundle ao seu AppKernel.php
```php
<?php
        public function registerBundles()
        {
                $bundles = array(
                        //...
                        new GerenciadorRedes\Bundle\CocarBundle\CocarBundle()
                );
        }
```

4 – Configure a rota do CocarBundle em (app/config/routing.yml)
```php
        CocarBundle_cocar_annotation:
            resource: "@CocarBundle/Resources/config/routing.yml"
            prefix:   /
```

4 – Configure os dados de acesso ao banco de dados em (app/config/parameters.yml).

4 – Crie um novo banco de dados.

        php app/console doctrine:database:create

5 – Crie as tabelas do bundle.

        php app/console doctrine:schema:create

6 – Instale os assets.

        php app/console assetic:dump
        php app/console assets:install –symlink

7 – Adicione os agendamentos ao cron.

Atenção: Verifique os caminhos existentes em "schedules.txt" antes de adicioná-lo ao cron.

        crontab -u {usuario} schedules.txt

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

