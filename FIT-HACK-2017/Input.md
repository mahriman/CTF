# Input (100 points)
### FIT-HACK 2017 <https://ctf.nw.fit.ac.jp>

So we're given a PCAP file containing USB keypresses. Sounds simple enough.
After having figured out which USB host is the keyboard it's a simple matter of sorting out that 'traffic' and extracting the "Leftover Capture Data" containing the actual keystrokes.
Some grep and text omission gives us these keys:
`09
0c
17
30
0c
87
1a
08
2a
21
11
17
87
21
87
0e
08
2a
20
1c
05
12
21
15
07
32
16`

Mapping the keys from http://www.usb.org/developers/hidpage/Hut1_12v2.pdf p. 53-60 gives us something that looks like a key: 
`FIT}IxWEx4NTx4xKEx3YBO4RDxS`

Now we know the key should begin with FIT{ and end with }, so something's up here.
Oh wait, it's a japanese CTF!
Let's take http://hp.vector.co.jp/authors/VA003720/lpproj/others/kbdjpn.htm into account and mark `2A` as backspace, 87 as japanese keyboard's underscore and correct 30 and 32 for japanese keyboard's { and }.

Our final mapping has these additions:

`0x30:"{", # Japanese 30 = {`

`0x32:"}", # Japanese 32 = }`

`0x87:"_", # Japanese 87 = Underscore _ or Pipe | or Backslash \`

`0x2A:"<backspace>", # DELETE (Backspace)`

Running our python script again, we get `FIT{I_WE<backspace>4NT_4_KE<backspace>3YBO4RD}S`
Submitting `FIT{I_W4NT_4_K3YBO4RD}` tells us incorrect flag. Hrm!
Going back to the leftover capture data, only a few of the characters have the shift key pressed, besides special characters only `I`, leaving us with 
`FIT{I_w4nt_4_k3ybo4rd}` - which submits as correct flag!

Note to self: Write a script that parses PCAP data automatically and checks if shift key is pressed.
