# FlashToROM

A TUI tool that I use to help learn the alphabet or anything else related to the Hindi Language, however it can be used to learn any alphabet/short phrases that you would like.
The program reads from the word or letter list that you would like it to use. These can either be custom or someone elses pre-existing setup.

Currently supports Linux only. I will be working on additional features and also to provide support to OSX and Windows in the near future.

[Motivation and Usage](#motivation)

[Installation](#install)

[Importing/Creating Wordlists (configuration)](#config)

[Modes/Flags](#flags)

For obvious reasons, make sure you don't have a program on your system with the same name as this program xD.
---

<a name="motivation"/>

## Motivation and Usage

I have embarked on a journey to learn Hindi. To do this I use duolingo however learning Sanskrit is a big obsticle. I noticed that in all my attempts to learn a language I ended up chosing languages that used alphabets that i was not used to: Russian, Norwegian, and now Hindi. What held me back was practicing those symbols/letters and their meanings. DuoLingo is a amazing platform I think but the one thing it struggles with is burning those letters and their meanings into my brains ROM. Hence why I have designed this application.

### Indended Usage

The way that you are supposed to use this app is for letters however I've extended its applicable functionality slightly. In any mode the usage is indended to work similarly. I suggest slowly extending your wordlist so that you can properly learn stuff instead of throwing yourself into the deep end of things.
There are two main modes:
1. `-r (read)`
2. `-w (write)`

Read will provide you with the language you are learnings phrase/letter/word in the spelling of that language that you configured from your wordlist. You must then try to think of the sound or meaning in your native language. Once your hit enter it will show the correct answer that you configured and when you hit enter again it will clear the screen and pick a new random phrase/letter/word from your list.

Write will provide you with your native way of saying whatever it is that you need to say. Be that a phrase/letter/word. You are then expected to take a pen and paper and write out what that letter/word/phrase is in the language that you are learning. Once you hit enter it will show you the answer that you configured and then once you hit enter again the screen will be cleared and you will be provided with a new phrase.

There are a few more additional flags that you can use. But for that just use the `-h` menu or look at the bottom of the ReadMe. I explain everything well enough there. If you have made it this far and are interested. Here is how you can install and setup your wordlists. I have tried to make it as easy and automated as possible. Nothing fancy here :)

<a name="install"/>

## Installation:

You will require any version of python 3 to be installed. You do not require any additional packages.
1. Clone this repository to a location of your chosing:
```sh
git clone git@github.com:Daniel-Radloff/LanguageROMBurner.git
```
or
```sh
git clone https://github.com/Daniel-Radloff/LanguageROMBurner.git
```
2. Copy flashtorom.py to your `~/.local/bin` or equivalent. If you don't have something like this then please run this copy paste in any terminal window:
```sh
mkdir -p ~/.local/bin
echo 'export PATH="$PATH:$HOME/.local/bin"' >> .profile
```
If you run these commands you might have to relog in order for it to take effect.

---

And thats it, now all you need to do is create a wordlist or import one and you are done.

<a name="config"/>

## Importing/Creating a Wordlist

I have tried to make this as simple as I possibly can:
1. run `flashtorom` once if you have never ran it before, then navigate to ~/.config/flashtorom
2. Either copy an existing file or create a new file with the name that you would like the word list to be called.
3. Run `flashtorom --setdefaultlist <wordlistname>`. You don't need to give a path it will use relative pathing to the config directory.
Now when you run `flashtorom` it will use that wordlist by default :)
I suggest that you name the file the name of the language.
If you have not set up a means of quickly accessing your config directory or you would just like the convienence of opening and modifying your wordlist elsewhere, I would suggest making a symlink (shortcut) to that file so that you can edit it quickly.
### Wordlist Format
The format of a wordlist is very simple:
Words/Letters/Phrases are mapped between your native language/phonetic representation and then the symbols/phrases in the language of your choosing. The format looks like this:
```
$$ Phrases
Hello, this is a phrase in hindi. = नमस्ते, यह हिंदी में एक मुहावरा है.
$$ Letters
na = न
```
You have 3 different headings that you can use that pertain to the different modes that are availible for you to  use. All of them are case insensitive. They can appear in any order however each one can only appear once.
1. `$$ Letters`
2. `$$ Words`
3. `$$ Phrases`

All your Letters go under Letters etc etc.

#### Competence
If you have learnt something enough that you want to reduce its change of being pulled from the question pool, then you can do this by adding a `;` to the end of the line. If a `;` is detected in the middle of a sentence then it will be ignored, only `;`'s at the end of lines are tallied. If you want to reduce the chance of that line being in the question pool even further: append more `;`'s to the line.

---

<a name="flags" />

## Modes

You can add as many flags/modes as you want. You can have read, write, letters, words, and phrases all active at once for instane. You can also configure default behavior to use these flags etc.
```
-h (help) : Prints this menu and leaves
-r (read) : Flash a phrase/letter/word of the language you are
            learning and you need to guess the corresponding
            meaning/pronounciation.
-w (write): Flash the phrase/letter/word of your native language
            and you need to write it out on paper and compare.
-l (letters) : Use the letters section of your wordlist.
-W (words) : Use the words section of your wordlist.
-p (phrases) : Use the phrases section of your wordlist.
-a (all) : Use everything under letters and words and
            phrases in your wordlist.
-u (use) : Use a specified list. Use just the name of the list
            without any path, list must be in the config directory.
--setdefault : Set the default behavior of the program called with
            no commands to the commands that you specify now.
            NOTE: this ignores the -u/--use flag.
--setdefaultlist <listname> : sets the list you provide to the
            default list that the program uses.
```
