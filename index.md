# Lab 4

## Steps
4. Log into ieng6

<img width="303" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/d9da77e2-e03c-4630-9dd1-715f4c37ea29">

`ssh cs15lfa23ij@ieng6.ucsd.edu` was stored in the previous command, so I only needed to do `<up> <enter> `

5. Clone your fork of the repository from your Github account (using the SSH URL)
<img width="286" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/c1a60b90-4341-4c2b-b16d-3bba43654544">

`git clone git@github.com:Waterblokey/lab7.git` was the first command that came up when searching for g, so I only needed to do `<ctrl> r g <enter>`


6. Run the tests, demonstrating that they fail
<img width="221" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/d3416c20-8e09-4aa8-af7a-88ce14a79ad6">

`c d <space> l <tab> <enter> b a s h t <tab> <enter>` By pressing tab, I could automatically complete all of `lab7/` and `test.sh`

7. Edit the code file to fix the failing test
<img width="254" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/d9ed0f65-253b-4aed-82d6-9abe8fafd495">

Before:
<img width="258" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/84fcbf5e-e974-4d43-8f15-5134ace89e56">

After:
<img width="260" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/b0e8ba53-739c-42c2-8c2e-4451a1c6507c">


`vim <space> <shift> L <tab> . <tab> <enter> 43 j e r 2 <shift> : w q <enter>` By doing `<shift> L`, I could auto fill `ListExamples` with tab, then by pressing `.` and `<tab>` again, I could add `.java`. `43 j` jumps down 43 lines to line 44, then `e` will go to the end of the first word, which was `index1`, `r` replaces that character, and `2` changes it from 1 to 2. I then did `<shift> : w q <enter>` to save my edits and exit.

8. Run the tests, demonstrating that they now succeed
<img width="217" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/081aa626-e063-479e-9d63-287622eb9e7c">

`bash t <tab> <enter>` I again use `<tab>` to autofill `test.sh`

9. Commit and push the resulting change to your Github account (you can pick any commit message!)
    
`<ctrl> r g i t <space> a <enter> <ctrl> r g i t <space> c o <enter> g i t p u s h <enter>` `git clone` was higher in the history than `git commit` so I needed to type out `git co` to find it. I then git pushed manually, finishing the assignment.

<img width="354" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/322490e1-8a18-4cb8-9249-9f05887199cf">


<img width="293" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/b77ee98d-3b96-4676-b732-cf930e1c77c9">

<img width="192" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/c95b3763-3afe-425f-905a-c5e132f80509">
