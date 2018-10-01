# Markdown

Markdown is a plain-text file format. There are lots of programming tools that use Markdown, and it's useful and
easy to learn. Hash marks (the number sign) indicate headers. Asterisks indicate lists.

# Template

Use the following Code Smell template (copy and paste it at the end of this file and then edit it; don't include the "Begin template" or "End template" lines):

==== Begin template ====
## Code Smell: [Write the code smell name]

### Code Smell Category: [Write the code smell category name]

### List of classes and line numbers involved:

* [Write a class and list of line numbers, one class per asterisk, that describe the smell]

### Description:

[In your own words, explain how this particular code smells.]

### Solution:

[In your own words, explain how you might solve this code smell:
how would you refactor the code?]
==== End template ====

# List of code smells

## Code Smell: Long Method

### Code Smell Category: Bloaters

### List of classes and line numbers involved:

* simulation.WarehouseSimulation.start, Lines 41 - 96

### Description:

This class WarehouseSimulation.start inplemented the entire program functionality within one sole method.
The method, considering the tasks it is aimed to make, is huge.
It makes me (the newly hired programmer) a great pain in the mind.

### Solution:

This method contains the entire functionality of the program, which has a number of different tasks in the flow.
To make a method more programmer-friendly, I will retrieve each of the tasks along the workflow, and make it a method it self.
When rewriting the original start method, instead of lining up all the code, I can simply call the method for each of the tasks
(or steps).

## Code Smell: Speculative Generality

### Code Smell Category: Dispensables

### List of classes and line numbers involved:

* TranslationTable.TranslationTable, Line 24
* Order.Order, Line 26

### Description:

Both generators of class Order and class TranslationTable made space for adapting to different translation tables.
However, in this program (or in this warehouse) only fascias of one minivan model is dealt with,
indicating that only one translation table is in use.
This lead to extra code for a future situation that does not happen now.

### Solution:

Delete the class TranslationTable, and make the code (adapting to the one and only translation table file instead of a file f)
a method in class Order. Delete the parameter translationTable in the generator of class Order, and directly call the method
TranslationTable to do all the translating job.

## COde Smell: Dead Code

### Code Smell Category: Dispensables

### List of classes and line numbers involved

* PickerOrderList.getIDs, Lines 97 - 104

### Description:

The method getIDs is never used.

### Solution:

Delete it.
