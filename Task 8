#include <stdio.h>

#define MESSAGE "Electricity Billing System"

int main(void)
{
    int units = 150;
    long energy_charge = (long)(units - 100) * 225L;
    long fixed_charge = 5000L;
    long total = fixed_charge + energy_charge;

    printf("%s\n", MESSAGE);
    printf("Units consumed: %d\n", units);
    printf("Energy charge: Rs %ld.%02ld\n",
           energy_charge / 100, energy_charge % 100);
    printf("Total bill: Rs %ld.%02ld\n",
           total / 100, total % 100);

    return 0;
}
