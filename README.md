import random  

def choose_word():  
    words = ["слово", "гитара", "программа", "разработка"]  
    return random.choice(words)  

def display_progress(word, guessed_letters):  
    return ' '.join(letter if letter in guessed_letters else '_' for letter in word)  

def main():  
    word = choose_word()  
    guessed_letters = set()  
    attempts = 6  

    while attempts > 0:  
        print("Текущий статус:", display_progress(word, guessed_letters))  
        guess = input("Введите букву: ").lower()  

        if guess in guessed_letters:  
            print("Вы уже пытались угадать эту букву.")  
            continue  

        guessed_letters.add(guess)  

        if guess in word:  
            print("Вы угадали букву!")  
        else:  
            attempts -= 1  
            print(f"Неверно! Осталось попыток: {attempts}")  

        if all(letter in guessed_letters for letter in word):  
            print(f"Поздравляем! Вы угадали слово: {word}")  
            break  
    else:  
        print(f"Вы проиграли! Загаданное слово: {word}")  

if name == "main":  
    main()
