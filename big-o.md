Simplify the following big O expressions as much as possible:

O(n + 10) = O(n)

O(100 × n)  = O(n)

O(25)   = O(1)

O(n^2 + n^3)  = O(n^3)

O(n + n + n + n)    = O(n)

O(1000 × log(n) + n)    = O(n)

O(1000 × n × log(n) + n)    = O(n log(n))

O(2^n + n^2)  = O(2^n)

O(5 + 3 + 1)    = O(1)




Step Two: Calculating Time Complexity»

Determine the time complexities for each of the following functions.
If you’re not sure what these functions do, copy and paste them into the console
and experiment with different inputs!


function logUpTo(n) {
  for (let i = 1; i <= n; i++) {
    console.log(i);
  }
}

    Time Complexity: O(n)



function logAtLeast10(n) {
  for (let i = 1; i <= Math.max(n, 10); i++) {
    console.log(i);
  }
}

    Time Complexity: O(n)



function logAtMost10(n) {
  for (let i = 1; i <= Math.min(n, 10); i++) {
    console.log(i);
  }
}
    Time Complexity: O(1)



function onlyNumsAtEvenIndexes(nums) {
  let numsAtEvens = [];

  for (let i = 0; i < nums.length; i++) {
    if (i % 2 === 0) {
      numsAtEvens.push(nums[i]);
    }
  }

  return numsAtEvens;
}

    Time Complexity: O(n)



function runningSubtotals(nums) {
  let subtotals = [];

  for (let i = 0; i < nums.length; i++) {
    let subtotal = 0;
    for (let j = 0; j <= i; j++) {
      subtotal += nums[j];
    }
    subtotals.push(subtotal);
  }

  return subtotals;
}

    Time Complexity:   O(n^2)



const VOWELS = "aeiouAEIOU";

function vowelsCounts(word) {
  let vowelsToCounts = {};

  for (let char of word) {              -- O(n)
    if (VOWELS.includes(char)) {        -- O(1)
      if (char in vowelsToCounts) {     -- O(1)
        vowelsToCounts[char] += 1;
      } else {
        vowelsToCounts[char] = 1;
      }
    }
  }

  return vowelsToCounts;
}

    Time Complexity:   O(n)







Step Three: Short answer»
Answer the following questions

True or false: n^2 + n is O(n^2).       -- True

True or false: n^2 * n is O(n^3).        -- True

True or false: n^2 + n is O(n).          -- False

What’s the time complexity of the .indexOf array method?    -- O(n)

What’s the time complexity of the .includes array method?   -- O(n)

What’s the time complexity of the .every array method?      -- O(n)

What’s the time complexity of the .sort array method?       -- O(n log n)

What’s the time complexity of the .unshift array method?    -- O(n)

What’s the time complexity of the .push array method?       -- O(1)

What’s the time complexity of the .pop array method?        -- O(1)

What’s the time complexity of the Object.keys() function?   -- O(n)





Further Study»

Write a function called pairSum that takes an array of positive numbers and
finds the largest sum of two numbers in the array.


an easy and clear implementation that is O(n2):

function pairSum(nums) {
    let highestSum = -Infinity;

    for (let i = 0; i < nums.length; i++) {         == O(n)
        for (let j = i+1; j < nums.length; j++) {     == O(n)
            let sum = nums[i] + nums[j];
                if (sum > highestSum) {
                    highestSum = sum;
                }
        }
    }

    return highestSum;
}

Time Complexity: O(n^2)




a solution that is easy to write, relies on a JS array methods, and is O(n log n)

function pairSum(nums) {
    nums.sort();                                    -- O(n log(n));
    let highestNum = nums[nums.length-1];
    let secondHighestNum = nums[nums.length-2];
    return (highestNum + secondHighestNum);
}

Time Complexity: O(n log(n))



a solution that might be harder to find/understand, but is O(n)

function pairSums(nums) {
    let highestNum = -Infinity;
    let secondHighestNum = -Infinity;

    for (let i = 0; i < nums.length; i++) {             -- O(n)
        if (nums[i] >= highestNum) {
            secondHighestNum = highestNum;
            highestNum = nums[i];
        }
    }

    return (highestNum + secondHighestNum);
}

Time Complexity: O(n)