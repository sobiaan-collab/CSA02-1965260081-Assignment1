#include <stdio.h>

int main(void)
{
    int previous, current, units;
    long energy, total;

    printf("Enter previous reading: ");

    if (scanf("%d", &previous) != 1 || previous < 0)
    {
        printf("Invalid previous reading\n");
        return 1;
    }

    printf("Enter current reading: ");

    if (scanf("%d", &current) != 1 || current < previous)
    {
        printf("Invalid current reading\n");
        return 1;
    }

    units = current - previous;

    if (units <= 100)
        energy = 0;
    else if (units <= 200)
        energy = (long)(units - 100) * 225L;
    else
        energy = 100L * 225L + (long)(units - 200) * 450L;

    total = 5000L + energy;

    printf("Units consumed: %d\n", units);
    printf("Energy charge: Rs %ld.%02ld\n",
           energy / 100, energy % 100);
    printf("Total bill: Rs %ld.%02ld\n",
           total / 100, total % 100);

    return 0;
}
