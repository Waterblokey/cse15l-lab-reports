## Part 1 – Debugging Scenario



`Student: Help! my code is running like this. I double checked my code and I do not understand why the indices are off. I am incrementing all the correct indices at the right times. What might be wrong?`

<img width="448" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/c0f92f5a-d2b2-41c8-91e3-7ca3b033e7dd">

<img width="563" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/b917b705-9df4-4120-8c53-37376ff9ae22">

`ListExamples.java`

```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() || index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index2 += 1;
    }
    return result;
  }


}
```

`ListExamplesTests.java`

```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
	@Test(timeout = 500)
	public void testMerge1() {
    		List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
		assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
	}
	
	@Test(timeout = 500)
        public void testMerge2() {
		List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
		assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
        }

}
```

`test.sh`

```
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests
```

`TA: Have you checked all of the index variables, and the conditions that decide whether you should increment or not?`

`Student: Thank you! It turns out I was using || when I should have been using && in my conditional, causing my program to over index.`

`Here is the bugged code, where i use || in the conditional for merge`

<img width="423" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/8a6a5dfc-970e-4884-a32d-f1b847232e31">

`Here is the fixed code, using && instead`

<img width="378" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/50594c08-cfb8-4abd-81ea-ba40e865f246">

`And the result of the tests with the debugged code`

<img width="349" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/7007e4df-3ee5-4a83-8748-368a7c432d8d">


Part 2 – Reflection

`One cool and useful thing I learned in the second half of the quarter is how to use an ssh key to easily commit changes to GitHub. By doing this, I don't have to sign into github everytime I want to push a change, which is super useful`
