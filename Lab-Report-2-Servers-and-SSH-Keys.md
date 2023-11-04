# Lab Report 2
Ryan Livengood
Joe Politz
10/17/2023
CSE 15L


## Part 1 - Implementing StringServer
<img width="288" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/a3ad778e-989d-48ef-93aa-c5a796af546d">
<br />
- In this example, the `handleRequest` method and the `main` method are called.
<br />
- `main` has a `String` parameter called `args` which is meant to take the port number, while `handleRequest` has a `URI` parameter called `url` which takes the URL up to the beginning of the path. In the screenshot provided, the value of `main`'s parameter is 7127, since that is the port number, while the value of `handleRequest`'s parameter is localhost:. There are also relevant values, including `str`, `count`, and `strCount`. `str` and `strCount` are initialized as "", while `count` is initialized to 0.
<br />
- From this specific request, /add-message?s=Hello, `str`, `count`, `strCount` and `url` are changed. `str` is changed from "" to "Hello", `count` is changed from 0 to 1, `strCount` is changed from "" to "1", and `url` is changed to localhost:7127/add-message?s=Hello.
<br />
<br />


<img width="359" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/21d40cc2-72dc-45fb-8054-89d799418ada">
<br />
- In this example, the `handleRequest` and `main` method are called again. 
<br />
- Once again, the relevant arguments are `args` and `url`, while the relevant values are `str`, `count` and `strCount`. `args` remains 7127.
<br />
- `url` changes from localhost:7127/add-message?s=Hello to localhost:7127/add-message?s=How are you?. `str` changes from "Hello" to "Hello\nHow are you?". `count` changes from 1 to 2, and `strCount` changes from "1" to "2"
<br />

**Code for StringServer.java**
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
                    str += strCount + ". " + parameters[1] + "\n";
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

## Part 2 
<br />

Logging into ieng6 without being asked for password
<br />
<img width="361" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/95decbd1-f878-47b6-9f03-2f25c7e5a584">
<img width="220" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/cd736c27-1d73-4c61-b89c-76cf66159284">

<br />
Path to private key for SSH key
<br />

<img width="211" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/53c5056c-2458-414d-86ca-4ac6b3eaa01b">

Path to public key for SSH key

<img width="179" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/9603c404-3ba3-4b69-9496-db47d7f5f3c2">


## Part 3
One thing I learned from week 2 was how to remotely connect to a server. To do this from the terminal, you must use the ssh command, then enter the account you would like to connect to. It will then prompt you for your password, after which it will tell you when previous users were on this server.


