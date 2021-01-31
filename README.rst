discord.py
==========

.. image:: https://discord.com/api/guilds/336642139381301249/embed.png
   :target: https://discord.gg/r3sSKJJ
   :alt: Discord server invite
.. image:: https://img.shields.io/pypi/v/discord.py.svg
   :target: https://pypi.python.org/pypi/discord.py
   :alt: PyPI version info
.. image:: https://img.shields.io/pypi/pyversions/discord.py.svg
   :target: https://pypi.python.org/pypi/discord.py
   :alt: PyPI supported Python versions

Uma API wrapper moderna, fácil de usar, rica em funcionalidades, e assíncrona para o Discord, escrita em Python.

Funcionalidades
----------------

- API moderna e Pythonica usando a sintaxe ``async`` e ``await``
- Tratamento adequado de ratelimits.
- Cobertura de 100% da API suportada do Discord.
- Otimizado tanto em velocidade quanto memória.

Instalação
----------

**Python 3.5.3 ou maior é necessário**

Para instalar a biblioteca sem completo suporte de voz, você pode apenas executar o comando seguinte:

.. code:: sh

    # Linux/macOS
    python3 -m pip install -U discord.py

    # Windows
    py -3 -m pip install -U discord.py

Caso contrário, para incluir suporte á voz você deverá executar o comando seguinte:

.. code:: sh

    # Linux/macOS
    python3 -m pip install -U "discord.py[voice]"

    # Windows
    py -3 -m pip install -U discord.py[voice]


Para instalar a versão de desenvolvimento, faça o seguinte:

.. code:: sh

    $ git clone https://github.com/Rapptz/discord.py
    $ cd discord.py
    $ python3 -m pip install -U .[voice]


Pacotes opcionais
~~~~~~~~~~~~~~~~~~

* PyNaCl (para suporte á voz)

Lembre-se que para instalar voz no linux você deve instalar os seguintes pacotes pelo seu gerenciador de pacotes favorito (ex. ``apt``, ``dnf``, etc) antes de executar os comandos abaixo.

* libffi-dev (ou ``libffi-devel`` em alguns sistemas)
* python-dev (ex. ``python3.6-dev`` para Python 3.6)

Exemplo rápido
---------------

.. code:: py

    import discord

    class MyClient(discord.Client):
        async def on_ready(self):
            print('Logado como', self.user)

        async def on_message(self, message):
            # não responda a nós mesmos
            if message.author == self.user:
                return

            if message.content == 'ping':
                await message.channel.send('pong')

    client = MyClient()
    client.run('token')

Exemplo de bot
~~~~~~~~~~~~~~~~

.. code:: py

    import discord
    from discord.ext import commands

    bot = commands.Bot(command_prefix='>')

    @bot.command()
    async def ping(ctx):
        await ctx.send('pong')

    bot.run('token')

Você pode encontrar mais exemplos na pasta exemplos.

Links
------

- `Documentação <https://discordpy-pt.readthedocs.io/pt/latest/index.html>`_
- `Servidor oficial do Discord <https://discord.gg/r3sSKJJ>`_
- `API do Discord <https://discord.gg/discord-api>`_
