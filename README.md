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
            
            #for comment
            bot.find_element_by_xpath('/html/body/div[3]/div[2]/div/article/div[2]/section[1]/span[2]/button/span').click()
            time.sleep(2)
            #Write in the comment box
            bot.find_element_by_xpath("/html/body/div[3]/div[2]/div/article/div[2]/section[3]/div/form/textarea").send_keys("Nice")
            time.sleep(2)
            #Click on Post
            bot.find_element_by_xpath("/html/body/div[3]/div[2]/div/article/div[2]/section[3]/div/form/button").click()
            time.sleep(5)
            
            bot.find_element_by_class_name('coreSpriteRightPaginationArrow').click()
            time.sleep(10)
            
if __name__=="__main__":
    ig_bot= TwitterBot("Enter_Username", "Password")
    ig_bot.login()
    ig_bot.like_post("Enter_hashtag_name")
