# pick-a-number.bf explained

* Compares a numerical value input by the user to a predefined value (set to '1').
* Displays a different message depending on whether:
    * (1.) the user-input is **greater than** the predefined value, or 
    * (2.) not (ie. **less than or equal to**) the predefined value.

## code
```befunge
v
                                                         > "ENO si tuptuO" ,,,,,,,,,,,,,, !|
                                         v  ,  <         ^                                .|
>    " :01 dna 0 neewteb rebmun a retnE" >  :  |         ^                                .|
                                               > & 1 ` > |                                .|
                                                         > "orez si tuptuO" ,,,,,,,,,,,,,, @

```
                                                         
> [!TIP]
> * `<` symbol on line 3 MUST align with `|` below;
> * `>` symbol on line 5 MUST align with `|` above;

## program flow

* from line 1 **DOWN** to line 4;
* on line 4, from left to right until `|` instruction;
* **LOOP:** ***UP** to line 3 and **right-to-left** on it until `v`; then **DOWN** to line 4 and **left-to-right** (from `>` to `|`), repeat from * until whole message (`Enter a number between 0 and 10: `) is displayed, then...
* ...**DOWN** (since stack is empty - ie. popped value is `0`) to line 5 `>` (under `|` instruction) and **left-to-right** performing the following:
    * `&` - accepts **user input**
    * `1` - pushes **predefined value** (of 1) to the stack
    * `` ` `` - **compares** the user input with the predefined value:
        * pushes '1' to stack if input is **greater than** the predefined,
        * otherwise pushes '0'
        * *(NOTE: this will be the next **popped value**)*
    * `>` - moves to the **right** to the next instruction
    * `|` - perfoms a **conditional operation** based on the popped value:
        * if the **popped value** is **NOT** `0`:
            * moves **UP** to line 4 ,
            * from there moves **UP** to line 3,
            * moves **UP** to line 2,
            * moves **RIGHT** and prints `Output is ONE` [<sup>1</sup>](#superscript-1);
            * (on line 2) the (non-zero) value is **negated** (ie. set to `0`) and popped off the stack by the `!` instruction - this sets the direction of the `|` instruction to **DOWN**,
            * (on lines 3-5 left-to-right) the `.` instruction pops the top value from the stack, the direction of the `|` instruction is **DOWN**,
            * (on line 6) the `@` instruction is reached and ends the program.
        *  if the popped value **IS** `0`:
            *  moves **DOWN** to line 6
            *  from there moves **RIGHT** and prints `Output is zero` [<sup>2</sup>](#superscript-2)
            * (on line 6) the `@` instruction ends the program.

> [!NOTE]
> * <a name="superscript-1"></a><sup>1</sup>, <a name="superscript-2"></a><sup>2</sup> - These printed messages were **intentionally** *not* optimized, for easier readability
>
> * `,` - pops value and prints it as ASCII value

- - -
## output
```console
Enter a number between 0 and 10: 0
Output is zero

Enter a number between 0 and 10: 5
Output is ONE.

```

> [!NOTE]
> A **newline character** *may* be automatically appended when a string is printed (by default) causing *unexpected characters* (such as a `.`) to be displayed at the end of the output.

