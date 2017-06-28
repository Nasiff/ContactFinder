#! python3
# phoneAndEmail.py - This program allows you to find phone numbers & emails after they have been copied to your clipboard

import pyperclip, re

# Regex for finding phone numbers
phoneRegex = re.compile(r'''(   
        (\d{3}|\(\d{3}\))?     # Area Code
        (\s|-|\.)?             # Separator
        (\d{3})                # First 3 Digits
        (\s|-|\.)              # Separator
        (\d{4})                # Last 4 Digits
        )''', re.VERBOSE)      

# Regex for finding email addresses
emailRegex = re.compile(r'''(
        [A-Za-z0-9._%+-]+      # First Part Of The Email; Before the @
        @                      # The '@'
        [A-Za-z0-9.-]+         # The Name Of The Domain
        (\.[a-zA-Z]{2,4})      # dot-something
         )''', re.VERBOSE)

# Finding matches in clipboard text

text = str(pyperclip.paste())
matcher = []

for groups in phoneRegex.findall(text): # Finding phone numbers
    phoneNum = '-'.join([groups[1], groups[3], groups[5]]) # This was done so that the phone number that gets matched is put in a standard format (Putting hyphens in between)
    matcher.append(phoneNum)

for groups in emailRegex.findall(text): # Finding email addresses
    matcher.append(groups[0])

# Copy results to the clipboard.

if len(matcher) > 0:
    pyperclip.copy('\n'.join(matcher))
    print('Copied to clipboard:')
    print('\n'.join(matcher))
else:
    print('No phone numbers or email addresses found.')
