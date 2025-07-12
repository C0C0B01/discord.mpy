discord.mpy
==========

.. image:: https://discord.com/api/guilds/336642139381301249/embed.png
   :target: https://discord.gg/6cN7wKa8gp
   :alt: Discord server invite

A modern, easy to use, feature-rich, and async ready API wrapper for Discord written in MicroPython.

Key Features
-------------

- Modern Pythonic API using ``async`` and ``await``.
- Proper rate limit handling.
- Optimised in both speed and memory.
- Support for Rpi Pico 2W (Rpi Pico W support planned)

Installing
----------

Voice is not supported due to it probably making your Rpi explode O_O

.. code:: sh

    # MicroPython
    mip.install("github:C0C0B01/discord.mpy/tree/master/dist")


Quick Example
--------------

.. code:: py

    import mip
    mip.install("C0C0B01/discord.mpy")
    import discord

    class MyClient(discord.Client):
        async def on_ready(self):
            print('Logged on as', self.user)

        async def on_message(self, message):
            # don't respond to ourselves
            if message.author == self.user:
                return

            if message.content == 'ping':
                await message.channel.send('pong')

    intents = discord.Intents.default()
    intents.message_content = True
    client = MyClient(intents=intents)
    client.run('token')

Bot Example
~~~~~~~~~~~~~

.. code:: py

    import mip
    mip.install("C0C0B01/discord.mpy")
    import discord
    from discord.ext import commands

    intents = discord.Intents.default()
    intents.message_content = True
    bot = commands.Bot(command_prefix='>', intents=intents)

    @bot.command()
    async def ping(ctx):
        await ctx.send('pong')

    bot.run('token')

You can find more examples in the examples directory.
