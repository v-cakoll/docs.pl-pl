---
title: Typy liczbowe zmiennoprzecinkowe — C# odwołanie
description: 'Poznaj wbudowane typy C# zmiennoprzecinkowe: float, Double i Decimal'
ms.date: 02/10/2020
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 95b7f266654bbbcdcd0f81e3aa11cfc94af9f0e5
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215241"
---
# <a name="floating-point-numeric-types-c-reference"></a>Zmiennoprzecinkowe typy liczbowe (C# odwołanie)

*Typy liczbowe zmiennoprzecinkowe* reprezentują liczby rzeczywiste. Wszystkie zmiennoprzecinkowe typy liczbowe to [typy wartości](value-types.md). Są one również [typami prostymi](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literałów](#real-literals). Wszystkie zmiennoprzecinkowe typy liczbowe obsługują operatory [arytmetyczne](../operators/arithmetic-operators.md), [porównania](../operators/comparison-operators.md)i [równości](../operators/equality-operators.md) .

## <a name="characteristics-of-the-floating-point-types"></a>Charakterystyki typów zmiennoprzecinkowych

C#obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:
  
|C#Type/słowo kluczowe|Przybliżony zakres|Precyzja|Rozmiar|Typ .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|± 1,5 x 10<sup>− 45</sup> do ± 3,4 x 10<sup>38</sup>|~ 6-9 cyfr|4 bajty|<xref:System.Single?displayProperty=nameWithType>|
|`double`|± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup>|~ 15-17 cyfr|8 bajtów|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|1,0 x 10<sup>-28</sup> do ± 7,9228 x 10<sup>28</sup>|28-29 cyfr|16 bajtów|<xref:System.Decimal?displayProperty=nameWithType>|

W powyższej tabeli każde C# słowo kluczowe type z lewej kolumny jest aliasem odpowiadającego typu .NET. Są one zamienne. Na przykład następujące deklaracje deklarują zmienne tego samego typu:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Wartość domyślna każdego typu zmiennoprzecinkowego wynosi zero, `0`. Każdy z typów zmiennoprzecinkowych ma stałe `MinValue` i `MaxValue`, które zapewniają minimalną i maksymalną skończoną wartość tego typu. Typy `float` i `double` zawierają również stałe, które reprezentują wartości nieliczbowe i nieskończone. Na przykład typ `double` zapewnia następujące stałe: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Ponieważ typ `decimal` ma większą precyzję i mniejszy zakres niż `float` i `double`, jest on odpowiedni dla obliczeń finansowych i pieniężnych.

Można mieszać typy [całkowite](integral-numeric-types.md) oraz `float` i `double` typy w wyrażeniu. W takim przypadku typy całkowite są niejawnie konwertowane na jeden z typów zmiennoprzecinkowych i, w razie potrzeby, typ `float` jest niejawnie konwertowany na `double`. Wyrażenie jest oceniane w następujący sposób:

- Jeśli w wyrażeniu występuje `double`, wyrażenie oblicza `double`lub, aby [`bool`](bool.md) porównania relacyjne i równość.
- Jeśli w wyrażeniu nie ma `double` typu, wyrażenie oblicza `float`lub, aby `bool` porównania relacyjne i równość.

Można również mieszać typy całkowite i typ `decimal` w wyrażeniu. W takim przypadku typy całkowite są niejawnie konwertowane na typ `decimal`, a wyrażenie oblicza `decimal`lub do `bool` w porównaniach relacyjnych i równości.

Nie można mieszać typu `decimal` z typami `float` i `double` w wyrażeniu. W tym przypadku, jeśli chcesz wykonywać operacje arytmetyczne, porównania lub równości, musisz jawnie skonwertować operandy z lub do typu `decimal`, jak pokazano w poniższym przykładzie:

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

Aby sformatować wartość zmiennoprzecinkową, można użyć [standardowych ciągów formatu liczb](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu liczbowego](../../../standard/base-types/custom-numeric-format-strings.md) .

## <a name="real-literals"></a>Literały prawdziwe

Typ literału rzeczywistego jest określany na podstawie jego sufiksu w następujący sposób:

- Literał bez sufiksu lub z sufiksem `d` lub `D` jest typu `double`
- Literał z sufiksem `f` lub `F` jest typu `float`
- Literał z sufiksem `m` lub `M` jest typu `decimal`

Poniższy kod ilustruje przykład każdego z nich:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

W powyższym przykładzie przedstawiono również użycie `_` jako *separatora cyfr*, który jest obsługiwany od C# 7,0. Można użyć separatora cyfr z wszystkimi rodzajami literałów liczbowych.

Można również użyć notacji wykładniczej, czyli określić część wykładnika rzeczywistego literału, jak pokazano na poniższym przykładzie:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Konwersje

Istnieje tylko jedna niejawna konwersja między typami liczb zmiennoprzecinkowych: od `float` do `double`. Można jednak skonwertować dowolnego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy z [jawnym rzutem](../operators/type-testing-and-cast.md#cast-operator-). Aby uzyskać więcej informacji, zobacz [wbudowane konwersje numeryczne](numeric-conversions.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Typy zmiennoprzecinkowe](~/_csharplang/spec/types.md#floating-point-types)
- [Typ dziesiętny](~/_csharplang/spec/types.md#the-decimal-type)
- [Literały prawdziwe](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Typy wartości](value-types.md)
- [Typy całkowite](integral-numeric-types.md)
- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
