# MITx6.00.1Unit5.ProblemSet5
Program goal: to casesar cipher a given string

**The code with the solved problems can be found in the file psy6**

**Problem 1**

The Message class contains methods that could be used to apply a cipher to a string, either to encrypt or to decrypt a message (since for Caesar codes this is the same action).

In the next two questions, you will fill in the methods of the Message class found in ps6.py according to the specifications in the docstrings. The methods in the Message class already filled in are:

  __init__(self, text)
  The getter method get_message_text(self)
  The getter method get_valid_words(self), notice that this one returns a copy of self.valid_words to prevent someone from mutating the original list.

**In this problem, you will fill in two methods:**

1. Fill in the build_shift_dict(self, shift) method of the Message class. Be sure that your dictionary includes both lower and upper case letters, but that the shifted character for a lower case letter and its uppercase version are lower and upper case instances of the same letter. What this means is that if the original letter is "a" and its shifted value is "c", the letter "A" should shift to the letter "C".

2. Fill in the apply_shift(self, shift) method of the Message class. You may find it easier to use build_shift_dict(self, shift). Remember that spaces and punctuation should not be changed by the cipher.

**Problem 2**

1 point possible (ungraded)
For this problem, the graders will use our implementation of the Message class, so don't worry if you did not get the previous parts correct.

PlaintextMessage is a subclass of Message and has methods to encode a string using a specified shift value. Our class will always create an encoded version of the message, and will have methods for changing the encoding.

Implement the methods in the class PlaintextMessage according to the specifications in ps6.py. The methods you should fill in are:

  __init__(self, text, shift): Use the parent class constructor to make your code more concise.
  The getter method get_shift(self)
  The getter method get_encrypting_dict(self): This should return a COPY of self.encrypting_dict to prevent someone from mutating the original dictionary.
  The getter method get_message_text_encrypted(self)
  change_shift(self, shift): Think about what other methods you can use to make this easier. It shouldn???t take more than a couple lines of code.

**Problem 3 - CiphertextMessage**

0.0/15.0 points (graded)
For this problem, the graders will use our implementation of the Message and PlaintextMessage classes, so don't worry if you did not get the previous parts correct.

Given an encrypted message, if you know the shift used to encode the message, decoding it is trivial. If message is the encrypted message, and s is the shift used to encrypt the message, then apply_shift(message, 26-s) gives you the original plaintext message. Do you see why?

The problem, of course, is that you don???t know the shift. But our encryption method only has 26 distinct possible values for the shift! We know English is the main language of these emails, so if we can write a program that tries each shift and maximizes the number of English words in the decoded message, we can decrypt their cipher! A simple indication of whether or not the correct shift has been found is if most of the words obtained after a shift are valid words. Note that this only means that most of the words obtained are actual words. It is possible to have a message that can be decoded by two separate shifts into different sets of words. While there are various strategies for deciding between ambiguous decryptions, for this problem we are only looking for a simple solution.

Fill in the methods in the class CiphertextMessage acording to the specifications in ps6.py. The methods you should fill in are:

  __init__(self, text): Use the parent class constructor to make your code more concise.
  decrypt_message(self): You may find the helper function is_word(wordlist, word) and the string method split() useful. Note that is_word will ignore punctuation and other special characters when considering whether a word is valid.
