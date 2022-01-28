# Lab Report 2: Code Changes to Solve Bugs
# 1. Solving the Problem of Infinite Loop

>The following is the screenshot for the failure: 

<img src = "D8053206-4A6A-4C99-981E-42D80819EB5A.jpeg" width = "500" height = "300">

>Apparently, the program goes into infinite loop. Here is the [link](test-file2.md) for the test file that causes this problem. The reason why the infinite loop occurs is that there are some other characters after the parentheses. Therefore, currentIndex will be always smaller than markdown.length(), and the while condition always holds. The following is the screenshot of the code change to solve this bug and the correct output. 

<img src = "B8B82D0F-23F0-4E6B-BE9D-484FDBD1C85A.jpeg" width = "500" height = "300">
<img src = "EC39CC6B-A667-44C1-B4DB-0A8F21D1BE5A.jpeg" width = "500" height = "300">


>Four extra conditions that check whether nextOpenBracket, nextCloseBracket, openParen, and closeParen are smaller than zero are added to solve the infinite loop. This works because when all brackets and parentheses are already dealt with, the result of indexOf() will be -1. With these if statements, the while loop will break. The output of our revised program indicates the correctness of our code change. 

<br>

# 2. Solving the Problem of EmptyStackException

>During the lab, we try to use the data structure of stack to do markdown parse. The following is the original code that causes EmptyStackException.

<img src = "60BAD62C-3E65-4B0E-B8ED-4B203876AF86.jpeg" width = "500" height = "300">

>Here is the [link](test-file7.md) for the test file that causes EmptyStackException. The reason why this problem occurs is that we didn't check whether the stack is empty. Calling pop() method when the stack is already empty causes this EmptytackException. The following pictures are the code changes and output of our refined program. 

<img src = "410907A2-0389-44CE-B179-1349FF7DD610.jpeg" width = "500" height = "300">

<br>

<img src = "3ED5F9C2-9787-4C26-9774-7532493D0DDF.jpeg" width = "500" height = "300">

<br>

>By adding an extra if statement, we exclude the possibility of EmptyStackException, as when the stack is empty, it breaks the for loop. 

# 3. Solving the Problem of Not Instantiating Varaible

>During the lab, to deal with many test methods, we try to use @Before and setUp() method to instantiate all the variables. However, cannot find symbol occurs when we use command line to run the test program. 

<img src = "0A8B32FB-3F47-43BC-A2B6-61FF86CBE98A_1_105_c.jpeg" width = "500" height = "300">
<br>

>The error occurs because we put the instantiation of variables inside the @Before method. Actually, @Before annotation only functions in runtime, so the Java static checker can't find the variables and gives cannot find symbol error. The following pictures are code changes and correct output. 

<img src = "950AB1D3-5D67-43B5-A393-8BCCE647729F.jpeg" width = "500" height = "300">
<img src = "CE9839A8-B661-40F1-AC96-E578B49165FC_1_105_c.jpeg" width = "500" height = "300">

>We solve this bug by putting the variable as class field and instantiate in @Before method. Here is the [link](MarkdownParseTest.java) for revised test file. 
