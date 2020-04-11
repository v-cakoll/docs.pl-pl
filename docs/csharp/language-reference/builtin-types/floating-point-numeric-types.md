---
title: Typy liczbowe zmiennoprzecinowe — odwołanie do języka C#
description: 'Dowiedz się więcej o wbudowanych typach zmiennoprzecinkowych języka C#: float, double i decimal'
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
ms.openlocfilehash: a277215d438b5f6b0bbbef72e5e0121b6ce41990
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121481"
---
# <a name="floating-point-numeric-types-c-reference"></a>Zmiennoprzecinowe typy liczbowe (odwołanie do języka C#)

*Typy liczbowe zmiennoprzecinkowe* reprezentują liczby rzeczywiste. Wszystkie typy liczbowe zmiennoprzecinkowe są [typami wartości](value-types.md). Są to również [proste typy](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literałów](#real-literals). Wszystkie typy liczbowe zmiennoprzecinkowe obsługują [operatory arytmetyczne,](../operators/arithmetic-operators.md) [porównawcze](../operators/comparison-operators.md)i [równościowe.](../operators/equality-operators.md)

## <a name="characteristics-of-the-floating-point-types"></a>Charakterystyka typów zmiennoprzecinkowych

C# obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:
  
|Typ/słowo kluczowe C#|Przybliżony zakres|Dokładność|Rozmiar|Typ .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1,5 x 10<sup>−45</sup> do ±3,4 x 10<sup>38</sup>|~6-9 cyfr|4 bajty|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5,0 × 10<sup>−324</sup> do ±1,7 × 10<sup>308</sup>|~15-17 cyfr|8 bajtów|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1,0 x 10<sup>-28</sup> do ±7,9228 x 10<sup>28</sup>|28-29 cyfr|16 bajtów|<xref:System.Decimal?displayProperty=nameWithType>|

W poprzedniej tabeli każde słowo kluczowe typu C# z lewej kolumny jest aliasem dla odpowiedniego typu .NET. Są wymienne. Na przykład następujące deklaracje deklarują zmienne tego samego typu:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Wartość domyślna każdego typu zmiennoprzecinkowego wynosi zero, `0`. Każdy z typów zmiennoprzecinkowych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość skończoną tego typu. I `float` `double` typy zapewniają również stałe, które reprezentują wartości nie-liczba i nieskończoności. Na przykład `double` typ zawiera następujące <xref:System.Double.NaN?displayProperty=nameWithType>stałe: <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>, i .

Ponieważ `decimal` typ ma większą precyzję i `float` `double`mniejszy zakres niż oba i , jest odpowiedni dla obliczeń finansowych i pieniężnych.

Można mieszać [typy integralne](integral-numeric-types.md) i `float` typy i `double` typy w wyrażeniu. W takim przypadku typy integralne są niejawnie konwertowane na `float` jeden z typów zmiennoprzecinkowych i, jeśli to konieczne, typ jest niejawnie konwertowany na `double`. Wyrażenie jest oceniane w następujący sposób:

- Jeśli istnieje `double` typ w wyrażeniu, `double`wyrażenie [`bool`](bool.md) ocenia do , lub w porównaniach relacyjnych i równości.
- Jeśli nie `double` ma żadnego typu w wyrażeniu, wyrażenie ocenia do `float`, lub `bool` w porównaniach relacyjnych i równości.

Można również mieszać typy integralne i `decimal` typ w wyrażeniu. W takim przypadku typy integralną są `decimal` niejawnie konwertowane na typ i wyrażenie ocenia do `decimal`, lub `bool` w porównaniach relacyjnych i równości.

Nie można `decimal` mieszać `float` typu `double` z i typów w wyrażeniu. W takim przypadku, jeśli chcesz wykonać operacje arytmetyczne, porównania lub równości, należy jawnie przekonwertować operandy z lub do `decimal` typu, jak pokazano w poniższym przykładzie:

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

Można użyć [standardowych ciągów formatu liczbowego](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu liczbowego](../../../standard/base-types/custom-numeric-format-strings.md) do formatowania wartości zmiennoprzecinkowej.

## <a name="real-literals"></a>Prawdziwe literały

Typ prawdziwego literału jest określany przez jego sufiks w następujący sposób:

- Literał bez przyrostka lub `d` z `D` przyrostkiem lub przyrostkiem jest typu`double`
- Literał z `f` lub `F` przyrostkiem jest typu`float`
- Literał z `m` lub `M` przyrostkiem jest typu`decimal`

Poniższy kod pokazuje przykład każdego z nich:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

W poprzednim przykładzie pokazano `_` również użycie jako *separator cyfry*, który jest obsługiwany począwszy od C# 7.0. Separatora cyfr można używać z wszelkiego rodzaju literałami liczbowymi.

Można również użyć notacji naukowej, czyli określić wykładniczą część rzeczywistego literału, jak pokazano w poniższym przykładzie:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Konwersje

Istnieje tylko jedna niejawna konwersja między `float` zmiennoprzecinkowymi typami liczbowymi: od do `double`. Można jednak przekonwertować dowolny typ zmiennoprzecinkowy na dowolny inny typ zmiennoprzecinkowy z [jawnym rzutowania](../operators/type-testing-and-cast.md#cast-expression). Aby uzyskać więcej informacji, zobacz [Wbudowane konwersje numeryczne](numeric-conversions.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Typy zmiennoprzecinowe](~/_csharplang/spec/types.md#floating-point-types)
- [Typ dziesiętny](~/_csharplang/spec/types.md#the-decimal-type)
- [Prawdziwe literały](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [Typy integralne](integral-numeric-types.md)
- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
