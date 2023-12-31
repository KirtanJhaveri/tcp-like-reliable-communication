# Reliable Communication

- [Overview](#overview)
- [Getting Started](#getting-started)
  - [Running the Solution](#running-the-solution)
  - [Testing the Solution](#testing-the-solution)
- [Code Structure and Functions](#code-structure-and-functions)
  - [Key Functions](#key-functions)
  - [Sender and Receiver Logic](#sender-and-receiver-logic)
- [Testing and Grading](#testing-and-grading)

## Overview

This repository contains an implementation of reliable communication over an unreliable network, emulating TCP-like behavior. The goal is to establish a protocol ensuring accurate and efficient data transmission between a sender and receiver despite network constraints such as latency, packet loss, and bandwidth limitations.

## Getting Started

### Running the Solution

- **File Structure:**
  - `Solution.py`: Contains the sender and receiver function implementations.
  - `tester.py`: tester.py: Utilizes receiver.py, sender.py, and server.py to simulate an unreliable connection and test the solution
  

- **Implementation:**
  - Modify the `send` and `recv` functions within `Solution.py` to establish a reliable communication protocol.
  - Employ timeouts on socket reads and develop acknowledgment mechanisms for data integrity.

### Testing the Solution

- **Usage:**
  - Utilize `tester.py` to execute exhaustive tests under diverse network conditions (loss rates, latency) and file sizes.
  - Debug effectively by adjusting script parameters and leveraging verbose mode for detailed insights.

## Code Structure and Functions

### Key Functions

- **`get_timeout(SampleRTT, EstRTT, DevRTT)`**
  - Estimates timeout intervals based on Exponentially Weighted Moving Average (EWMA) techniques for Round-Trip Time (RTT) estimation.

- **`extract_header(packet)` / `extract_data(packet)`**
  - Parsing functions to extract header and data from received packets.

- **`make_ACK(seqNum)` / `make_pkt(seqNum, data)`**
  - Creation of acknowledgment packets and data packets with sequence numbers.

- **`delete_acked_pkts(buf, seqNum, base)` / `deliver_data(dest, numBytes, buf, seqNum)`**
  - Management functions to handle acknowledged packets, buffer maintenance, and data delivery.

### Sender and Receiver Logic

- **`send(sock, data)`**
  - Implements the sender's logic, handling packet transmission, acknowledgments, timeouts, and congestion control.

- **`recv(sock, dest)`**
  - Implements the receiver's logic, managing received packets, acknowledgment responses, and writing data to the destination file.

