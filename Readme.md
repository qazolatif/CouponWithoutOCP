# CouponWithoutOCP

Aplikasi ini merupakan console untuk mempelajari Open Closed Principle.
Aplikasi ini menerapkan Open Closed principle.

## Scope & Functionalities
* User dapat mempelajari abstraction.
* User dapat mempelajari penerapan polymorphism.
* User dapat mempelajari penerapan Open Closed principle.

## How does it works?
Pada class `Program.cs` terdapat kode berikut:
```C#
static void Main(string[] args)
        {
            Coupon coupon1 = new Coupon();
            coupon1.discNominal = 2000;
            Console.WriteLine(coupon1.priceNett(10000));

            Coupon coupon2 = new Coupon();
            coupon2.discPercentage = 15;
            Console.WriteLine(coupon2.priceNett(10000));

            Coupon coupon3 = new Coupon();
            coupon3.discPercentage = 90;
            coupon3.discNominal = 3000;
            Console.WriteLine(coupon3.priceNett(10000));
        }
```
Kode di atas digunakan untuk menjalankan aplikasi perhitungan kupon.

Kemudian pada class `Coupon.cs` terdapat kode-kode berikut:
```C#
public double priceNett(double originPrice)
        {
            double net = 0;
            if (discNominal == 0 && discPercentage > 0)
            {
                net = (100 - discPercentage) * originPrice / 100;
            }
            else if (discNominal > 0 && discPercentage == 0)
            {
                net = originPrice - discNominal;
            }
            else if (discNominal > 0 && discPercentage > 0)
            {
                net = originPrice - discNominal;
            }
            return net;
        }
```
Kode di atas berguna sebagai logika utama untuk perhitungan kupon.

```C#
if (discNominal == 0 && discPercentage > 0)
            {
                net = (100 - discPercentage) * originPrice / 100;
            }
```
Kode di atas merupakan logika yang digunakan ketika **discMinimal** sama dengan 0 dan **discPercentage** kurang dari 0.

```C#
else if (discNominal > 0 && discPercentage == 0)
            {
                net = originPrice - discNominal;
            }
```
Kode di atas merupakan logika yang digunakan ketika **discMinimal** lebih besar daripada 0 dan **discPercentage** sama dengan 0.

```C#
else if (discNominal > 0 && discPercentage > 0)
            {
                net = originPrice - (discNominal - (100 - discPercentage) * originPrice / 100);
            }
```
Kode di atas merupakan logika yang digunakan ketika **discMinimal** dan **discPercentage** lebih besar daripada 0.
