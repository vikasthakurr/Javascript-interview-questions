# 11. JavaScript Coding Puzzles / Practical Questions – 50 Interview Questions with Detailed Explanations

---

## 1. Reverse a string
**Theory:**
Reverse the characters in a string.

**Code:**
```js
function reverseString(str){
  return str.split('').reverse().join('');
}
console.log(reverseString('hello'));
```

---

## 2. Check for palindrome
**Theory:**
A palindrome reads the same forward and backward.

**Code:**
```js
function isPalindrome(str){
  const reversed = str.split('').reverse().join('');
  return str === reversed;
}
console.log(isPalindrome('level'));
```

---

## 3. Factorial of a number
**Theory:**
Calculate product of all positive integers up to n.

**Code:**
```js
function factorial(n){
  if(n===0) return 1;
  return n * factorial(n-1);
}
console.log(factorial(5));
```

---

## 4. Fibonacci sequence
**Theory:**
Generate a sequence where each number is sum of previous two.

**Code:**
```js
function fibonacci(n){
  const seq=[0,1];
  for(let i=2;i<n;i++) seq.push(seq[i-1]+seq[i-2]);
  return seq;
}
console.log(fibonacci(10));
```

---

## 5. Find max in array
**Theory:**
Find largest number using Math.max or iteration.

**Code:**
```js
const arr=[1,5,3];
console.log(Math.max(...arr));
```

---

## 6. Find min in array
**Theory:**
Find smallest number in array.

**Code:**
```js
console.log(Math.min(...arr));
```

---

## 7. Sum of array elements
**Theory:**
Add all elements using reduce.

**Code:**
```js
console.log(arr.reduce((a,b)=>a+b,0));
```

---

## 8. Remove duplicates from array
**Theory:**
Use Set to store unique elements.

**Code:**
```js
const unique=[...new Set(arr)];
```

---

## 9. Flatten nested array
**Theory:**
Convert multi-dimensional array into single dimension.

**Code:**
```js
const nested=[1,[2,3],[4,[5]]];
console.log(nested.flat(2));
```

---

## 10. Find missing number
**Theory:**
Find number missing in a consecutive sequence.

**Code:**
```js
function findMissing(arr){
  const n=arr.length+1;
  const sumExpected=n*(n+1)/2;
  const sumActual=arr.reduce((a,b)=>a+b,0);
  return sumExpected-sumActual;
}
```

---

## 11. Reverse words in a sentence
**Theory:**
Reverse order of words, not characters.

**Code:**
```js
function reverseWords(str){
  return str.split(' ').reverse().join(' ');
}
```

---

## 12. Capitalize first letter of each word
**Theory:**
Make first character uppercase.

**Code:**
```js
function capitalize(str){
  return str.split(' ').map(w=>w[0].toUpperCase()+w.slice(1)).join(' ');
}
```

---

## 13. Count vowels in string
**Theory:**
Iterate and check for vowels.

**Code:**
```js
function countVowels(str){
  return str.match(/[aeiou]/gi)?.length||0;
}
```

---

## 14. Check prime number
**Theory:**
Number divisible only by 1 and itself.

**Code:**
```js
function isPrime(n){
  if(n<2) return false;
  for(let i=2;i<=Math.sqrt(n);i++) if(n%i===0) return false;
  return true;
}
```

---

## 15. Generate random number in range
**Theory:**
Use Math.random and scale to desired range.

**Code:**
```js
function random(min,max){ return Math.floor(Math.random()*(max-min+1))+min; }
```

---

## 16. Remove falsy values from array
**Theory:**
Filter out undefined, null, 0, false, '', NaN.

**Code:**
```js
const clean=arr.filter(Boolean);
```

---

## 17. Deep clone object
**Theory:**
Copy object including nested structures.

**Code:**
```js
const clone=JSON.parse(JSON.stringify(obj));
```

---

## 18. Shallow copy object
**Theory:**
Copy only top-level properties.

**Code:**
```js
const copy={...obj};
```

---

## 19. Merge two objects
**Theory:**
Combine properties of objects.

**Code:**
```js
const merged={...obj1,...obj2};
```

---

## 20. Check if array includes value
**Theory:**
Use `includes` method for simplicity.

**Code:**
```js
arr.includes(5);
```

## 21. Find largest element in array
**Theory:**
Iterate through array to find max value.

**Code:**
```js
function findMax(arr){
  return Math.max(...arr);
}
```

---

## 22. Find smallest element in array
**Theory:**
Iterate through array to find min value.

**Code:**
```js
function findMin(arr){
  return Math.min(...arr);
}
```

---

## 23. Sum of digits of number
**Theory:**
Convert number to string or use modulo to sum digits.

**Code:**
```js
function sumDigits(n){
  return n.toString().split('').reduce((a,b)=>a+Number(b),0);
}
```

---

## 24. Count occurrence of element in array
**Theory:**
Count how many times a value appears.

**Code:**
```js
function countOccur(arr,val){
  return arr.filter(x=>x===val).length;
}
```

---

## 25. Remove duplicates from string
**Theory:**
Keep unique characters.

**Code:**
```js
function uniqueChars(str){
  return [...new Set(str)].join('');
}
```

---

## 26. Find second largest number
**Theory:**
Sort array and pick second last element.

**Code:**
```js
function secondLargest(arr){
  const sorted=[...arr].sort((a,b)=>b-a);
  return sorted[1];
}
```

---

## 27. Rotate array by k elements
**Theory:**
Move last k elements to start.

**Code:**
```js
function rotate(arr,k){
  k=k%arr.length;
  return arr.slice(-k).concat(arr.slice(0,-k));
}
```

---

## 28. Check Armstrong number
**Theory:**
Number equals sum of digits raised to power of digits count.

**Code:**
```js
function isArmstrong(n){
  const digits=n.toString();
  return n===digits.split('').reduce((sum,d)=>sum+Math.pow(Number(d),digits.length),0);
}
```

---

## 29. Merge two sorted arrays
**Theory:**
Combine and sort or merge manually.

**Code:**
```js
function mergeSorted(a,b){
  return [...a,...b].sort((x,y)=>x-y);
}
```

---

## 30. Find common elements in arrays
**Theory:**
Use filter and includes or sets.

**Code:**
```js
function commonElements(a,b){
  return a.filter(x=>b.includes(x));
}
```

---

## 31. Convert string to title case
**Theory:**
Capitalize first letter of each word.

**Code:**
```js
function titleCase(str){
  return str.split(' ').map(w=>w[0].toUpperCase()+w.slice(1).toLowerCase()).join(' ');
}
```

---

## 32. Find missing numbers in array
**Theory:**
Compare against expected range.

**Code:**
```js
function missingNumbers(arr,start,end){
  const full=Array.from({length:end-start+1},(_,i)=>i+start);
  return full.filter(x=>!arr.includes(x));
}
```

---

## 33. Check anagram
**Theory:**
Two strings have same characters in any order.

**Code:**
```js
function isAnagram(a,b){
  return a.split('').sort().join('')===b.split('').sort().join('');
}
```

---

## 34. FizzBuzz problem
**Theory:**
Print numbers, multiples of 3 as 'Fizz', multiples of 5 as 'Buzz', both as 'FizzBuzz'.

**Code:**
```js
for(let i=1;i<=100;i++){
  let str='';
  if(i%3===0) str+='Fizz';
  if(i%5===0) str+='Buzz';
  console.log(str||i);
}
```

---

## 35. Count words in string
**Theory:**
Split string by spaces and count.

**Code:**
```js
function wordCount(str){ return str.trim().split(/\s+/).length; }
```

---

## 36. Find longest word
**Theory:**
Iterate and compare lengths.

**Code:**
```js
function longestWord(str){
  return str.split(' ').reduce((a,b)=>b.length>a.length?b:a);
}
```

---

## 37. Sum of two numbers equals target
**Theory:**
Check for pair of numbers adding to target.

**Code:**
```js
function hasPair(arr,target){
  const set=new Set();
  for(let n of arr){
    if(set.has(target-n)) return true;
    set.add(n);
  }
  return false;
}
```

---

## 38. Check if array is sorted
**Theory:**
Compare each element with previous.

**Code:**
```js
function isSorted(arr){
  for(let i=1;i<arr.length;i++) if(arr[i]<arr[i-1]) return false;
  return true;
}
```

---

## 39. Remove falsy values from array
**Theory:**
Filter out null, undefined, 0, false, ''.

**Code:**
```js
arr.filter(Boolean);
```

---

## 40. Deep flatten array
**Theory:**
Convert nested arrays to single-level array.

**Code:**
```js
function deepFlatten(arr){
  return arr.reduce((acc,val)=>acc.concat(Array.isArray(val)?deepFlatten(val):val),[]);
}
```
# 11. JavaScript Coding Puzzles / Practical Questions – 50 Interview Questions with Detailed Explanations (Final Set)

---

## 41. Rotate matrix by 90 degrees
**Theory:**
Transform 2D array clockwise.

**Code:**
```js
function rotateMatrix(matrix){
  const n=matrix.length;
  const res=Array.from({length:n},()=>Array(n));
  for(let i=0;i<n;i++){
    for(let j=0;j<n;j++){
      res[j][n-1-i]=matrix[i][j];
    }
  }
  return res;
}
```

---

## 42. Spiral order of matrix
**Theory:**
Traverse 2D array in spiral order.

**Code:**
```js
function spiral(matrix){
  const res=[];
  while(matrix.length){
    res.push(...matrix.shift());
    for(let row of matrix) res.push(row.pop());
    if(matrix.length) res.push(...matrix.pop().reverse());
    for(let row of matrix.reverse()) res.push(row.shift());
    matrix.reverse();
  }
  return res;
}
```

---

## 43. Find duplicate numbers
**Theory:**
Identify repeated elements.

**Code:**
```js
function findDuplicates(arr){
  const seen=new Set(), duplicates=new Set();
  for(let n of arr){
    if(seen.has(n)) duplicates.add(n);
    seen.add(n);
  }
  return [...duplicates];
}
```

---

## 44. Intersection of arrays
**Theory:**
Find common elements.

**Code:**
```js
function intersection(a,b){
  return a.filter(x=>b.includes(x));
}
```

---

## 45. Union of arrays
**Theory:**
Combine elements uniquely.

**Code:**
```js
function union(a,b){
  return [...new Set([...a,...b])];
}
```

---

## 46. Longest substring without repeating characters
**Theory:**
Sliding window technique for efficiency.

**Code:**
```js
function lengthOfLongestSubstring(s){
  const set=new Set();
  let left=0,maxLen=0;
  for(let right=0;right<s.length;right++){
    while(set.has(s[right])) set.delete(s[left++]);
    set.add(s[right]);
    maxLen=Math.max(maxLen,set.size);
  }
  return maxLen;
}
```

---

## 47. Valid parentheses
**Theory:**
Check if all parentheses are properly closed using stack.

**Code:**
```js
function isValid(s){
  const stack=[], map={')':'(', '}':'{', ']':'['};
  for(let c of s){
    if(map[c]){
      if(stack.pop()!==map[c]) return false;
    }else stack.push(c);
  }
  return stack.length===0;
}
```

---

## 48. Two sum problem
**Theory:**
Find indices of two numbers that add to target.

**Code:**
```js
function twoSum(nums,target){
  const map={};
  for(let i=0;i<nums.length;i++){
    if(map[target-nums[i]]!==undefined) return [map[target-nums[i]],i];
    map[nums[i]]=i;
  }
}
```

---

## 49. Maximum subarray sum
**Theory:**
Use Kadane's algorithm for optimal sum of contiguous subarray.

**Code:**
```js
function maxSubArray(nums){
  let maxCurrent=nums[0], maxGlobal=nums[0];
  for(let i=1;i<nums.length;i++){
    maxCurrent=Math.max(nums[i],maxCurrent+nums[i]);
    maxGlobal=Math.max(maxGlobal,maxCurrent);
  }
  return maxGlobal;
}
```

---

## 50. Merge intervals
**Theory:**
Combine overlapping intervals.

**Code:**
```js
function mergeIntervals(intervals){
  intervals.sort((a,b)=>a[0]-b[0]);
  const res=[intervals[0]];
  for(let i=1;i<intervals.length;i++){
    if(intervals[i][0]<=res[res.length-1][1]) res[res.length-1][1]=Math.max(res[res.length-1][1],intervals[i][1]);
    else res.push(intervals[i]);
  }
  return res;
}

