# Application State Synchronization

Application State Synchronization means, syncing the application state to a redundant machine running redundant backup instance of the application.

Application state means the **snapshot** of all data structure kept in the memory. Data structures include:
* heap memory
* global variables

It is desirable for Applications which needs to up and running 24/7 to have backup instance running on alternate machine. In case the primary machine fails for any reason, backup instance should take over and continue to provide application service. For example, Network equipments such as Router disrupt many network users when they go down. It is desirable to have a backup Router which takes over the primary Router **instantly** when primary router goes down. Backup equipment must resume from the **same state** where primary equipment failed.

![picture](data/sync.png)

All this Synchronization mechanisms are based on data (de)serialization. So, the receiver side should be able to reconstruct the clone of data structures. We can use this concept or technique to implement **Data Redundancy** or **High Availability**. 

There should be a mechanism to inform the redundant node that primary node has failed. One way to implement this mechanism is using **Keep Alive** messages. The primary machine periodically sends Keep Alive messages to inform the redundant machine that the primary machine is still operational, and once the redundant machine does not receive any Keep Alive message for specific amount of time, it will be operational.
