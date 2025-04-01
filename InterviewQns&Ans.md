## React Js Logical Interview Questions and Answers

Q1. From the below sentence,
the banned word is 'test', print only repeated words from that sentence
sentence = 'This is a test sentence and this test is only a test'

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

---

Q2. Find the zero sum of an array const arr = [-9,-8,-5,0,5,8,15] output should be [5, -5]

<details><summary>Answer</summary>

```js
import react from "react";
const zeroSumPair = () => {
  const arr = [-9, -8, -5, 0, 5, 8, 15];

  const findZeroSumPair = (arr) => {
    const numset = new Set();
    for (let num of arr) {
      if (numset.has(-num)) {
        return [num, -num];
      }
      numset.add(num);
    }
    return [];
  };

  const result = findZeroSumPair(arr);

  return (
    <div>
      <h1>Zero Sum Pair</h1>
      <p>
        {" "}
        {result.length ? `[${result.join(",")}]` : "No Zero Sum Pair Found"}
      </p>
    </div>
  );
};

export default zeroSumPair;
```

</details>

---

Q3. Create an application with two buttons i.e (Add new and Clear All)  
(i) Whenever we click on the Add new button, a row should open which contains day, start time and end time, if we click the Add new button multiple times, then corresponding to that multiple rows to come.
(ii) And if we click on clearAll button, all the rows should be cleared.

<details><summary>Answer</summary>

```js
import React, { useState } from "react";

const TimeScheduler = () => {
  const [rows, setRows] = useState([]);

  const addRow = () => {
    setRows([...rows, { day: "", startTime: "", endTime: "" }]);
  };

  const clearAll = () => {
    setRows([]);
  };

  const handleChange = (index, field, value) => {
    const updatedRows = [...rows];
    updatedRows[index][field] = value;
    setRows(updatedRows);
  };

  return (
    <div>
      <h2>Time Scheduler</h2>
      <button onClick={addRow}>Add New</button>
      <button onClick={clearAll}>Clear All</button>
      <table border="1" style={{ marginTop: "10px", width: "100%" }}>
        <thead>
          <tr>
            <th>Day</th>
            <th>Start Time</th>
            <th>End Time</th>
          </tr>
        </thead>
        <tbody>
          {rows.map((row, index) => (
            <tr key={index}>
              <td>
                <input
                  type="text"
                  value={row.day}
                  onChange={(e) => handleChange(index, "day", e.target.value)}
                />
              </td>
              <td>
                <input
                  type="time"
                  value={row.startTime}
                  onChange={(e) =>
                    handleChange(index, "startTime", e.target.value)
                  }
                />
              </td>
              <td>
                <input
                  type="time"
                  value={row.endTime}
                  onChange={(e) =>
                    handleChange(index, "endTime", e.target.value)
                  }
                />
              </td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
};

export default TimeScheduler;
```

</details>
