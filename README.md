* TOC
{:toc}
## Rust for Python Developers
I come from a low level (C/C++) background but wrote Python/Java/Scala for several years working in Data Engineering/ Machine Learning / Data Science/ Data Architecture roles.
Python has been my primary language becase it is flexible, easy to write, learn and read. The ecosystem around Data Science, ETL and general purpose tasks - Api's, Scraping, database interaction is well developed.
Several times I have run into situations where python has been great to prototype a concept, to finalize my logic and iron out the edge cases. It jsut does not scale well in several scenarios.
ALthough python is a great language for scientists, analysts etc who use programming as a tool for their trade - such as data processing, machine learning, complex math etc. It is also an excellent scripting language and serves the purpose of glue to orchestrate several different components, explore data, prototype systems etc. Python libraries such as numpy, tensorflow, pandas etc also get around a lot of the limitations by calling into native libraries. 
There are still scenarios where you need that extra bit of performance. Specially in cases where the code is mature and the performance has a higher weight over the ease of writing code.
This is where using languages like Rust or Go comes in.
A good example would be writing an ETL job in Python to get the logic right. Lets say this is a command line tool that reads a CSV and then manipulates some data and outputs a Protobuff file. Initially written in in Python, this job is now mature and we want to get better performance out of it. Since the job is heavy on string processing we can gain performance from a lower level language and leveraging the concurrency our CPU provides us.

### Learning Rust when you know Python
In my career i came across several developers, data scientists, analysts etc who are brilliant in their field and learned to use Python as a general purpose tool to work with data. Not coming from a computer science background several of these people lack the understanding of what goes on under the hood - Memory management, Type inferencing, storing objects on stack vs on heap and passing around pointers etc. It is jsut not necessary for the end goal of being able to work with the data. At some point you may be curious to learn more about what goes under the hood or needing to get that extra performance.
If you come from this background but would like to learn a little bit more of what happens under the hood and learn Rust in the process this series is for you.

### Reference Material
This section shares some reference material that will be useful along the way
- [Rust By Example](https://doc.rust-lang.org/rust-by-example) - This is an excellent resource to learn everything about Rust.
- [Rustlings Course](https://github.com/rust-lang/rustlings/) - This course helps you get started with hands on coding.
- [RUst Programming Language Book](https://doc.rust-lang.org/book/) - This book is a comprehensize resource for learning Rust.

### Laying out the Foundation
So first we will start with a major difference between Python and Rust. Python is interpreted whereas Rust is compiled.
#### Interpreted Vs Compiled

#### Python
Python is interpreted. The python interpreter converts the python code to machine code at run time (Although you can compile python to .pyo or .pyc files).
Python is focused on ease of use. It was targeted at an audience that were not professional programmers but needed to write code for thier trade - Scientists, mathameticians, Statisticians etc. It really serves that purpose well.

###### Advantages:
- Portability - as long as there is a python interpreter for your platform you can run the same python code (Assuming all the dependencies etc can be installed).
- Dynamic Typing - Being interpreted allows us the freedom of passing around variables etc without having to worry about the type. The types are determined at run time.
###### Disadvantages:
- Slower run time - the code is interpreted at the time the code is ran, it also does not allow the interpreter the opportunity to fully optimize the machine code.
- Lack of compile time checking - In a compiled language your code is validated in several ways at compile time - Type compatibility of variables, possible unreachable paths etc.
- The GIL - Pythons interpreter has limitations to run on a single process due to how the interpreter works which does not allow us to always leverage the full capabilities of the processor. 
- Garbage collection - Python does automatic garbage collection like several modern languges. Garbage collection adds some memory and CPU overhead. More on this later.
- Lack of early bug detection - Since it is interpreted a lot of issues do not show up till the code is ran. This could lead to several edge cases not being detected till a later stage, import of unused libraries etc. This can be aleviated to a large extent by propper testing.
#### Rust
Rust on the other hand is compiled. Rust focuses on memory safety, speed and parallelism. Although a little more complex and tedious to write than Python it has it's own niche.
###### Advantages
- Static Typing - developers can have debates over the advantages os static vs dynamic typing but both have their place. In Rust the variables types are determined at compile time and there is no `null` type like there is in languages like Java/ Javascript leading to the dreaded null reference errors. 
- Maintainability/ Ease of debugging - Compiled languages bring out the best in programmer by needing them to think of several cases. E.g. - It checks if functions are in scope at compile time. Makes sure variables are in scope, variable types are not changed etc. This makes the code easier to maintain and debug in the long run.
- Concurrency - Rust allows us to handle concurrent programming safely and efficiently. This lets use leverage the full capability of the CPU and provides better performance.
- Memory management - Rust does not yet have a defined memory model. Memory management is largely addressed at compile time. This is a massive oversimplification but when variables go out of scope their memory is freed. This is what affords the much boasted memory safety.
- Performance - With all the features we have been talking of and being low-level and compiled Rust has small binaries (Minimal run time- More on this later). Code is memory efficient and can provice bare meta performance.

###### Disadvantages
- Harder to write - It by no means is as easy to write as Python. You really have to think about what is happening in the machine and not jsut focus on how you want to manipulate your data. Rust is not as suited for quick and dirty prototyping or data exploration as Python is. It is more focused on performance, stability and backwards compatibility.
- The static typing and strong memory management, borrow checker can be quite cumbersome. It leads to several compile time errors that can be hard to understand and debug coming from higher level languages. Although this is all in the interest of higher performance and better memory utilization.
- Not as developed eco-system around Data Science - Python has a very well developed adata science ecosystem which is not quite yet to that level in Rust. 
- Learning curve - Rust requires you to understand a lot more of what goes on at a lower level and be aware of how variables are passed, variable references etc. This can add a significant learning curve compared to say Python.

