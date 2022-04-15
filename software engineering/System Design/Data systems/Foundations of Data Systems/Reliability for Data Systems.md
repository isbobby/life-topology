# Reliability
The system should continue to work correctly (performing the correct function at the desired level of performance) even in the face of adversity. An *adversity* can be a hardware fault, software fault or human errors.

### Faults and Failures
A *fault* is usually defined as one component of the system deviating from its spec, whereas a *failure* is when the system as a whole stop providing the required service to the user.

It is impossible to reduce the probability of fault to zero, therefore it is usually best to design fault-tolerance mechanisms that prevent faults from causing failures.

Although we generally prefer tolerating fault than preventing fault, there are cases where prevention is better than cure (because no good cure exists). 

### Hardware Faults
In recent years (2022), data volumes and application's computing demand have increased and many applications have begun using larger number of machines. This proportionally increases the rate of hardware faults.

Hence, there is a move towards systems that can tolerate the loss of entire machines, by using software fault-tolerance techniques in preference or in addition to hardware redundancy. These systems also allow rolling updates without needing to shut down the whole system.

Tools such as [[Datadog]] provide system check, where users can get metrics from the base system about the CPU, IO, load, memory, swap, and up-time.

### Software Errors
Another class of errors are systematic errors within the system, such faults are harder to anticipate and can cause many more system failures than uncorrelated hardware faults.

Some of the examples are **leap seconds**, **runaway process** uses up shared resources, **dependent service** becomes unresponsive, and **cascading failures**.

The bugs that causes these software faults often lie dormant for a long time until they are triggered by an unusual set of circumstances. In those circumstances, it is revealed that the software is making some kind of *assumption about the environment* - this assumption eventually becomes false for some reason.

### Human Errors
Humans - operators and engineers, are the least reliable part of the system. The best system combine several approaches 

1. Design systems in a way that minimizes opportunities for error, for example, by imposing a set of strict interfaces

2. Decouple the places where people make mistakes from the places where they can cause failures - provide fully featured non-production sandbox environment where people can explore and experiment safely.

3. Test through out all levels

4. Have quick and easy recovery from human errors, to minimize the impact in the case of a failure.

5. Set up detailed and clear monitoring, such as *performance metrics* and *error rates*,  monitoring can show us early warning signals and allow us to check whether any assumptions or constraints are being violated. (Improve [[Software Observability]]) 