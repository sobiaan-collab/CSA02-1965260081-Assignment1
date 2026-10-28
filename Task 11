#include <stdio.h>

int main()
{
    int units, slab1, slab2;
    int rate1, rate2, rate3;
    long fixed, energy = 0, total;
    FILE *fp;

    fp = fopen("tariff.txt", "r");

    if (fp == NULL)
    {
        printf("File not found!");
        return 1;
    }

    fscanf(fp, "%d %d %d %d %d %ld",
           &slab1, &slab2, &rate1, &rate2,
           &rate3, &fixed);

    fclose(fp);

    printf("Enter units consumed: ");
    scanf("%d", &units);

    if (units < 0)
    {
        printf("Invalid units!");
        return 1;
    }

    if (units > slab2)
    {
        energy += (long)(units - slab2) * rate3;
        units = slab2;
    }

    if (units > slab1)
    {
        energy += (long)(units - slab1) * rate2;
        units = slab1;
    }

    energy += (long)units * rate1;

    total = fixed + energy;

    printf("Energy Charge: Rs %ld.%02ld\n",
           energy / 100, energy % 100);

    printf("Total Bill: Rs %ld.%02ld\n",
           total / 100, total % 100);

    return 0;
}
