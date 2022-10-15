hello
## Search Engine and fix bugs in codes. ##

## Part 1 ##
1. ![image](https://user-images.githubusercontent.com/114331111/195962781-04c2d95d-7de6-4fe1-b653-2f1008039ea7.png)

The codes called are
if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                myStrings.add(parameters[1]);
            }
            return String.format("String added");
}
        
Because the path contains "/add", the if statement url.getPath().contains("/add" is called; in which http://localhost:4050/add?s=coconut 's query is split by the "=" into a string array {"s", "coconut}. Then move onto the next if statement if (parameters[0].equals("s")), since yes, then "coconut" is added into the myStrings List, and prints out "String added"

2. ![image](https://user-images.githubusercontent.com/114331111/195963174-8499eee8-d898-418c-9beb-c86510d7fb32.png)
Because the path of http://localhost:4050/search?s=coco contains "/search", then the codes here run:
else if(url.getPath().contains("/search")){
            String[] parameters2 = url.getQuery().split("=");
            for(String str: myStrings){
                if(str.contains(parameters2[1])){
                    newOne.add(str);
                }
            }
            return String.format("Search Results : " + newOne);
        }
because i refreshed the page a few times, a myStrings contains 6 coconuts. Parameters2 is now {"s", "coco"}. Loops through the Strings mystrings, if it contains the "coco" in parameters[2], then adds it into the new String list. It prints out "Search Results: [coconut, coconut, coconut, coconut, coconut, coconut]" 
3. ![image](https://user-images.githubusercontent.com/114331111/195963433-188be959-8bca-4c70-86b2-ec6426d6d609.png)
Since the path doesn't contain either /add or /search, it prints out "404 No match"
## Part 2
Failure inducing input
![image](https://user-images.githubusercontent.com/114331111/195963695-2ff18788-b6cb-47e4-a1a7-df5a9385c41f.png)

Symptom:
![image](https://user-images.githubusercontent.com/114331111/195963711-0e88c71f-8920-4b33-b6d2-f386bb915ab6.png)

The bug
![image](https://user-images.githubusercontent.com/114331111/195963812-00c4d44d-902a-4e07-92f9-a504473c0cf5.png)

Connection between symptom and bug. Basically the bug reverses everything from the array but the last element, so the last array will be the first element of the new inversed array. So the error says that the code returns {3,2,3} instead of {3,2,1}



In ListExamples.java, the filter method has a bug
if input is List<String> a = [true, false, false, true], it will only returns [true] instead of [true, true]

The problem is that the code keeps on updating the result in index 0 instead of adding the another right result to the new arraylist. 
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }



