title: Rust for Python Developers
## Rust for Python Developers
I come from a low level (C/C++) background but wrote Python/Java/Scala for several years working in Data Engineering/ Machine Learning / Data Science/ Data Architecture roles.
Python has been my primary language becase it is flexible, easy to write, learn and read. The ecosystem around Data Science, ETL and general purpose tasks - Api's, Scraping, database interaction is well developed.
Several times I have run into situations where python has been great to prototype a concept, to finalize my logic and iron out the edge cases. It jsut does not scale well.
This is where using languages like Rust and Go comes in.
A good example would be writing an ETL job in Python to get the logic right. Lets say this is a command line tool that reads a CSV and then manipulates some data and outputs a Protobuff file. Works in Python, this job is now mature and we want to get better performance out of it.

### Learning Rust when you know Python
In my career i came across several developers, data scientists, analysts etc who are brilliant in their field and learned to use Python as a general purpose tool to work with data. Not coming from a computer science background several of these people lack the understanding of what goes on under the hood - Memory management, Type inferencing, storing objects on stack vs on heap and passing around pointers etc. It is jsut not necessary for the end goal of being able to work with the data.
If you come from this background but would like to learn a little bit more of what happens under the hood and learn Rust in the process this series is for you.

### Reference Material
This section shares some reference material that will be useful along the way
- [Rust By Example](https://doc.rust-lang.org/rust-by-example) - This is an excellent resource to learn everything about Rust.
- [Rustlings Course](https://github.com/rust-lang/rustlings/) - This course helps you get started with hands on coding.
- [RUst Programming Language Book](https://doc.rust-lang.org/book/) - This book is a comprehensize resource for learning Rust.

### Laying out the Foundation
So first we will start with a major difference between Python and Rust. Python is interpreted whereas Rust is compiled.
