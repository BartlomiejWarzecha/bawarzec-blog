+++ 
date = 2020-09-23T19:04:26+02:00
title = "My favourite array questions"
slug = "three-arrays-questions" 
tags = []
categories = []
series = []
+++


## What I want to write about?

I want to write an article to present some questions that I really enjoy solving during my first month of one year coding preparation. In the previous month I worked on Strings Arrays and Big O notation. Presentent problems are on different sorts of level categories. 

## Why do I want to write about it?

I want to write about the most interesting questions that I face off, that make me feel great after solving them. I want to write about it because I want to refresh and share my knowledge. Finding out this kind of question is really something, so I want to dedicate more time to them.

## How do I want to present It?

I Will explain my thought process in the first  rough approach. Then I Will explain a better solution to the problem. I Will write what is the time and space complexity of each problem that I want to present. At the end of each problem I will write why I pick this problem, what in my opinion is making him special and worth solving.

## What are Arrays in Python?
In Arrays we can store multiple informations.
In Arrays we can store different kinds of information. Most commonly it will be different numbers, different types of categories. You can make a matrix, store multiple results.

## How to use Arrays in problem solving?
There are many things that you can do using Arrays:
+ Manipulate
  - change 
  - add 
  - delete 
  - sort
  - swap values
+ Check
  - loop through values
  - compare things in different Arrays 
  - Find minimum and maximum value 
+ Calculate 
  - arthmetic operations
  - median
  - average
  - quartiles etc.


### First: Explanation Problem

This is Basic problem in which I will present how does problems Works


In this problem we need to find number which is missing in order


###### This input for 2 cases:

**How much test cases**
>2

**How much numbers in first case**
>5      

**First case**
>1 2 3 5 

**How much number in second case**
>10     

**Second case**
>1 2 3 4 5 6 7 8 10

In the first test case output will be 4 : 1 2 3 4 5
In the second output will be 9: 1 2 3 4 5 6 7 8 9 10


__You can try to solve this problem__ [here](https://practice.geeksforgeeks.org/problems/missing-number-in-array/0#)

OK let's get to work

First we need to make scheme for our problem

This is Java approach
The main idea is simple I make it in comments
This scheme you can easily copy paste to many problems

``` java
import java.util.Scanner; 
import java.util.Arrays;  

public class MissingNumber {

  public static void main(String[] args) {
    Scanner scan = new Scanner(System.in);
    // Taking scan value from user
    int T = scan.nextInt();
    // Declaring Array for test case
    int[] anArray;
    int end = 0;

    // Looping T times
    for (int i = 0; i < T; i++) {

      // Taking N value of how long list will be
    int N = scan.nextInt();
    anArray = new int[N];

      // Adding values to list
    for (int j = 0; j < N-1; j++) {
    anArray[j] = scan.nextInt();
      }
    }
    scan.close();
  }
}

```

Explanation rough approach

First we need to sort array


```java
      Arrays.sort(anArray, 0, N-1);
```
in case when we got numbers not in the right order

for example

> 2 3 5 1

Then we can make our problem solving loop

__Iterating through every element starting 0__
```java
        for(int k = 0; k < N-1; k += 1)
```
 __This is our excepion result in case: N is 2 numbers AND first number is 2__
```java
        end = k + 2;
```
 __If element in array is not equal k + 1 then we end our example__

```java
        if(anArray[k] != k + 1){
              end = k + 1;
              break;
        }
```
__for example__
> k = 0, anArray[k] == __1__  ==  __k + 1__  __correct__ 

> k = 1, anArray[k] == __3__  !=  __k + 1__ __uncorrect__

> end = __2 <-- missingNumber__

__Full example looks like this__

```java
      Arrays.sort(anArray,0, N-1);

      for(int k = 0; k < N-1; k += 1)
      {
        // Exception case  
        end = k + 2;
        
        // main loop
        if(anArray[k] != k + 1)
        {
              end = k + 1;
              // break the loop if the  statement is True
              break;
        }

        //print result
        System.out.println(end);

      }
 ```



Write time and space complexity of the problem

Time complexity of the problem is O(n)
In the worst case scenario we need to iterate through all numbers

N = 5

1 2 3 4 

Write time and space complexity of the problem

We need to iterate 5 times


Space complexiy is O(N)

Input 4bytes * N + 4 iterator + 4 bytes end_result  = 4N + 4 + 4 == O(N)

If you wanna learn more about Time and space complexity just [google it](https://www.google.com/search?q=time+and+space+complexity&rlz=1C1SQJL_plPL904PL904&oq=time+and+space+comp&aqs=chrome.0.0i19j69i57j0i19l6.7704j0j4&sourceid=chrome&ie=UTF-8)


Why do I think this problem is important?

This problem is great opener for solving Array problems.

+ We learned 
  1. How to take input values
  2. How to find given pattern in Arrays
  3. What is Time and Space Complexity of the Problem


Explanation better approach

### Second Problem : Trapping Rain Water

Explanation Problem

Next problem is medium level problem you can find it [here](https://practice.geeksforgeeks.org/problems/trapping-rain-water/0)

We count how much water is trapped inside columns after rain.

###### This input for 2 cases:

Most important is to find where containers are
Containers have 2 borders and space between them like : 6 4 6, 7 2 2 5, 5 1 8

Trapped water depend on equation: for item in space:(smallest border - space)

For example

6 4 6 = 6 - 4 = 2
7 2 2 5  = (5 - 2) + (5 - 2) = 6
5 1 8 = 5 - 1 = 4


**How much test cases**
>2

**How much numbers in first case**
>6      

**First case**
>5 4 0 7 2 7 

**How much number in second case**
>3     

**Second case**
>6 3 3 

In the first test case output will be 6 + 5 = 11 : We have 2 containers ( 5 4 0 7 = (5 - 4) + (5 - 0) = 6 ) AND (7 2 7 = 7 - 2 = 5)
for T in range(int(input())):
In the second output will be 0 becouse we dont have containers.

Below it there is step by step approach

__Main loop in python is 
much easier than java__
```python
for T in range(int(input())):
  
    n = int(input())
    a = list(map(int,input().split()))
```

First step

Declaring starting borders and water counter
```python
# Left border
    lmax=a[0]
# Right border
    rmax=max(a[1:])
# Variable for counting water spaces
    count=0
```

Second step we are opening for loop to iterate through all values in Array
```python
    for i in range(n):
```

Third step
Inside loop we are looking for for borders

left border:

If current position is higher than previous left border, we are changing our left border to this
```python
        if(a[i]>lmax):
            lmax=a[i]
```
right border:

If current border is our rmax we are looking for next rmax in remaining space
```python
        if(a[i]==rmax and i<n-1):
            rmax=max(a[i+1:])
```
Fourth step

Now we are looking for lowest border, then we are counting lower_border - current position. If current position is higher than lowest border then we are adding 0 to counter, to prevent adding negative valuse

At the end we are printing our result

```python
        h=min(lmax,rmax)
        count+=max(h-a[i],0)
      print(count) 
```

Here is full code  in python

```python
for T in range(int(input())):
  

    n = int(input())
    a = list(map(int,input().split()))

# Left border
    lmax=a[0]
# Right border
    rmax=max(a[1:])
# Variable for counting water spaces
    count=0

    for i in range(n):
      # We are iterating and checking if current item is new left border
        if(a[i]>lmax):
            lmax=a[i]
      # We are looking for highest right border in remaining space
        if(a[i]==rmax and i<n-1):
            rmax=max(a[i+1:])

      # We are checking which border is lower(lower border is making limit for our container)
        h=min(lmax,rmax)
      # We are adding to counter difference between lower border and current column.
      # if current column is higher than h(lower border), 0 will be added.
        count+=max(h-a[i],0)
    print(count)    
```

Write time and space complexity of the problem

Time complexity = O(N)
Space complexity = O(N)

Explanation better approach

Write time and space complexity of the problem
Why do I think this problem is important

We are using max/min function in this program, you can check more of there in python documentation [here](https://docs.python.org/3/library/functions.html).

I think this problem is important becosue it pushes you to think abstract.

### Third Problem : Merge two sorted arrays

This problem you can find [here](https://practice.geeksforgeeks.org/problems/merge-two-sorted-arrays-1587115620/1)

Explanation Problem

Explanation rough approach

Write time and space complexity of the problem

Explanation better approach

Write time and space complexity of the problem

Why do I think this problem is important


void merge(int arr1[], int arr2[], int n, int m)
{
int x=n-1, y = 0;
while(x>=0 && y<m){ if(arr1[x]=""> arr2[y]){
swap(arr1[x] , arr2[y]);
x--;
y++;
}
else{
x--;
}
}
sort(arr1 , arr1+n);
sort(arr2 , arr2+m);
}


Brief Summary
What’s in the next month
