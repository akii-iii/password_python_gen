import random

# константы
digits = '012345'
lowercase_letters = 'abcdefghijklmnopqrstuvwxyz'
uppercase_letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
punctuation = '!#$%&*+-=?@^_.'


need = int(input('How many passwords?'))
# детали
def passwords(chars):
    length = int(input('Length of this password? '))
    num = input('Any numbers in this password? y = yes/ n = no ')
    lower_letters = input('Any lower letters in this password? y = yes/ n = no ')
    upper_letters = input('Any upper letters in this password? y = yes/ n = no ')
    pun = input('Any of these signs in this password: !#$%&*+-=?@^_. ? y = yes/ n = no ')
    bad_ones = input('Any of these commonly mistaking signs in this password: il1Lo0O ? y = yes/ n = no ')
    while True:
        if num == 'y':
            chars += random.choice(digits)
        if len(chars) == length:
            break
        if lower_letters.lower() == 'y':
            chars += random.choice(lowercase_letters)
        if len(chars) == length:
            break
        if upper_letters.lower() == 'y':
            chars += random.choice(uppercase_letters)
        if len(chars) == length:
            break
        if pun.lower() == 'y':
            chars += random.choice(punctuation)
        if len(chars) == length:
            break
    if bad_ones.lower() == 'y':
        for i in 'il1Lo0O':
            chars = chars.replace(i, random.choice(chars))
    chars = list(chars)
    random.shuffle(chars)
    print(''.join(chars))
chars = ''
passwords(chars)
for _ in range(need - 1):
    passwords(chars)
