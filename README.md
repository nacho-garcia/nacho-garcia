const express = require('express')
const app = express()

const PLACES = 7;

// no db - so global var to keep track of count
let counter = 0

function getCountImage(count) {
   ...
}

// get the image
app.get('/count.svg', (req, res) => {
  counter++;
  
  // This helps with GitHub's image cache 
  //   see more: https://rushter.com/counter.svg
  res.set({
  'content-type': 'image/svg+xml',
  'cache-control': 'max-age=0, no-cache, no-store, must-revalidate'
  })
  
  // Send the generated SVG as the result
  res.send(getCountImage(counter));
})

const listener = app.listen(process.env.PORT, () => {
  console.log('Your app is listening on port ' + listener.address().port)
})

// set up the counter variable
let counter = 0;

...
app.get('/count.svg', (req, res) => {
  // update the counter on any image request
  counter++;
  ...
}

function getCountImage(count) {
  // This is not the greatest way for generating an SVG but it'll do for now
  const countArray = count.toString().padStart(PLACES, '0').split('');

  const parts = countArray.reduce((acc, next, index) => `
        ${acc}
        <rect id="Rectangle" fill="#000000" x="${index * 32}" y="0.5" width="29" height="29"></rect>
        <text id="0" font-family="Courier" font-size="24" font-weight="normal" fill="#00FF13">
            <tspan x="${index * 32 + 7}" y="22">${next}</tspan>
        </text>
`, '');
  
  return `<?xml version="1.0" encoding="UTF-8"?>
<svg width="${PLACES * 32}px" height="30px" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <title>Count</title>
    <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
      ${parts}
    </g>
</svg>
}

<div id="header" align="center">
  <img src="https://media.giphy.com/media/qP2YwW2BpB2K0qMjMk/giphy.gif" width="300"/>
  <h1 align="center"> Hi 👋🏼, I'm Nacho García</h1>
  <h3 align="center"> I'm a computer engineering student from Asturias, Spain. I'm eager to advance my career, expand my knowledge, and gain experience.</h3>
</div>

- - -

- 🌱 I’m currently studying, but open to work
- 📫 You can find me as @nachogarez in multiple platforms
- 🔧 Languages: Java, Python, C, C++, Machine, Prolog, Haskell, VHDL, MATLAB.
- 🧰 Tools: Visual Studio, Visual Studio Code, Eclipse, Xcode, Wireshark, Matlab, Spyder...
- 🖥️ OS: MacOS, Windows and Linux

- - -
