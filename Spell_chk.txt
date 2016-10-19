#reading from the file dictionary.txt
f=open("dictionary.txt","r")
vocabulary=f.read()
print(vocabulary)

#Tokenizing the vocabulary
tokenized_vocabulary = vocabulary.split(" ")
print(tokenized_vocabulary[0:5])

#Process the file that should be spell checked

t = open("story.txt", 'r')
story_string = t.read()
clean_chars = [",", ".", "'", ";", "\n"]
print(story_string)

#Pre-process the text in file to be used for spell checking
def clean_text(text_string,special_characters):
    cleaned_string=text_string
    for chr1 in special_characters:
        cleaned_string = cleaned_string.replace(chr1,"")
    return(cleaned_string.lower())

#cleaned_story = clean_text(story_string,clean_chars)
#print(cleaned_story)

#Tokenize the preprocessed file
def tokenize(text_string,special_characters):
    cleaned_story=clean_text(text_string,special_characters)
    story_tokens=cleaned_story.split(" ")
    return(story_tokens)

tokenized_story=tokenize(story_string,clean_chars)
#print(tokenized_story)

#Identify Misspelled Words
for word in tokenized_story:
    if(word not in tokenized_vocabulary):
        misspelled_words.append(word)
print(misspelled_words)

