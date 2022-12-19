import telebot
import random
import json

from telebot import types

TOKEN = 'Your TOKEN'

bot = telebot.TeleBot(TOKEN)

global place
global w

place = list()
w = list()
save = dict()

with open('save.json', 'r') as f:
    save = json.load(f)

with open("ways.txt", "r") as f:
    w = json.load(f)
    
for i in range(0, 16):
    print(w[i])

rnd = random.random()

    
keyboard = types.ReplyKeyboardMarkup(resize_keyboard = True)

@bot.message_handler(commands = ['start'])
def start_com(message):
    bot.send_message(message.chat.id, "Press start to Start", reply_markup = keyboard)
    start_button = types.KeyboardButton(text="Start")
    keyboard.add(start_button)
    bot.send_message(message.chat.id, "Start?", reply_markup = keyboard)
    save[message.chat.id] = w[0]
    open('save.json', 'w').write(json.dumps(save))
    
@bot.message_handler(commands = ['restart'])
def restart_com(message):
    restart_button = types.KeyboardButton(text = 'Restart')
    #keyboard.add(restart_button)
    save[message.chat.id] = w[0]
    open('save.json', 'w').write(json.dumps(save))

@bot.message_handler(content_types=["text"])
def game_com(message):
    global place
    remove = telebot.types.ReplyKeyboardRemove()
    keyboard = types.ReplyKeyboardMarkup(resize_keyboard = True)
    i = message.chat.id
    place = save[i]
    

    if message.text == "Забраться на гору" and place == w[1]:
        print("world sucks")
        bot.send_message(message.chat.id, text[1], reply_markup = keyboard)
        first_choice = types.KeyboardButton(text="Залезть на орла")
        keyboard.add(first_choice)  
        second_choice = types.KeyboardButton(text="Слезть с горы")
        keyboard.add(second_choice)    
        bot.send_message(message.chat.id, "choose",  reply_markup = keyboard)
        place = w[2]
    
    if message.text == "Залезть на орла" and place == w[2]:
        bot.send_message(message.chat.id, text[5], reply_markup = keyboard)
        next_button = types.KeyboardButton(text = "Next")
        keyboard.add(next_button)
        bot.send_message(message.chat.id, "Press Next Button to continue", reply_markup = keyboard)
        place = w[3]

    if place == w[3] and message.text == "Next":
        bot.send_message(message.chat.id, text[13], reply_markup = keyboard)
        next_button = types.KeyboardButton(text = "Go Next")
        keyboard.add(next_button)
        bot.send_message(message.chat.id, "Press Next Button to continue", reply_markup = keyboard)
        place = w[5]

    if place == w[5] and message.text == "Go Next":
        bot.send_message(message.chat.id, text[12], reply_markup = keyboard)

        if rnd < 0.5:
            bot.send_message(message.chat.id, "плохая концовка", reply_markup=remove)
            place = w[0]
            print("1")
        else:
            next_button = types.KeyboardButton(text = "To Next")
            keyboard.add(next_button)
            bot.send_message(message.chat.id, "Press Next Button to continue", reply_markup = keyboard)
            place = w[4] 
            print("2")
    
    if place == w[4] and message.text == "To Next" :
        bot.send_message(message.chat.id, text[14], reply_markup = keyboard)
        place = w[7]

    if message.text == "Слезть с горы" and place == w[2]:
        bot.send_message(message.chat.id, text[5], reply_markup = keyboard)
        next_button = types.KeyboardButton(text = "Next")
        keyboard.add(next_button)
        bot.send_message(message.chat.id, "Press Next Button to continue", reply_markup = keyboard)
        place = w[6]

    if place == w[6] and message.text == "Next":
        bot.send_message(message.chat.id, text[6], reply_markup = remove)
        place = w[7]

    if place == w[7]:
        bot.send_message(message.chat.id, text[15], reply_markup = remove)
        next_button = types.KeyboardButton(text = "Next ~>")
        keyboard.add(next_button)
        bot.send_message(message.chat.id, "Press Next Button to continue", reply_markup = keyboard)
        place = w[16]
    
    if message.text == "Обойти гору" and place == w[1]:
        bot.send_message(message.chat.id, text[3], reply_markup = keyboard)
        next_button = types.KeyboardButton(text = "Next")
        keyboard.add(next_button)
        bot.send_message(message.chat.id, "Press Next Button to continue", reply_markup = keyboard)
        place = w[8]
    
    if place == w[8] and message.text == "Next":
        
        first_choice = types.KeyboardButton(text = "Зайти внутрь")
        second_choice = types.KeyboardButton(text = "Остаться снаружи")
        keyboard.add(first_choice)
        keyboard.add(second_choice)
        bot.send_message(message.chat.id, text[4], reply_markup = keyboard)
        #bot.send_message(message.chat.id, "choose", reply_markup = keyboard)
        place = w[9]
    
    if message.text == "Зайти внутрь" and place == w[9]:
        bot.send_message(message.chat.id, text[7], reply_markup = keyboard)
        
        if rnd < 0.75:
            place = w[14]
        else:
            place = w[13]

    if message.text == "Остаться снаружи" and place == w[9]:
        bot.send_message(message.chat.id, text[8], reply_markup = keyboard)
        if rnd < 0.3:
            place = w[0]
            bot.send_message(message.chat.id, "плохая концовка", reply_markup=remove)
        else:
            place = w[12] 
        
    if place == w[12]:
        bot.send_message(message.chat.id, text[9], reply_markup = remove)
        place = w[13]
    
    if place == w[13]:
        bot.send_message(message.chat.id, text[12], reply_markup = keyboard)
        next_button = types.KeyboardButton(text = "Next ~>")
        keyboard.add(next_button)
        bot.send_message(message.chat.id, "Press Next Button to continue", reply_markup = keyboard)
        place = w[16]

    if place == w[14]:
        bot.send_message(message.chat.id, text[10], reply_markup=keyboard)
        first_choice = types.KeyboardButton(text = "Попробовать убежать")
        second_choice = types.KeyboardButton(text = "Сдаться")
        keyboard.add(first_choice)
        keyboard.add(second_choice)
        bot.send_message(message.chat.id, "choose", reply_markup = keyboard)
        place = w[10]

    if place == w[10] and message.text == "Попробовать убежать":
        if rnd < 0.2:
            place = w[15] 
        else:
            bot.send_message(message.chat.id, "плохая концовка", reply_markup=remove)
            bot.send_message(message.chat.id, "Try again", reply_markup=keyboard)
            place = w[0]
            
    
    if place == w[15]:
        bot.send_message(message.chat.id, text[11], reply_markup=keyboard)
        next_button = types.KeyboardButton(text = "Next ~>")
        keyboard.add(next_button)
        bot.send_message(message.chat.id, "Press Next Button to continue", reply_markup = keyboard)
        place = w[16]

    if place == w[10] and message.text == "Сдаться":
        bot.send_message(message.chat.id, "плохая концовка", reply_markup=remove)
        place = w[0]

    if place == w[16] and message.text == "Next ~>":
        bot.send_message(message.chat.id, text[16], reply_markup=remove)
        bot.send_message(message.chat.id, "to restart - /start", reply_markup = remove)

    if message.text == "Start" or place == w[0]:
        print("YES")
        bot.send_message(message.chat.id, text[0], reply_markup = keyboard) 
        first_choice = types.KeyboardButton(text="Забраться на гору")
        keyboard.add(first_choice)  
        second_choice = types.KeyboardButton(text="Обойти гору")
        keyboard.add(second_choice)
        bot.send_message(message.chat.id, "choose",  reply_markup = keyboard)
        place = w[1]
    save[i] = place
    open('save.json', 'w').write(json.dumps(save))


if __name__ == '__main__':
     bot.infinity_polling()
