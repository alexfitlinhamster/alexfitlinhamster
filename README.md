import discord
from discord.ext import commands
import os, random
import requests

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'Бот {bot.user} успешно запущен!')
@bot.command()
async def animal(ctx):
    animal = random.choice(os.listdir('animal'))
    with open(f'animal/{animal}', 'rb') as f:
        picture = discord.File(f)
    await ctx.send(file=picture)

@bot.command()
async def mem(ctx):
    mem = random.choice(os.listdir('image'))
    with open(f'image/{mem}', 'rb') as f:
        picture = discord.File(f)
    await ctx.send(file=picture)

@bot.command()
async def sos(ctx):
    message = '''
    Три наиболее эффективных способов уменьшить количество отходов:
    ⦁ Утилизация - береработка помогает поддерживать обращение сырья в течение нескольких жизненных циклов продукта. Это также отлично подходит для экономии энергии; на создание банки из переработанного металла уходит на 95% меньше энергии, чем из руды.
    ⦁ Повторное использование - ткань может сделать работу сотен бумажных полотенец, а многоразовая бутылка для воды может пережить тысячи одноразовых. Выбирайте универсальные альтернативы везде, где они доступны.
    ⦁ Пожертвование - многие предметы, предназначенные для свалки, по-прежнему работают нормально. Например, носимую одежду часто выбрасывают, потому что она потускнела или усохла. Пожертвование вещей, которые все еще работают, помогает уберечь их от свалок и сделать их доступными для тех, кто в них нуждается.
    '''
    await ctx.send(message)





@bot.command()
async def fuction(ctx):
    message_2 = '''
    Время разложения ТБО:
    ⦁ Пищевые отходы - до 1 месяца 
    ⦁ Газетная бумага - до 1 года
    ⦁ Картонные коробки - до 1 года
    ⦁ Бумага - 2 года 
    ⦁ Доски деревянные - до 10 лет
    ⦁ Железная арматура - до 10 лет
    ⦁ Железные банки - до 10 лет
    ⦁ Старая обувь - до 10 лет 
    ⦁ Обломки кирпича, бетона - до 100 лет 
    ⦁ Автоаккумуляторы - до 100 лет 
    ⦁ Фольга - до 100 лет 
    ⦁ Электрические батарейки - до 100 лет 
    ⦁ Резиновые покрышки - более 100 лет 
    ⦁ Пластиковые бутылки - более 100 лет
    ⦁ Полиэтиленовые пленки - 200 лет
    ⦁ Алюминиевые банки - 500 лет
    ⦁ Стекло - более 1000 лет
    '''
    await ctx.send(message_2)


def get_duck_image_url():    
    url = 'https://random-d.uk/api/random'
    res = requests.get(url)
    data = res.json()
    return data['url']


@bot.command('duck')
async def duck(ctx):
    '''По команде duck вызывает функцию get_duck_image_url'''
    image_url = get_duck_image_url()
    await ctx.send(image_url)
bot.run("MTE0NTMwOTgwMTY3MzQwMDM3MQ.GmVWCT.TebqysztIJj1D3K1i0oUxiyGTSCBGztfM1gAVY")
