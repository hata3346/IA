# IA
# Installer la librairie transformers si ce n'est pas fait :
# pip install transformers

from transformers import pipeline

# Créer une "IA polyvalente" : conversation et réponses
chatbot = pipeline("text-generation", model="gpt2")  # GPT-2, modèle léger pour tester

# Fonction pour discuter avec l'IA
def parler_ia(question):
    reponse = chatbot(question, max_length=100, do_sample=True, temperature=0.7)
    return reponse[0]['generated_text']

# Exemple d'utilisation
while True:
    user_input = input("Vous : ")
    if user_input.lower() in ["quit", "exit"]:
        break
    print("IA :", parler_ia(user_input))
