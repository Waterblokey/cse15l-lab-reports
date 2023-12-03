## Part 1 – Debugging Scenario
Design a debugging scenario, and write your report as a conversation on EdStem. It should have:

The original post from a student with a screenshot showing a symptom and a description of a guess at the bug/some sense of what the failure-inducing input is. (Don’t actually make the post! Just write the content that would go in such a post)
A response from a TA asking a leading question or suggesting a command to try (To be clear, you are mimicking a TA here.)
Another screenshot/terminal output showing what information the student got from trying that, and a clear description of what the bug is.
At the end, all the information needed about the setup including:
The file & directory structure needed
The contents of each file before fixing the bug
The full command line (or lines) you ran to trigger the bug
A description of what to edit to fix the bug
You should actually set up and run the scenario from your screenshots. It should involve at least a Java file and a bash script. Describing the bug should involve reading some output at the terminal resulting from running one or more commands. Design an error that produces more interesting output than a single message about a syntax or unbound identifier error – showcase some interesting wrong behavior! Feel free to set this up by cloning and breaking some existing code like the grading script or code from class, or by designing something of your own from scratch, etc.

`Student: Help! my code is running like this. I double checked my code and I do not understand why the indices are off. I am incrementing all the correct indices at the right times. What might be wrong?`

<img width="448" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/c0f92f5a-d2b2-41c8-91e3-7ca3b033e7dd">

<img width="563" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/b917b705-9df4-4120-8c53-37376ff9ae22">


`TA: Have you checked all of the index variables, and the conditions that decide whether you should increment or not?`

`Student: Thank you! It turns out I was using || when I should have been using && in my conditional, causing my program to over index.`

<img width="423" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/8a6a5dfc-970e-4884-a32d-f1b847232e31">

Part 2 – Reflection
In a couple of sentences, describe something you learned from your lab experience in the second half of this quarter that you didn’t know before. It could be a technical topic we addressed specifically, something cool you found out on your own building on labs, something you learned from a tutor or classmate, and so on. It doesn’t have to be specifically related to a lab writeup, we just want to hear about cool things you learned!

`One cool and useful thing I learned in the second half of the quarter is how to use an ssh key to easily commit changes to GitHub. By doing this, I don't have to sign into github everytime I want to push a change, which is super useful`

A Note on Grading at the End of the Quarter
We will try, but there might not be a resubmission window for lab report 5, so do your best to be thorough, creative, and clear in your submission.

<img width="354" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/322490e1-8a18-4cb8-9249-9f05887199cf">


<img width="293" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/b77ee98d-3b96-4676-b732-cf930e1c77c9">

<img width="192" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/c95b3763-3afe-425f-905a-c5e132f80509">
