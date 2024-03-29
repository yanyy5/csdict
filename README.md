# csdict
This is Assignment 1 of Distributed System.


## 1 Problem Context
In this project, a multi-thread dictionary server is implemented in client-server architecture. Multiple clients can be connected to the server concurrently, and they can query, add, remove and update the dictionary. Thread-per-connection architecture is implemented in the multi- thread server side. All the communication are built based on TCP, which is a reliable way to transmit the JSON data. Some errors in both client and server sides are handled properly, such as the lack of input parameters from console, wrong server address and so on. And we also design simple GUI for both client and server.

## 2 System Components
### 2.1 Server
The components of server side can be divided into two parts: server threads and server GUI. When the program runs, a server GUI with input port number and dictionary file path will be displayed. When the “Setup” button is clicked, the loading of dictionary file will be checked first and the server will start to wait the connection from any clients.
Since we use a thread-per-connection architecture, a server thread will be created to handle the requests when a new client is connected to the server successfully.
Finally, when the “Disconnect” button is clicked, all the connections will be closed and the program will exit.
### 2.2 Client
Like the server, there are also two parts in the client side: client connection and the main function of accessing the dictionary, both of which have simple GUI.
First, in the stage of client connection, two parameters (server address and port number) will be loaded from console to the connection GUI. The user can modify their input before they click the “Connect” button. If the client connects the server successfully, the GUI will jump into the main function of accessing the dictionary. If not, some messages will be displayed to remind the user to change their input.
The client can query, add, remove and update the dictionary. And all the modification can be seen from other clients.

## 3 System Design 
### 3.1 Class Design 
#### 3.1.1 Client
There are three classes for client: ClientConnection, ClientGUI and Client. ClientConnection will handle the connection to server, and generate a Client object for ClientGUI. And all the function for dictionary are implement in ClientGUI.

![image](https://github.com/yanyy5/csdict/blob/main/pics/clientuml.png)

#### 3.1.2 Server
There are three server classes and one dictionary class. First the ServerSetup will check the dictionary file (right path and valid format), and wait for client connection. And it will new a ServerThread to handle a connection. All the read and write to the dictionary will be implemented in Dictionary class.

![image](https://github.com/yanyy5/csdict/blob/main/pics/serveruml.png)

### 3.2 User Interface
#### 3.2.1  Client GUI 
Connect to the server:

![image](https://github.com/yanyy5/csdict/blob/main/pics/connect.png)

The main ClientGUI for query, add, remove update word from dictionary:

![image](https://github.com/yanyy5/csdict/blob/main/pics/clientgui.png)

#### 3.2.2 Server GUI
The GUI for Server: click the setup to wait for connection and click the disconnect to close the connection.

![image](https://github.com/yanyy5/csdict/blob/main/pics/servergui.png)

The displayed messages for these two button.

![image](https://github.com/yanyy5/csdict/blob/main/pics/servermsg.png)

#### 3.2.3 JSON file format
We simply design the JSON file format for the dictionary: {word: meaning}

## 4 Run the .jar file
To start the server:
```
java –jar Server.jar <port> <dictionary-file>
```
To start the client:
```
java –jar Client.jar <server-address> <server-port>
```
