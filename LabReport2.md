
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


### Second instance of **/add-message**
