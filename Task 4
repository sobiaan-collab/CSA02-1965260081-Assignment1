#include <stdio.h>

#define RUPEES_TO_PAISE(x) ((long)(x) * 100L)
#define SQUARE(x) ((x) * (x))
#define MAX(a, b) ((a) > (b) ? (a) : (b))

static inline int square_function(int x)
{
    return x * x;
}

static inline int max_function(int a, int b)
{
    return (a > b) ? a : b;
}

int main(void)
{
    int a = 5, b = 10;

    printf("Rupees to paise: %ld\n", RUPEES_TO_PAISE(50));
    printf("Square of a+1: %d\n", SQUARE(a + 1));
    printf("Maximum: %d\n", MAX(a, b));
    printf("Square function: %d\n", square_function(a + 1));
    printf("Maximum function: %d\n", max_function(a, b));

    return 0;
}
