
text = input("Enter a paragraph:\n")
text_lower = text.lower()

clean_text = ""
for ch in text_lower:
    if ch not in string.punctuation:
        clean_text += ch

words = clean_text.split()
word_count = len(words)

freq = Counter(words)
top_words = freq.most_common(5)


sentences = text.replace("!", ".").replace("?", ".").split(".")
sentence_lengths = []

for s in sentences:
    s = s.strip()
    if s != "":
        s_clean = ""
        for ch in s.lower():
            if ch not in string.punctuation:
                s_clean += ch
        sentence_lengths.append(len(s_clean.split()))

# display results
print("\n--- Text Analysis ---")
print("Total words:", word_count)

print("\nTop 5 frequent words:")
for w, c in top_words:
    print(w, ":", c)

print("\nSentence lengths:")
for i in range(len(sentence_lengths)):
    print("Sentence", i + 1, ":", sentence_lengths[i], "words")

# save output to file
file = open("text_analysis_result.txt", "w")

file.write("Text Analyzer Result\n")
file.write("--------------------\n")
file.write("Total words: " + str(word_count) + "\n\n")

file.write("Top 5 frequent words:\n")
for w, c in top_words:
    file.write(w + " : " + str(c) + "\n")

file.write("\nSentence lengths:\n")
for i in range(len(sentence_lengths)):
    file.write("Sentence " + str(i + 1) + " : " + str(sentence_lengths[i]) + " words\n")

file.close()

print("\nResult saved in text_analysis_result.txt")
