
# **Lab Report 2**

## 1. Bugs

### averageWithoutLowest(doube[] arr)
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
}
```
#### **Failure Inducing**
Input: {5, 5, 5}
```
@Test
public void testAverageWithoutLowest(){
    double[] input2 = {5, 5, 5};
    assertEquals("Testing same number", 5, ArrayExamples.averageWithoutLowest(input2), 0.001);
}
```
Expect: 5, Output: 0


#### **Non-Failure Inducing**
Input: {1, 2, 3}
```
@Test
public void testAverageWithoutLowest(){
    double[] input1 = {1, 2, 3};
    assertEquals(3, ArrayExamples.averageWithoutLowest(input1), 0.001);
}
```
Expect: 2.5, Output: 2.5

#### **Symptom**
![Image](JUnit1.png)
> The test with input {1, 2, 3} passes and is the first "." in the terminal output
> 
> The test with input {5, 5, 5} is the failure, resulting in the "E" and the rest of the terminal output

#### **Fixing the Bug**

Bug: Does not check for a null array input

Bug: Input being of all same number
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```
Fix
```
static double averageWithoutLowest(double[] arr) {
    if(arr == null || arr.length < 2) { return 0.0; }
    
    boolean same = true;
    double firstElement = arr[0]; // Get the first element
    
    for (double num : arr) {
        if (num != firstElement) {
            same = false; // Found an element different from the first one
        }
    }
    
    if(same)return arr[0];

    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
}
```
## Researching Commands: find

### 
