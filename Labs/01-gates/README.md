# Lab 1

### De Morgan's laws

1. Equations of all three versions of logic ![function]<img src="https://latex.codecogs.com/svg.image?\begin{align*}&space;&space;&space;&space;f(c,b,a)_{\textup{ORG}}&space;=&~&space;!{b}~*~a~&plus;~!{c}~*~!{b}\\&space;&space;&space;&space;f(c,b,a)_{\textup{NAND}}&space;=&~&space;!(!(!{b}~*~{a})~*~!(!{b}~*~!{c}))\\&space;&space;&space;&space;f(c,b,a)_{\textup{NOR}}&space;=&~&space;(!({b}~&plus;~!{a}))~&plus;~!(c~&plus;~b)\\\end{align*}" title="\begin{align*} f(c,b,a)_{\textup{ORG}} =&~ !{b}~*~a~+~!{c}~*~!{b}\\ f(c,b,a)_{\textup{NAND}} =&~ !(!(!{b}~*~{a})~*~!(!{b}~*~!{c}))\\ f(c,b,a)_{\textup{NOR}} =&~ (!({b}~+~!{a}))~+~!(c~+~b)\\\end{align*}" /> f(c,b,a):

   ![demorganlaw](images/demorganlaw.png)
   
2. Listing of VHDL architecture from design file (`design.vhd`) for all three functions. Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

```vhdl
architecture dataflow of demorgan is
begin
    f_org_o  <= (not(b_i) and a_i) or (not(c_i) and not(b_i));
    f_nand_o <= not (not (not b_i and a_i) and not(not b_i and not c_i));
    f_nor_o  <= (not (b_i or not a_i)) or not (c_i or b_i);
end architecture dataflow;
```

3. Complete table with logic functions' values:

| **c** | **b** |**a** | **f(c, b, a)_ORG** | **f(c, b, a)_NAND** | **f(c, b, a)_NOR** |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 1 | 1 | 1 |
| 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 1 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 | 1 | 1 |
| 1 | 1 | 0 | 0 | 0 | 0 |
| 1 | 1 | 1 | 0 | 0 | 0 |

### Distributive laws

1. Screenshot with simulated time waveforms. Always display all inputs and outputs (display the inputs at the top of the image, the outputs below them) at the appropriate time scale!

   ![waveforms](images/waveforms2.png)

2. Link to your public EDA Playground example:

   [L I N K](https://www.edaplayground.com/x/TcqB)
