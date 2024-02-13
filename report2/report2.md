# Report 2
## Part 1
**Code for Chat Server**
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String[] messages = new String[100];

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            // Find arguments of user and message
            String[] parameters = url.getQuery().split("&");
            // Obtain string value of user and message
            String message = parameters[0].substring(parameters[0].indexOf("=") + 1);
            String user = parameters[1].substring(parameters[1].indexOf("=") + 1);
            // Concantentating conversation
            String conversation = "";
            
            // Find empty conversation slot
            for(int i = 0; i < messages.length; i++) {
                if(messages[i] == null) {
                    messages[i] = user + ": " + message + "\n";
                    break;
                }
            }
            
            // Concatenate conversation
            for(String lines : messages) {
                if(lines == null) {break;}
                conversation += lines;
            }
            return conversation;
        }
        return "404 Not Found!";
    }
}

class ChatServer {
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
**Add Message 1**
![Image](add_message1.png)
Method | Arguments | Values Updated
| :--- | :--- | :---
Main method | String[] args: Passes port as a string | int port: argument is converted into an int and assigned to port
handleRequest method  | URI url: The url is passed through as a URI object| String[] messages: The handleRequest finds the next empty index in the array and adds the new message with the user and value
