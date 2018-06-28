---
title: float — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: 9500aceed62904e68d6b7ee8bec569d12103bb18
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028243"
---
# <a name="float-c-reference"></a>float (odwołanie w C#)

`float` — Słowo kluczowe oznacza typu prostego, która przechowuje 32-bitowych wartości zmiennoprzecinkowych. W poniższej tabeli przedstawiono dokładność i zakres przybliżonej `float` typu.

|Typ|Zakresie|Dokładność|Typ architektury .NET|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|-3,4 x 10<sup>38</sup> do + 3,4 x 10<sup>38</sup>|7 cyfr|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a>Literały

Domyślnie rzeczywistym literałem po prawej stronie operatora przypisania jest traktowany jako [podwójne](double.md). W związku z tym można zainicjować zmiennej typu float, używają sufiksu `f` lub `F`, jak w poniższym przykładzie:

```csharp
float x = 3.5F;
```

Jeśli nie używasz sufiks w poprzedniej deklaracji, otrzymasz błąd kompilacji, ponieważ chcesz przechowywać [podwójne](double.md) wartości do `float` zmiennej.

## <a name="conversions"></a>Konwersje

Można mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu. W takim przypadku typów całkowitych są konwertowane na typów zmiennoprzecinkowych. Obliczanie wyrażenia odbywa się zgodnie z następującymi zasadami:

- Po spełnieniu jednego z typów zmiennoprzecinkowych [podwójne](double.md), wyrażenie ma [podwójne](double.md) lub [bool](bool.md) w wyrażeniach relacyjnych lub Boolean.

- W przypadku nie [podwójne](double.md) typ w wyrażeniu wyrażenie daje w wyniku `float` lub [bool](bool.md) w wyrażeniach relacyjnych lub Boolean.

Zmiennoprzecinkowe wyrażenie może zawierać następujące zestawy wartości:

- Zero dodatnie i ujemne

- Dodatnie i ujemne infinity

- Wartość nie-liczby (NaN)

- Ograniczone zbiór niezerowe wartości

Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne Floating-Point operacje arytmetyczne, dostępnych na [IEEE](http://www.ieee.org) witryny sieci Web.

## <a name="example"></a>Przykład

W poniższym przykładzie [int](int.md), [krótki](short.md), a `float` są uwzględnione w wyrażeniu matematycznym nadanie `float` wynik. (Należy pamiętać, że `float` jest aliasem <xref:System.Single?displayProperty=nameWithType> typu.) Należy zauważyć, że istnieje nie [podwójne](double.md) w wyrażeniu.

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

<xref:System.Single>  
[Dokumentacja języka C#](../index.md)  
[Przewodnik programowania w języku C#](../../programming-guide/index.md)  
[Rzutowanie i konwersje typów](../../programming-guide/types/casting-and-type-conversions.md)  
[Słowa kluczowe języka C#](index.md)  
[Tabela typów całkowitych](integral-types-table.md)  
[Tabela typów wbudowanych](built-in-types-table.md)  
[Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)  
[Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)  