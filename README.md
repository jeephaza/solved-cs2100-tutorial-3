Download Link: https://assignmentchef.com/product/solved-cs2100-tutorial-3
<br>
D1. Given two integer arrays <em>A</em> and <em>B</em> with unknown number of elements, and their base addresses stored in registers <strong>$s0</strong> and <strong>$s1</strong> respectively, study the MIPS code below. Note that an integer takes up 32 bits of memory.

<strong>      addi $t0, $s0, 0       addi $t1, $s1, 0 loop: lw   $t3, 0($t0)       lw   $t4, 0($t1)       slt  $t5, $t4, $t3      </strong><strong># line A</strong><strong>       beq  $t5, $zero, skip   </strong><strong># line B</strong><strong>       sw   $t4, 0($t0)       sw   $t3, 0($t1) skip: addi $t0, $t0, 4       addi $t1, $t1, 4       bne  $t3, $zero, loop </strong>




<ol>

 <li>What is the purpose of register <strong>$t1</strong> in this code?</li>

</ol>




<ol>

 <li>If array <em>A</em> = {7, 4, 1, 6, 0, 5, 9, 0} and                   array <em>B</em> = {3, 4, 5, 2, 1, 0, 0, 9},     give the final content of these two arrays.</li>

</ol>

<strong> </strong>

<ol>

 <li>How many <strong>store word</strong> operations are performed given the contents of the arrays in part (b)?</li>

</ol>




<ol>

 <li>What is the value (in decimal) of the immediate field in the machine code representation of the <strong>bne</strong> instruction?</li>

</ol>




<ol>

 <li>The two lines indicated as “line A” and “line B” represent the translation of a MIPS pseudo-instruction. Give the corresponding pseudo-instruction.</li>

</ol>







<strong><em>Tutorial Questions: </em></strong>

<ol>

 <li>Below is a C code that performs palindrome checking. A palindrome is a sequence of characters that reads the same backward or forward. For example, “madam” and “rotator” are palindromes.</li>

</ol>

<table width="593">

 <tbody>

  <tr>

   <td width="593"><strong>char string[size] = { … }; </strong><strong>// some string</strong><strong> int low, high, matched; </strong><strong> </strong><strong>// Translate to MIPS from this point onwards </strong><strong>low = 0; high = size-1; matched = 1;     </strong><strong>// assume this is a palindrome </strong><strong>     // In C, 1 means true and 0 means false </strong><strong>while ((low &lt; high) &amp;&amp; matched) {  if (string[low] != string[high])   matched = 0; </strong><strong>// found a mismatch</strong><strong>  else {   low++;   high–; </strong><strong> }          </strong><strong>} </strong><strong>// “matched” = 1 (palindrome) or 0 (not palindrome) </strong></td>

  </tr>

 </tbody>

</table>




Given the following variable mappings:       low è $s0;   highè $s1;

matched è $s3;

base address of string[] è $s4;     size è $s5

<ol>

 <li>Translate the C code into MIPS code by keeping track of the indices.</li>

 <li>Translate the C code into MIPS code by using the idea of “array pointer”. Basically, we keep track of the actual addresses of the elements to be accessed, rather than the indices. Refer to <u>lecture set #8, slide 34</u> for an example.</li>

</ol>




<strong>Note:</strong> Recall the “short circuit” logical AND operation in C. Given condition (A &amp;&amp; B), condition B will not be checked if A is found to be false.







<ol start="2">

 <li>You accidentally spilled coffee on your best friend’s MIPS assembly code printout. Fortunately, there are enough hints for you to reconstruct the code. Fill in the missing lines (shaded cells) below to save your friendship.</li>

</ol>

<strong>Answer: </strong>

<table width="571">

 <tbody>

  <tr>

   <td width="110">InstructionEncoding</td>

   <td width="461">MIPS Code</td>

  </tr>

  <tr>

   <td width="110"> </td>

   <td width="461"># <strong>$s1</strong> stores the result, <strong>$t0</strong> stores a non-negative number</td>

  </tr>

  <tr>

   <td width="110"> </td>

   <td width="461"><strong>      addi $s1, $zero, 0 </strong>#Inst. address is 0x00400028</td>

  </tr>

  <tr>

   <td width="110"><strong>0x00084042 </strong></td>

   <td width="461"><strong>loop: srl $t0, $t0, 1</strong></td>

  </tr>

  <tr>

   <td width="110"><strong>0x11000002 </strong></td>

   <td width="461"><strong>       </strong></td>

  </tr>

  <tr>

   <td width="110"><strong>0x22310001 </strong></td>

   <td width="461"><strong>       </strong></td>

  </tr>

  <tr>

   <td width="110"> </td>

   <td width="461"><strong>      j loop</strong></td>

  </tr>

  <tr>

   <td width="110"> </td>

   <td width="461"><strong>exit:</strong></td>

  </tr>

 </tbody>

</table>




<ol>

 <li>Give a simple mathematic expression for the relationship between <strong>$s1</strong> and <strong>$t0</strong> as calculated in the code.</li>

</ol>







<ol start="3">

 <li>[AY2012/13 Semester 2 Assignment 3]</li>

</ol>

Your friend Alko just learned <strong>binary search</strong> in CS1020 and could not wait to impress you. As a friendly gesture, show Alko that you can do the same, but in MIPS! J

Complete the following MIPS code. To simplify your tasks, some instructions have already been written for you, so you only need to fill in the missing parts in <strong>[ ]</strong>. Please translate as close as possible to the original code given in the comment column. You can assume registers $s0 to $s5 are properly initialized to the correct values before the code below.




<ol>

 <li></li>

</ol>

<table width="605">

 <tbody>

  <tr>

   <td colspan="2" width="300">Variable Mappings</td>

   <td width="305">Comments</td>

  </tr>

  <tr>

   <td colspan="3" width="605">address of array[] è $s0target è $s1     // value to look for in array low è $s2          // lower bound of the subarray high è $s3                // upper bound of the subarray mid è $s4                  // middle index of the subarray ans è $s5                  // index of the target if found, -1 otherwise. Initialized to -1.</td>

  </tr>

  <tr>

   <td width="270">loop:slt $t9, $s3, $s2       bne $t9, $zero, end</td>

   <td colspan="2" width="335">#while (low &lt;= high) {</td>

  </tr>

  <tr>

   <td width="270">   add $s4, $s2, $s3   <strong>            [</strong><strong>                    </strong><strong>] </strong></td>

   <td colspan="2" width="335">#   mid = (low + high)/ 2</td>

  </tr>

  <tr>

   <td width="270">   sll $t0, $s4, 2                 add $t0, $s0, $t0           <strong>[                    ] </strong></td>

   <td colspan="2" width="335">#   t0 = mid*4#   t0 = &amp;array[mid] in bytes#   t1 = array[mid]</td>

  </tr>

  <tr>

   <td width="270">   slt $t9, $s1, $t1           beq $t9, $zero, bigger</td>

   <td colspan="2" width="335">#   if (target &lt; array[mid])</td>

  </tr>

  <tr>

   <td width="270">   addi $s3, $s4, -1     j loopEnd</td>

   <td colspan="2" width="335">#      high = mid – 1</td>

  </tr>

  <tr>

   <td width="270">bigger:<strong>[                    ] </strong><strong>   [                    ]</strong></td>

   <td colspan="2" width="335">#   else if (target &gt; array[mid])</td>

  </tr>

  <tr>

   <td width="270">   addi $s2, $s4, 1    j loopEnd</td>

   <td colspan="2" width="335">#      low = mid + 1</td>

  </tr>

  <tr>

   <td width="270">equal:add $s5, $s4, $zero  <strong>[                    ] </strong></td>

   <td colspan="2" width="335">#   else {        ans = mid        break #   }</td>

  </tr>

  <tr>

   <td width="270">loopEnd:<strong>[                    ] </strong></td>

   <td colspan="2" width="335">#} //end of while-loop</td>

  </tr>

  <tr>

   <td width="270">end:</td>

   <td colspan="2" width="335"> </td>

  </tr>

  <tr>

   <td width="270"></td>

   <td width="30"></td>

   <td width="305"></td>

  </tr>

 </tbody>

</table>







<ol>

 <li>What is the immediate value in <u>decimal</u> for the “<strong>bne $t9, $zero, end</strong>” instruction? You should count only the instructions; labels are not included in the machine code.</li>

</ol>







<ol>

 <li>If the first instruction is placed in memory address at 0xFFFFFF00, what is the <strong>hexadecimal representation</strong> of the instruction “<strong>j loopEnd</strong>” (for “high = mid – 1”)?</li>

</ol>







<ol>

 <li>Is the encoding for the second “<strong>j loopEnd</strong>” different from part (c)? If yes, give the new encoding, otherwise briefly explain the reason.</li>

</ol>