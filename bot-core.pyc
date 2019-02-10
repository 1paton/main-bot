import discord
from discord.ext import commands

client= commands.Bot(command_prefix='!')


#Start Up
@client.event
async def on_ready():
    await client.change_presence(game=discord.Game(name="Beta Test"))
    print('bot is working')

#auto-role
@client.event
async def on_member_join(member):
    role =discord.utils.get(member.server.roles, name='Member')
    await client.add_roles(member, role)


#Announcement
@commands.has_role('Admin')
@client.command()
async def announce(*,msg:str):
	channel=client.get_channel('543863545826246712') #set channel to send to
	await client.send_message(channel,msg) #channel to send to, message input
#Clear Chat
@commands.has_role('Admin')
@client.command(pass_context = True)
async def clear(ctx, number):
    mgs = [] #Empty list to put all the messages in the log
    number = int(number) #Converting the amount of messages to delete to an integer
    async for x in client.logs_from(ctx.message.channel, limit = number):
        mgs.append(x)
    await client.delete_messages(mgs)

#ban member
@commands.has_role('Admin')
@client.command(pass_context = True)
async def ban(ctx, userName: discord.User):
    await client.ban(userName)
    channel=client.get_channel('543863545826246712')
    await client.send_message(channel,"A user has been banned!")
#kick member
@commands.has_role('Admin')
@client.command(pass_context = True)
async def kick(ctx, user: discord.Member):
    await client.kick(user)
    channel=client.get_channel('543863545826246712')
    await client.send_message(channel,"A user has been kicked!")
#Report Users
@commands.has_role('Member')
@client.command()
async def report(*,msg:str):
    channel=client.get_channel('543926439464927232')
    ptext="__**Reported User : **__"
    await client.send_message(channel,ptext)
    await client.send_message(channel,msg)
#https://discord.gg/C9UNnG
client.run('NTQzODU4OTc4NDcyMzI5MjI2.D0GLzg.09qRo9CHW8StNjOIZ36cOxLg_yw')
