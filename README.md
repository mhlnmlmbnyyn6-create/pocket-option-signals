import os
import telebot

TOKEN = os.getenv("BOT_TOKEN")
bot = telebot.TeleBot(TOKEN)

@bot.message_handler(commands=["start"])
def start(message):
    bot.reply_to(
        message,
        "أهلاً بك! بوت إشارات Pocket Option جاهز لاستقبال صورة الشارت."
    )

@bot.message_handler(content_types=["photo"])
def photo(message):
    bot.reply_to(
        message,
        "وصلت صورة الشارت بنجاح. سنضيف ميزة تحليل الصورة في الخطوة التالية."
    )

bot.infinity_polling()
