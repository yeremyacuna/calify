# JavaScript, JSON, and Input Validation

**Track:** Phase 00 — Recovery & Audit  
**Difficulty:** Beginner to intermediate  
**Project link:** Calify historical Apps Script API  
**Status:** Learning note; code samples are synthetic and contain no production identifiers.

## 1. Learning goals

By the end of this lesson you should be able to:

- Explain the difference between a JavaScript object and a JSON string.
- Read a request body and choose the correct validation order.
- Distinguish a missing score from a legitimate numerical zero.
- Explain why backend validation is required even when a mobile interface validates.
- Write a small, independently testable JavaScript function.

## 2. Key terminology

| Term | Meaning |
| --- | --- |
| **Object** | A JavaScript value containing properties and methods. |
| **JSON** | A text-based format for transferring structured data. |
| **Serialization** | Converting data to a transport/storage representation. |
| **Parsing** | Interpreting a serialized format as a usable value. |
| **Payload** | The data sent in an HTTP request or response. |
| **Validation** | Checking that input meets declared rules. |
| **Coercion** | JavaScript automatically or explicitly converting one type into another. |
| **Trust boundary** | The point where untrusted input enters a system. |

## 3. JavaScript objects vs. JSON

A JavaScript object exists inside the language runtime:

```js
const assessment = {
  course: "DEMO",
  assessment: "Quiz 1",
  score: 0,
  maxScore: 20,
};
```

JSON is a string representation of the same information:

```js
const serialized = JSON.stringify(assessment);
const parsed = JSON.parse(serialized);

console.log(typeof assessment); // "object"
console.log(typeof serialized); // "string"
console.log(parsed.score); // 0
```

A backend commonly receives a JSON request body, parses it, validates its fields, performs a controlled operation, and serializes a response.

## 4. HTTP request anatomy

Example of an invented demo request — **not a production endpoint**:

```http
POST /v2/assessments/record-score HTTP/1.1
Content-Type: application/json

{
  "course": "DEMO",
  "assessmentId": "demo-quiz-001",
  "score": 0
}
```

`POST` indicates a request that may cause a server-side change. JSON defines the structure of its body; it does not itself provide authentication, authorization, or protection from duplicate submissions.

**Historical Calify note:** The inspected Legacy backup implements action dispatch within `doPost(e)`; active Production must be audited separately.

## 5. A real JavaScript pitfall: Number conversion

Try this in Node.js:

```js
console.log(Number(""));        // 0
console.log(Number(null));      // 0
console.log(Number("15"));      // 15
console.log(Number(undefined)); // NaN
```

A legitimate score of `0` and an empty input must not be treated as equivalent. In Calify, a blank score can mean **Pending**, while numerical zero is a valid recorded result.

## 6. A safer validation function

```js
function parseScore(input, maxScore) {
  // Reject absent values before converting types.
  if (input === null || input === undefined || input === "") {
    throw new Error("A score is required.");
  }

  // Reject booleans and other unsupported input types.
  if (typeof input !== "number" && typeof input !== "string") {
    throw new Error("The score must be a number.");
  }

  const value = Number(input);

  if (!Number.isFinite(value)) {
    throw new Error("The score must be finite.");
  }

  if (!Number.isFinite(maxScore) || maxScore <= 0) {
    throw new Error("The maximum score is invalid.");
  }

  if (value < 0 || value > maxScore) {
    throw new Error(`The score must be between 0 and ${maxScore}.`);
  }

  return value;
}

console.log(parseScore(0, 20));    // 0
console.log(parseScore("17", 20)); // 17
```

This function is a **teaching example**. Production integration still needs an explicit API contract, a decision on accepted score formats, state checks, authentication and an idempotency strategy.

## 7. Basic tests

```js
import assert from "node:assert/strict";

assert.equal(parseScore(0, 20), 0);
assert.equal(parseScore("17", 20), 17);
assert.throws(() => parseScore("", 20));
assert.throws(() => parseScore(null, 20));
assert.throws(() => parseScore(21, 20));
assert.throws(() => parseScore(-1, 20));
assert.throws(() => parseScore("invalid", 20));
assert.throws(() => parseScore(10, 0));
```

Run the assertions in an ES module environment after defining or importing `parseScore`. The tests demonstrate the idea, not that Calify Production has passed them.

## 8. Common mistakes and edge cases

- Calling `Number(input)` before checking whether the value is empty.
- Accepting a numeric score for an activity that only supports completion.
- Assuming a client-generated score is trustworthy.
- Updating a completed assessment without a correction policy.
- Retrying a write after a timeout without an idempotency key.
- Using a display label as though it were a globally unique identifier.
- Returning a successful response before data has been verified.

## 9. Practice exercises

**Exercise A — Beginner:** Add `parseScore("20", 20)` and `parseScore(20.5, 20)` to the tests. Predict their results first.

**Exercise B — Intermediate:** Modify `parseScore` to reject strings containing only spaces. Explain the difference between checking `input === ""` and `input.trim() === ""`.

**Exercise C — Applied:** Design a function `canRecord(status)` that returns `true` only for a pending assessment. Write three test cases.

**Exercise D — System design:** Describe how a unique request ID could help the backend distinguish a retry from a second write. What must the server remember?

## 10. Self-check

1. Can `JSON.parse` establish that a request is authorized? **No.** It only parses a serialized value.
2. Why is `Number("")` dangerous in a grade tracker? **It converts missing input to a valid-looking zero.**
3. Is client-side validation enough? **No.** The backend must enforce the rules.
4. Is a JavaScript `Error` the same thing as an HTTP status code? **No.** The API must define its response mapping.

## 11. Further study

- MDN: [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)
- MDN: [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)
- MDN: [Number.isFinite](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isFinite)
- Google: [Apps Script Web Apps](https://developers.google.com/apps-script/guides/web)

## 12. Learning reflection

Fill out after practice:

- **I can explain:** ...
- **I implemented:** ...
- **I tested:** ...
- **I still need to study:** ...
- **Related commit/PR:** ...
