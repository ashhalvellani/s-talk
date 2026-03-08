
# s-talk

**s-talk** is a simple terminal-based chat application written in **C** that allows two users on different machines to communicate in real time.

The program uses **UDP sockets for network communication** and **POSIX threads (pthreads)** to handle concurrent tasks such as user input, message transmission, message reception, and screen output.

The goal of the project is to demonstrate **network programming, concurrency, and inter-process communication** in a lightweight messaging tool.

----------

# Features

-   Real-time text communication between two terminals
    
-   UDP-based networking for message transmission
    
-   Multithreaded architecture using **pthreads**
    
-   Concurrent handling of:
    
    -   keyboard input
        
    -   sending messages
        
    -   receiving messages
        
    -   displaying output
        
-   Graceful termination of chat sessions
    

----------

# How It Works

Each running instance of `s-talk` connects to another instance running on a remote machine.

When a user types a message:

1.  The message is captured from the keyboard.
    
2.  It is placed into a shared message queue.
    
3.  A sending thread transmits the message over UDP.
    
4.  The receiving instance reads the message from the network.
    
5.  The message is placed into another queue and displayed on the terminal.
    

Multiple threads coordinate through **shared data structures and synchronization mechanisms** to ensure safe communication between components.

----------

# Building the Project

Compile using the Makefile:

`make`

This will produce the executable:

`s-talk`

To remove compiled files:

`make clean`

----------

# Usage

After compiling, run the program with:

``s-talk [local_port] [remote_hostname] [remote_port]``

Example:

``s-talk 6060 remote-machine 6001``

Two users must start the program with opposite port configurations to establish communication.

Typing a message and pressing **Enter** sends it to the other user.

Entering a line containing only:

``!``

terminates the session.

----------

# Project Structure
```plaintext
s-talk  
├── main.c        # Program entry point and thread initialization  
├── list.c        # Linked list implementation used for message queues  
├── list.h        # List interface definitions  
├── Makefile      # Build configuration  
└── README.md
```

----------

# Technologies Used

-   **C**
    
-   **POSIX Threads (pthreads)**
    
-   **UDP sockets**
    
-   **Linux system calls**
