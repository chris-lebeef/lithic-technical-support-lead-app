# Chris LeBoeuf - Lithic Technical Support Lead Readme

## How I found the hidden challenge

I scanned the job application for anything hidden. My first thought was there might be some white-colored text hidden against the white background of the page, so I highlighted all the text and scrolled up and down to see if I was correct. I was not.

Then I found a URL under the 'What You'll Bring' section (the alias 'problem-solving'). I clicked this and it brought me to another greenhouse page, but an error at top told me the job I was looking for is no longer available. I found that odd, so I copied the actual URL text and pasted it into a new browser tab. That's when I saw the long encoded string at the end of the greenhouse URL.

I asked ChatGPT to decode this string (actually my first thought was this was a hash of some kind, so I asked ChatGPT to 'un-hash'). ChatGPT told me this could be decoded with Python or directly in a terminal window, and gave me the command to do so.

## How I decoded the original string
I opened up a terminal window and entered this (string truncated for brevity):

    echo 'IyEvdXNyL2Jpbi9lbnYgcHl0aG9uMwo...' | base64 -d

This decoded the string into the python script, which I've saved as puzzle.py and added to my repository.

## What this script does
1. Decrypts a hidden answer (42)
2. Combines the input string (my name) normalized to lowercase, with the hidden answer and a fixed phrase
3. Computes a SHA-256 hash on this phrase
4. Truncates the hash to just the first 12 characters

## The command I ran
In a terminal window, from the same directory where I saved puzzle.py, I ran this:

    DONT_PANIC=1 python3 puzzle.py --candidate "Chris LeBoeuf"

## The exact output I received

>Decrypted password: 42 <br>
>Candidate: Chris LeBoeuf <br>
>Proof code: 3e6d2ec5f925 <br>

## The final decrypted answer

Decrypted password is 42. The proof code is 3e6d2ec5f925.

## Tools I used

I used ChatGPT to help with figuring out what to do with the initial encoded string, also used it to further my understanding of what the puzzle.py script is actually doing.

I used Terminal on my Macbook to decode the string & run the Python script.

I used Atom to write this readme file.  
