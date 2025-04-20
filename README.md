# Endpoint-Messaging-System / SDI-3203-Term-Project

## Client-Server Chat System with Party Chat

## Overview

This project implements a multi-featured, client-server chat application using Python's standard libraries. It runs on local networks, allowing multiple clients to connect to a central server, register with unique usernames, and engage in real-time public chat, private whispers (with reply functionality), and temporary group chats (parties). The server pushes messages directly to recipients, ensuring immediate communication.

---

## 📦 Project Structure

    chat_project/
    ├── client.py        # Client application script
    ├── server.py        # Server application script
    └── README.md        # This file

---

## 🚀 Getting Started

### Prerequisites

- Python 3.6+

### Dependencies

- Uses only standard Python libraries:
  - `socket`
  - `threading`
  - `logging`
  - `argparse`
  - `time`
  - `sys`

### Setup

1.  Clone this repository or download the source code (`client.py`, `server.py`).
2.  Open a terminal or command prompt.
3.  Navigate to the directory containing the downloaded files.

### Running the Server

Open a terminal and run:

    python server.py [--host <ip_address>] [--port <port_number>]

-   `--host`: The IP address the server should listen on. Defaults to `0.0.0.0` (listens on all available interfaces). Use your machine's specific LAN IP if you want clients on other machines to connect.
-   `--port`: The port number the server should use. Defaults to `5555`.

*Example (Defaults):*

    python server.py

*Example (Specific IP/Port):*

    python server.py --host 192.168.1.100 --port 6789

### Running a Client

Open a *new* terminal for each client instance and run:

    python client.py [--host <server_ip_address>] [--port <server_port_number>]

-   `--host`: The IP address of the running server. Defaults to `127.0.0.1` (localhost). **Use the server's actual IP address if connecting from a different machine.**
-   `--port`: The port number the server is running on. Defaults to `5555`.

*Example (Connecting to localhost default):*

    python client.py

*Example (Connecting to specific server IP/Port):*

    python client.py --host 192.168.1.100 --port 6789

---

## 💡 Usage & Features

### Core Functionality

-   **Client-Server Model:** Central server manages connections and message routing via TCP/IP.
-   **Multi-Client Support:** Handles multiple simultaneous client connections using Python's `threading`.
-   **Real-time Communication:** Server pushes messages instantly to relevant clients.
-   **User Registration:** Clients are prompted for a username upon connection.
-   **Unique Usernames:** Usernames must be unique, ignoring case (e.g., "Alice" and "alice" cannot both be online). Registration fails if the name is taken.

### Chat Commands & Features

-   **Public Chat:** Simply type a message and press Enter to send it to all connected users. Your message will appear prefixed with your username (e.g., `<YourUsername> Hello!`).

-   **Private Whispers:** Send a message only to a specific user. User matching is case-insensitive.
    ` /w <username> <message> `
    *Example:* `/w Bob yo bob run me yo lunch money boy!`

-   **Reply to Whisper:** Quickly reply to the last person you whispered with (sent or received).
    ` /r <message> `
    *Example:* `/r noooo please my mommy said i need to eat and hit my protein goals!`

-   **Party Chat (Group Chat):** Create temporary group chats.
    -   **Invite:** Invite a user to your party. If you're not in one, this creates a new party.
        ` /party invite <username> `
        *Example:* `/party invite Lucifer`
    -   **Accept Invite:** Accept a pending party invitation.
        ` /party accept `
    -   **Decline Invite:** Decline a pending party invitation.
        ` /party decline `
    -   **Party Message:** Send a message only to members of your current party.
        ` /p <message> `
        *Example:* `/p Show us the light Lucifer?`
    -   **Leave Party:** Exit your current party. Notifications are sent, and leadership transfers if needed. The party dissolves if empty.
        ` /party leave `
    -   **Party Info:** See the current leader and members of your party.
        ` /party who `

-   **Utility Commands:**
    -   **List Online Users:** See who is currently connected to the server globally.
        ` /who ` (or ` /list `)
    -   **Help:** Display the list of available commands and their usage.
        ` /help `
    -   **Exit:** Disconnect cleanly from the server.
        ` /exit `

---


## 🧰 To-be Implemented

- [ ] TLS/SSL encryption
- [ ] User Authentication & Persistent Accounts
- [ ] Containerization (Docker)
- [ ] Scalability & Performance Improvements (Asynchronous I/O)
