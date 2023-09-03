import discord
from discord.ext import commands
import random
from googletrans import Translator
intents = discord.Intents.all()
intents.message_content = True
import os
bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'{bot.user} olarak giriş yaptık')

@bot.event 
async def on_member_bans():
    print(f'{bot.ban} ')

@bot.command()
async def hello(ctx):
    await ctx.send(f'Merhaba {bot.user}! Ben bir botum!')

@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)


@bot.event
async def on_member_join(member):
    print(f"{member.name}")
    print(f'{member.created_at}')  

@bot.event 
async def on_message_delete(message):
    print(f"{message.content}")

@bot.command()
async def meme_at(ctx):
    meme = random.choice(os.listdir("memes"))

    f = open(f"memes/{meme}", "rb")
    
    dosya = discord.File(f)

    await ctx.send(file=dosya)




