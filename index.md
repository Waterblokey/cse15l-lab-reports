# Part 1 - Bugs
ArrayExamples.java `reversed` method
<br />
<br />
Failure Inducing input: {1, 2}
<br />
Asociated code:

```
  @Test
  public void ryantestReversed() {
    int[] input1 = { 1, 2 };
    assertArrayEquals(new int[]{ 2, 1 }, ArrayExamples.reversed(input1));
  }
```

<br />
<br />
non-failure inducing input: {0, 0}
<br />
Associated test code:

```
  @Test
  public void ryantestReversed() {
    int[] input1 = { 0, 0 };
    assertArrayEquals(new int[]{ 0, 0 }, ArrayExamples.reversed(input1));
  }
```

<br />
<br />
Symptom as shown by tests:
<br />
<br />
Buggy Symptoms: 

![image](https://media.discordapp.net/attachments/1145551780747419648/1170243820923920434/image.png?ex=6558557c&is=6545e07c&hm=97058437c8d4f0be8288e92b78cf2d7309df1e0ff7a01b40dc4599e461b4bc5e&=&width=1060&height=598)

non-faliure symptoms:
<br />
<br />
<img width="453" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/5255c6f8-f65a-4ca1-9f26-6100375eae96">

Buggy Code
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

Fixed code:

```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[arr.length - i - 1] = arr[i];
    }
    return newArray;
  }
```

<br />
Explanation of Fix:
<br />
The `reversed` method was not working because it set the given `array` 's elements to the elements of a newly initialized array, `newArray`, which has all values equal to 0. This can be fixed by making the values in `newArray` equal `array` array, because this will keep the values in the given array, but reverse them, instead of overwriting them as 0.
<br />

# Part 2 - Researching Commands

<br />
The command I chose is grep, and the command line options I will show are -i, -r, -v, and -l

## grep -i command line option with grep. 

Total: 3 examples
<br />
<br />
I found out about this option by prompting chatGPT with "What are 5 command-line options to use grep?"
ChatGPT gave the following output:
<br />
<br />
grep is a powerful command-line tool for searching text using regular expressions. Here are five common command-line options you can use with grep:
<br />
-i (or --ignore-case): This option makes grep perform a case-insensitive search, so it will match lines regardless of whether the characters are uppercase or lowercase. For example, grep -i "example" will match "Example," "EXAMPLE," and "example."
<br />
-r (or --recursive): Use this option to search for text recursively in directories and subdirectories. It's helpful when you want to search for a pattern in multiple files within a directory tree. For example, grep -r "pattern" /path/to/directory will search for "pattern" in all files under the specified directory.
<br />
-v (or --invert-match): This option inverts the match, which means it will only display lines that do not contain the specified pattern. For example, grep -v "exclude" will show lines that do not contain "exclude."
<br />
-l (or --files-with-matches): When you only want to see a list of filenames that contain the matching pattern, you can use this option. For example, grep -l "pattern" /path/to/files/* will list the filenames that contain "pattern."
<br />
-A, -B, and -C (or --after-context, --before-context, and --context): These options allow you to display lines of context around the matching lines. -A shows lines after the match, -B shows lines before the match, and -C shows lines both before and after the match. You can specify the number of lines to display as context. For example, grep -A 2 -B 2 "pattern" file.txt will display the lines containing "pattern" and two lines before and two lines after.
<br />
These are just a few of the many options available in grep to help you customize your text searches. You can access the full list of options and more details in the grep manual by running man grep in your terminal.
<br />
<br />
I then asked could you give an example using -i ? And ChatGPT output:
<br />
<br />
Certainly! The `-i` option in `grep` is used to perform a case-insensitive search. Here's an example of how to use it:
<br />
Let's say you have a file called `sample.txt` with the following content:

```
This is a sample text file.
Here's an EXAMPLE line.
Another example is here.
CASE-INSENSITIVE search is useful.
```

If you want to search for the word "example" in a case-insensitive manner, you can use the `-i` option as follows:

```bash
grep -i "example" sample.txt
```

The `-i` option tells `grep` to ignore the case, so it will match lines with "example," "EXAMPLE," and "Example." Running the command will produce the following output:

```
Here's an EXAMPLE line.
Another example is here.
CASE-INSENSITIVE search is useful.
```

As you can see, all lines containing variations of "example" were matched, regardless of their case.
<br />
<br />
I changed ChatGPT's suggestions to fit the file structure we were working with. First, I did ` grep "given" technical/biomed/gb-2002-3-12-research0086.txt` which only printed versions that had given with a lowercase g. 

Then I did `grep "Given" technical/biomed/gb-2002-3-12-research0086.txt` which only printed versions with an uppercase "G". Finally, using the -i option, a case-insensitive search is conducted, meaning both lowercase and uppercase "G" cases are printed. Here, I did ` grep -i "Given" technical/biomed/gb-2002-3-12-research0086.txt`
<br />
<img width="405" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/d47857fc-3e74-41b0-86c0-de7916be6e74">

## grep -r

This command recursively searches through a directory for any instance of the given pattern. 
<br />
I found out about this option from the first ChatGPT prompt I put in this lab report
<br />
First, I looked for any pattern "phospholipid" in the biomed directory. This is useful to find all instances of "phospholipid."
`grep -r "phospholipid" ~/cse15l-lab-reports/lab-5/docsearch/technical/biomed/`
here is the output
```
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2091-3-30.txt:        sn-2 arachidonate from phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2091-3-30.txt:        cellular localization and access to membrane-phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2091-3-30.txt:          phospholipids.
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2091-3-30.txt:        that ERK activity is required for phospholipid hydrolysis
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2091-3-31.txt:        highly basic and binds to acidic phospholipids [ 11 ] .
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2105-4-24.txt:        binding to a receptor). For example, the lysophospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-11.txt:        injury. The phospholipid-binding protein annexin V has a
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-11.txt:        by generating pores in phospholipid bilayer. We observed
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:        to bind acidic phospholipids, usually one or more derived
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:        of PH domains to phospholipids may simply be to promote
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:        the binding of PH domains to phospholipids appears to be
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:        to bind acidic phospholipids, we wanted to know whether the       
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:        PH domain of Boi1 binds acidic phospholipids and, if it
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          Binding of Boi1-PH to phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          also be stimulated by other inositol-based phospholipids.       
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipid PC (phosphatidylcholine) instead of PS.
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          To investigate whether binding to phospholipid may be
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipid is simply to target Boi1 to the plasma
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          impaired in the ability to bind phospholipid. One type of       
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipid.
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          To investigate whether binding to phospholipid may be
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          impaired in the ability to bind phospholipid. The
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipid is not critical for this pattern of
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipid may be important for the localization of
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          Binding to phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          different acidic phospholipids appears to be a fairly
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipids, suggesting that many PH domains bind
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          promiscuously to negatively charged phospholipids [ 11 ]        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          impaired in the ability to bind acidic phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          non-specifically to acidic phospholipids.
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          Significance of binding to phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipids generally) may be critical for Boi1
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipids may depend on the myristoyl group being
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          impair binding to phospholipids is the localization of
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipids may promote the localization of Boi1 to
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          How might binding to phospholipids promote
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          relevant phospholipid(s) (e.g., PIP
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          Another possibility is that the binding to phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipids. These findings suggest that binding to
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipid is not necessary for the interaction between       
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          that the mechanism by which binding to phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          one or more types of phospholipid influences Boi1's
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          phospholipids might regulate the binding of Boi1 to some        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          of the binding of any phospholipid to Boi1 would be the
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          regulated by that phospholipid.
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:        that binding to phospholipids is important for Boi1 action.       
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:        localization of Boi1 to the neck, the phospholipid-binding        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-16.txt:          Inositol-based phospholipids were stored at 1 mg/ml
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2121-3-19.txt:        phospholipids [ 32 ] , and data presented here documents
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2148-2-12.txt:          concentration of phospholipids in the outer membrane, for
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2156-2-1.txt:          biologically active phospholipid mediator. PAF acts by
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2164-4-24.txt:        the phospholipid bilayer or even to pass through the
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2172-3-16.txt:        hydrolysis of membrane phospholipids, fluxes in the
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2202-2-16.txt:        -an enzyme that hydrolyzes the phospholipid into choline
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2202-2-16.txt:          and the phospholipids were visualized with
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2202-2-16.txt:          comigrating with the appropriate phospholipid standards
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2202-4-16.txt:        phospholipid synthesis and metabolism (see Discussion), we
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2202-4-16.txt:        in synthesis of ether phospholipids and cholesterol [ 62 63       
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2210-1-3.txt:        membrane phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1475-2867-3-3.txt:        unsaturated fatty acids less available for phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-4598-1-6.txt:        hydrolyzes membrane phospholipids to generate inositol
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-1-2.txt:          and hepatic phospholipid (PL) pools (Table 1) was further
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-1-2.txt:        PL phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        serum phospholipids of children with SCD and healthy
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        the serum phospholipids of SCD patients and controls had
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        serum total phospholipid composition of children with SCD
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        The fatty acid composition of serum phospholipids is
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        known to reflect the phospholipid composition of cell
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        membrane phospholipids is a major determinant of membrane
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        composition of membrane phospholipids could contribute to
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids and correlated fatty acid proportions with
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids are truly surrogates for membrane
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids, as is widely believed, then the correlations        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids as well.
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        Cholesterol and phospholipids are the major lipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        polyunsaturated fatty acids in the red cell phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          eluted with 5 ml chloroform. Total phospholipids were
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          tubes containing the extracted phospholipids and the
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          membrane phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          phospholipid preparation. The melting points used for the        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          phospholipid fatty acid proportions and the cholesterol
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          in Table 2, the red cell phospholipids of the SCD
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          in the red cell membrane phospholipids of the SCD
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          membrane phospholipids of the SCD subjects compared to
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          significantly reduced in the membrane phospholipids of
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          phospholipids and significantly decreased proportions of
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          phospholipids
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          lower melting points in the red cell phospholipids of the        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          relative fluidity of the acyl chains of the phospholipids        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          by estimating the MMP of the phospholipids using the
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          of the red cell phospholipids was also inversely
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          phospholipid fatty acids and cholesterol
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          be significantly different between the phospholipids of
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:          fatty acid in the red cell phospholipids (Fig. 2, p <
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        based on analyses of serum phospholipids conducted in two
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        that red cell phospholipids of children with SCD contain
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        the red cell phospholipids of U.S. children with SCD. The
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        red cell phospholipids of the SCD subjects we studied may
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        acids in serum phospholipids to speculate that children
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids.
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        that comprise the phospholipids of membranes. One way to
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        the fatty acids in the total phospholipid fraction of the
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids. We found that the MMP of the membrane
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids of the children with SCD was significantly
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        chains of the membrane phospholipids, directly influence
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids. In a study of subjects with type 2 diabetes,        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        skeletal-muscle phospholipids. They speculated that changes        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        composition of tissue phospholipids in children with SCD.
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1476-511X-2-2.txt:        phospholipids were obtained after supplementation with fish        
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/ar319.txt:        phospholipids), and indirectly by depositing immune
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/ar328.txt:        6, 7], lupus anticoagulant and antiphospholipid syndrome
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/ar328.txt:        associated with anti-phospholipid antibodies), one had JRA,
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/ar429.txt:        increased production of rheumatoid factor, antiphospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2001-2-12-research0051.txt:          substrates, such as Ca 2+, phospholipids, inositol
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2001-2-12-research0054.txt:        phospholipids, and repair and recombination. Small-genome
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2002-3-11-research0060.txt:          glucosamine-based phospholipid that makes up the
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2003-4-2-r8.txt:        membrane phospholipid PIP2, which is generated from PIP by
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2003-4-2-r8.txt:        membrane phospholipid and is a precursor to second
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2003-4-2-r8.txt:        membrane structure and/or phospholipid signaling
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2003-4-2-r8.txt:        transport, phospholipid metabolism, signal transduction and       
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2003-4-2-r8.txt:        Cct1 are involved in phospholipid
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/gb-2003-4-2-r8.txt:        metabolism, and phospholipid signaling pathways are
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/rr191.txt:        Surfactant, a lipoprotein comprised of phospholipids
```
I also did a more targeted search, looking for arachidonate. This is useful for finding rare words since you search several files.
`grep -r arachidonate ~/cse15l-lab-reports/lab-5/docsearch/technical/biomed/`
```
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2091-3-30.txt:        sn-2 arachidonate from phospholipid
```

## grep -E

In this example, I also used -v and |. -v will only display lines that do not contain the given pattern. -E will allow for extended reular expressions, meaning multiple patterns are allowed. This in conjunction with the and operator, |, allowed me to only display lines that did not have many common words. This is useful if you want to get rid of many words, and only look at very specific patterns.
<br />
I found out about -E from asking chatGPT: can you list multiple patterns that you would like grep to produce? Which prompted:
<br />
<br />
Yes, you can list multiple patterns that you would like `grep` to produce by using the OR (`|`) operator in conjunction with `-E` option (for extended regular expressions). This allows you to specify multiple patterns and matches lines that contain any of those patterns. 
<br />
Here's an example:
<br />
Let's say you have a file called `data.txt` with the following content:

```
This is a sample text file.
Here's some data to search.
Another line with more information.
Searching for specific patterns.
```

Suppose you want to search for lines that contain either "sample" or "information." You can use `grep` with the `-E` option and the `|` operator like this:

```bash
grep -E "sample|information" data.txt
```

Running this command will produce the following output:

```
This is a sample text file.
Another line with more information.
```

The `-E` option enables extended regular expressions, and the `|` operator specifies the "or" condition, so `grep` will match lines that contain either "sample" or "information."
<br />
You can extend the list of patterns separated by `|` to include more search criteria, and `grep` will produce lines that match any of those patterns.
<br />
<br />
<br />
I used ChatGPT's example `"sample|information"` , and extended it to `"and|or|is|for|has|of|at|to"`

```
grep -v -E "and|or|is|for|has|of|at|to" technical/biomed/1471-2490-3-2.txt




        Background
        in their course, which may be helpful in decreasing the
        flank pain.


        Methods
        renal/ureteral colic were reviewed. The UHCT were obtained
        on a Cti/pro single slice helical CT scanner (General
        Electrical medical systems, Milwaukee, WI). The exposure


        Results
        diagnoses.


        ureteral/renal colic [ 9 10 11 12 13 ] . Apart from its
        Medical Center, Philadelphia, Marcella et al [ 8 ] noted an
        pain.


        Conclusion
        suspected renal/ureteric colic. In the present series, such


        Competing interests
        None declared.


        writing
```

And another example using -E by itself to search for either DNA or fluorescent. This is useful for finding multiple patterns that you're interested in.

```
grep -E "DNA|fluorescent" ~/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2350-2-11.txt
        over 235 kb of genomic DNA in chromosome band 15q21.1
          Genomic DNA and total RNA were extracted from
          FBN1 cDNA fragments and restriction enzyme digestions
          (QIAGEN) and directly sequenced with fluorescent
          terminators on an ABI Prism 377 DNA sequencer
          amplified genomic DNA with the ExpandTM PCR System
        samples had previously been screened with a cDNA
        amplification/SSCA protocol [ 14 ] and a genomic DNA/exon
        amplicons (Fig. 1a). Sequence analysis of the altered cDNA
        exons and their splice sites individually from genomic DNA
        for amplification of genomic DNA. Long-range PCR analysis
        gene is completely screened with a DNA-based PCR
        Bgl II digested genomic DNA from 18
        generated from a normal cDNA template as described above.
        genomic DNA are much more laborious and more difficult to
        DNA level with the list of phenotypic features, we feel
```

## grep -l
This option will only list the files that contain the given pattern.
One example of me using it is to search for a specific term in all of the `biomed` folder. This is useful to find a very rare word in a group of files.

```
grep -l "Multi-exon"  ~/cse15l-lab-reports//lab-5/docsearch/technical/biomed/*
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2350-2-11.txt
```

Another example is me using it to find a more general word in the biomed directory. This is useful because you may not want every line displayed, but only to know the files the pattern is in. This is especially helpeful for big directories like the biomed directory.

```
grep -l "phospholipids"  ~/cse15l-lab-reports//lab-5/docsearch/technical/biomed/*
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2091-3-30.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2091-3-31.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2105-4-24.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2121-3-16.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2121-3-19.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2148-2-12.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2172-3-16.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2202-2-16.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1471-2202-4-16.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1476-4598-1-6.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/1476-511X-2-2.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/ar319.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/gb-2001-2-12-research0051.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/gb-2001-2-12-research0054.txt
/c/Users/Ryan Livengood/cse15l-lab-reports//lab-5/docsearch/technical/biomed/rr191.txt
```
