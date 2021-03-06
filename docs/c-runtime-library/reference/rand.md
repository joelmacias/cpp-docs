---
title: "rand | Microsoft Docs"
ms.custom: ""
ms.date: "1/02/2018"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-standard-libraries"]
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: ["rand"]
apilocation: ["msvcrt.dll", "msvcr80.dll", "msvcr90.dll", "msvcr100.dll", "msvcr100_clr0400.dll", "msvcr110.dll", "msvcr110_clr0400.dll", "msvcr120.dll", "msvcr120_clr0400.dll", "ucrtbase.dll", "api-ms-win-crt-utility-l1-1-0.dll"]
apitype: "DLLExport"
f1_keywords: ["rand"]
dev_langs: ["C++"]
helpviewer_keywords: ["generating pseudorandom numbers", "random numbers, generating", "numbers, pseudorandom", "rand function", "pseudorandom numbers", "numbers, generating pseudorandom"]
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
ms.workload: ["cplusplus"]
---
# rand

Generates a pseudorandom number by using a well-known and fully-reproducible algorithm. A more programmatically secure version of this function is available; see [rand_s](../../c-runtime-library/reference/rand-s.md). Numbers generated by `rand` are not cryptographically secure. For more cryptographically secure random number generation, use `rand_s` or the functions declared in the C++ Standard Library in [\<random>](../../standard-library/random.md).

## Syntax

```C
int rand( void );
```

## Return Value

`rand` returns a pseudorandom number, as described above. There is no error return.

## Remarks

The `rand` function returns a pseudorandom integer in the range 0 to `RAND_MAX` (32767). Use the [srand](../../c-runtime-library/reference/srand.md) function to seed the pseudorandom-number generator before calling `rand`.

The `rand` function generates a well-known sequence and is not appropriate for use as a cryptographic function. For more cryptographically secure random number generation, use `rand_s` or the functions declared in the C++ Standard Library in [\<random>](../../standard-library/random.md). For information about what's wrong with `rand()` and how `<random>` addresses these shortcomings, see [this video](http://go.microsoft.com/fwlink/?LinkId=397615).

## Requirements

|Routine|Required header|
|-------------|---------------------|
|`rand`|\<stdlib.h>|

For additional compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md) in the Introduction.

## Example

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
 3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## See also

[Floating-Point Support](../../c-runtime-library/floating-point-support.md)  
[srand](../../c-runtime-library/reference/srand.md)  
[rand_s](../../c-runtime-library/reference/rand-s.md)  