**Week 3 Lab Report**

*Part 1*

**Below is the code of SearchEngine:**
``` 
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.

    ArrayList<String> list = new ArrayList<>();
    public String handleRequest(URI url) {
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                list.add(parameters[1]);
                return parameters[1] + " is added";
                }
        }
        else if(url.getPath().contains("/search")) {
            ArrayList<String> SearchList = new ArrayList<>();
            String[] parameter= url.getQuery().split("=");
            if (parameter[0].equals("s")) {
                for(String element:list){
                    element.contains(parameter[1]);
                    SearchList.add(element);
                }
                return SearchList.toString();
            }
        }
        return "404 Not Found!";

    }
}


class SearchEngine {
    public static void main(String[] args) throws IOException {

        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
![Image](/lab3/Add1.png)

Method called: handleRequest

Values of the relevant arguments:localhost:4000/add?s=pineapple

Values of relevant fields of the class: ArrayList is added [pineapple]

When handleRequest is called, pineapple is added to the arraylist.

![Image](/lab3/Add2.png)

Method called: handleRequest

Values of the relevant arguments:localhost:4000/add?s=apple

Values of relevant fields of the class: ArrayList is added [apple]

When handleRequest is called, apple is added to the arraylist.

![Image](/lab3/Search.png)

Method called: handleRequest

Values of the relevant arguments:localhost:4000/search?s=app

Values of relevant fields of the class: ArrayList items = [pineapple,apple]

*Part 2*

**Array Method**:

The failure-inducing input (the code of the test):
    
![Image](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Array%20Test.png)

The symptom (the failing test output): When the above test is run, the output of the reversed function is: [0,0,0].

![Image](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Array%20Faild%20Test.png)

The bug: The program is reassigning the values in the input array based on values from the returned array, that is uninitialized.

![Image](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Array%20Fixed%20Code.png)

The connection between the symptom and the bug is the output is printing an uninitialized array not the expected result.

**List Method**:

The failure-inducing input (the code of the test):
  
![Image](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/List%20Test.png)

The symptom (the failing test output): Items saved in the reverse order.
  
![Image](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/List%20Failed%20Test.png)

The bug: It filters and adds items in reverse order rather than the original list order.
  
![Image](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/List%20Fixed%20Test.png)

The connection between the symptom and the bug is the original code adds elements to the front, the order of elements in the actual result does not match with the order in the expected result.
