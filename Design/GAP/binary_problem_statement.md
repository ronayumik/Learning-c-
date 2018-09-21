#

The binary search algorithm allows you to find the position of a specific value in a sorted array of data very quickly. It works by checking the middle of that array. If the middle is smaller than the value we're looking for, then we can be sure that the value we're looking for must be in the larger half of the array. Otherwise it's in the smaller half. We can repeatedly apply that idea, with each repetition cutting away half of the items we're looking through. Below is an implementation of binary search, but something is wrong with it. Find it and fix it by modifying one line!

Input:

The input consists of the sorted array of length 10,000, followed by 10,000 queries. Each integer is given in its own line (there are 20,000 lines in total).

It is guaranteed that there are no duplicates in the array.

Output:

For every query value, output one line of output containing a single integer: the index that matches the query value, or -1 if the value is not in the array.

Select your language below:

## C++
```
#include <stdio.h>
#include <stdlib.h>
int binary_search(int* array, int value, int low, int high) {
    int mid;
    if (high < low) {
        return -1;
    } else {
        mid = (low + high)/2;
        if (array[mid] > value) {
            return binary_search(array, value, low, mid);
        } else if (array[mid] < value) {
            return binary_search(array, value, mid+1, high);
        } else {
            return mid;
        }
    }
}
main() {
    int i, value, answer;
    int array[10000];
    for (i=0; i<10000; i++) {
        scanf("%d", array+i);
    }
    for (i=0; i<10000; i++) {
        scanf("%d", &value);
        answer = binary_search(array, value, 0, 9999);
        printf("%d\n", answer);
    }
}
```

## Java
```
import java.util.*;
public class Main {
    static int binarySearch(int[] array, int value, int low, int high) {
        int mid;
        if (high < low) {
            return -1;
        } else {
            mid = (low + high)/2;
            if (array[mid] > value) {
                return binarySearch(array, value, low, mid);
            } else if (array[mid] < value) {
                return binarySearch(array, value, mid+1, high);
            } else {
                return mid;
            }
        }
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int i, value, answer;
        int[] array = new int[10000];
        for (i=0; i<10000; i++) {
            array[i] = sc.nextInt();
        }
        for (i=0; i<10000; i++) {
            value = sc.nextInt();
            answer = binarySearch(array, value, 0, 9999);
            System.out.printf("%d\n", answer);
        }
    }
}
```

## PHP
```
<?php
    function binary_search($array, $value, $low, $high) {
        if ($high < $low) {
            return -1;
        } else {
            $mid = ($low + $high)/2;
            if ($array[$mid] > $value) {
                return binary_search($array, $value, $low, $mid);
            } else if ($array[$mid] < $value) {
                return binary_search($array, $value, $mid+1, $high);
            } else {
                return $mid;
            }
        }
    }
    $array = array();
    for ($i=0; $i<10000; $i++) {
        fscanf(STDIN, "%d", $array[$i]);
    }
    for ($i=0; $i<10000; $i++) {
        fscanf(STDIN, "%d", $value);
        $answer = binary_search($array, $value, 0, 9999);
        printf("%d\n", $answer);
    }
?>
```

## Python
```
def binary_search(array, value, low, high):
    if high < low:
        return -1
    else:
        mid = (low + high)/2;
        if array[mid] > value:
            return binary_search(array, value, low, mid)
        elif array[mid] < value:
            return binary_search(array, value, mid+1, high)
        else:
            return mid
array = []
for i in xrange(10000):
    array.append(input())
for i in xrange(10000):
    value = input()
    answer = binary_search(array, value, 0, 9999)
    print("%d" % answer)
```

## Ruby
```
require 'scanf'
def binary_search(array, value, low, high)
    if high < low
        return -1
    else
        mid = (low + high)/2
        if array[mid] > value
            return binary_search(array, value, low, mid)
        elsif array[mid] < value
            return binary_search(array, value, mid+1, high)
        else
            return mid
        end
    end
end
arr = Array.new()
10000.times {
    arr << gets.to_i
}
10000.times {
    value = gets.to_i
    answer = binary_search(arr, value, 0, 9999)
    puts answer
}
```

## Javascript

```
function binarySearch(array, value, low, high) {
    if (high < low) {
        return -1;
    } else {
        var mid = Math.floor((low + high)/2);
        if (array[mid] > value) {
            return binarySearch(array, value, low, mid);
        } else if (array[mid] < value) {
            return binarySearch(array, value, mid+1, high);
        } else {
            return mid;
        }
    }
}
var input = document.getElementById('stdin').value.split("\n");
var converted = [];
for(var x in input){
    converted.push(parseInt(split[x]));
}
converted.reverse()
array = [];
for(var i=0; i<10000; i++){
    array.push(converted.pop());
}
for(var i=0; i<10000; i++){
    var value = converted.pop();
    var answer = binarySearch(array, value, 0, 9999);
    console.log(answer);
}
```
