# Burmese Crossword

Make crossword puzzles in Burmese / Myanmar language. Unicode and Zawgyi input OK.

<img src="http://i.imgur.com/LCKxGpu.png" width="650"/>

## Also in Nepali and Tamil

<strong><a href="http://mapmeld.github.io/crossword-unicode/nepali.html">Nepali Version</a></strong>

<strong><a href="http://mapmeld.github.io/crossword-unicode/tamil.html">Tamil Version</a></strong>

## Usage

### Client-side javascript

```javascript
var game = new Crossword(HTML5canvas, columns, rows);
game.clearCanvas(true);

var clue = 'What does a duck say?';
var answer = 'quack';

game.addWord(answer, function(error, clueAnchor, direction) {
  // error is null or an error (answer is too small, too big, cannot be placed etc)
  // clueAnchor is the number used by the system (for example "2" for "2 across")
  // direction is "across" or "down"
});

// advanced language options
game.setNumberTransform(function (n) {
  // convert integer marker to local language
  return tamilNumbers(n);
});
```

### Node module

Use <a href="https://github.com/Automattic/node-canvas/">node-canvas</a>.

<a href="https://github.com/Automattic/node-canvas/wiki/Installation-on-Heroku">Guide to using node-canvas on Heroku.</a>

```bash
npm install canvas crossword --save
```

```javascript
var Canvas = require('canvas');
var Crossword = require('crossword');

var width = 20;
var height = 15;
var canv = new Canvas(40 * width, 40 * height);

var game = new Crossword(canv, width, height);
game.clearCanvas(true);

game.addWord(answer, function(err, clueAnchor, direction) {
  //
});
```

### Command Line

Make crosswords from a word list using command line.

Prerequisites: NodeJS and fonts which support your language (preferably Noto Sans Myanmar, Noto Sans Devanagari,
  and Noto Sans Tamil, included in the styles directory of this project)

```bash
npm install crossword-unicode -g
crosswordjs wordlist.txt output.png

# more custom setup
# 20 columns wide, 15 rows high
# myanmar (other languages supported: ne Nepali, ta Tamil)
xwordjs wordlist.txt output.png -w 20 -h 15 -l my
```

## Built with open source software

* <a href="https://github.com/Rabbit-Converter/Rabbit-Node">Rabbit-Node</a> Unicode-Zawgyi converter
* <a href="https://github.com/mapmeld/myanmar-numbers-js">Myanmar Numbers</a>
* <a href="https://github.com/mapmeld/preeti">Preeti</a> for Nepali typing
* jQuery

## License

Open source, MIT license
