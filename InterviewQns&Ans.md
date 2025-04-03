## React Js Logical Interview Questions and Answers

Q1. From the below sentence,
the banned word is 'test', print only repeated words from that sentence
<br>
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

Q2. Find the zero sum of an array
<br>
const arr = [-9,-8,-5,0,5,8,15]
<br>
output should be [5, -5]

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
<br>
(i) Whenever we click on the Add new button, a row should open which contains day, start time and end time, if we click the Add new button multiple times, then corresponding to that multiple rows to come.
<br>
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

---

Q4. Write a program to find the second largest number in an array

<details><summary>Answer</summary>

```js
import React, { useState } from "react";

const SecondLargestNumber = () => {
  const [numbers, setNumbers] = useState([10, 20, 5, 30, 30, 25, 15]);
  const [secondLargest, setSecondLargest] = useState(null);

  const findSecondLargest = () => {
    const uniqueNumbers = [...new Set(numbers)]; // Remove duplicates
    if (uniqueNumbers.length < 2) {
      setSecondLargest("Not enough elements");
      return;
    }
    uniqueNumbers.sort((a, b) => b - a); // Sort in descending order
    setSecondLargest(uniqueNumbers[1]); // Second largest element
  };

  return (
    <div style={{ padding: "20px" }}>
      <h3>Array: {JSON.stringify(numbers)}</h3>
      <button onClick={findSecondLargest}>Find Second Largest</button>
      {secondLargest !== null && <h4>Second Largest: {secondLargest}</h4>}
    </div>
  );
};

export default SecondLargestNumber;
```

</details>

---

Q5. Rotate the elements in an array with respect to its index.
<br>
Let arr=[1,2,3,4,5,6]
index=2
<br>
Output=[3,4,5,6,1,2]

<details><summary>Answer</summary>

```js
import React, { useState } from "react";

const RotateArray = () => {
  const [arr, setArr] = useState([1, 2, 3, 4, 5, 6]);
  const [index, setIndex] = useState(2);
  const [rotatedArray, setRotatedArray] = useState([]);

  const rotateArray = () => {
    if (index < 0 || index >= arr.length) {
      setRotatedArray("Invalid index");
      return;
    }
    const rotated = [...arr.slice(index), ...arr.slice(0, index)];
    setRotatedArray(rotated);
  };

  return (
    <div style={{ padding: "20px" }}>
      <h3>Original Array: {JSON.stringify(arr)}</h3>
      <h4>Rotation Index: {index}</h4>
      <button onClick={rotateArray}>Rotate Array</button>
      {rotatedArray.length > 0 && (
        <h4>Rotated Array: {JSON.stringify(rotatedArray)}</h4>
      )}
    </div>
  );
};

export default RotateArray;
```

</details>

---

Q6. We have a button called add circle. Whenever we click on that circle, it should create circle and also the count should increase. Whenever you click on the circle, the circle background color should change to Grey color and also the count should increase. If we once again click on that circle background, the color should change into white and there should be a decrease in the count.

<details><summary>Answer</summary>

```js
import React, { useState } from "react";

const CircleApp = () => {
  const [circles, setCircles] = useState([]); // Stores circle objects
  const [count, setCount] = useState(0); // Keeps track of count

  // Function to add a new circle
  const addCircle = () => {
    setCircles([...circles, { id: circles.length, isGray: false }]);
    setCount(count + 1);
  };

  // Function to toggle circle color
  const toggleCircleColor = (id) => {
    setCircles((prevCircles) =>
      prevCircles.map((circle) =>
        circle.id === id ? { ...circle, isGray: !circle.isGray } : circle
      )
    );

    // Adjust count based on color change
    setCount((prevCount) =>
      circles.find((circle) => circle.id === id)?.isGray
        ? prevCount - 1
        : prevCount + 1
    );
  };

  return (
    <div style={{ padding: "20px", textAlign: "center" }}>
      <h3>Count: {count}</h3>
      <button
        onClick={addCircle}
        style={{ padding: "10px", marginBottom: "20px" }}
      >
        Add Circle
      </button>
      <div
        style={{
          display: "flex",
          gap: "10px",
          flexWrap: "wrap",
          justifyContent: "center",
        }}
      >
        {circles.map((circle) => (
          <div
            key={circle.id}
            onClick={() => toggleCircleColor(circle.id)}
            style={{
              width: "50px",
              height: "50px",
              borderRadius: "50%",
              backgroundColor: circle.isGray ? "gray" : "white",
              border: "2px solid black",
              cursor: "pointer",
            }}
          ></div>
        ))}
      </div>
    </div>
  );
};

export default CircleApp;
```

</details>

---

Q7. const arr = ['hello', 'sky', 'cloud']; <br>
Without using inbuilt methods and if using loops, use only one loop and find the number of vowels in each element of the given array.  
<br>
Output array should be ['2', '0', '2']

<details><summary>Answer</summary>

```js
import React, { useState } from "react";

const VowelCount = () => {
  const [arr] = useState(["hello", "sky", "cloud"]); // Given array
  const [vowelCounts, setVowelCounts] = useState([]);

  const countVowels = () => {
    let result = new Array(arr.length).fill(0); // Initialize an array with 0s
    let vowels = { a: true, e: true, i: true, o: true, u: true }; // Set to check vowels

    // Single loop to iterate through all words and characters
    for (
      let i = 0, wordIndex = 0, charIndex = 0;
      i < arr.join("").length;
      i++
    ) {
      if (charIndex === arr[wordIndex].length) {
        wordIndex++;
        charIndex = 0;
      }
      if (wordIndex >= arr.length) break;

      if (vowels[arr[wordIndex][charIndex]]) {
        result[wordIndex]++;
      }
      charIndex++;
    }

    setVowelCounts(result);
  };

  return (
    <div style={{ padding: "20px", textAlign: "center" }}>
      <h3>Original Array: {JSON.stringify(arr)}</h3>
      <button
        onClick={countVowels}
        style={{ padding: "10px", marginBottom: "20px" }}
      >
        Count Vowels
      </button>
      <h4>Vowel Counts: {JSON.stringify(vowelCounts)}</h4>
    </div>
  );
};

export default VowelCount;
```

</details>

---
