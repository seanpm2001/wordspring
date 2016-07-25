# What is wordspring?
wordspring is a word generator based on a simple pattern language.  You can use it to generate words for a constructed language.  Uniquely, wordspring is written in the Hy language, a dialect of Python that has Lisp-like syntax.

## Usage
    $ hy wordspring.hy

## Pattern Language
To change what kind of words are generated, you must edit the source code of wordspring.

The master variable in the pattern language is `P`.  `P` is normally a quasiquoted S-Expression that references other lists.  `P` names a "pattern", which can be any of the following:

* `(| pat pats ...)`: selects a random pattern from `(pat pats ...)` and interprets it.
* `(pat pats ...)`: interprets each of `(pat pats ...)` in turn and concatenates them as a string.
* `'symbol`: turns into a string

This simple language makes it surprisingly easy to make words of various classes, structures, etc.  In the pattern that comes with the script, the `C` pattern represents consonants, the `V` pattern vowels, the `E` pattern endings for small words, and the `S` pattern syllables.  These are all combined in the `P` variable which is then fed to the pattern interpreter.

If you haven't learned about quoting and quasiquoting in Hy, you should [read about them](http://docs.hylang.org/en/latest/language/api.html#quasiquote).

## Tweaking
At the bottom of the script is a "threaded" list of operations.  The two most interesting are:

* `(distinct)`: this ensures that no word duplicates form.
* `(take 100)`: this makes the generator produce 100 words.

You can comment out the `(distinct)` line if you are okay with duplicate words.  You can change the number of words produced by changing the number in the `take` statement.

## License
wordspring is licensed under the CC0 1.0 Universal license, a copy of which should have come with this package.  Basically, that means that I waive all copyright and related or neighboring rights to the work, make no warranty about the work, and disclaim liability for all uses of the work, to the extent possible under law.
