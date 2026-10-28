#include <stdio.h>

int main(void)
{
    int n;
    float float_total = 0.0f;
    long long paise_total = 0;

    printf("Enter number of bills: ");

    if (scanf("%d", &n) != 1 || n < 1)
    {
        printf("Invalid number of bills\n");
        return 1;
    }

    for (int i = 0; i < n; i++)
    {
        float_total += 162.50f;
        paise_total += 16250LL;
    }

    printf("Float total: Rs %.2f\n", float_total);
    printf("Integer-paise total: Rs %lld.%02lld\n",
           paise_total / 100, paise_total % 100);

    printf("Float storage: %zu bytes\n", sizeof(float));
    printf("Long long storage: %zu bytes\n", sizeof(long long));

    return 0;
}
