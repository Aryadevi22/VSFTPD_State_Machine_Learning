# VSFTPD_State_Machine_Learning

## VSFTPD Automata Learning Project

This project implements the L Learning Algorithm* to perform black-box state machine inference on the vsftpd (Very Secure FTP Daemon). By treating the FTP server as an unknown DFA/Mealy Machine, the system automatically maps the server's protocol logic, session states, and authentication vulnerabilities.

### Objective

The primary goal is to infer a formal Mealy Machine that represents the control flow of a live FTP server. This is achieved by systematically executing "Membership Queries" (interaction) and "Equivalence Queries" (hypothesis testing) to discover state transitions without access to the server's source code.

### System Architecture
The project is structured as a closed-loop learning system:

Learner: Implements the L* algorithm to maintain the Observation Table and construct Hypotheses.

Oracle (Membership Queries): Acts as the bridge between the Learner and the network. It translates abstract symbols into raw FTP socket commands.

Target (Black Box): A local vsftpd instance running on 127.0.0.1:21.

Equivalence Oracle: Validates the learned model against the real server using randomized sequence testing to find counterexamples.
### Setup

* Install vsftpd
* Configure the server (e.g., enable/disable anonymous login)
* Run the server locally on `127.0.0.1:21`

### Key Components

* **Alphabet**: FTP commands (USER, PASS, LIST, RETR, etc.)
* **Oracle**: Sends commands to vsftpd and collects responses
* **Learner**: Implements the L* algorithm to infer the automaton
* **Evaluation**: Uses metrics like Accuracy, Precision, Recall, and F1-score

### Output

* Learned state machine (Mealy machine)
* Visualization using Graphviz (.dot files)

### Folder Structure
```
/oracle        → Membership queries (interaction with real FTP server)
/learner       → L* algorithm implementation and Mealy machine construction
/evaluation    → Evaluation metrics (F1-score, accuracy)
/ftp           → FTP client code
/configs       → vsftpd configuration files (includes settings and defined alphabet)
/algorithm     → Minimization of inferred automata
```

### 👥 Team Members

Aryadevi P N

A Sireesha Menon

Goury Unnikrishnan

Gayathri Shaji
