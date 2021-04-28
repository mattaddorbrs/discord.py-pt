.. currentmodule:: discord

.. _intro:

Introdução
==============

Essa é a documentação PT-BR para discord.py, uma biblioteca para
ajudar na criação de Aplicativos que utilizam a API do Discord.

Pré-requisitos
---------------

A discord.py funciona com o Python 3.5.3 ou versão superior. Suporte para versões antigas do Python
não é fornecido. Python 2.7 ou versão inferior não é suportada. Python 3.4 ou versão Inferior não é suportada
por causa que uma das dependências (:doc:`aiohttp <aio:index>`) não ter suporte no Python 3.4.

.. _installing:

Instalando
-----------

Para você conseguir instalar direto do PyPi: ::

    python3 -m pip install -U discord.py

Se você estiver no Windows, então deverá ser: ::

    py -3 -m pip install -U discord.py

Para conseguir o suporte de voz, você deverá usar a ``discord.py[voice]`` em vez da ``discord.py``, exemplo. ::

    python3 -m pip install -U discord.py[voice]

Em ambientes derivados do Linux, para instalar o suport de voz você precisa das seguintes dependências:

- `libffi <https://github.com/libffi/libffi>`_
- `libnacl <https://github.com/saltstack/libnacl>`_
- `python3-dev <https://packages.debian.org/python3-dev>`_

Para sistemas baseados em Debian, use o seguinte comando para conseguir as dependências:

.. code-block:: shell

    $ apt install libffi-dev libnacl-dev python3-dev

Lembre de checar suas permissões ! Talvez necessite usar o comando como Administrador (``sudo``).

Ambientes Virtuais
~~~~~~~~~~~~~~~~~~~~~

Sometimes you want to keep libraries from polluting system installs or use a different version of
libraries than the ones installed on the system. You might also not have permissions to install libraries system-wide.
For this purpose, the standard library as of Python 3.3 comes with a concept called "Virtual Environment"s to
help maintain these separate versions.

A more in-depth tutorial is found on :doc:`py:tutorial/venv`.

However, for the quick and dirty:

1. Go to your project's working directory:

    .. code-block:: shell

        $ cd your-bot-source
        $ python3 -m venv bot-env

2. Activate the virtual environment:

    .. code-block:: shell

        $ source bot-env/bin/activate

    On Windows you activate it with:

    .. code-block:: shell

        $ bot-env\Scripts\activate.bat

3. Use pip like usual:

    .. code-block:: shell

        $ pip install -U discord.py

Congratulations. You now have a virtual environment all set up.

Basic Concepts
---------------

discord.py revolves around the concept of :ref:`events <discord-api-events>`.
An event is something you listen to and then respond to. For example, when a message
happens, you will receive an event about it that you can respond to.

A quick example to showcase how events work:

.. code-block:: python3

    import discord

    class MyClient(discord.Client):
        async def on_ready(self):
            print('Logged on as {0}!'.format(self.user))

        async def on_message(self, message):
            print('Message from {0.author}: {0.content}'.format(message))

    client = MyClient()
    client.run('my token goes here')

