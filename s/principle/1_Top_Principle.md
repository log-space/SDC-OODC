<p align="right">
	<b>Top Principle</b>
</p>

<hr/>

###### Cohesion and Coupling

```c
// Cohesion

/*
 * Low Cohesion
 */

// Not all of subroutines use global variable
```

```c
/*
 * High Cohesion
 */

// Subroutines use 80% of global variable and subroutine is having strong relation and a part of file
```

```c
// Coupling

/*
 * Low Coupling
 */

#include <stdio.h>

int check_size();
int input_warning();

int input_data(check_size, input_warning) {

    FILE* file;
    
	if (file = fopen("index", "r")) {
	    
        fclose(file);
        return check_size;
    };
    
	return input_warning;
};

int save_data(check_size, input_warning) {

	return input_data(check_size, input_warning);
};

int main(void) {
	
	save_data(check_size(), input_warning());
	return 0;
};

int check_size() {
    
    return 1;
};

int input_warning() {
    
    printf("Warning...");
    return 0;
};
```

```c
/*
 * High Coupling
 */

#include <stdio.h>

int input_warning() {
    
    printf("Warning...");
    return 0;
};

int check_size() {
    
    return 1;
};

int input_data() {

    FILE * file;
    
	if (file = fopen("index", "r")) {
	    
        fclose(file);
        return check_size();
    };
    
	return input_warning();
};

int save_data() {

	return input_data();
};

int main(void) {

	save_data();
	return 0;
};
```

