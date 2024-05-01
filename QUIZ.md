### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?
The DevBoard uses interrupt to react to the incoming serial messages, uses on_recieve function to validate the data and the LED control commands and sends back a success or error message to the computer. This is better than the naive approach because it doesn't overload the port and is more responsive. 

### What does `detached_callback` do? What would happen if it wasn't used?
The detached_callback decorator makes the functions run in threads so it doesn't freeze the main user interface. Without the detached_callback decorator, the UI may have been unresponsive upon slow serial operations. 

### What does `LockedSerial` do? Why is it _necessary_?
LocledSerial is the custom type of the serial object that wraps it in a lock. This is necessary because it prevents multiple threads from using the serial port at the same time.  