Simple CMake project demonstrating the following dependencies:

- abstract library a
- implementations r0 and r1 for a
- seperate library b using a
- Two applications using b and choosing either r0 or r1.

b -> a

TestingCMakeR0 -> b, r0

TestingCMakeR1 -> b, r1