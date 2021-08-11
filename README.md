# About this project
THIS README SERVES AS A COMMENT TO THE PROJECT DONE, AND IS NOT INTENDED FOR EVALUATION. 
IT IS FOR THE PURPOSE OF CLOSURE ONLY.

Acknowledgments: 

Before this project was undertaken, I need to confess that I do not watch Cricket at all. I did not understand the rules and I did not find it interesting. 

I would like to thank my brother Arjun for helping with the error handling process, as he had tried and tested every possible input to the program and making me realise there are more errors to handle.

I would like to thank my classmates who gave encouraging words during the process of completing this project.

I have to extend a special thanks to my friend Neelabh Somani who is an aspiring cricketer in the school circuit (now starting college, but unfortunately the pandemic has come) and convinced me to try and enjoy cricket. I tried to make sense of the actual score sheet that most matches follow, but it was an overload of information. 

And finally, I would like to thank Uma Maheswari Ma'am of SSNCE for being a great teacher during the 2nd Semester of the 2019-2020 Academic Year.

So, this program is made with people like me in mind - new to cricket, and want to understand the details of a match in the shortest time possible.


////////////////////////////////////////////////////////
Challenges Faced: 

Dealing with strings being read from and written into files was a difficult task. C as a language has certain limitations that makes reading the file hard. What I mean to say is that, in other languages like C++ and Python, structures stored in a .dat file would always take up the same number of bytes in a files. 

Say a structure took 100 bytes. If I use fseek() to move to the next 100 bytes, I would always end up at the the beginning of the next strucure that has been stored. This was in my experience with C++ and Python. In C however, I could not achieve a similar result.
C has a feature called Structure Packing, such that the bytes taken by a structure in a file always take the least bytes possible. Where this matters is with strings - not every string will have the same amount of characters.

The Structure itself may be defined to hold a string for a maximum length of 30, but if the numbers of characters entered are, say 10, the bytes taken will be 11 and not 30.

This feature definitely saves a lot of space for storage, but however makes traversing a file through manipulation of bytes impossible. 
If the first object has a string of 11 bytes, using fseek() to traverse the next 100 bytes WILL NOT land me at the starting byte of the next structure, but will land at 100-(30-11) = 81 bytes from the current position. 

Keeping in mind this limitation, I had chosen to store the score sheets in multiple different files instead to make the accessibility much easier. 

//////////////////////////////////////////////////////////

Final Note:

1. Some notable difficulties I faced was taking string inputs to write and read into files as described above. fgets() was a really useful tool and strcspn was used in removing the "\n" from the end of the strings.

2. Taking input for the choice in the menu screen was initially done with integers. But when a character was given, the program had crashed. This was changed later to taking a single character for the menu choice. If a string is entered now, after pressing the enter button for n times (n=strlen), the program returns to normal after the buffer is cleared.

3. When taking the first string input of the score sheet, the character buffer had to be cleared with a scanf() statement to a temporary char variable. Prior to implementing this,  writing into the file gave the wrong values.

Overall, this was a very fun and interesting project to do.
