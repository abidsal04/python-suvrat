# python-suvrat
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time

class TwitterBot:
    def __init__(self,username,password):
        self.username = username
        self.password = password
        self.bot = webdriver.Firefox()
         
    def login(self):
        bot = self.bot
        bot.get("https://www.instagram.com/accounts/login/")
        time.sleep(3)
        email = bot.find_element_by_name('username')
        password = bot.find_element_by_name('password')
        email.clear()
        password.clear()
        email.send_keys(self.username)
        password.send_keys(self.password)
        password.send_keys(Keys.RETURN)
        time.sleep(3)
  
    def like_post(self,hashtag):
        bot = self.bot
        bot.get('https://www.instagram.com/explore/tags/'+hashtag)
        time.sleep(5)
        bot.find_element_by_class_name('eLAPa').click()
        time.sleep(5)                                  
        for i in range(1,100):
            bot.find_element_by_class_name('fr66n').click()
            time.sleep(3)
            bot.find_element_by_class_name('coreSpriteRightPaginationArrow').click()
            time.sleep(10)
            
sv = TwitterBot('suvrat72000@gmail.com','meuandfamily')
sv.login()
time.sleep(3)
sv.like_post('codergirl')
