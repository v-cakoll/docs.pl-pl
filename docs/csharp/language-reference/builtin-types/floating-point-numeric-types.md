---
title: Typy liczbowe zmiennoprzecinkowe — C# odwołanie
description: Przegląd wbudowanych typów C# zmiennoprzecinkowych
ms.date: 06/30/2019
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
ms.openlocfilehash: 17ae154780679dd1f42f43f1ec345cdc722815d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002197"
---
# <a name="floating-point-numeric-types-c-reference"></a>Zmiennoprzecinkowe typy liczbowe (C# odwołanie)

**Typy zmiennoprzecinkowe** są podzbiorem **typów prostych** i mogą być inicjowane za pomocą [*literałów*](#floating-point-literals). Wszystkie typy zmiennoprzecinkowe są również typami wartości. Wszystkie zmiennoprzecinkowe typy liczbowe obsługują operatory [arytmetyczne](../operators/arithmetic-operators.md), [porównania i równości](../operators/equality-operators.md) .

## <a name="characteristics-of-the-floating-point-types"></a>Charakterystyki typów zmiennoprzecinkowych

C#obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:
  
|C#Type/słowo kluczowe|Przybliżony zakres|Dokładność|Rozmiar|Typ .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|± 1,5 x 10<sup>− 45</sup> do ± 3,4 x 10<sup>38</sup>|~ 6-9 cyfr|4 bajty|<xref:System.Single?displayProperty=nameWithType>|
|`double`|± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup>|~ 15-17 cyfr|8 bajtów|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|1,0 x 10<sup>-28</sup> do ± 7,9228 x 10<sup>28</sup>|28-29 cyfr|16 bajtów|<xref:System.Decimal?displayProperty=nameWithType>|

W powyższej tabeli każde C# słowo kluczowe type z lewej kolumny jest aliasem odpowiadającego typu .NET. Są one zamienne. Na przykład następujące deklaracje deklarują zmienne tego samego typu:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Wartość domyślna każdego typu zmiennoprzecinkowego wynosi zero, `0`. Każdy z typów zmiennoprzecinkowych ma stałe `MinValue` i `MaxValue`, które zapewniają minimalną i maksymalną skończoną wartość tego typu. Typy `float` i `double` zawierają również stałe, które reprezentują wartości nieliczbowe i nieskończone. Na przykład typ `double` zawiera następujące stałe: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Ponieważ typ `decimal` ma większą precyzję i mniejszy zakres niż `float` i `double`, jest to odpowiednie dla obliczeń finansowych i pieniężnych.

W wyrażeniu można mieszać typy [całkowite](integral-numeric-types.md) i typy zmiennoprzecinkowe. W takim przypadku typy całkowite są konwertowane na typy zmiennoprzecinkowe. Obliczanie wyrażenia jest wykonywane zgodnie z następującymi regułami:

- Jeśli jeden z typów zmiennoprzecinkowych ma wartość `double`, wyrażenie oblicza do `double` lub do wartości [logicznej](../keywords/bool.md) w porównaniach relacyjnych lub porównaniach dla równości.
- Jeśli w wyrażeniu nie ma żadnego typu `double`, wyrażenie zwróci wartość `float` lub do wartości [logicznej](../keywords/bool.md) w porównaniach relacyjnych lub porównaniach dla równości.

Wyrażenie zmiennoprzecinkowe może zawierać następujące zestawy wartości:

- Dodatnie i ujemne zero
- Dodatnia i ujemna nieskończoność
- Wartość niebędąca liczbą (NaN)
- Skończoną zbiór niezerowych wartości

Aby uzyskać więcej informacji na temat tych wartości, zobacz IEEE Standard for Binary-zmiennoprzecinkowej arytmetycznej, dostępny w witrynie sieci Web [IEEE](https://www.ieee.org) .

Aby sformatować wartość zmiennoprzecinkową, można użyć [standardowych ciągów formatu liczb](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu liczbowego](../../../standard/base-types/custom-numeric-format-strings.md) .

## <a name="floating-point-literals"></a>Literały zmiennoprzecinkowe

Domyślnie literał liczbowy zmiennoprzecinkowy po prawej stronie operatora przypisania jest traktowany jako `double`. Można użyć sufiksów do przekonwertowania literału zmiennoprzecinkowego lub całkowitego na określony typ:

- Sufiks `d` lub `D` konwertuje literał na `double`.
- Sufiks `f` lub `F` konwertuje literał na `float`.
- Sufiks `m` lub `M` konwertuje literał na `decimal`.

W poniższych przykładach pokazano każdy sufiks:

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Konwersje

Istnieje niejawna konwersja (nazywana *konwersją rozszerzającą*) z `float` do `double`, ponieważ zakres `float` wartości jest prawidłowym podzbiorem `double` i nie ma żadnej utraty dokładności od `float` do `double`.

Należy użyć jawnego rzutowania do przekonwertowania jednego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy, gdy niejawna konwersja nie jest zdefiniowana z typu źródłowego na typ docelowy. Jest to tzw. *Konwersja na wąskie*. Jawny przypadek jest wymagany, ponieważ konwersja może spowodować utratę danych. Nie istnieje niejawna konwersja między innymi typami zmiennoprzecinkowymi a typem `decimal`, ponieważ typ `decimal` ma większą precyzję niż `float` lub `double`.

Aby uzyskać więcej informacji na temat niejawnych konwersji liczbowych, zobacz [tabela niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md).

Aby uzyskać więcej informacji na temat jawnych konwersji liczbowych, zobacz [jawna tabela konwersji liczbowych](../keywords/explicit-numeric-conversions-table.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Typy całkowite](integral-numeric-types.md)
- [Tabela typów wbudowanych](../keywords/built-in-types-table.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
- [Rzutowanie i konwersje typów](../../programming-guide/types/casting-and-type-conversions.md)
- [Tabela niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Formatowanie tabeli wyników liczbowych](../keywords/formatting-numeric-results-table.md)
- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
