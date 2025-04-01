## React Js Logiccal Interview Questions and Answers

## From the below sentence,

## the banned word is 'test', print only repeated words from that sentence

## sentence = 'This is a test sentence and this test is only a test'

<details><summary>Answer</summary>

```js
import React, { useState } from "react";

function App() {
  const sentence = "This is a test sentence and this test is only a test";

  // Function to get repeated words excluding banned words
  const getRepeatedWords = (sentence) => {
    const bannedWord = "test";
    const words = sentence.toLowerCase().split(" ");
    const wordCount = {};
    const repeatedWords = [];

    words.forEach((word) => {
      if (word !== bannedWord) {
        wordCount[word] = (wordCount[word] || 0) + 1;
      }
    });

    for (const word in wordCount) {
      if (wordCount[word] > 1) {
        repeatedWords.push(word);
      }
    }

    return repeatedWords;
  };

  const repeatedWords = getRepeatedWords(sentence);

  return (
    <div>
      <h1>Repeated Words</h1>
      <p>{repeatedWords.join(", ")}</p>
    </div>
  );
}

export default App;
```

</details>
