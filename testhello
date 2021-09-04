import random
import ast
from discord.ext import commands
import asyncio
import traceback
import discord
import inspect
import textwrap
import importlib
from contextlib import redirect_stdout
import io
import os
import re
import sys
import copy
import time
import typing
from datetime import datetime




bot = commands.Bot(command_prefix=('y!','y.','Y!','Y.'))
token = os.environ['DISCORD_BOT_TOKEN']
bot.owner_id = 541290054447005706

#エラーログ出すやつ
@bot.event
async def on_command_error(ctx, error):
    orig_error = getattr(error, "original", error)
    error_msg = ''.join(traceback.TracebackException.from_exception(orig_error).format())
    await ctx.send(error_msg)

async def is_owner(ctx):
    return ctx.author.id == 541290054447005706

@bot.command()
@commands.check(is_owner)
async def f(ctx):
    await ctx.send('::i f')
    
@bot.command()
@commands.check(is_owner)
async def a(ctx):
    await ctx.send('::atk')
    
@bot.command()
async def sinfo(ctx):
    embed = discord.Embed(title=f'**{ctx.guild.name}**の情報', color=0x404040)
    embed.add_field(name=f'サーバー人数:{len(ctx.guild.members)}人\nサーバーオーナー:{ctx.guild.owner}\nブーストされている回数:{ctx.guild. premium_subscription_count}\nブーストレベル:{ctx.guild.premium_tier}\nブーストしているメンバー:{ctx.guild.premium_subscribers}\nサーバーが作られた時間:{ctx.guild.created_at}', value=f'実行者:<@{ctx.author.id}>')
    embed.set_thumbnail(url=ctx.guild.icon_url)
    await ctx.send(embed=embed)
    
@bot.command()
async def myinfo(ctx):
    embed = discord.Embed(title=f'**{ctx.author.name}**の情報', color=0x200000)
    #embed.set_thumbnail(url=ctx.author.icon)
    await ctx.send(embed=embed)
    
@bot.command()
async def binfo(ctx):
    embed = discord.Embed(title=f'**優姫-ゆき-**の情報', color=0x1f1f1f)
    embed.add_field(name=f'このbotが認識しているユーザーの数:{len(bot.users)}', value=f'実行者:<@{ctx.author.id}>')
    await ctx.send(embed=embed)

   
    
@bot.command()
@commands.check(is_owner)
async def kick(ctx, member: discord.Member, *, reason='by優姫-ゆき-'):
    await member.kick (reason=reason)
    embed = discord.Embed(description=f'**実行者:{ctx.author}**', color=0x888000)
    await ctx.send(embed=embed)
    

bot.command()
@commands.check(is_owner)
async def ban(ctx, member: discord.Member, *, reason=message):
    await member.kick (reason=reason)
    embed = discord.Embed(description=f'**実行者:{ctx.author}**', color=0x888000)
    await ctx.send(embed=embed)

    
#@bot.event
#async def on_message(message):
    #if message.content.startswith('$greet'):
        #channel = message.channel
        #await channel.send('Say hello!')

        #def check(m):
            #return m.content == 'hello' and m.channel == channel

        #msg = await client.wait_for('message', check=check)
        #await channel.send('Hello {.author}!'.format(msg))
        
@bot.command()
async def ts(ctx):
    await ctx.send('say 1 or 2')
    
    def check(m):
        return m.content == '1' and m.channel == ctx.channel
    
    msg = await bot.wait_for('message', check=check)
    await ctx.send('いち')
    
    
    
@bot.command()
async def he(ctx):
    await ctx.send('ページ番号を送信するとhelpのページが変わります(このページは0です)')
    
    def check(m):
        return m.content == '1' and m.channel == ctx.channel
    
    await ctx.send('///')
        
#@bot.event 
#async def on_message(message):
    #if message.content.startswith('$thumb'):
        #channel = message.channel
        #await channel.send('Send me that 👍 reaction, mate')

       # def check(reaction, user):
          # return user == message.author and str(reaction.emoji) == '👍'

    #    try:
    #        reaction, user = await client.wait_for('reaction_add', timeout=60.0, check=check)
   #     except asyncio.TimeoutError:
  #          await channel.send('👎')
   #     else:
    #        await channel.send('👍')
    
@bot.command()
async def embed(ctx, *, text):
    embed = discord.Embed(description=text, color=0x800000)
    await ctx.send(embed=embed)
    await ctx.message.delete()
    
@bot.command()
async def say(ctx, *, message:discord.ext.commands.clean_content()):
    await ctx.send(message)
    await ctx.message.delete()

@bot.command()
async def ping(ctx):
    embed = discord.Embed(title='pingの測定結果',  color=0x000000)
    embed.add_field(name=f'{ctx.bot.latency * 1000} ms', value='PONG!')
    await ctx.send(embed=embed)

    
bot.remove_command("help")

@bot.command()
async def help(ctx):
    embed = discord.Embed(title='このbotのコマンドのhelpです', color=0x000000)
    embed.add_field(name='help　このコマンドを表示\n**ping**  botのping速度を測ります\n**invite**  botの招待リンク、公式サーバーのリンクを送信します\n**embed** [text] textに書いたメッセージをembedに載せて送信します\nkick [user] ユーザーをキックできます\nban [user] ユーザーをバンできます\nsinfo サーバーの情報を送信します',value='製作中です')
    await ctx.send(embed=embed)

@bot.command()
async def invite(ctx):
    embed = discord.Embed(title='このbotの招待リンク', color=0x000000)
    embed.add_field(name='下の青い文字をタップ or クリックすると招待できます。', value='[このBOTの招待](<https://discord.com/api/oauth2/authorize?client_id=728281988892721254&permissions=8&scope=bot>)\n[公式サーバー](<https://discord.gg/pSZGXqZ>)')
    await ctx.send(embed=embed)
    
@bot.command()
async def bottles(ctx, amount: typing.Optional[int] = 99, *, liquid="beer"):
    await ctx.send('{} bottles of {} on the wall!'.format(amount, liquid))
  
@bot.command()
async def htkz(ctx, amount: typing.Optional[int] = 1, *, liquid="beer"):
    await ctx.send('{}回{}をはたきます^ ^'.format(amount, liquid))
    
@bot.command()
async def prefix(ctx):
    embed = discord.Embed(title='このbotのprefix一覧', color=0x900000)
    embed.add_field(name='**y! y. Y! Y.**', value='.')
    await ctx.send(embed=embed)
    

    
@bot.event
async def on_ready():
    activity = discord.Game(name="y!help|prefix|y! y.\n owner @たつどん#2239\n 公式サーバー→discord.gg/pSZGXqZ\n ver.2.0.1", type=3)
    await bot.change_presence(status=discord.Status.idle, activity=activity)
    print("Bot is ready!")

@bot.command()
async def dice(ctx):
    await ctx.send('…')
    
@bot.command()
async def update(ctx):
    embed = discord.Embed(title='このbotの最新のアップデート情報', description='ver.2.0.2', color=0x080000)
    embed.add_field(name='prefixが大文字でも反応するようにしました', value='次回のアップデートに期待してください！\n アップデート日時|10/2 20:14')
    await ctx.send(embed=embed)
    #バージョンもくわえる！
 #botを止める用  
           

    
    
bot.run(token)
