# Pseudocode Rules

**P.S.: Developing a syntax specification for pseudocode, as it is done here, defeats the purpose of using pseudocode, which is to simplifying instructions (algorithms) in a way that they are understandable and not tied to a specific programming language. Having a specification implies that there is a right syntax (that syntax could very easily become a programming language, which has happened). This, again, defeats one important purpose for using pseudocode, namely _that it is not tied to a specific language_.**

**Of course, this does not mean that the pseudocode shouldn't have coherence. It should be easy to understand. This means that some conventionality is accepted (for example, using `x = 0` is a common way to refer to assignment, but it shouldn't be the strictly the case; `assign x the value of 0` should be accepted as well, although it may be a bit impractical since it is wordy).**

---

This is a personal quick reference on pseudocode syntax. There is no official pseudocode syntax, but I made this reference so I can have some consistency among my pseudocodes.

Some things came from a [towards data science](https://towardsdatascience.com/pseudocode-101-an-introduction-to-writing-good-pseudocode-1331cb855be7) article, some from [Flogorithm](http://flowgorithm.org/), and some came from my own experience.

**Some reminders**
* Keywords are always **capitalized** (e.g. `WHILE`).
* **One statement per line**.
* **Indentation** shows hierarchy (nested constructions).
* End constructions **prepending an END** or END_ (e.g. `ENDWHILE`)
* Statements are **programming language independent**.
* **Keep it simple, concise, and readable.**
* **FOCUS ON THE LOGIC AND PROCESS, NOT ON THE PSEUDOCODE SYNTAX.**

## Main Keywords
**DATA TYPES**

Specifying data types are not always necessary. That must be chosen during implementation, but specifying the types on the pseudocode can facilitate implementation (it can also help find bugs beforehand).
- `INTEGER`
- `REAL`
- `CHARACTER`
- `STRING`
- `BOOLEAN`

**ARRAYS**

Keyword: `ARRAY`

This does not apply to `CHARACTER` since an array of characters is just a `STRING`.

Syntax: `DECLARE ARRAY DATA_TYPE variable_name[size]`

Example:
```
DECLARE ARRAY INTEGER numbers[10]
```

**SEQUENCE**
* _Input_: `READ`, `OBTAIN`, `GET`
* _Output_: `PRINT`, `DISPLAY`, `SHOW`
* _Compute_: `COMPUTE`, `CALCULATE`, `DETERMINE`
* _Declare_: `DECLARE`
* _Initialize_: `INIT`
* _Assign_: `SET`, `ASSIGN`
* _Add_: `INCREMENT`, `BUMP`
* _Sub_: `DECREMENT`

**LOOPS AND CONTROL**
* _Comparison_: `GREATER THAN`, `LESS THAN`, `EQUAL TO`
* _Logical_: `AND`, `OR`, `NOR`

- `FOR`
```
FOR iteration bounds
	sequence
ENDFOR
```
- `WHILE`
```
WHILE condition
	sequence
ENDWHILE
```
- `CASE`
```
CASE expression OF
	condition 1: sequence 1
	condition 2: sequence 2
	...
	condition n: sequence n
	OTHERS: default sequence
ENDCASE
```
- `REAPEAT-UNTIL`
```
REPEAT
	sequence
UNTIL condition
```
- `IF-THEN-ELSE`
```
IF condition THEN
	sequence
ELSE
	sequence 1
ENDIF
```
For `If-elseif-else` constructions, follow the `CASE` syntax. This is pseudocode, not an implementation.

**ROUTINES**
* **Declaring routines**:

Keywords: `FUNCTION`, `RETURN`, `CALL`

Single function:
```
FUNCTION function_name with DATA_TYPE param1, DATA_TYPE param2
	sequence
	RETURN variable_name
ENDFUNTION
```

Although not all programming languages have an entry point (like the `main` in C/C++), `ENTRY_FUNCTION` can serve as that starting point if there are more than one routine in a pseudocode file. Arguments are not always needed (except when they are used within the routine).
```
ENTRY_FUNCTION with INTEGER arguments_counter, STRING ARRAY arguments
	sequence
END_ENTRY_FUNCTION
```

**EXCEPTIONS**

Although things like data abstraction, modularity, and error handling are ignored most of the time in pseudocode (because pseudocode focuses in the essence of the algorithm), it may be helpful to explicitly go over these things (in specific scenarios) in pseudocode.

Keywords: `BEGIN_EXCEPTION`, `END_EXCEPTION`, `EXCEPTION`, `WHEN`

```
BEGIN_EXCEPTION
	statements
	EXCEPTION
		WHEN exception1
			statements to handle exception1
		WHEN exception2
			statements to handle exception2
END_EXCEPTION
```

### Structures and Objects
Not all languages are object-oriented (like plain old `C`), so use this with caution. Regardless, pseudocode that contains objects could be implemented in `C` with the use of structures. It may be limited since there will be no _behaviors_, but there is always a workaround.

**Structures**

Keywords: `STRUCTURE`
```
STRUCTURE Structure_name
	DATA_TYPE variable_name
ENDSTRUCTURE
```

Structure names (like with object) capitalize the first letter. To declare and assign the structure, use the convention you prefer.
```
STRUCTURE Point
	INTEGER value_in_x
	INTEGER value_in_y
ENDSTRUCTURE

ENTRY_FUNCTION
	DECLARE Point my_point
	ASSIGN 10 to my_point value_in_x
	ASSIGN 20 to my_point value_in_y

	...
END_ENTRY_FUNCTION
```

**Objects**

Keywords: `CLASS`, `CONSTRUCTOR`, `NEW`, `THIS`
```
CLASS Class_name
	DATA_TYPE variable_name
	CONSTRUCTOR Class_name
	FUNCTION routine_name
ENDCLASS
```

Use the same convention as for the structure, but with the addition of behaviors. Declare the routine names and constructor in the class declaration, write the definitions in another section. Formal parameters are not always required within the class declaration.

`THIS` always refers to the instance of the class.

The constructor doesn't have to be defined or even declared most of the time. The constructor may be intuitive (just assign arguments to the attributes). However, use them in the pseudocode if they are more complex. Example:
```
CLASS Car
	STRING color
	REAL gas
	INTEGER position

	CONSTRUCTOR Car with color, gas, and position
	FUNCTION drive with INTEGER new_position
ENDCLASS

FUNCTION Car drive with INTEGER new_position
	DECREASE THIS Car gas
	SET THIS Car position to new_position
ENDFUNTION

ENTRY_FUNCTION
	DECLARE NEW Car my_car with color = "Blue", gas = 10.0, position = 5
	CALL my_car drive with new_position = 10
END_ENTRY_FUNCTION
```

Since the behaviors' parameters and the constructor are not always required in the class declaration, the previous examples could have also be written as:
```
CLASS Car
	STRING color
	REAL gas
	INTEGER position

	FUNCTION drive
ENDCLASS

FUNCTION Car drive with INTEGER new_position
	DECREASE THIS Car gas
	SET THIS Car position to new_position
ENDFUNTION

ENTRY_FUNCTION
	DECLARE NEW Car my_car with color = "Blue", gas = 10.0, position = 5
	CALL my_car drive with new_position = 10
END_ENTRY_FUNCTION
```

**Remember, pseudocode is not strict. It is just for planning and thinking about the process. Do not waste time checking syntax; pseudocode does not have a syntax.** This is just a reference I use to keep some consistency in my pseudocode. However, not all my pseudocode follows these rules.

**DON'T FOCUS ON THE SYNTAX. Focus on the process and logic of your program.**
