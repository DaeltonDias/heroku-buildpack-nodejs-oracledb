# heroku-buildpack-nodejs-oracledb

Baixe e configure automaticamente o [oracle/node-oracledb](https://github.com/oracle/node-oracledb) e suas dependências no momento da criação do Heroku.

## oracledb

Remova a dependência `oracledb` seu `package.json`. Este buildpack o instalará depois que as bibliotecas do Oracle Instant Client forem baixadas e as variáveis ​​de ambiente adequadas forem definidas.

## heroku-buildpack-apt

As bibliotecas do Oracle Instant Client dependem de uma biblioteca compartilhada (`libaio`) que não está instalada na imagem do Heroku Cedar 14 Ubuntu por padrão. Usaremos o [heroku-buildpack-apt](https://github.com/heroku/heroku-buildpack-apt) do Heroku para baixar e instalar esta biblioteca no momento da compilação.

Use a [CLI Heroku](https://toolbelt.heroku.com/) para adicionar o `heroku-buildpack-apt` buildpack ao seu aplicativo:

    $ heroku buildpacks:add https://github.com/heroku/heroku-buildpack-apt.git [ -a APP_NAME ]

Adicione um arquivo chamado `Aptfile` à raiz do seu código-fonte com este conteúdo:

    libaio1

## heroku-buildpack-nodejs-oracledb

Use a [CLI Heroku](https://toolbelt.heroku.com/) para adicionar o `heroku-buildpack-nodejs-oracledb` buildpack ao seu aplicativo:

    $ heroku buildpacks:add https://github.com/DaeltonDias/heroku-buildpack-nodejs-oracledb.git [ -a APP_NAME ]
