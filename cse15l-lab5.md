# Lab report 5: Putting it all together

## Part 1

### Step 1: Edstem Post by Student
In `lab7` I ran the tests by running `test.sh`, but one of my tests failed. It was the second test `testMerge2()`. Here is a screenshot of the symptom. I have isolated the error to the 
second method in `ListExamples.java`, and I believe that it is in the last while loop but I am not sure which part it is in and am afraid of messing up the code, and being unable to 
change it. I thought that I would ask for some guidance and help with this.

![image](https://github.com/adutt1010/cse15l-lab-reports/assets/146874656/dc8e8d82-72c3-4a7b-8de1-1b9220ef9dbf)

### Step 2: Response
You are in the right direction, and were able to narrow down the error. In the second while loop, it adds the elements of `list1` onto the list `result`. The third while loop has similar
functionality. If you can find out the use of the third while loop you should be able to find the error in the code. 

Don't be afraid to remove parts of the code, you can always use `Command+z`(Mac user) or `Ctrl+Z`(Windows) to undo and `Command+y`(Mac user) or `Ctrl+y`(Windows user) to redo. 
If you run into an issue where you are unable to undo or redo you can come to 
office hours where we can help you acquire the original code and guide you in the right dircetion. Trial and error is a huge asset and can be used to solve most problems in 
programming.

### Step 3: Implementing TA's guidance
I found the error and fixed the bug by changing `index1` to `index2` in the third while loop in `ListExamples.java`.
![image](https://github.com/adutt1010/cse15l-lab-reports/assets/146874656/c74185eb-1a77-4eb3-86ed-43100dc7c4d8)


### Step 4: Information
- Directory Structure

lab7

lab7 -- ListExamples.java

lab7 -- ListExamplesTest.java

lab7 --  test.sh

lab7 -- lib

lab7 -- lib -- hamcrest-core-1.3.jar

lab7 -- lib -- junit-4.13.2.jar

- `ListExamples.java`
  
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
    while(index1 < list1.size() && index2 < list2.size()) {
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
    while(index1 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index2 += 1;
    }
    return result;
  }


}
```


- `ListExamplesTests.java`
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


- `test.sh`
```
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests
```


- The commands I entered in the command line was `bash test.sh`

- To fix the bug I edited the code in `ListExamples.java`, by changing `index1` to `index2` in the last while loop.

 
## Reflection
The second half of the quarter was very interesting. I learned a lot from the labs. Some things that I believe will help me through my journey in computer science is the jdb debugger.
It can help me isolate bugs and solve issues with programming. Even vim is extremely interesting with editing files on command line. I used to believe that we always needed somehting like VSCode or Eclipse to edit it. This has been an incredible experience and I thoroughly enjoyed my time in CSE 15L.
