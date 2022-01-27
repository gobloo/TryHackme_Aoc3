# Day 22:

- McSkidy has finally gotten around to identifying the first trace of Grinch Enterprises within their network. They're looking at local machines to determine what exactly they did when they first entered the network. Can you help them make sense of what happened?

- I START the machine, I checked up the env: 2 folders "Santa_claus_Naughty-List_2021" and "Tools"

## Answer questions 1,2,3,4,6:

- I opened the santa folder I found the malicious file then I copy this file to "Tools/oledump_V0_0_60"  
Then I run the command Prompt 
and run the command: `oledump.py Santa_claus_Naughty-List_2021.doc`
I find 17 streams

- then I run this command : `oledump.py -s 8 -d Santa_claus_Naughty-List_2021.doc`
The stream 8 contains the obfuscated script which I decod with  [CyberChef](https://gchq.github.io/CyberChef/)
`FROM BASE64 + XOR with key 35 and Decimal + FROM BASE64`

- Then now you can answer the questions 1-2-3-4 from this clearText

- I noticed that there's is a file in `$env:USERPROFILE\Picture\Grinch2021\`
- I checked this directory and find `image` contain a FLAG it's the answer of qst 6

## Question 5:
- Now i returned to qst 5 I read the hint, so I need to check all stream number to find something contain caption 
```
$oledump.py -s 1 -d Santa_claus_Naughty-List_2021.doc
.
.
.
$oledump.py -s 17 -d Santa_claus_Naughty-List_2021.doc
```
- I run commands till I find the answer in one of these streams.

#credit : 5ob10
