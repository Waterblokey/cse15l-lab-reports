# Part 1 - Bugs
ArrayExamples.java `reversed` method
<br />
<br />
Failure Inducing input: {1, 2}
<br />
<br />
non-failure inducing input: {0, 0}
<br />
<br />
Symptom as shown by tests:
<br />
<br />
Buggy Symptoms: 
![image](https://media.discordapp.net/attachments/1145551780747419648/1170243820923920434/image.png?ex=6558557c&is=6545e07c&hm=97058437c8d4f0be8288e92b78cf2d7309df1e0ff7a01b40dc4599e461b4bc5e&=&width=1060&height=598)
non-faliure symptoms:
<br />
<br />
<img width="453" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/5255c6f8-f65a-4ca1-9f26-6100375eae96">

Buggy Code
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
Fixed code:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[arr.length - i - 1] = arr[i];
    }
    return newArray;
  }
```
<br />
Explanation of Fix:
<br />
The 'reversed' method was not working because it set the given `array`'s elements to the elements of a newly initialized array, `newArray`, which has all values equal to 0. This can be fixed by making the values in `newArray` equal `array` array, because this will keep the values in the given array, but reverse them, instead of overwriting them as 0.
# Part 2 - Researching Commands
