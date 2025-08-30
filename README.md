# CyberSecurity-AI-Chatbot
# Developed a beginner level chatbot that answers your questions related to the feild of cybersecurity.
%%writefile app.py
import streamlit as st
import wikipedia
import nltk
from nltk.chat.util import Chat, reflections

nltk.download('punkt')

# Predefined rule-based chatbot pairs
pairs = [
    [r"(hi|hello|hey)", ["Hello! How can I help you with cybersecurity today?"]],
    [r"(what is phishing)", ["Phishing is a fraudulent attempt to obtain sensitive information by pretending to be a trustworthy entity."]],
    [r"(what is malware)", ["Malware is malicious software designed to harm, exploit, or otherwise compromise a computer system."]],
    [r"(.*)", ["Sorry, I don't understand. Can you rephrase?"]]
]

chatbot = Chat(pairs, reflections)

st.title("Cybersecurity AI Chatbot")
st.write("Ask me anything about cybersecurity.")

user_input = st.text_input("You:")

if user_input:
    response = chatbot.respond(user_input.lower())
    if response == "Sorry, I don't understand. Can you rephrase?":
        try:
            wiki_summary = wikipedia.summary(user_input, sentences=2)
            st.write(wiki_summary)
        except:
            st.write(response)
    else:
         st.write(response)
!nohup streamlit run app.py --server.port 8501 &>/dev/null &
!ngrok config add-authtoken 31BzCoEu8sUEkj5ch2j7o4SACWj_5Bp9oH5gu6AebK4hZ9Qt8
from pyngrok import ngrok
public_url = ngrok.connect(8501)
print("Public URL:", public_url)

    
        st.write(response)

