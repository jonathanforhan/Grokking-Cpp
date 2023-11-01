# Lesson 1 - Datatypes

## Datatypes

In C we have many stand datatypes. These datatypes represent some block of memory that we can write to. All datatypes have a size, in bytes that is the amount of memory that they can hold. The first datatype we will cover is the ```int```

an ```int``` is *typically* 32 bits, or 4 bytes. (on arduino I believe they are 16-bit). They ```int``` represents a 4 bytes chunk that can store values. ```int``` is signed so the least value will be -2^31 and the highest will be (2^31)-1 you can check this for yourself! The cstdlib provide macros that tell use the minimum and maximum values of int. Compile this code to see:

```C
#include <stdio.h>
#include <limits.h> /* this header contains the INT_MIN and INT_MAX defines */

int main(void) {
    printf("The lowest int value is: %d, and the highest is: %d\n", INT_MIN, INT_MAX);
    return 0;
}
```

this outputs:

```The lowest int value is: -2147483648, and the highest is: 2147483647\n```

this makes sense seeing as how -2147483648 is -2^31 and 2^31-1 is 2147483647

see what other types you can print, like 

``` LONG_MIN LLONG_MIN LONG_MAX LLONG_MAX UINT_MAX ULLONG_MAX```

**NOTE** you will need to change %d to %ll or %ull if you try to print the LLONG_* macros, this is because %d is for ints and the LLONG_MAX is too big to fit in the data type! (The U in these macros stand for unsigned)

what other datatypes are there?

1 byte signed - ```char```

1 byte unsigned - ```unsigned char```

4 bytes* signed - ```int```

4 bytes* unsigned - ```unsigned int```

4 bytes signed - ```long```

4 bytes unsigned - ```unsigned long```

8 bytes signed - ```long long```

8 bytes unsigned - ```unsigned long long```

4 byte floating point - ```float```

8 byte floating point - ```double```

\* the size of an int depends on the system. Int was typically a *WORD* size or the size that a CPU used but that has changed overtime (C is an OLD language). On desktops it is now 32 bits (same as a long) and we will cover how to deal with this inconsistancy later

## In practice

We will create a function that can now manipulate or datatypes. This is no trivial leap. We must cover now the anatomy of a function, the heart of C.

a C function has 3 parts:

- A return type

- A name

- Parameters

example:

```C
// the comment below is a *docstring* and it is a common programming practice
// to show the components of a function.
// This has no effect other than documentation of the function
/**
 * @name square
 * @param int x
 * @return int
 */
int square(int x) {
    return x * x;
}
```

this function takes 1 int and returns an int and the name is *square*

this that out of the way we can create a little more complicated function to show off our new knowledge of types and functions and now operations (like *)

```C
#include <math.h> /* gives use the sqrt() function (square root) */

// NOTE we use floats now
float square(float x) {
    return x * x;
}

float hypothenuse(float a, float b) {
    float c_squared = square(a) + square(b);
    float c = sqrt(c_squared);
    return c;
}
```

and as a whole program

```C
#include <stdio.h>
#include <math.h>

float square(float x) {
    return x * x;
}

float hypotenuse(float a, float b) {
    float c_squared = square(a) + square(b);
    float c = sqrt(c_squared);
    return c;
}

int main(void) {
    float a = 4;
    float b = 3;
    float c = hypotenuse(a, b);
    printf("A = %f, and B = %f, so C = %f\n", a, b, c);
    return 0;
}
```

note we get ```A = 4.000000, and B = 3.000000, so C = 5.000000``` because we have %f which prints floating points. Try printing them as ints
