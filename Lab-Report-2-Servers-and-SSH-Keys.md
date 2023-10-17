# Lab Report 1
Ryan Livengood
Joe Politz
10/17/2023
CSE 15L

## Part 1 - Implementing StringServer
<img width="288" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/a3ad778e-989d-48ef-93aa-c5a796af546d">
In this example, the handleRequest method and the main method are called. Main has a String parameter called args which is meant to take the port number, while handleRequest has a URI parameter called url which takes the URL up to the beginning of the path. In the screenshot provided, the value of main's parameter is 7127, since that is the port number, while the value of handleRequest's parameter is localhost:. From this specific request, /add-message?s=Hello, str, count, strCount and url are changed.
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
