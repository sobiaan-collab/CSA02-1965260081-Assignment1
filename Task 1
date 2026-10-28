#include <stdio.h>

int main(void)
{
    int household_no, previous, current, units;
    long energy_charge, fixed_charge = 5000L, total;

    printf("Enter household number: ");
    scanf("%d", &household_no);

    printf("Enter previous reading: ");
    scanf("%d", &previous);

    printf("Enter current reading: ");
    scanf("%d", &current);

    if (current < previous || previous < 0)
    {
        printf("Invalid meter readings\n");
        return 1;
    }

    units = current - previous;

    if (units <= 100)
        energy_charge = 0;
    else if (units <= 200)
        energy_charge = (units - 100) * 225L;
    else
        energy_charge = 100 * 225L + (units - 200) * 450L;

    total = fixed_charge + energy_charge;

    printf("\nHousehold Number: %d\n", household_no);
    printf("Units Consumed: %d\n", units);
    printf("Energy Charge: Rs %ld.%02ld\n",
           energy_charge / 100, energy_charge % 100);
    printf("Fixed Charge: Rs 50.00\n");
    printf("Total Bill: Rs %ld.%02ld\n",
           total / 100, total % 100);

    return 0;
}
