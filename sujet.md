# Practical Session #1: Introduction

1. Find in news sources a general public article reporting the discovery of a software bug. Describe the bug. If possible, say whether the bug is local or global and describe the failure that manifested its presence. Explain the repercussions of the bug for clients/consumers and the company or entity behind the faulty program. Speculate whether, in your opinion, testing the right scenario would have helped to discover the fault.

2. Apache Commons projects are known for the quality of their code and development practices. They use dedicated issue tracking systems to discuss and follow the evolution of bugs and new features. The following link https://issues.apache.org/jira/projects/COLLECTIONS/issues/COLLECTIONS-794?filter=doneissues points to the issues considered as solved for the Apache Commons Collections project. Among those issues find one that corresponds to a bug that has been solved. Classify the bug as local or global. Explain the bug and the solution. Did the contributors of the project add new tests to ensure that the bug is detected if it reappears in the future?

3. Netflix is famous, among other things we love, for the popularization of *Chaos Engineering*, a fault-tolerance verification technique. The company has implemented protocols to test their entire system in production by simulating faults such as a server shutdown. During these experiments they evaluate the system's capabilities of delivering content under different conditions. The technique was described in [a paper](https://arxiv.org/ftp/arxiv/papers/1702/1702.05843.pdf) published in 2016. Read the paper and briefly explain what are the concrete experiments they perform, what are the requirements for these experiments, what are the variables they observe and what are the main results they obtained. Is Netflix the only company performing these experiments? Speculate how these experiments could be carried in other organizations in terms of the kind of experiment that could be performed and the system variables to observe during the experiments.

4. [WebAssembly](https://webassembly.org/) has become the fourth official language supported by web browsers. The language was born from a joint effort of the major players in the Web. Its creators presented their design decisions and the formal specification in [a scientific paper](https://people.mpi-sws.org/~rossberg/papers/Haas,%20Rossberg,%20Schuff,%20Titzer,%20Gohman,%20Wagner,%20Zakai,%20Bastien,%20Holman%20-%20Bringing%20the%20Web%20up%20to%20Speed%20with%20WebAssembly.pdf) published in 2018. The goal of the language is to be a low level, safe and portable compilation target for the Web and other embedding environments. The authors say that it is the first industrial strength language designed with formal semantics from the start. This evidences the feasibility of constructive approaches in this area. Read the paper and explain what are the main advantages of having a formal specification for WebAssembly. In your opinion, does this mean that WebAssembly implementations should not be tested? 

5.  Shortly after the appearance of WebAssembly another paper proposed a mechanized specification of the language using Isabelle. The paper can be consulted here: https://www.cl.cam.ac.uk/~caw77/papers/mechanising-and-verifying-the-webassembly-specification.pdf. This mechanized specification complements the first formalization attempt from the paper. According to the author of this second paper, what are the main advantages of the mechanized specification? Did it help improving the original formal specification of the language? What other artifacts were derived from this mechanized specification? How did the author verify the specification? Does this new specification removes the need for testing?

## Answers
1.
Title: 362,000 Tesla cars ‘recalled’ due to serious software bug and multiple crashes: What you need to know
https://gettotext.com/362000-tesla-cars-recalled-due-to-serious-software-bug-and-multiple-crashes-what-you-need-to-know/

Tesla cars are equipped with an autonomous driving AI called FSD for Full Self-Driving. A bug was recently detected in this software system, causing Tesla cars to “disrespect traffic laws in the US. Some instances of the effects of this bug are, Tesla cars don’t avoid obstacles, drive through intersections and ignore the STOP signs, or through cross-road at full speed when the light is fixed orange. The cruise control also misread speed limit signs.

The bug seems to be local since the vehicle is not communicating with any other external devices when these incidents occur. The bugs are possibly due to either the sensors of the car not detecting correctly the obstacles that should be avoided, the traffic signs, and speed limits, or the AI based system that is not taking the appropriate measures for the information that it receives, in very specific contexts.

The repercussions for the customers are the dangers of running into an accident where they can either hurt themselves, or a passerby. For the company Tesla, this bug damaged its brand image, the trust customers have in its cars, and the massive recall and damaged cars that will need to be replaced/returned will be a major financial loss.

In my opinion, being aware of obstacles, road signs, and speed limits, and slowing down or turning in another direction as a way to deal with the formers are already part of the default test cases of the Tesla FSD development team.
Testing the right scenario would have definitely helped discover the fault, but, this bug being due to very specific conditions and contexts make identifying that testing scenario the greatest challenge.




2. [COLLECTIONS-709](https://issues.apache.org/jira/browse/COLLECTIONS-709)

The bug has been discovered in the **getCount()** method of the **MultiSet.Entry** interface.
MultiSet.Entry is an interface in the Apache Commons Collections library for Java that represents an element in a MultiSet. And the Multiset is a collection that supports order-independent equality, like Set, but may have duplicate elements.

**The bug**:

When the last element in a MultiSet is removed using the remove() method, the count of the corresponding MultiSet.Entry should be set to zero. However, due to the bug, the getCount() method is not setting the count to zero even when the last element has been removed.

3. The main advantages of having a formal specification for WebAssembly.
The binary format of the WebAssembly language is highly efficient and can be loaded and executed much faster than equivalent JavaScript code. It's structured control flow ensures that code is well-formed and cannot contain certain types of errors or bugs that are common in other low-level languages. And also the WebAssembly's stack-based architecture and use of an SSA-form intermediate representation enable efficient compilation and execution on a wide range of hardware and operating systems.
A formal specification helps ensure that all implementations of WebAssembly are compatible and can interoperate with each other. This is especially important for a language like WebAssembly, which is designed 
to run in a wide range of environments.
With a formal specification, WebAssembly programs can be compiled once and run on any platform that supports the WebAssembly runtime. 
This makes it easier for developers to write code that can run on different devices and operating systems without having to make significant changes.
It can help optimize the performance of WebAssembly programs by defining the exact semantics of the language. 
This can help compiler developers create more efficient code and make better use of hardware resources.

