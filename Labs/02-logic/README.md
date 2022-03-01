# Lab 2

## Preparation tasks (done before the lab at home)

*Digital* or *Binary comparator* compares the digital signals A, B presented at input terminal and produce outputs depending upon the condition of those inputs.

1. Complete the truth table for 2-bit *Identity comparator* (B equals A), and two *Magnitude comparators* (B is greater than A, B is less than A). Note that, such a digital device has four inputs and three outputs/functions.

   | **Dec. equivalent** | **B[1:0]** | **A[1:0]** | **B is greater than A** | **B equals A** | **B is less than A** |
   | :-: | :-: | :-: | :-: | :-: | :-: |
   |  0 | 0 0 | 0 0 | 0 | 1 | 0 |
   |  1 | 0 0 | 0 1 | 0 | 0 | 1 |
   |  2 | 0 0 | 1 0 | 0 | 0 | 1 |
   |  3 | 0 0 | 1 1 | 0 | 0 | 1 |
   |  4 | 0 1 | 0 0 | 1 | 0 | 0 |
   |  5 | 0 1 | 0 1 | 0 | 1 | 0 |
   |  6 | 0 1 | 1 0 | 0 | 0 | 1 |
   |  7 | 0 1 | 1 1 | 0 | 0 | 1 |
   |  8 | 1 0 | 0 0 | 1 | 0 | 0 |
   |  9 | 1 0 | 0 1 | 1 | 0 | 0 |
   | 10 | 1 0 | 1 0 | 0 | 1 | 0 |
   | 11 | 1 0 | 1 1 | 0 | 0 | 1 |
   | 12 | 1 1 | 0 0 | 1 | 0 | 0 |
   | 13 | 1 1 | 0 1 | 1 | 0 | 0 |
   | 14 | 1 1 | 1 0 | 1 | 0 | 0 |
   | 15 | 1 1 | 1 1 | 0 | 1 | 0 |

<a name="part1"></a>

### 2-bit comparator

1. Karnaugh maps for three functions:

   Equals:
   
   ![K-maps](images/BequalsA.png)

   Greater than:

   ![K-maps](images/BisgreaterthanA.png)

   Less than:

   ![K-maps](images/Bislessthan.png)

2. Equations of simplified SoP (Sum of the Products) form of the "greater than" function and simplified PoS (Product of the Sums) form of the "less than" function.

   <img src="https://latex.codecogs.com/svg.image?greater_{SoP}^{min}=(\overline{A1}*B1)&plus;(\overline{A0}*B1*B0)&plus;(\overline{A1}*\overline{A0}*B0)\\less_{poS}^{min}=(A1&plus;A0)*(\overline{B0}&plus;\overline{B1})*(A0&plus;\overline{B1})*(\overline{B0}&plus;A1)*(\overline{B1}&plus;A1)" title="greater_{SoP}^{min}=(\overline{A1}*B1)+(\overline{A0}*B1*B0)+(\overline{A1}*\overline{A0}*B0)\\less_{poS}^{min}=(A1+A0)*(\overline{B0}+\overline{B1})*(A0+\overline{B1})*(\overline{B0}+A1)*(\overline{B1}+A1)" />

### 4-bit comparator

1. Listing of VHDL stimulus process from testbench file (`testbench.vhd`) with at least one assert (use BCD codes of your student ID digits as input combinations). Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

   Last two digits of my student ID: **xxxx10**

```vhdl
    p_stimulus : process
    begin
        -- Report a note at the beginning of stimulus process
        report "Stimulus process started" severity note;

        -- First test case
        s_b <= "0001"; if ID = xxxx10
        s_a <= "0000"; if ID = xxxx10
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '1') and
                (s_B_equals_A  = '0') and
                (s_B_less_A    = '0'))
        -- If false, then report an error
        report "Input combination COMPLETE_THIS_TEXT FAILED" severity error;

        -- Report a note at the end of stimulus process
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```

2. Text console screenshot during your simulation, including reports.

Pri spravnem nastaveni:

   ![](images/pri_spravnem.png)
   
Pri nespravnem nastaveni:
   
   ![](images/pri_nespravnem.png)

3. Link to your public EDA Playground example:

   [L I N K](https://www.edaplayground.com/x/jdmm)
