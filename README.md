# Make-AI-with-Python
#Make Advanced AI using Python

# first install with pip module in cmd

# pip install pyttsx3
# pip install os
# pip install wikipedia
# pip install pyautogui
# pip install webbrowser
# pip install speech_recognition
# pip install pyaudio
# pip install keyboard
# pip install time

# Second import all in python
 
 # for speak
import pyttsx3 
 # for time
import datetime
 # for open files
import os 
# for wikipedia
import wikipedia 
# for cursor click automatic
import pyautogui 
# for open website
import webbrowser 
# for listen to respond
import speech_recognition as sr # for listen to respond
# for control keyboard
import keyboard 
# for time sleep
import time  

# make engine to speak id [0] for david voice
engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[0].id)
engine.setProperty('rate',180)


def speak(audio):
    engine.say(audio)
    engine.runAndWait()
 
# for wish 
 
def wishMe():

   hour  = int(datetime.datetime.now().hour)
   if hour>=0 and hour<12:
        speak("good morning!")

   elif  hour>=12 and hour<18:
          speak("good afternoon!")

   else:
        speak("good evening!")
   speak("I am assistant sir. Please tell me how may I help you")
   
 wishme()
 
 # for taking command for user using speech_recognition from google without internet this will not work
 
def speechr():
    r = sr.Recognizer()
    with sr.Microphone() as source:
            print("Listening...")
            r.pause_threshold = 1  
            r.energy_threshold = 4000

            audio = r.listen(source)
    try:
            print("Recogizing...")
            query = r.recognize_google(audio, language='en-in') 
            print(f"You said: {query}\n")

    except Exception as e:
        print("I did not hear that say that again please")
        speak("i did not hear that say that again please")
        return speechr()
     
    
    
# command
    
if 'hello' in query:
        speak("hello sir")
        print("Hello Sir")
        speak("how can i help you")
        
        

elif 'how are you' in query:
        speak("i am fine sir and how are you")
        print("I am fine sir, and how are you")
        
elif 'I am fine' in query:
        speak("nice to hear sir")
        print("Nice to hear sir")
        

# from pyautogui position   
elif 'close' in query:
        pyautogui.click(1343,6) # from pyautogui position

elif 'minimize' in query:
        pyautogui.click(1246,11)

# from keyboard    
elif 'open Chrome' in query:
        keyboard.press_and_release("ctrl + alt + g")

# for get cursor position
elif 'position' in query:
        pos = pyautogui.position() 
        print(pos)
        speak(pos)

# from datetime
elif 'time' in query: 
        strtime = datetime.datetime.now().strftime("%H:%M:%S") 
        speak(f"Sir the time is {strtime}\n")
        print(f"Sir the time is {strtime}\n")
        
# from webbrowser 
elif 'open YouTube' in query: 
        speak("opening youtube")
        webbrowser.open("www.youtube.com")
        print("Opened")
        
elif 'open Google' in query:
        speak("opening google")
        webbrowser.open("www.google.com")
        print("Opened")

# from os
elif 'code' in query: 
        speak("opening")
        codePath =  "C:\\Users\\pc\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"
        os.startfile(codePath)
        print("Opened")
# from time
elif 'stop 2 minutes' in query: 
             speak("ok sir")
             time.sleep(120)
             speak("speak sir")


        
   
        






