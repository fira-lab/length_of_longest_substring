# length_of_longest_substring
#Length of longest substring. this is one of the data structure and algorithm problem. hash map is very use full in terms of saving the and retrieving data. I made #the code very clear and and explain each line of the code on what they are useful. feel free to comment any confusion.


def length_of_longest_substring(s):
    # Create a dictionary to store the last seen index of each character
    char_map = {}
    max_length = 0
    start = 0

    for end in range(len(s)):
        # Check if the current character is already in the dictionary and its index is after the start pointer
        if s[end] in char_map and start <= char_map[s[end]]:
            # Move the start pointer to the next index after the last occurrence of the current character
            start = char_map[s[end]] + 1

        # Update the last seen index of the current character
        char_map[s[end]] = end

        # Calculate the length of the current substring
        current_length = end - start + 1

        # Update the maximum length if necessary
        max_length = max(max_length, current_length)

    return max_length

# Test the function
s = "abcabcbb"
print(length_of_longest_substring(s))
def word_pattern(pattern, s):
    words = s.split()
    if len(pattern) != len(words):
        return False

    char_to_word = {}
    word_to_char = {}

    for char, word in zip(pattern, words):
        if char in char_to_word:
            if char_to_word[char] != word:
                return False
        else:
            char_to_word[char] = word

        if word in word_to_char:
            if word_to_char[word] != char:
                return False
        else:
            word_to_char[word] = char

    return True

# Test the function
pattern = "abba"
s = "dog cat cat dog"
print(word_pattern(pattern, s))
