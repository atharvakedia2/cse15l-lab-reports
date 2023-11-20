
# Lab Report 3
# Part 1
## Failure inducing input
```
@Test
public void testReverseInPlace() {
    int[] input1 = {1, 2, 3, 4 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{4, 3, 2 , 1}, input1);
}
```
## Non-Failure inducing input
```
@Test
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```
## Symptom
# Input:{1,2,3,4}

![Image](ss11.png)

# Input:{3}

![Image](ss12.png)

## The Bug
In the initial code, the first half of the array's values were replaced, but the second half's values were incorrectly swapped. This issue arose because the values intended for the second half were lost when the first half was altered. To resolve this, a second array was introduced to hold the original array's values. Then, each value in the original array was replaced with the corresponding values from the second array, starting from the last index. This approach ensured the correct values were inserted into the array as intended.

# Original Code
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```

# Fixed Code
```
static void reverseInPlace(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0;i < arr.length;i++) {
    newArray[i] = arr[i];
  }
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
 }
}
```

## Part 2
