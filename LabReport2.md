
# **Lab Report 1**

## 1. Web Server **ChatServer**

### ChatServer.java code
```
import java.io.IOException;
import java.net.URI;

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

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String history = "";
    String s = "";
    String u = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            if(history.equals("")) return "Chat history is empty!";
            else return history;
        } else if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("&");
            String[] message = parameters[0].split("=");
            String[] user = parameters[1].split("=");
            if (message[0].equals("s")) {
                s = message[1];
                s.replace("+", " ");
            }
            if (user[0].equals("user")) {
                u = user[1];
                u.replace("+", " ");
            }
            history += u + ": " + s + "\n";
            return history;
        }else if(url.getPath().equals("/clear")){
            history = "";
            return "Chat history has been cleared!";
        }else{
            return "404 not found!";
        }
    }
}
```
### First instance of **/add-message**
URL[^1].
![Image](FirstInstance.png)

- Methods Called:

>`main`: The class `chatServer` has no fields that affect this method but it takes in the command line as arguments. It takes in a number to be used as a port number with the following method.
>
>`handleRequest`: This method has three String fields within the class `Handler`; `history`-Stores the chat history, `s`-Temporarily stores the intended message, `u`-Temporarily stores the user sending the message. The method takes in a URL and does something different depending on the path

### Second instance of **/add-message**
>URL: `https://0-0-0-0-4000-no9itgkuo7tmkseqnml4o8866k.us.edusercontent.com/add-message?s=She fell off the first step!&user=Answer`
![Image](SecondInstance.png)


[^1] `https://0-0-0-0-4000-no9itgkuo7tmkseqnml4o8866k.us.edusercontent.com/add-message?s=A girl fell off a 20-foot ladder. She wasn’t hurt. How?&user=Riddle`
