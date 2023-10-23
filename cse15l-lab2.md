# Lab Report 2
# Part 1
## Code
![Image](ss4.png)
## Server
![Image](ss5.png)
![Image](ss6.png)
* The method called is handleRequest in the above images
* The argument of handleRequest is url which is a member of the URI class. The initial value is localhost:2994/, which becomes localhost:2994/add-messages?s=Hello, and finally it becomes localhost:2994/add-message?s=How%27s%20it%20going.

* The relevant fields of the class are:
  - path: This is called by getPath() , and remains unchanged in the screenshots because even though the url is changed, it extracts the same Path as the previous part. Its value is /add- message .
  - query: This is called by getQuery() , and this value is changed in the screenshots. Initally it’s value is s=Hello , and it changes to s=How%27s%20it%20going.
 
 # Part 2
 

