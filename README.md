import vk_api
from vk_api.longpoll import VkLongPoll, VkEventType
def write_msg(user_id, message):
    vk.method('messages.send', {'user_id': user_id, 'message': message})
    token =vk1.a.hIkRDYG2mg8w2QJd0jF4hVC4-eYQktaoBMUn6kSIn1GkKQQR-HVii0mrXzzj_81UCfiWNZHDaM-RXMe7aAvkyPNmoDvelWk-PZA4e7hZjcuA16BeTvtDOrP91e-Vtp76KUImzytjug-EDyGL99-Ed98ehW2LqOqyyltjTfQAyhnaQfOMloVWsMQ5c6UsfrS2vk = vk_api.VkApi(token=token)
vk = vk_api.VkApivk1.a.hIkRDYG2mg8w2QJd0jF4hVC4-eYQktaoBMUn6kSIn1GkKQQR-HVii0mrXzzj_81UCfiWNZHDaM-RXMe7aAvkyPNmoDvelWk-PZA4e7hZjcuA16BeTvtDOrP91e-Vtp76KUImzytjug-EDyGL99-Ed98ehW2LqOqyyltjTfQAyhnaQfOMloVWsMQ5c6UsfrS2
longpoll = VkLongPoll(vk)
for event in longpoll.listen()
 if event.type == VkEventType.MESSAGE_NEW:
  if event.to_me: я
   request = event.text
     if request == "привет":
         write_msg(event.user_id, "Хай")
         elif request == "пока":
          write_msg(event.user_id, "Пока((")
           else: 
             write_msg(event.user_id, "Не понял вашего ответа...")
             token = vk1.a.hIkRDYG2mg8w2QJd0jF4hVC4-eYQktaoBMUn6kSIn1GkKQQR-HVii0mrXzzj_81UCfiWNZHDaM-RXMe7aAvkyPNmoDvelWk-PZA4e7hZjcuA16BeTvtDOrP91e-Vtp76KUImzytjug-EDyGL99-Ed98ehW2LqOqyyltjTfQAyhnaQfOMloVWsMQ5c6UsfrS2
             vk = vk_api.VkApivk1.a.hIkRDYG2mg8w2QJd0jF4hVC4-eYQktaoBMUn6kSIn1GkKQQR-HVii0mrXzzj_81UCfiWNZHDaM-RXMe7aAvkyPNmoDvelWk-PZA4e7hZjcuA16BeTvtDOrP91e-Vtp76KUImzytjug-EDyGL99-Ed98ehW2LqOqyyltjTfQAyhnaQfOMloVWsMQ5c6UsfrS2
             longpoll = VkLongPoll(vk)
             for event in longpoll.listen():
             class VkBot:

    def __init__(self, user_id):
    
        print("Создан объект бота!")
        self._USER_ID = user_id
        self._USERNAME = self._get_user_name_from_vk_id(user_id)
        
        self._COMMANDS = ["ПРИВЕТ", "ПОГОДА", "ВРЕМЯ", "ПОКА"]
        def _get_user_name_from_vk_id(self, user_id):
    request = requests.get("https://vk.com/id"+str(user_id))
    bs = bs4.BeautifulSoup(request.text, "html.parser")
    
    user_name = self._clean_all_tag_from_str(bs.findAll("title")[0])
    
    return user_name.split()[0]
    def _get_time(self):
    request = requests.get("https://my-calend.ru/date-and-time-today")
    b = bs4.BeautifulSoup(request.text, "html.parser")
    return self._clean_all_tag_from_str(str(b.select(".page")[0].findAll("h2")[1])).split()[1]

# Получение погоды
def _get_weather(city: str = "санкт-петербург") -> list:
    request = requests.get("https://sinoptik.com.ru/погода-" + city)
    b = bs4.BeautifulSoup(request.text, "html.parser")
    
    p3 = b.select('.temperature .p3')
    weather1 = p3[0].getText()
    p4 = b.select('.temperature .p4')
    weather2 = p4[0].getText()
    p5 = b.select('.temperature .p5')
    weather3 = p5[0].getText()
    p6 = b.select('.temperature .p6')
    weather4 = p6[0].getText()
    result = ''
    result = result + ('Утром :' + weather1 + ' ' + weather2) + '\n'
    result = result + ('Днём :' + weather3 + ' ' + weather4) + '\n'
    temp = b.select('.rSide .description')
    weather = temp[0].getText()
    result = result + weather.strip()
    
    return result
    @staticmethod
def _clean_all_tag_from_str(string_line):
    """
    Очистка строки stringLine от тэгов и их содержимых
    :param string_line: Очищаемая строка
    :return: очищенная строка
    """
    result = ""
    not_skip = True
    for i in list(string_line):
        if not_skip:
            if i == "<":
                not_skip = False
            else:
                result += i
        else:
            if i == ">":
                not_skip = True
    
    return result
    def new_message(self, message):

    # Привет
    if message.upper() == self._COMMANDS[0]:
        return f"Привет-привет, {self._USERNAME}!"
    
    # Погода
    elif message.upper() == self._COMMANDS[1]:
        return self._get_weather()
    
    # Время
    elif message.upper() == self._COMMANDS[2]:
        return self._get_time()
    
    # Пока
    elif message.upper() == self._COMMANDS[3]:
        return f"Пока-пока, {self._USERNAME}!"
    
    else:
        return "Не понимаю о чем вы..."
        print("Server started")
for event in longpoll.listen():
    if event.type == VkEventType.MESSAGE_NEW:
        if event.to_me:
        
            print('New message:')
            print(f'For me by: {event.user_id}', end='')
            
            bot = VkBot(event.user_id)
            write_msg(event.user_id, bot.new_message(event.text))
            
            print('Text: ', event.text)
