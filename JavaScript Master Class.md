Notes from Salesforce Senior Engineer

Data Structures
-------------------------
  Linear
    - Arrays
    - Stacks (Recursion!)
    - Queues
    - Hash Tables
    - Linked Lists

  Hierarchical
    - Trees
    - Graphs
    - Heaps
--------------------------

Algorithms
--------------------------
  - Binary Search
  - Depth-First Search
  - Breadth-First Search
  - Two-Pointer Solutions
  - Quicksort/Mergesort
  - Dynamic Programming
------------------------------
These are the fundamental building blocks of all tech companies
----------------------------------------------------------------------------------------------------------------



The 4 Pillars of a Technical Interview

    Communication
        Introduction without rambling
        Demonstrates technical knowledge verbally before execution (communicate what you would do on a white board 
            in general steps) (No extensive gaps in conversation i.e. 10 minutes, but small pauses are fine just say "hey I need a minute or two to think in silence")
    Problem Solving
        Don't need optimal answer, the question is can you communicate well with good syntax and idea exploration
        Identify the brute force way, then ideas to make it better
        Did you discuss the time and space complexity
    Syntax
        Well-named variables and functions
        Helper methods when applicable
        Demonstrates proficiency in chosen language
        Good sense of software engineering conventions (function called isValid() will return a boolean)
    Verification
        Considers edge cases (for ambiguous instances)
----------------------------------------


What you DON'T NEED TO WORRY ABOUT IN AN INTERVIEW.
    - Brain teasers
    - Math
    - Memorizing library information
    - Leabing a specific language for interviewing, just stick to .js or React.


How do I get good at these interviews?
    Time spent practicing interview questions directly correlates with their capability and success. (Can start with Hackerrank if leetcode easy is too hard at first)
    Get good at Leetcode Mediums as your end goal. For a top tech company, complete two leetcode mediums in an hour. (Don't bother with leetcode hard, time waster.)

********TOP RECOMMENDATION********
Get good at time/space complexity. (See image in this folder)

--> If you know which algorithms are popular for the respective complexity, you're set. Just    practice those. 

If you're going to practice, practice in the same environment as the interview. Witeboard... record with a camera...






JS Masterclass with Colt Steel:

Time complexity: Big O Notation for runtime

O(1) : Constant time regardless of size of input
    function addUpToSecond(n) {
        return n * (n + 1) / 2;
    }
    <!-- O(any sole integer) like O(500) is simplified to O(1) and the 
    <!--    runtime chart will always be flat-->


O(n) : As n increases, the runtime grows relative to the increase
    function AddUpToFirst(n) {
        let total = 0;
        for (let i = 0; i <= n; i++) {
            total += i;
        }
        return total;
    }
    <!-- O(any constant before n) like O(5n) is simplified to O(n) -->


O(n^2) : Exponential curve, quadratic. Example, two nested for-loops
    function printAllPairs(n) {
        for (let i = 0; i < n; i++) {
            for (let j = 0; j < n; j++) {
                console.log(i, j)
            }
        }
    }

    <!-- O(14n^2) is simplified to O(n^2) -->
    <!-- O(n^4) is truly O(n^4) -->

    <!--  all of these simplifications are so, because when we look at the chart
            and zoom out, they all look either flat, increasing linearly, or exponential. -->

    <!--  O(n + 10) = O(n)
          O(1000n + 50) = O(n)
          O(n^2 + 5n + 8) = O(n^2)-->



Rules of thumb for time complexity:
    1. Arithmetic operations are constant
    2. Variable assignment is also constant
    3. Accessing elements in an array (by index) or object (by key) is constant
    4. In a loop, the complexity is (the length of the loop) * (the complexity of whatever happens inside of the loop).







Space (Memory) Complexity (Auxiliary space complexity)
    The amount of space reqiured by the algorithm (NOT the size of n, because we already 
    know how that changes with size).
 
    Most primitives (bnooleans, numnbers, undefined, null etc) are constant space.
    Strings are O(n) space, because they take up more character space than say a single integer of 100.
    Reference types (arrays or objects) are also O(n), because an array.length = 4 is twice as much space
        as an array.length of 2. 

        This function has two space takers. total = 0, and let i = 0. 
    function summ(arr) {
        let total = 0; 
        for (let i = 0; i < arr.length; i++) {
            total += arr[i]
        }
        return total;
    }
        This means constant space, O(1) space, because the space is always the same.


        This function has two space takers. The first (newArr) increases proportionally to the input arr length; so when the input
            doubles, newArr doubles and so forth. So it's O(n) SPACE complexity.
    function double(arr) {
        let newArr = [];
        for (let i = 0; i < arr.length; i++) {
            newArr.push(2 * arr[i])
        }  
        return newArr;
    }

        This is O(n) space complexity because the output increases proportional to the size of the input.
    function onlyElementsAtEvenIndex(array) {
    let newArray = Array(Math.ceil(array.length / 2));

    for (let i = 0; i < array.length; i++) {
        if (i % 2 === 0) {
            console.log(i)
            newArray[i / 2] = array[i]
            console.log(newArray)
        }
    }
    return newArray;
}





LOGARITHMS

log(base2)(8) = 3
<!-- what power of 2 to we need to get 8? Well, 2^3 = 8. So the answer is 3. -->
<!-- the default log expression is always log(base2) -->
You can also say okay how many times do i have to halve 8 to get to either 1 or less?
or for 25: 25 / 2 = 12.5
12.5 / 2 = 6.25
6.25 / 2 = 3.125
3.125 / 2 = 1.56525
1.5625 / 2 = .78125 This was 5 total divisions or halvings, so log(25) which is the same as log(base2)(25) = 5.

O(log n) is basically just as good as O(1) for time complexity.

Certain searching algorithms do have logarithmic time complexity. 
So do efficient sorting algorithms. 
So does recursion. That's it. 





BUILT-IN DATA STRUCTURES

OBJECTS
Objects work well when:
    When you don't need order
    When you need fast access (looking for keys), insertion and removal, all O(1)
    Searching however is O(n). Searching is checking if a given piece of information is located as a value. 

Object methods: 
    Object.keys() O(n) because as the numnber of items in an object increases, the number of keys increases the same for the output.
    Object.values() O(n)
    Object.entries() O(n) (this gives all the keys AND values :) )
    hasOwnProperty() O(n)

Objects are basic, quick, and work very well in a lot of situations. (Arrays do to, but complexity can be higher depending on their operations.)


ARRAYS (which are ordered lists)
Work well when
    You need order
    When you need fast access and insertion (unless inserting at front). Access is fast because there's a direct shortcut to that index location
        without having to start from the beginning. So its constant time. 

Insertion and removal
    End is super fast
    Beginning is terrible if long length since every element has to be re-indexed. O(n) time for this. 
        But, it can be meaningful to add to the front, so just be aware of the inefficiency.
        push() and pop() always faster than shift() and unshift(). 

Searching
    You have to search the entire array from the beginning to see if a value is present, so this is O(n) time.  

All major array operations: 
    push O(1)
    pop O(1)
    shift O(n)
    unshift O(n)
    concatO(n)
    slice O(n)
    splice O(n)
    sort O(n * log n) more on this later
    forEach/map/filter/reduce/etc O(n)





ALGORITHMS AND PROBLEM SOLVING PATTERNS

OBJECTIVES
    Define what an algorithm is
    Devise a plan to solve algorithms
    Compare and contrast problem solving patterns including frequency counters, two pointer problems and divide and conquer

An algorithm is a process or set of steps to accomplish a certain task. 

How do you improve?
    - Devise a plan for solving problems
    - Master common problem solving patterns










    Problem solving
        Understand the problem
            1. Can I restate the problem in my own words?
            2. What are the inputs that go into the problem?
            3. What are the outputs that should come from the solution to the problem?
            4. Can the outputs be determined from the inputs? In other words, do I have enough information to solve the problem? (You may not be able to answer this question until you set about solving the problem. That's okay; it's still worth considering the question at this early stage.)
            5. How should I label the important pieces of data that are a part of the problem?
        Explore concrete examples (inputs and outputs, edge cases)
        Break it down
        Solve/simplify
        Look back and refactor



Above steps applied in interiew:

-Understand the problem: Above 
    Can explicity write out the steps you need to take .This forces you to think about the code you'll write before you write it, and helps you catch any lingering conceptual issues or misunderstandinfs before yoou dive in and have to worroy about details (e.g. language syntax) as well.

EXAMPLE: "Write a function which takes in a string and returns the counts of each character in the string.

-Explore concrete examples: Can write out some examples of inputs and outputs and edge cases
    "Hello, there!" (capital letters, punctuation, spaces)
    "sadmo dsoiwedn ASOIJW 21302384" (with numbers)
    "" (empty string)

-Break it down: Then type out the skeleton of the problem function

    function charCount (str) {
        // create object variable 
        // loop over string
            // if current char is a number/ letter and is a isnt present, create key,
            and create value that starts at 1. 
            // if char is something else (" ", ".", etc) don't do anything.
            // if exists again and is number\letter, increment++. 
        // return object
    }

-Solve / Simplify
    Find the core difficulty in what you're trying to do.. the thing that you may be panicking about and that's tripping you up. Then, temporarily ignore that thing. 
    Write a simplified solution. 
    Then, incorporate that difficulty back in.

    function charCount (str) {
        // create object variable 
        let charsPresent = {};

        // loop over string
        for (let i = 0; i < str.length; i++) {
            let char = str[i]

            // if current char is a number/ letter and is a isnt present, create key with value of 1,
            if (!charsPresent[char]) {
                charsPresent[char] = 1

            // if exists and is number\letter, increment++. 
            } else {
                charsPresent[char]++
            }
        }
            // if char is something else (" ", ".", etc) don't do anything.
        // return object
        return charsPresent;
    }

Look back and refactor
    Balance between efficiency and readability

    Refactoring questions: 
    - Can you check the result? (does the code work?)
    - Can you derive the result differently? (Is there another viable way now)
    - Can you see it at a glance? (Does it make sense/ is it intuitive)
    - Can you use the result or method to solve another problem? (can the solution unlock a solution to another problem you've experienced? maybe less so in an interview but yeah.)
    - Can you improve the performance of your solution? (time and space complexity)
    - Can you think of any other ways to refactor your code? (spacing, organizational standards, ackknowledge that your code may not be neat and you'd like to make it better)
    - After completing a working solution, even if not refactored, you can pick the interviewers brain to ask how other people have solved it. 

Another solution

    function charCount(str) {
        let charsPresent = {};

        for (let char of str) {
            char = char.toLowerCase();
            if (/[a-z0-9]/.test(char))
                (if (!charsPresent) {
                    charsPresent[char] = 1
                } else charsPresent[char]++)
        }
        return charsPresent;
    }

    // notes on above: 
        For-of loop used can be better than a for-loop, because you don't have to work with i and use it to access different parts of the input.
        Regex used to evaluate conditions.

    even better: 

    function charCount(str) {
        let charsPresent = {};
        for (let char of str) {
            char = char.toLowerCase();
            if (/[a-z0-9]/.test(char)) {
                charsPresent[char] = ++charsPresent[char] || 1
        }
        return charsPresent;
    }

    SECRET! .charCodeAt(). Much faster than regex expressions. 

    function isAlphaNumeric(str) {
        let code;

        for (let i = 0; len = str.length; i < len; i++) {
            code = str.charCodeAt(i);
            if (!(code > 47 && code < 58) &&   // numeric (0-9)
                !(code > 64 && code < 91) &&   // upper alpha (A-Z)
                !(code > 96 && code < 123)) {  // lower alpha (a-z)
              return false;
            }
        }
        return true;
    }

    isAlphaNumeric("smOSDAo234908")

->In an interview, you could say "I have a feeling regex expressions can be a bit slow, so I could have used a for loop to evaluate the character codes to determine if the input string is alphanumeric."


^^THIS IS THE BULK OF HOW TO GET A JOB^^
/////////////////////////////////////////////////////////////////////////








How can I improve?
1. Devise a plan for solving problems (checked off since covered above but always review)
2. Common problem solving patterns

PROBLEM SOLVING PATTERNS
- Frequency counter
- Multiple Pointers
- Sliding Window 
- Divide and Conquer
- Dynamic Programming
- Greedy Algorithms
- Backtracking
- Many more out there

:Frequency Counter ---------------------------------------------------------------------------
    This pattern uses objects or sets to collect values/frequencies of values and is O(n) time
    This can often avoid the need for nested loops or O(n^2) operations with arrays/strings

Naive approach O(n^2) because indexOf is basically a loop, which is occuring inside the for-loop:

function same(arr1, arr2) {
    if (arr1.length !== arr2.length) return false;
    
    for (let i = 0; i < arr1.length; i++) {
        let correctIndex = arr2.indexOf(arr1[i] ** 2)
        if (correctIndex === -1) {
            return false;
        }
        arr2.splice(correctIndex, 1)
    }
    return true;
}

same([1,2,3,4,5], [9,16,25,4,1])


Better approach: 

function same(arr1, arr2) {
    if (arr1.length !== arr2.length) return false;

    let frequencyCounter1 = {};
    let frequencyCounter2 = {};
    for (let val of arr1) {
        frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1
    }
    for (let val of arr2) {
        frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1
    }

    for (let key in frequencyCounter1) {
        if (!(key ** 2 in frequencyCounter2)) return false
        if (frequencyCounter2[key ** 2] !== frequencyCounter1[key]) return false;
    }
    return true
}

same([1,2,3,2,5], [9,1,4,4,11])

see google dev tools, sources tab for more "Squares Present" problems. 


:Multiple Pointers ---------------------------------------------------------------------------
(Only works for sorted arrays). Creating pointers or values that correspond to an index or position and move towards the beginning, end or middle based on a certain condition

Very efficient for solving problems with minimal space complexity as well

Write a function that takes a sorted array and returns the first pair that sums to zero. 

Naive solution: O(n^2)
function sumToZero(arr) {
    for (let i = 0; i < arr.length; i++>) {
        for (let j = 0+1; j < arr.length; j++) {
            if (arr[i] + arr[j] === 0) {
                return [arr[i], arr[j]]
            } else return [];
        }
    }
}

Refactored to multiple pointers: (this video clicked well for me)
function sumToZero(arr) {
    let left = 0; 
    left right = arr.length - 1;
    while (left < right) {
        let sum = arr[left] + arr[right];
        if (sum === 0) {
            return [arr[left], arr[right]]
        } else if (sum > 0) {
            right --;
        } else left ++
    }
}

<!-- function countUniqueValues(arr) {
    let i = 0;
    let j = i + 1;
    if (arr[i] === arr[j]) {
        j++;
    } else {
        i++;
        arr[i] = arr[j]
        j++;
    }
    return i + 1;
} -->

function countUniqueValues(arr) {
    if (arr.length === 0) return 0;
    let i = 0;
    for (let j = 1; j < arr.length; j++) {
        if (arr[i] !== arr[j]) {
            i++;
            arr[i] = arr[j]
        }
    }
    return i + 1;
}

countUniqueValues([1,2,3,4,4,4,7,7,12,12,13])



:Sliding Window ---------------------------------------------------------------------------
Useful with dataset like array or string, and we need a subset of that data which is continuous. 
i.e. longest substring of uinique characters. Or, find the max sum of two adjacent digits. 

This pattern involves creating a window which can be either an array or a number from one position to another. Depending on a certain condition, the window either increases or closes (and a new window is created). Very useful for keeping track of a subset of data in an array/string etc. 


example: Write a function maxSubarraySum, which accepts an array of integers and a number called n. The function should calcualte the maximum sum of n consecutive elements in the array.

o(n^2) naive
    function maxSubarraySum(arr, num) {
        // edge case for n being larger than the array
        if (num > arr.length) return null;
        
        let max = -Infinity // so that we start at the absolute beginning if the input data has negative numbers.
        for (let i = 0; i < arr.length - (num + 1); i++) {
            console.log("OUTER i:", i) 

            let temp = 0; 
            // below is the moving window part
            for (let j = 0; j < num; j++) {
                console.log("i:", i)
                console.log("J:", j)
                temp += arr[i + j]
                console.log("temp:", temp)
            }

            if (temp > max) {
                max = temp;
            }
            return max;
        }
    }
    
    maxSubarraySum([2,6,9,2,1,8,5,6,3],3)




:Divide and Conquer ---------------------------------------------------------------------------
log(n) time
function search(array, val) {

    let min = 0; 
    let max = array.length -1
    
    while (min <= max) {
        let middle = Math.floor((min + max) / 2);
        let currentElement = array[middle];
    
        if (array[middle] < val) {
            min = middle + 1;
        } else if (array[middle] > val) {
            max = middle - 1;
        } else {
            return middle;
            }
    }
    return -1;
}





********************************************************************
SEARCHING ALGORITHMS

--> Linear Search, usually o(n). One for-loop. 

-Iterates over an array from start to finish

ex. 

function linearSearch(array, value) {
    for (let i = 0; i < array.length; i++) {
        if (array[i] === value) {
            return i
        } else {
            return -1
        }
    }
}



--> Binary Search (can be much faster than linear search)


-Eliminates half of the array at a time but array MUST BE SORTED. Divide and conquer. 

ex. 

function binarySearch(array, value) {
    let left = 0
    let right = array.length - 1
    let middle = Math.floor((array.length - 1) / 2)

    while (arr[middle] !== value) {

        if (array[middle] === value) return middle
        
        if (value < array[middle]) {
            right = middle - 1
            middle = Math.floor(right / 2)
        } else {
            left = middle
            middle = Math.floor(left * 2)
        }
    } 
}

binarySearch([1,3,4,5,6,7,11,14,16,18,20,24,25,27,28,30,32,34,35,36,40,50,60,70,90,99], 11)