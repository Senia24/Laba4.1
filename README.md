# Лабораторная работа №4: Структуры данных
## Задание:
Задание: Словарь.

Дано слово и словарь. Необходимо найти все слова из словаря, которые можно составить из букв данного слова, и вывести их в порядке уменьшения длины.

В качестве словаря можно использовать любой текстовый файл с любыми словами, но желательно использовать словарь со словами русского языка.

Ограничение времени на решение 2 с.

Допустимо использовать больше времени (до 1 мин) на этап инициализации или обработки словаря. Но после этого этапа время на обработку нового слова не более 2 с.

Список слов (словарь) можно взять тут https://github.com/Harrix/Russian-Nouns/releases

## Реализация:

### Листинг программы:
``` python
from collections import Counter

def load_dictionary(filename):
    with open(filename, encoding='utf-8') as file:
        return [line.strip() for line in file if line.strip()]

def can_build(word, letters):
    return not (Counter(word) - letters)


dictionary = load_dictionary('Russian_nouns.txt')

input_word = input("Введите слово: ").strip().lower()
if not input_word:
    print(" Пустой ввод.")
    exit(1)

input_letters = Counter(input_word)

matches = [word for word in dictionary if can_build(word, input_letters)]

# Сортировка по убыванию длины
matches.sort(key=lambda w: (-len(w), w))
print("Автор: Кочаров Арсений Андреевич, группа:090301-ПОВа-о25")
print("Найдено слов:", len(matches))
for word in matches:
    print("-", word)
```
## Результат выполнения программы:
<img width="527" height="306" alt="image" src="https://github.com/user-attachments/assets/fc671fef-a0e9-4b6e-9bcc-97cedaef3ff0" />
