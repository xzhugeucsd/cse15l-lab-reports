**Week 3 Lab Report**

*Part 1*

Below is the code of SearchEngine:
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
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Add1.png)
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Add2.png)
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Search.png)

The three screenshots are added and searched with the handleRequest method, while they use different if statements. The different operations are performed by the query category inside the separate url. The search will return to create a new array list by contain to check the previous array list. So the result of the search will contain only specific content.

*Part 2*

**Array Method**:

    The failure-inducing input (the code of the test):
    
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Array%20Test.png)

    The symptom (the failing test output): When the above test is run, the output of the reversed function is: [0,0,0].
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Array%20Faild%20Test.png)

    The bug: The program is reassigning the values in the input array based on values from the returned array, that is uninitialized.
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/Array%20Fixed%20Code.png)


**List Method**:

    The failure-inducing input (the code of the test):
  
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/List%20Test.png)

    The symptom (the failing test output): Items saved in the reverse order.
  
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/List%20Failed%20Test.png)

    The bug: It filters and adds items in reverse order rather than the original list order.
  
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/lab3/List%20Fixed%20Test.png)

