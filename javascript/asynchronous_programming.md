# Asynchronous Programming


### The Concept
The time it takes for a program to execute, for it to go through all of its steps, is dependent on the speed of the processor. However, there are times when a program may interact with things external to the processors domain, such as communicating with something over a network. Such an action takes time, time that would be wasted if the processor waited for a response. 

In an async model, you can start an action and the processor can move on to another action, and then when the first action finished, the program is informed and can get access to the result. 