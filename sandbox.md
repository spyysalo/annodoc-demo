---
layout: base
title:  'Sandbox'
---

# Some markdown

*italics* and **bold**

`inline code`

* bulleted
* list

1. numbered
2. list

Link: [link text](http://www.example.com)

## header 2

### header 3

----------

# Some visualizations

~~~ sdparse
Just some tokens
~~~

~~~ sdparse
Tokens/Noun with/Adpos POS/Noun
~~~

~~~ sdparse
Token/Noun[Num=Sg] features/Noun[Num=Pl]
~~~

~~~ sdparse
A dependency
det(dependency, A)
~~~

~~~
Dynamic visualization (click "edit!")
~~~
{:.sdparse tabs="yes"}

~~~ sdparse
Example with error
det(no-such, token)
~~~

----------

## CoNLL-U example

<div class="conllu-parse" tabs="yes">
1     I         I        PRON    PRN      Num=Sing|Per=1     2      nsubj _ _
2-3   haven't   _        _       _        _                  _      _ _ _
2     have      have     VERB    VB       Tens=Pres          0      root _ _
3     not       not      ADV     RB       _                  2      neg _ _
4     a         a        DET     DT       _                  5      det _ _
5     clue      clue     NOUN    NN       Num=Sing           2      dobj _ _
6     .         .        PUNCT   .        _                  2      punct _ _
</div>

With secondary dependencies

<div class="conllu-parse" tabs="yes">
1    She       _   PRON    _   _   2   nsubj   _ _
2    declared  _   VERB    _   _   0   root    _ _
3    the       _   DET     _   _   4   det     _ _
4    cake      _   NOUN    _   _   2   dobj    5:nsubj _
5    beautiful _   ADJ     _   _   2   xcomp   _ _
6    .         _   PUNCT   _   _   2   punct   _ _
</div>

French example with English translation:

<pre><code class="language-conllu"># give the toys to the children
1 donner donner VERB _ VerbForm=Inf 0 root _ give
2 les le DET _ Definite=Def|Number=Plur 3 det _ the
3 jouets jouet NOUN _ Gender=Masc|Number=Plur 1 dobj _ toys
4-5 aux _ _ _ _ _ _ _ _
4 à à ADP _ _ 6 case _ to
5 les le DET _ Definite=Def|Number=Plur 6 det _ the
6 enfants enfant NOUN _ Gender=Masc|Number=Plur 1 nmod _ children

# now the parallel English tree
1 give donner VERB _ VerbForm=Inf 0 root _ give
2 the le DET _ Definite=Def|Number=Plur 3 det _ the
3 toys jouet NOUN _ Gender=Masc|Number=Plur 1 dobj _ toys
4 to à ADP _ _ 6 case _ to
5 the le DET _ Definite=Def|Number=Plur 6 det _ the
6 children enfant NOUN _ Gender=Masc|Number=Plur 1 nmod _ children
</code></pre>

Sentence label and style

~~~ conllu
# sentence-label long-label
# visual-style 2 bgColor:yellow
# visual-style 2 1 nsubj color:red
1     I         I        PRON    PRN      Num=Sing|Per=1     2      nsubj _ _
2     have      have     VERB    VB       Tens=Pres          0      root _ _
~~~

## Kanji

~~~ sdparse
ロボットは 東大に  入れる か 。/。
nsubj(入れる, ロボットは)
nommod(入れる, 東大に)
~~~

## Right-to-left text

Hebrew (Stanford Dependencies format)

~~~ sdparse
דני/NOUN ראה/VERB סרט/NOUN
nsubj(ראה, דני)
dobj(ראה, סרט)
~~~

Same sentence in CoNLL-U format:

~~~ conllu
1     דני       _        NOUN    _      _     2      nsubj _ _
2     ראה       _        VERB    _      _     0      root  _ _
3     סרט       _        NOUN    _      _     2      dobj  _ _
~~~

Arabic

~~~ conllu
1     وَ       _        NOUN    _      _     2      nsubj _ _
2     لاحَظَ       _        VERB    _      _     0      root  _ _
3     التَقْرِيرُ       _        NOUN    _      _     2      dobj  _ _
~~~

----------
