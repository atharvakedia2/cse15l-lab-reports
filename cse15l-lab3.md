
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
##Symptom
# Input:{1,2,3,4}

![Image](ss5.png)

# Input:{3}

![Image](ss5.png)

![Image](ss7.png)
# Part 3
In labs two and three, I really got the hang of linking up to remote servers through the command line on my laptop. This is a skill I can see coming in super handy during internships, especially when I need to dial into a company's servers from a distance. I also got a good grip on how to get servers up and running online, and what goes on behind the scenes when we shoot requests across the web. Plus, I picked up a few handy terminal commands, like mkdir and scp, which I'm sure will be useful down the line.
