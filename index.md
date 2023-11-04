# Part 1 - Bugs
ArrayExamples.java `reversed` method
<br />
<br />
Failure Inducing input: {1, 2}
<br />
<br />
non-failure inducing input: {0, 0}
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
The 'reversed' method was not working because it set the given `array`'s elements to the elements of a newly initialized array, `newArray`, which has all values equal to 0. This can be fixed by making the values in `newArray` equal `array` array, because this will keep the values in the given array, but reverse them, instead of overwriting them as 0.
# Part 2 - Researching Commands

## grep -i command line option with grep. 
First, I did ` grep "given" technical/biomed/gb-2002-3-12-research0086.txt` which only printed versions that had given with a lowercase g. 
Then I did `grep "Given" technical/biomed/gb-2002-3-12-research0086.txt` which only printed versions with an uppercase "G". Finally, using the -i option, a case-insensitive search is conducted, meaning both lowercase and uppercase "G" cases are printed. Here, I did ` grep -i "Given" technical/biomed/gb-2002-3-12-research0086.txt`
<br />
<img width="405" alt="image" src="https://github.com/Waterblokey/cse15l-lab-reports/assets/118576768/d47857fc-3e74-41b0-86c0-de7916be6e74">
## grep -r
This command recursively searches through a directory for any instance of the given pattern. 
<br />
First, I looked for any pattern "phospholipid" in the biomed directory.
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
I also did a more targeted search, looking for arachidonate
`grep -r arachidonate ~/cse15l-lab-reports/lab-5/docsearch/technical/biomed/`
```
/c/Users/Ryan Livengood/cse15l-lab-reports/lab-5/docsearch/technical/biomed/1471-2091-3-30.txt:        sn-2 arachidonate from phospholipid
```
