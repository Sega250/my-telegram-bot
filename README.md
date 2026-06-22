# my-telegram-botimport os
import telebot

# Токен берём из переменных окружения (НЕ вшиваем в код!)
BOT_TOKEN = os.getenv("BOT_TOKEN")
bot = telebot.TeleBot(BOT_TOKEN)

@bot.message_handler(commands=["start"])
def start(message):
    bot.send_message(message.chat.id, "Привет! 👋 Я работаю 24/7.")

@bot.message_handler(content_types=["text"])
def echo(message):
    bot.send_message(message.chat.id, f"Ты написал: {message.text}")

if __name__ == "__main__":
    bot.remove_webhook()
    bot.infinity_polling(skip_pending=True)
