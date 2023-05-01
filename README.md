Download Link: https://assignmentchef.com/product/solved-csc3022h-assignment1-architecture-and-interface
<br>
<h1>Architecture and interface</h1>

Build a simple text-based interface which can be used to perform operations on your database. You must write “stubs” so when an option is invoked, the function prints a message like “function QueryDatabase() called”. You will provide the correct functions during the second part of the tutorial.

Your database interface must have options to do the following:

<ol>

 <li>add student</li>

 <li>read database</li>

 <li>save database</li>

 <li>display given student data</li>

 <li>grade student</li>

</ol>

Do not worry about the underlying functions right now; just ensure that when an option is selected, the right “stub” message is printed and the screen is sensibly redrawn. The menu could look something like the following:

0: Add student 1: Read database …

q: Quit

Enter a number (or q to quit) and press return…

To clear the terminal window, you can use a shell command:

void clear(void) { system(“clear”); } // include <strong>cstdlib</strong>

Since you are reading menu options continuously, you will need an “event loop” to process your menu selection. You can use a for statement to achieve this:

for (;;) { // loop forever

… // process key press and call relevant functions if (<em>terminate condition</em>) break;

}

Recall that you can use a struct to bundle together multiple fields into a single datatype. The <strong>StudentRecord </strong>struct must have the following fields:

Name (String), Surname (String), StudentNumber (String), ClassRecord (String).

The <strong>ClassRecord </strong>field is a string of space separated numbers which reflect various marks the student has obtained during the year. For example: “54 66 72 34”

You must set up the basic code structures you need: a <strong>StudentRecord </strong>struct and a <strong>std::vector </strong>to store a number of <strong>StudentRecord </strong>instances. The <strong>std::vector </strong>data structure is an expanding array-based structure that comes bundled with C++ and you can consult the documentation at <a href="http://www.cplusplus.com/reference/vector/vector/">http://www.cplusplus.com/reference/vector/vector/ </a>on how to use it. The vector data structure supports random addressing using the familiar [] notation. For readability please ensure that your methods and the vector of records is defined in a separate C++ file with its own header and <strong>NOT </strong>in your driver.

Please ensure that you always use your student id as <strong>namespace </strong>when defining methods, structs and classes in this course:

<table width="567">

 <tbody>

  <tr>

   <td width="567"><em>/**</em><em>*.h file:</em><em>*/</em>#ifndef DATABASE_H#define DATABASE_H <em>//any includes here </em>namespace STUDENT_NO { void add_student(std::string name …); …}#endif<em>/**</em><em>*.cpp file:</em><em>*/</em>#include “database.h”STUDENT_NO::add_student(std::string name …){ …}</td>

  </tr>

 </tbody>

</table>

Remember that you usually have a basic driver file, containing main() and other necessary functionality (such as the event loop) and a collection of class source files, along with appropriate header files for other cpp files.

You must also write a Makefile (or mod the one from the consolidation session) to compile your work. This should be easily extended, since you may need to change it for the next part of the tutorial.

<h1>The Database Engine</h1>

In this part of the assignment you will provide definitions for all the method stubs you created in Part One.

The functionality required is as follows:

<strong>Add student </strong>Enter new student data

<strong>Read/Save database </strong>Write or read a simple text file which stores a list of database entries (see below);

<strong>Display student data </strong>Print the record for a given student, based on the student number

entered;

<strong>Grade student </strong>Print an average for a student based on a given student number. The average will be constructed by extracting all the number in the ClassRecord string and averaging them.

<strong>Exit </strong>Exit from the application; any information not saved will be lost.

<strong>Handin</strong> <strong>Date:</strong> 27 March 2017 at 10AM.

<strong>Notes:</strong>

<ol>

 <li>when comparing strings, note that string comparisons are case sensitive (so <em>Durban </em>is not the same as <em>durban</em>);</li>

 <li>You must use a std::vector&lt;&gt; container to hold your record data; this will require you to include the header file <strong>vector</strong>. The vector data is not sorted by default. It is not expected that you will sort the data — a simple sequential search will be adequate for this work;</li>

 <li>File I/O requires the use of ifstream and ofstream Basic I/O uses &lt;&lt; and</li>

</ol>

&gt;&gt; in the same manner as console I/O. For example,

#include &lt;fstream&gt; …

int myint; ifstream ifs(“inputfile.txt”); // argument is ‘‘char*’’ NOT String ifs &gt;&gt; myint; ifs.close();

opens an input file stream and reads an integer from it, placing it in myint. The stream is then closed. Output file streams work in a similar manner. More on this can be found in the notes;

Do <strong>not </strong>use C-like mechanisms to accomplish this.

<ol start="4">

 <li>You can read input from a string (instead of a file): use an <em>input stringstream:</em></li>

</ol>

#include &lt;sstream&gt; …

string X = “buenos dias mi amigo”, value; istringstream iss(X); while (!iss.eof())

{ iss &gt;&gt; value;

cout &lt;&lt; “value =” &lt;&lt; value &lt;&lt; endl;

}

<ol start="5">

 <li>You can write the record data out in the order in which it is stored in the vector.To reconstruct the list, simply read each record in turn and “push” it back onto an empty vector. You must decide on a format for your database file;</li>

 <li>You may <strong>not </strong>have duplicate records (i.e. two or more records for the same student number). When you enter new data, you must first check to see whether that student exists. If so, overwrite the old data with the new, otherwise create a new record as expected.</li>

 <li>You must hand in the Makefile and your source file(s). The Makefile must functioncorrectly.</li>

</ol>