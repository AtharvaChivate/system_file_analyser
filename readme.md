# System Information Collector and File Analyzer

## Project Overview

This project is designed to analyze and process `.xyz` files, and to collect and transmit system, process, and network information between a client and server. It includes three main components: the file analyzer, the client, and the server. The analyzer processes specific types of files and generates new files with transformed data. The client collects system information and communicates it to the server, which receives and handles the data.

## Files Description

### `analyser.py`

This script processes files with the `.xyz` extension in the current working directory. It reads each file, extracts metadata from the first line, creates a new file with a specific naming convention, writes the remaining content into the new file, and then deletes the original file.

**Functionality:**
- Lists all files in the current directory.
- For each `.xyz` file, it reads the content, extracts metadata (type and name), and prints them.
- Creates a new filename based on the metadata and the current date.
- Writes the file content to the new file, except for the first line, and deletes the original `.xyz` file.

### `client.py`

This script collects system, process, and network information from the client machine and sends it to the server. It establishes a non-blocking connection to the server and handles the sending and receiving of messages asynchronously.

**Functionality:**
- Collects detailed system information such as platform details, CPU, RAM, and network connections.
- Establishes connections to the server and sends system information in predefined message formats.
- Handles sending and receiving messages asynchronously using the `selectors` module.

### `server.py`

This script acts as the server counterpart to `client.py`. It listens for incoming connections and handles the data received from clients, including system, process, and network information. It also sends responses back to the client.

**Functionality:**
- Collects system, process, and network information similar to the client.
- Listens for incoming connections and handles them using the `selectors` module.
- Processes incoming data from clients, prints the size of received data, and sends responses.

## Example Usage

### Running the Analyzer
To run the analyzer, simply execute `analyser.py` in the directory containing your `.xyz` files:
```bash
python analyser.py

### Running the Client and Server
First, start the server on your desired host and port:

python server.py <host> <port>

Then, start the client and connect it to the server:

python client.py <host> <port>

### Replace <host> and <port> with your servers IP address and port number.

