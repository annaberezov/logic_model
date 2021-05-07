import fugashi

# The Tagger object holds state about the dictionary. 
tagger = fugashi.Tagger()

file = open("C:/Users/Anna-Maria/Desktop/SENIOR CAPSTONE/Computer Science/model trees/mixed.txt","r", encoding="utf-8")
text = file.readlines()  # opening and reading the file with sentences line by line

# this is the list of special verbs which indicate that the level of formality is polite / humble formal
verbs = ["くださる", "ごさる", "おありです", "おめにかかる", "いらっしゃる", "おいでになる", "おっしゃる", "おききになる", "おめしになる",
         "おこしになる", "おみえになる", "なさる", "めしあがる", "ごらんになる", "さしあげる", "ござる", "まいる", "おる", "もうす",
         "もうしあげる", "はいしゃくする", "うかがう", "おじゃまする", "ぞんじる", "いたす", "いただく", "はいけんする"]

for t in text:  # for every sentence in the file
    points = total = 0
    reg = False
    for word in tagger(t):  # for every word in the sentence
        if word.feature.pos1 == "接頭辞":  # if it is a prefix
            if word.surface == "お" or "ご":
                points += 1
        elif word.feature.pos1 == "動詞":  # if it is a verb
            total += 1
            for x in tagger(word.surface):
                if x == "い" or "き" or "し" or "ち" or "に" or "ひ" or "み" or "り":
                    points += 1
            if [v for v in verbs if word.feature.lemma in v]: # if the verb is a special verb
                reg = True
    sent = t.replace('\n', "")

    if points > total and points != total or reg == True:
        print('The sentence: "', sent, '" is in Honorific / Humble Form - Verbs')
    elif points == total:
        print('The sentence: "', sent, '" is in Plain Formal Form - Verbs')
    else:
        print('The sentence: "', sent, '" is NOT Honorific / Humble Form - Verbs')


