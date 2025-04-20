# Endpoint-Messaging-System / SDI-3203-Term-Project

## Client-Server Chat System with Party Chat

### Overview

This project implements a multi-featured, client-server chat application using Python's standard libraries. It runs on local networks, allowing multiple clients to connect to a central server, register with unique usernames, and engage in real-time public chat, private whispers (with reply functionality), and temporary group chats (parties). The server pushes messages directly to recipients, ensuring immediate communication.

---

### 📦 Project Structure

chat_project/
├── client.py        # Client application script
├── server.py        # Server application script
└── README.md        # This file


---

### 🚀 Getting Started

#### Prerequisites

* Python 3.6+

#### Dependencies

Uses only standard Python libraries:
* `socket`
* `threading`
* `logging`
* `argparse`
* `time`
* `sys` (for client exit handling)

#### Setup

1.  Clone this repository or download the source code (`client.py`, `server.py`).
2.  Open a terminal or command prompt.
3.  Navigate to the directory containing the downloaded files.

#### Running the Server

Open a terminal and run:

```bash
python server.py [--host <ip_address>] [--port <port_number>]
--host: The IP address the server should listen on. Defaults to 0.0.0.0 (listens on all available interfaces). Use your machine's specific LAN IP if you want clients on other machines to connect.
--port: The port number the server should use. Defaults to 5555.
Example (Defaults):

Bash

python server.py
Example (Specific IP/Port):

Bash

python server.py --host 192.168.1.100 --port 6789
Running a Client
Open a new terminal for each client instance and run:

Bash

python client.py [--host <server_ip_address>] [--port <server_port_number>]
--host: The IP address of the running server. Defaults to 127.0.0.1 (localhost). Use the server's actual IP address if connecting from a different machine.
--port: The port number the server is running on. Defaults to 5555.
Example (Connecting to localhost default):

Bash

python client.py
Example (Connecting to specific server IP/Port):

Bash

python client.py --host 192.168.1.100 --port 6789
💡 Usage & Features
Core Functionality
Client-Server Model: Central server manages connections and message routing.
Multi-Client Support: Handles multiple simultaneous client connections using threading.
Real-time Communication: Messages are pushed instantly (no polling).
User Registration: Clients are prompted for a username upon connection.
Unique Usernames: Usernames must be unique, ignoring case (e.g., "Alice" and "alice" cannot both be online).
Chat Commands & Features
Public Chat: Simply type a message and press Enter to send it to all connected users.
Hello everyone!
Private Whispers: Send a message only to a specific user. User matching is case-insensitive.
Bash

/w <username> <message>
Example: /w Bob Want to team up?
Reply to Whisper: Quickly reply to the last person you whispered with (sent or received).
Bash

/r <message>
Example: /r Sure!
Party Chat (Group Chat): Create temporary group chats.
Invite: Invite a user to your party. If you're not in one, this creates a new party.
Bash

/party invite <username>
Example: /party invite Charlie
Accept/Decline: Respond to a party invitation.
Bash

/party accept
/party decline
Party Message: Send a message only to members of your current party.
Bash

/p <message>
Example: /p Okay team, let's go!
Leave Party: Exit your current party. The party dissolves if you're the last member; leadership passes if you were the leader.
Bash

/party leave
Party Info: See the current leader and members of your party.
Bash

/party who
Utility Commands:
List Online Users: See who is currently connected to the server globally.
Bash

/who
(Alias: /list)
Help: Display the list of available commands.
Bash

/help
Exit: Disconnect cleanly from the server.
Bash

/exit
