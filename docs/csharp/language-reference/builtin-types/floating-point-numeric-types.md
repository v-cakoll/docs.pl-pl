---
title: Zmiennoprzecinkowe typy liczbowe - C# odwołania
description: Omówienie języka C# zmiennoprzecinkowych typów wbudowanych
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
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664207"
---
# <a name="floating-point-numeric-types-c-reference"></a>Zmiennoprzecinkowe typy liczbowe (C# odwołania)

**Typów zmiennoprzecinkowych** stanowią podzestaw **typów prostych** i mogą być zainicjowane z [ *literały*](#floating-point-literals). Wszystkie typy zmiennoprzecinkowe są również typy wartości. Obsługa wszystkich typów liczbowych zmiennoprzecinkowych [arytmetyczne](../operators/arithmetic-operators.md) [porównania i równości](../operators/equality-operators.md) operatorów.

W poniższej tabeli przedstawiono dokładności i przybliżonej zakresy dla typów zmiennoprzecinkowych:
  
|Typ|Przybliżony zakres|Dokładność|  
|----------|-----------------------|---------------|  
|`float`|±1.5 x 10<sup>−45</sup> do ±3.4 x 10<sup>38</sup>|~ 6 – 9 cyfr|  
|`double`|±5.0 x 10<sup>−324</sup> do ±1.7 x 10<sup>308</sup>|około 15 – 17 cyfr|  
|`decimal`|±1.0 x 10<sup>-28</sup> do ±7.9228 x 10<sup>28</sup>|28 – 29 cyfr|  

Jest wartością domyślną dla wszystkich typów zmiennoprzecinkowych `0`. Każdy z typów zmiennoprzecinkowych ma nazwanych stałych `MinValue` i `MaxValue` minimalne i maksymalne wartości dla tego typu. `float` i `double` typy mają dodatkowe stałe dla `PositiveInfinity`, `NegativeInfinity`, i `NaN` (w przypadku "nie Number"). `decimal` Typu zawiera stałe dla `Zero`, `One`, i `MinusOne`.

`decimal` Typ ma większą dokładność i mniejszy zakres niż zarówno `float` i `double`, co czyni go odpowiedni do obliczeń finansowych i walutowych.

Można łączyć typów całkowitych i zmiennoprzecinkowych w wyrażeniu. W tym przypadku typów całkowitych są konwertowane do typów zmiennoprzecinkowych. Obliczania wyrażenia odbywa się zgodnie z następującymi zasadami:

- Po spełnieniu jednego z typów zmiennoprzecinkowych `double`, wyrażenie ma `double`, lub [bool](../keywords/bool.md) w porównania relacyjne i porównania dla równości.
- Jeśli ma nie `double` wpisz wyrażenie wyrażenie daje w wyniku `float`, lub [bool](../keywords/bool.md) w porównania relacyjne i porównania dla równości.

Wyrażenie typu zmiennoprzecinkowego może zawierać następujące zestawy wartości:

- Zero dodatnie i ujemne
- Dodatnie i ujemne nieskończoność.
- Wartość nie a liczbą (NaN)
- Ograniczone zbiór wartości wartość różną od zera

Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne zmiennopozycyjna operacje arytmetyczne, dostępne na [IEEE](https://www.ieee.org) witryny sieci Web.

Można użyć dowolnego [standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md) lub [ciągi niestandardowego formatu liczb](../../../standard/base-types/custom-numeric-format-strings.md) sformatować wartość zmiennoprzecinkową.

## <a name="floating-point-literals"></a>Literały zmiennoprzecinkowych

Domyślnie, literał liczbowy zmiennoprzecinkowych po prawej stronie operatora przypisania jest traktowany jako `double`. Sufiksy umożliwia konwertowanie zmiennoprzecinkowego lub całkowitego literał dla określonego typu:

- `d` Lub `D` sufiks konwertuje literału do `double`.
- `f` Lub `F` sufiks konwertuje literału do `float`.
- `m` Lub `M` sufiks konwertuje literału do `decimal`.

W poniższych przykładach pokazano każdego sufiksu:

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Konwersje

Istnieje niejawna konwersja (o nazwie *poszerzenie konwersji*) z `float` do `double` ponieważ zakres `float` wartości jest podzestawem odpowiednie `double` i bez utraty precyzji z `float` do `double`. 

Aby przekonwertować jednego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy, gdy niejawna konwersja nie jest zdefiniowana z typu źródłowego na typ docelowy należy użyć jawnego rzutowania. Jest to nazywane *konwersja zawężająca*. Jawne przypadek jest wymagana, ponieważ konwersja może spowodować utratę danych. Istnieje niejawna konwersja między innymi typami zmiennoprzecinkowymi a `decimal` typu, ponieważ `decimal` typ ma większą precyzję niż albo `float` lub `double`.

Aby uzyskać więcej informacji dotyczących niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).

Aby uzyskać więcej informacji dotyczących jawnych konwersji liczbowych, zobacz [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Typy całkowite](integral-numeric-types.md)
- [Tabela wartości domyślnych](../keywords/default-values-table.md)
- [Formatowanie tabeli wyników liczbowych](../keywords/formatting-numeric-results-table.md)
- [Tabela typów wbudowanych](../keywords/built-in-types-table.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
- [Rzutowanie i konwersje typów](../../programming-guide/types/casting-and-type-conversions.md)
- [Tabela niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
