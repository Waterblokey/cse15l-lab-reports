# Lab Report 1
Ryan Livengood
Joe Politz
10/17/2023
CSE 15L

## Part 1 - Implementing StringServer
<img width="288" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/a3ad778e-989d-48ef-93aa-c5a796af546d">
<br />
* In this example, the handleRequest method and the main method are called. 
* Main has a String parameter called args which is meant to take the port number, while handleRequest has a URI parameter called url which takes the URL up to the beginning of the path. In the screenshot provided, the value of main's parameter is 7127, since that is the port number, while the value of handleRequest's parameter is localhost:. There are also relevant values, including str, count, and strCount. str and strCount are initialized as "", while count is initialized to 0.
* From this specific request, /add-message?s=Hello, str, count, strCount and url are changed. str is changed from "" to "Hello", count is changed from 0 to 1, strCount is changed from "" to "1", and url is changed to localhost:7127/add-message?s=Hello.
<br />
<br />


<img width="359" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/21d40cc2-72dc-45fb-8054-89d799418ada">
<br />
* In This example, the handleRequest and main method are called again. 
* Once again, the relevant arguments are args and url, while the relevant values are str, count and strCount. args remains 7127.
* url changes from localhost:7127/add-message?s=Hello to localhost:7127/add-message?s=How are you?. str changes from \nHello to \nHello\nHow are you?. count changes from 1 to 2, and strCount changes from "1" to "2"

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String str = "";
    int count = 0;
    String strCount = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format(str);
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    count += 1;
                    strCount = Integer.toString(count);
                    str += strCount + ". " + parameters[1] + "\n";;pppppppppppp
                    return String.format(str);
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
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
