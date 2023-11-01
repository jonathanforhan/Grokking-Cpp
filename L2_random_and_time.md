# Lesson 2 Random and Time

It's useful when programming to obtain a psuedo-random number. This is bulit into the cstdlib. The function ```rand()``` will return a psuedo random number, **however** the random number will be the same every time you run your program. To solve with we need to ***seed*** the random number (think minecraft seed). We must use ```srand(unsigned)``` to seed the random number. We need a different seed every time our program runs. For that it is very common to use the current ```time(time_t*)```. Here is an example

```C
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    time_t t;           // declare a time variable
    srand(time(&t));    // seed the srand() with the current time since epoch

    printf("Random Number between 0-99: %d\n", rand() % 100);
}
```
