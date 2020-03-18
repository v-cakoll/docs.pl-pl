---
title: Typy liczbowe zmiennoprzecinkowe — odwołanie do języka C#
description: 'Dowiedz się więcej o wbudowanych typach zmiennoprzecinkowych c#: float, double i decimal'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77215241"
---
# <a name="floating-point-numeric-types-c-reference"></a>Typy liczbowe zmiennoprzecinkowe (odwołanie do języka C#)

*Typy liczbowe zmiennoprzecinkowe* reprezentują liczby rzeczywiste. Wszystkie typy liczbowe zmiennoprzecinkowe są [typami wartości](value-types.md). Są one również [proste typy](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literału](#real-literals). Wszystkie typy liczbowe zmiennoprzecinkowe obsługują [operatory arytmetyczne,](../operators/arithmetic-operators.md) [porównywanie](../operators/comparison-operators.md)i [równość.](../operators/equality-operators.md)

## <a name="characteristics-of-the-floating-point-types"></a>Charakterystyka typów zmiennoprzecinkowych

C# obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:
  
|Typ/słowo kluczowe języka C#|Przybliżony zakres|Dokładność|Rozmiar|Typ .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1,5 x 10<sup>−45</sup> do ±3,4 x 10<sup>38</sup>|~6-9 cyfr|4 bajty|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5,0 × 10<sup>−324</sup> do ±1,7 × 10<sup>308</sup>|~15-17 cyfr|8 bajtów|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1,0 x 10<sup>-28</sup> do ±7,9228 x 10<sup>28</sup>|28-29 cyfr|16 bajtów|<xref:System.Decimal?displayProperty=nameWithType>|

W powyższej tabeli każde słowo kluczowe typu C# z kolumny po lewej stronie jest aliasem dla odpowiedniego typu .NET. Są wymienne. Na przykład następujące deklaracje deklarują zmienne tego samego typu:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Domyślną wartością każdego typu zmiennoprzecinkowego jest zero, `0`. Każdy z typów zmiennoprzecinkowych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość skończoną tego typu. I `float` `double` typy zapewniają również stałe, które reprezentują nie-liczba i nieskończoność wartości. Na przykład `double` typ zawiera następujące <xref:System.Double.NaN?displayProperty=nameWithType>stałe: <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>, i .

Ponieważ `decimal` typ ma większą precyzję i `float` mniejszy `double`zakres niż oba i , jest odpowiedni do obliczeń finansowych i pieniężnych.

Można mieszać [typy całki](integral-numeric-types.md) i `float` typy i `double` w wyrażeniu. W takim przypadku typy całki są niejawnie konwertowane na jeden z `float` typów zmiennoprzecinkowych i, jeśli to konieczne, typ jest niejawnie konwertowany na `double`. Wyrażenie jest oceniane w następujący sposób:

- Jeśli w `double` wyrażeniu znajduje się `double`typ, [`bool`](bool.md) wyrażenie oblicza do , lub do w relacyjnych i równość porównań.
- Jeśli w `double` wyrażeniu nie ma żadnego `float`typu, `bool` wyrażenie oblicza do , lub do w relacyjnych i równość porównań.

Można również mieszać typy `decimal` całki i typ w wyrażeniu. W takim przypadku typy całki są `decimal` niejawnie konwertowane `decimal`na typ, a wyrażenie oblicza na , lub w `bool` porównaniach relacyjnych i równości.

Nie można `decimal` mieszać typu `float` `double` z i typów w wyrażeniu. W takim przypadku, jeśli chcesz wykonać operacje arytmetyczne, porównania lub równości, należy jawnie przekonwertować operandy z lub na `decimal` typ, jak pokazano w poniższym przykładzie:

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

Do formatowania wartości zmiennoprzecinkowej można użyć [standardowych ciągów formatu numerycznego](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu numerycznego.](../../../standard/base-types/custom-numeric-format-strings.md)

## <a name="real-literals"></a>Prawdziwe dosłowne

Typ rzeczywistego literału jest określany przez jego przyrostek w następujący sposób:

- Literał bez `d` sufiksu `D` lub z lub sufiksem jest typu`double`
- Literał z `f` `F` lub sufiksem jest typu`float`
- Literał z `m` `M` lub sufiksem jest typu`decimal`

Poniższy kod przedstawia przykład każdego z nich:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

W poprzednim przykładzie pokazano `_` również użycie jako *separatora cyfr*, który jest obsługiwany począwszy od Języka C# 7.0. Separatora cyfr można używać ze wszystkimi rodzajami literałów liczbowych.

Można również użyć notacji naukowej, czyli określić wykładniczą część prawdziwego literału, jak pokazano w poniższym przykładzie:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Konwersje

Istnieje tylko jedna niejawna konwersja między `float` typami liczbowymi zmiennoprzecinkowych: od do `double`. Można jednak przekonwertować dowolny typ zmiennoprzecinkowy na dowolny inny typ zmiennoprzecinkowy z [jawnym rzutem.](../operators/type-testing-and-cast.md#cast-operator-) Aby uzyskać więcej informacji, zobacz [Wbudowane konwersje liczbowe](numeric-conversions.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Typy zmiennoprzecinkowe](~/_csharplang/spec/types.md#floating-point-types)
- [Typ dziesiętny](~/_csharplang/spec/types.md#the-decimal-type)
- [Prawdziwe dosłowne](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [Typy całonowe](integral-numeric-types.md)
- [Standardowe ciągi formatu numerycznego](../../../standard/base-types/standard-numeric-format-strings.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
