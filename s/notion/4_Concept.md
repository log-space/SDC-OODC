<p align="right">
	<b>Concept</b>
</p>

<hr/>

###### Library Preprocessor
```c

#include <stdio.h>

int main()
{
    printf("Hello, world!\n");
    return 0;
};

/*
// Note :
// The preprocessor replaces the line #include <stdio.h> with the text of the file 'stdio.h',
// which declares the printf() function among other things.
*/

```

###### Recursion
```c

// Representation factorial number with looping

int loop_factorial(int i) {

     int result = 1;

    while (i > 1) {
        
        result = result * i--;
    };

    return result;
};

```

```c

/* Head Recursive */

#include <stdio.h>

int head_recursive_factorial(int i);

int main()
{

    printf("%i", head_recursive_factorial(5));			//Output : 120
    return 0;
};

int head_recursive_factorial(int i) {

    if (i > 1) {
    
        return i * head_recursive_factorial(i - 1);
    };
    
    return 1;
};

```

```c

/* Tail Recursive */

#include <stdio.h>

int tail_recursive_factorial(int i);

int main()
{

    printf("%i", tail_recursive_factorial(5));			//Output : 120
    return 0;
};

int tail_recursive_factorial(int i) {

    if (i == 1) {
    
        return 1;
    };
    
    return i * tail_recursive_factorial(i - 1);
};

```

###### Evaluation Strategy
```c

/* Call by Value */

#include <stdio.h>

void swap_number(int x, int y);

int main()
{
    int n0 = 0, n1 = 1;
    
    printf("%i & %i \n", n0, n1);				//Output : 0 1
    swap_number(n0, n1);					//Output : 1 0
    printf("%i & %i \n", n0, n1);				//Output : 0 1
    
    return 0;
};

void swap_number(int x, int y) {
    
    int temp = x;
    x = y;
    y = temp;
    
    printf("%i & %i \n", x, y);
};

		//Memory Layout

			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0005 [n0 = s0x0001]		//	s0x0005 []
		//	v0x0004 [n1 = s0x0002]		//	s0x0004 []
		//	v0x0003 []			//	s0x0003 []
		//	v0x0002 []			//	s0x0002 [1]
		//	v0x0001 []			//	s0x0001 [0]
		// --------------------- //		// --------------------- //
		
		/*after do swap_number(n0, n1); => @param x=n0; @param y=n1;*/
		
			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0005 [n0 = s0x0001]		//	s0x0005 [1]		// Duplicate value from (s0x0002)
		//	v0x0004 [n1 = s0x0002]		//	s0x0004 [0]		// Duplicate value from (s0x0001)
		//	v0x0003 []			//	s0x0003 []
		//	v0x0002 [x = s0x0004]		//	s0x0002 [1]
		//	v0x0001 [y = s0x0005]		//	s0x0001 [0]
		// --------------------- //		// --------------------- //

```

```c

/* Call by Reference */

#include <stdio.h>

void swap_number(int *x, int *y);

int main()
{
    int n0 = 0, n1 = 1;
    
    printf("%i & %i \n", n0, n1);				//Output : 0 1
    swap_number(&n0, &n1);					//Output : 1 0
    printf("%i & %i \n", n0, n1);				//Output : 1 0
    
    return 0;
};

void swap_number(int *x, int *y) {
    
    int temp;
    temp = *x;
    *x = *y;
    *y = temp;
    
    printf("%i & %i \n", *x, *y);
};

		//Memory Layout

			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0005 [n0 = s0x0001]		//	s0x0005 []
		//	v0x0004 [n1 = s0x0002]		//	s0x0004 []
		//	v0x0003 []			//	s0x0003 []
		//	v0x0002 []			//	s0x0002 [1]
		//	v0x0001 []			//	s0x0001 [0]
		// --------------------- //		// --------------------- //
		
		/*after do swap_number(&n0, &n1); => @param *x=&n0; @param *y=&n1;*/
		
			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0005 [n0 = s0x0001]		//	s0x0005 [s0x0002]
		//	v0x0004 [n1 = s0x0002]		//	s0x0004 [s0x0001]
		//	v0x0003 []			//	s0x0003 []
		//	v0x0002 [*x = s0x0004]		//	s0x0002 [1]
		//	v0x0001 [*y = s0x0005]		//	s0x0001 [0]
		// --------------------- //		// --------------------- //

```

```c

/* Call by Copy Restore */

#include <stdio.h>

void swap_number(int *x, int *y);

int main()
{
    int n0 = 0, n1 = 1;
    
    printf("%i & %i \n", n0, n1);               //Output : 0 1
    // -------------------------------------------------------
    //Copy phase
    int new_n0 = n0;
    int new_n1 = n1;
    // -------------------------------------------------------
    swap_number(&new_n0, &new_n1);              //Output : 1 0
    // -------------------------------------------------------
    //Restore phase
    n0 = new_n0;
    n1 = new_n1;
    // -------------------------------------------------------
    printf("%i & %i \n", n0, n1);               //Output : 1 0
    
    return 0;
};

void swap_number(int *x, int *y) {
    
    int temp;
    temp = *x;
    *x = *y;
    *y = temp;
    
    printf("%i & %i \n", *x, *y);
};

		//Memory Layout

		//Copy-Phase
		
			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0006 [n0 = s0x0001]		//	s0x0006 []
		//	v0x0005 [n1 = s0x0002]		//	s0x0005 []
		//	v0x0004 [new_n0 = s0x0003]	//	s0x0004 [1]		// Duplicate value from (s0x0002)
		//	v0x0003 [new_n1 = s0x0004]	//	s0x0003 [0]		// Duplicate value from (s0x0001)
		//	v0x0002 []			//	s0x0002 [1]
		//	v0x0001 []			//	s0x0001 [0]
		// --------------------- //		// --------------------- //
		
		/*after do swap_number(&new_n0, &new_n1); => @param *x=&new_n0; @param *y=&new_n1;*/
		
			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0006 [n0 = s0x0001]		//	s0x0006 [s0x0004]
		//	v0x0005 [n1 = s0x0002]		//	s0x0005 [s0x0003]
		//	v0x0004 [new_n0 = s0x0003]	//	s0x0004 [1]		// Duplicate value from (s0x0002)
		//	v0x0003 [new_n1 = s0x0004]	//	s0x0003 [0]		// Duplicate value from (s0x0001)
		//	v0x0002 [*x = s0x0005]		//	s0x0002 [1]
		//	v0x0001 [*y = s0x0006]		//	s0x0001 [0]
		// --------------------- //		// --------------------- //
		
		//Restore-Phase
		
			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0006 [n0 = s0x0001]		//	s0x0006 [s0x0004]
		//	v0x0005 [n1 = s0x0002]		//	s0x0005 [s0x0003]
		//	v0x0004 [new_n0 = s0x0003]	//	s0x0004 [1]
		//	v0x0003 [new_n1 = s0x0004]	//	s0x0003 [0]
		//	v0x0002 [*x = s0x0005]		//	s0x0002 [1] 		//Changed to value of duplicate value from (s0x0003)
		//	v0x0001 [*y = s0x0006]		//	s0x0001 [0] 		//Changed to value of duplicate value from (s0x0004)
		// --------------------- //		// --------------------- //

```

```c

/* Call by Sharing, It's exactly same as Call by Reference */

#include <stdio.h>

void swap_number(int *x, int *y);

int main()
{
    int n0 = 0, n1 = 1;
    
    printf("%i & %i \n", n0, n1);				//Output : 0 1
    swap_number(&n0, &n1);					//Output : 1 0
    printf("%i & %i \n", n0, n1);				//Output : 1 0
    
    return 0;
};

void swap_number(int *x, int *y) {
    
    int temp;
    temp = *x;
    *x = *y;
    *y = temp;
    
    printf("%i & %i \n", *x, *y);
};

		//Memory Layout

			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0005 [n0 = s0x0001]		//	s0x0005 []
		//	v0x0004 [n1 = s0x0002]		//	s0x0004 []
		//	v0x0003 []			//	s0x0003 []
		//	v0x0002 []			//	s0x0002 [1]
		//	v0x0001 []			//	s0x0001 [0]
		// --------------------- //		// --------------------- //
		
		/*after do swap_number(&n0, &n1); => @param *x=&n0; @param *y=&n1;*/
		
			Virtual Memory				Stack Memory
		// --------------------- //		// --------------------- //
		//	v0x0005 [n0 = s0x0001]		//	s0x0005 [s0x0002]
		//	v0x0004 [n1 = s0x0002]		//	s0x0004 [s0x0001]
		//	v0x0003 []			//	s0x0003 []
		//	v0x0002 [*x = s0x0004]		//	s0x0002 [1]
		//	v0x0001 [*y = s0x0005]		//	s0x0001 [0]
		// --------------------- //		// --------------------- //

```
