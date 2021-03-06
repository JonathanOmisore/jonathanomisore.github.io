---
layout: post
title:  "Cryptography and Knowledge Representation & Reasoning in AI"
date:   2021-03-21 12:59 -0500

---



In cryptography, the Caesar cipher is a simple type of cipher known as a substitution cipher.
With the Caesar cipher, each plaintext letter to be encrypted is replaced by a letter with a shift of n. With a left shift where n = 3, D would be replaced by A, E would become B, and so on. 
![image](/images/500px-Caesar_cipher_left_shift_of_3.svg.png)
<caption>Example of a Caesar cipher</caption>

This is within the scope of a subdiscipline of artificial intelligence known as <b>Knowledge Representation and Reasoning</b>. In Knowledge Representation and Reasoning,
information about the world is represented in a form that an intelligent agent can understand. 

Knowledge and representation and reasoning often makes use of a subdiscipline of mathematical logic known as first order logic.  Logic-programming languages such as Prolog and Lisp make use of first order logic, and they are very useful for AI. A specific paradigm known as Answer Set Programming can be used.

Consider the following Answer Set Program:
p(a) or p(b).
p(a).
p(b).
The program has two answer sets: {p(a),-p(b)} and {-p(a), p(b)}.
Now consider a more practical example:
eagle(eddy).
penguin(tux).
 fly(X) :- bird(X), not -fly(X). (If X is a bird, and it is false that X can not fly, then X can fly).
-fly(X) :- penguin(X). (If X is a penguin, the X can fly)
bird(X) :- penguin(X). (If X is a penguin, the X is a bird)
bird(X) :- eagle(X). (If X is an eagle, then X is a bird)
Based on this logic, the program returns the following Answer Set:
bird(eddy) bird(tux) -fly(tux) fly(eddy) penguin(tux) eagle(eddy)
Eddy is a bird, Tux is a bird, Eddy is an Eagle, Tux is a Penguin, Eddy can Fly, Tux can not Fly.




We can use the applications of Answer Set Programming to create a Caesar cipher that can encode the word apple with a shift of 27.

position(1) :- letter(a).
position(2) :- letter(b).
position(3) :- letter(c).
position(4) :- letter(d).
position(5) :- letter(e).
position(6) :- letter(f).
position(7) :- letter(g).
position(8) :- letter(h).
position(9) :- letter(i).
position(10):- letter(j).
position(11):- letter(k).
position(12):- letter(l).
position(13):- letter(m).
position(14):- letter(n).
position(15):- letter(o).
position(16):- letter(p).
position(17):- letter(q).
position(18):- letter(r).
position(19):- letter(s).
position(20):- letter(t).
position(21):- letter(u).
position(22):- letter(v).
position(23):- letter(w).
position(24):- letter(x).
position(25):- letter(y).
position(26):- letter(z).
shift(27).
encryption((X + Y)\26):- shift(X),position(Y).
letter(a).
letter(p).
letter(l).
letter(e).
cipherletter(a):- encryption(1).
cipherletter(b):- encryption(2).
cipherletter(c):- encryption(3).
cipherletter(d):- encryption(4).
cipherletter(e):- encryption(5).
cipherletter(f):- encryption(6).
cipherletter(g):- encryption(7).
cipherletter(h):- encryption(8).
cipherletter(i):- encryption(9).
cipherletter(j):- encryption(10).
cipherletter(k):- encryption(11).
cipherletter(l):- encryption(12).
cipherletter(m):- encryption(13).
cipherletter(n):- encryption(14).
cipherletter(o):- encryption(15).
cipherletter(p):- encryption(16).
cipherletter(q):- encryption(17).
cipherletter(r):- encryption(18).
cipherletter(s):- encryption(19).
cipherletter(t):- encryption(20).
cipherletter(u):- encryption(21).
cipherletter(v):- encryption(22).
cipherletter(w):- encryption(23).
cipherletter(x):- encryption(24).
cipherletter(y):- encryption(25).
cipherletter(z):- encryption(26).
