# LEETCODE-Strings-273
## Dry Run: Understanding the Code's Logic

### Understanding the Code
Before we dive into a dry run, let's recap the code's functionality:
* **Map Initialization:** A static map is created with key-value pairs representing numbers and their corresponding word representations.
* **numberToWords Method:**
  * Handles numbers up to billions.
  * Breaks down the number into billions, millions, thousands, and hundreds places.
  * Uses `get3Digits` to convert three-digit numbers to words.
  * Concatenates the results into a string.
* **get3Digits Method:**
  * Handles three-digit numbers.
  * Converts hundreds, tens, and ones places to words.
  * Concatenates the results into a string.

### Dry Run Example: Number = 1234567
Let's break down the process step by step:

#### Step 1: numberToWords(1234567)
* `num` is 1234567, which is not 0.
* `StringBuilder sb` is initialized.
* The loop starts with `i = 1000000000`.
  * `num >= i` is false (1234567 < 1000000000).
* The loop continues with `i = 1000000`.
  * `num >= i` is true (1234567 >= 1000000).
  * `get3Digits(num / i)` is called with `num / i = 1234567 / 1000000 = 1`.
  * `sb` becomes "One Million".
  * `num %= i` becomes 1234567 % 1000000 = 234567.

#### Step 2: get3Digits(1)
* `num` is 1.
* `num >= 100` is false.
* `num > 0` is true.
* `num < 20` is true.
* `sb` becomes "One".

#### Step 3: Back to numberToWords
* `sb` is now "One Million".
* The loop continues with `i = 1000`.
  * `num >= i` is true (234567 >= 1000).
  * `get3Digits(num / i)` is called with `num / i = 234567 / 1000 = 234`.
  * `sb` becomes "One Million Two Hundred Thirty Four Thousand".
  * `num %= i` becomes 234567 % 1000 = 567.

#### Step 4: get3Digits(234)
* `num` is 234.
* `num >= 100` is true.
* `sb` becomes "Two Hundred".
* `num %= 100` becomes 34.
* `num > 0` is true.
* `num < 20` is false.
* `num % 10` is not 0.
* `sb` becomes "Two Hundred Thirty Four".

#### Step 5: Back to numberToWords
* `sb` is now "One Million Two Hundred Thirty Four Thousand Two Hundred Thirty Four".
* The loop continues with `i = 1`.
  * `num >= i` is true (567 >= 1).
  * `get3Digits(num / i)` is called with `num / i = 567 / 1 = 567`.
  * `sb` becomes "One Million Two Hundred Thirty Four Thousand Two Hundred Thirty Four Five Hundred Sixty Seven".
  * `num %= i` becomes 567 % 1 = 0.

#### Step 6: Final Result
* The loop ends.
* `sb.substring(1)` removes the leading space and returns:
  "One Million Two Hundred Thirty Four Thousand Two Hundred Thirty Four Five Hundred Sixty Seven"

