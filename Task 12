#include <stdio.h>
#include <limits.h>

#define INTERVALS_PER_DAY 96
#define DAYS_PER_YEAR 365

int main(void)
{
    long long total_wh = 0;
    long long peak_wh = 0;
    long long offpeak_wh = 0;
    long long energy_paise = 0;
    long long total_paise;
    long long previous_wh = 0;
    long long current_wh;
    long long interval_wh;
    long long units;
    long long peak_units;
    long long offpeak_units;

    int slab1, slab2, rate1, rate2, rate3;
    long fixed;
    int surcharge;
    int intervals = 0;
    int hour;

    FILE *file = fopen("smart_tariff.txt", "r");

    if (file == NULL)
    {
        printf("Cannot open smart_tariff.txt\n");
        return 1;
    }

    if (fscanf(file, "%d %d %d %d %d %ld %d",
               &slab1, &slab2, &rate1, &rate2,
               &rate3, &fixed, &surcharge) != 7)
    {
        printf("Invalid tariff configuration\n");
        fclose(file);
        return 1;
    }

    fclose(file);

    if (slab1 < 0 || slab2 < slab1 ||
        rate1 < 0 || rate2 < 0 || rate3 < 0 ||
        fixed < 0 || surcharge < 0)
    {
        printf("Invalid tariff values\n");
        return 1;
    }

    printf("Enter watt-hour readings for 15-minute intervals.\n");
    printf("Enter -1 to finish.\n");

    while (intervals < INTERVALS_PER_DAY * DAYS_PER_YEAR)
    {
        printf("Enter hour (0-23): ");

        if (scanf("%d", &hour) != 1 || hour < 0 || hour > 23)
        {
            printf("Invalid hour\n");
            return 1;
        }

        printf("Enter cumulative watt-hour reading: ");

        if (scanf("%lld", &current_wh) != 1 || current_wh < 0)
        {
            printf("Invalid reading\n");
            return 1;
        }

        if (current_wh < previous_wh)
        {
            printf("Reading decreased; rollover or meter reset needs handling.\n");
            return 1;
        }

        interval_wh = current_wh - previous_wh;
        previous_wh = current_wh;

        total_wh += interval_wh;

        if (hour >= 18 && hour < 22)
            peak_wh += interval_wh;
        else
            offpeak_wh += interval_wh;

        intervals++;

        if (intervals >= INTERVALS_PER_DAY * DAYS_PER_YEAR)
            break;

        printf("Continue? Enter 1 for yes, 0 for no: ");

        int choice;

        if (scanf("%d", &choice) != 1 || (choice != 0 && choice != 1))
        {
            printf("Invalid choice\n");
            return 1;
        }

        if (choice == 0)
            break;
    }

    peak_units = peak_wh / 1000;
    offpeak_units = offpeak_wh / 1000;
    units = total_wh / 1000;

    if (offpeak_units <= slab1)
    {
        energy_paise += offpeak_units * rate1;
    }
    else if (offpeak_units <= slab2)
    {
        energy_paise += (long long)slab1 * rate1;
        energy_paise += (offpeak_units - slab1) * rate2;
    }
    else
    {
        energy_paise += (long long)slab1 * rate1;
        energy_paise += (long long)(slab2 - slab1) * rate2;
        energy_paise += (offpeak_units - slab2) * rate3;
    }

    long long peak_charge = peak_units * rate3;
    peak_charge += peak_charge * surcharge / 100;

    energy_paise += peak_charge;
    total_paise = fixed + energy_paise;

    printf("\nTotal energy: %lld Wh\n", total_wh);
    printf("Total units (whole kWh): %lld\n", units);
    printf("Peak energy: %lld Wh\n", peak_wh);
    printf("Off-peak energy: %lld Wh\n", offpeak_wh);

    printf("Energy charge: Rs %lld.%02lld\n",
           energy_paise / 100, energy_paise % 100);

    printf("Fixed charge: Rs %ld.%02ld\n",
           fixed / 100, fixed % 100);

    printf("Total bill: Rs %lld.%02lld\n",
           total_paise / 100, total_paise % 100);

    return 0;
}
