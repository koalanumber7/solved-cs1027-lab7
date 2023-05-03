Download Link: https://assignmentchef.com/product/solved-cs1027-lab7
<br>
<ul>

 <li>Implement comparison methods for ordered lists of custom object types</li>

 <li>Translate a complex sequence of ordering rules into Java code</li>

 <li>Create a persistent user input structure using a loop</li>

 <li>Determine alternate approaches to programming specific methods</li>

</ul>

<h1>Pre-Lab</h1>

<ul>

 <li>Create a new Java project called Lab7</li>

 <li>Download the files: <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ArrayOrderedList.java">java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ArrayOrderedList.java">,</a> <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ArrayList.java">ArrayList.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ArrayList.java">,</a> <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ArrayIterator.java">ArrayIterator.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ArrayIterator.java">,</a></li>

</ul>

<a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/OrderedListADT.java">OrderedListADT.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/OrderedListADT.java">,</a> <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ElementNotFoundException.java">ElementNotFoundException.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ElementNotFoundException.java">,</a> <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/EmptyCollectionException.java">EmptyCollectionException.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/EmptyCollectionException.java">,</a>

<a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ListADT.java">ListADT.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ListADT.java">,</a> <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/Card.java">Card.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/Card.java">,</a> <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/TestCards.java">TestCards.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/TestCards.java">,</a> <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/Person.java">Person.java</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/Person.java">,</a> and <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/ContactList.java">ContactList.java</a>        Save these downloaded files into the Lab7 src folder




<h1>Exercise 1 – Ordering a deck of cards</h1>




<ol>

 <li>Open Card.java and TestCards.java in Eclipse and examine the code in both classes.</li>

 <li>Try running the TestCards class. An exception will be thrown. Read the exception message in the console and click on the line it points to, from the add() method in ArrayOrderedList.java, to help you understand why this occurred.</li>

 <li>Go back into Card.java and modify the class header so that the class implements Comparable&lt;Card&gt;</li>

 <li>The class name will now show an error due to it missing the method that are required from the Comparable interface: compareTo()</li>

 <li>Hover over the class name in the error window and click “Add unimplemented methods” to auto-generate the compareTo() stub or just type in the method signature yourself.</li>

 <li>Before completing this method, there are a few other helper methods to implement.</li>

 <li>Create an equals() Make it return true if both the rank and suit are the same between this and other, and false otherwise.</li>

 <li>Create two helper methods called getSuitValue() and getRankValue() Both methods will have int return types. These methods will be used to order the cards given the specified rules and hints (note that this is a specific scenario and these orderings will not apply to many, if any, actual games):

  <ul>

   <li>suits are ordered as Diamonds (lowest), Clubs, Hearts, Spades (highest) [note that only the initial letters are being used to represent the suits]</li>

   <li>ranks are ordered as 2-10 in based on their numeric value, Jacks, Queens, and Kings are all considered equal, higher than the numeric cards, and Aces are considered the highest rank</li>

   <li>where applicable, you can choose which values to use for the ranking system so long as they perform the correct ordering.</li>

   <li>try to code these methods on your own, but if you are stuck then read the hint provided in <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/Lab7Hints.txt">txt</a> (note that this file also contains the solutions to the ordered deck)</li>

  </ul></li>

 <li>Go back to the compareTo() method to fill it in based on the following specifications:

  <ul>

   <li>Call the equals() method to see if the two cards are the same (return 0 if so).</li>

   <li>Use the getRankValue() method on both cards and compare them. If they have different rank values, use this comparison to determine their order. If they have the same rank value, proceed to the next option.</li>

   <li>Use getSuitValue() to compare two cards of the same rank value.</li>

  </ul></li>

 <li>Run TestCards.java to check if your ordering system was implemented correctly. The first example, at the top, should produce the following results:</li>

</ol>

7 of D 7 of D

7 of H

10 of C

K of S

A of H

<ol start="11">

 <li>The results of the second example are found in <a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/Lab7Hints.txt">txt</a><a href="https://www.csd.uwo.ca/courses/CS1027a/labs/lab07/Lab7Hints.txt">.</a></li>

</ol>




<h1>Exercise 2 – Ordering a contact list</h1>




<ol>

 <li>Open Person.java and ContactList.java in Eclipse and examine the code in both classes.</li>

 <li>The Person class already implements Comparable&lt;Person&gt; and contains an empty compareTo() This program, once it’s complete, will provide 3 options for ordering the contacts: sorting by name, email, or city. We’ll revisit compareTo() shortly.</li>

 <li>First, create 3 private helper methods called sortByName(Person other), sortByEmail(Person other), and sortByCity(Person other) and all should have int return types. Use the String compareTo() within these methods.</li>

 <li>Now fill in the Person class compareTo() with calls to these private helper methods within a conditional. Use sortBy to determine how to order the list. What kind of values are we expecting in this sortBy variable? Examine the code in ContactList if you are unsure. You may need to also want to read the steps below and then come back to this step once you understand how this variable works.</li>

 <li>Go into ContactList.java. There are two methods that have been left incomplete.</li>

 <li>The main() method needs the user input portion added. Use the Scanner class and char c = input.next().charAt(0); to read in the character typed by the user in the console.</li>

 <li>Add a loop to continuously prompt the user to enter a character to sort, until they enter a character other than ‘n’, ‘e’, or ‘c’. Display the message stored in msg every time the user is asked to enter a character.</li>

 <li>When they do enter one of the 3 valid character options, create a new ContactList object with the corresponding parameters (the contacts array and the entered character).</li>

 <li>The last part to fill in is the printContacts() There are multiple ways of printing out the contact list table. How many different approaches can you think of? Which one requires the least amount of code to be added?</li>

 <li>Run ContactList.java and enter each of the options ‘n’, ‘e’, and ‘c’ and check that the list is printed correctly and ordered on the corresponding parameter (name, email, or city).</li>

</ol>


