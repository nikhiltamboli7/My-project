# To study Basic operations of Speech



# Objectives:

# 1. Speech to Text Conversion
# 2. Storing same Speech as Text file
# 3. Recording of same Speech as .mp3
# 4. Read the Speech from same Text file


import gtts, pyttsx3           #TTS module
import os, sys
import re
import speech_recognition as sr #STT Module
import pywinauto



print(os.getcwd(),"\n")

    # Speech to Text Conversion

r=sr.Recognizer()                 # Initialize recognizer

with sr.Microphone() as source:   # Used Recogniser as Microphone
    print("Say something:")       
    audio=r.listen(source)        # Microphone content (speech) stored in variable
   # print(audio)

try:
    word=r.recognize_google(audio) # google recognizer to identify content of varable
    print("\nYour Speech is recognised. \nYou said: " + word) #Print the content of variable as string
    
    # Create the Text file to store the speech content
    f=open("My_speech.txt","w+")      # Text file created
    f.write(word)                  # Write the content of speech variable as string
    f.close()                      # Save the text file & Close
    print("\nYour speech is saved as text file")

    #To Record the Speech content in .mp3 formate
    tts = gtts.gTTS(text=word, lang='en')   # received the speech content of variable as string
    tts.save(r"C:\Users\Nikhil\Desktop\New folder\voice recording\My_Speech.mp3")
    print("\nYour recording is ready")
     

    # Read the Text file and coversion to Speech
    print("\nTTS conversion as:")
    engine = pyttsx3.init()     # Speech engine/driver initialised
    engine.say(word)            # Store the content of Text file
    engine.runAndWait()         # Stored content as Speech output

except:
    print("\nNo speech input given...")
