# SecureChatSystem
This is a fully functional secure chat system that offers a command line interface that allows multiple users to talk to multiple other users simultaneously through a chat server

Full trust is placed in this chat hub as it addresses all network security aspects including : managing conversation sessions, negotiating cipher suites, securely exchanging keys between users using Elliptic-curve Diffie–Hellman (ECDH) key exchange algorithm, verifying digital signatures and certificates, keeping track of all authenticated users, encrypting / decrypting messages using symmetric cipher algorithm AES with GCM integrity protection mode. It prevents and detects any security attacks throughout the chat session.


 # Getting started
 These instructions will get you a copy of the project up and running on your local machine for development and testing     purposes.

git clone git@github.com:Misty2018/SecureChatSystem.git

# Prerequisites
Our development environment :

git version 2.7.4 (Apple Git-66)

java version "1.8.0_73"

Java(TM) SE Runtime Environment (build 1.8.0_73-b02)

Java HotSpot(TM) 64-Bit Server VM (build 25.73-b02, mixed mode)

As long as you have git and JDK installed, you are fine.


# Installing
A step by step series of examples that tell you have to get a development env running

Open one terminal, and navigate into the project folder.

cd [PATH/TO/SecureChatSystem]
Make sure all files needed are there, including all java. And .jks files.

ls
Enter “make” in the command line. This command will compile all java files necessary to run the chat hub.

make
In the SAME terminal, type “make server”, this will create a server socket and start the dispatcher thread to infinitely accept client connections.

make server
Open a 2nd terminal, type “make alice” to allow the server connect and authorize the first client whose alias must be "alice".

make alice
Open a 3rd terminal, type “make bob” to allow the server connect and authorize the second client whose alias must be "bob".

make bob
Open a 4th terminal, type “make charles” to allow the server connect and authorize the fourth client with alias "charles".

make charles
Open a 5th terminal, type “make david” to allow the server connect and authorize the second client whose alias must be "david".

make david
Now, any one of the four clients can send messages to any other client or ALL clients including himself / herself.

To send messages to one other client, enter "To alias:message" in the corresponding terminal window.

To [ALIAS]:message
To send messages to all active clients, enter "To all:message". This command will also forward a copy of the message to the sender himself / herself.

To all:message
Any one in the chathub can stop the conversation by enter “exit”. But the other conversations will not terminated until all clients exit.

exit
All logs will be printed out in the server terminal window in real time, including runtime environment, cipher suite negotiation details, ECHD key exchange processes, signature and certiifcate verification and more.

Disclaimer

NakovChatServer class is entry point for the program, it must be the very 1st program to run.

During the conversation, sender MUST follow “To alias:message” or “To all:message” format. Failure of doing this will result in message sending failure. For example, “To bob: Hi, how are you” or “To all: hi, I am Alice” is okay, but “Hi, bob” or “Hi everyone” is wrong.

This program only deals with four clients. In fact, this program can add as many as client when needed. To add a client, a keystore and a self-signed certificate are needed to be established for the new client. Once the client keystore switches certificates with the chathub keystore, this client is ready to be added into the chat hub.

