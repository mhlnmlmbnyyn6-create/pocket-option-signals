import os
import telebot

# جلب توكن البوت من متغيرات البيئة
TOKEN = os.getenv("BOT_TOKEN")
bot = telebot.TeleBot(TOKEN)

# الرد على أمر /start
@bot.message_handler(commands=['start'])
def send_welcome(message):
    bot.reply_to(message, "مرحباً بك في بوت إشارات Pocket Option! أرسل /signal للحصول على الإشارة.")

# أمر لإرسال إشارة تجريبية
@bot.message_handler(commands=['signal'])
def send_signal(message):
    # هنا يمكنك وضع منطق جلب أو توليد الإشارات
    bot.reply_to(message, "📊 إشارة جديدة:\nالزوج: EUR/USD\nالاتجاه: صعود (CALL)\nالوقت: 5 دقائق")

# تشغيل البوت
if __name__ == '__main__':
    print("البوت يعمل الآن...")
    bot.polling()
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
