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
ms.openlocfilehash: 98f89ba3d79f7679b69ce10fd875b3caf69c5257
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198364"
---
# <a name="float-c-reference"></a>float (odwołanie w C#)

`float` — Słowo kluczowe oznacza prosty typ, który przechowuje 32-bitowych wartości zmiennoprzecinkowych. W poniższej tabeli przedstawiono dokładności i przybliżony zakres `float` typu.

|Typ|Przybliżony zakres|Dokładność|Typ architektury .NET|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|±1.5 x 10<sup>−45</sup> do ±3.4 x 10<sup>38</sup>|7 cyfr|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a>Literały

Domyślnie, literał liczby rzeczywistej liczbowy po prawej stronie operatora przypisania jest traktowany jako [double](double.md). W związku z tym, aby zainicjalizować zmienną float, należy użyć sufiksu `f` lub `F`, jak w poniższym przykładzie:

```csharp
float x = 3.5F;
```

Jeśli nie używasz sufiks w poprzedniej deklaracji, otrzymasz błąd kompilacji, ponieważ użytkownik próbuje zapisać [double](double.md) wartością do `float` zmiennej.

## <a name="conversions"></a>Konwersje

Możesz mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu. W tym przypadku typów całkowitych są konwertowane do typów zmiennoprzecinkowych. Obliczania wyrażenia odbywa się zgodnie z następującymi zasadami:

- Po spełnieniu jednego z typów zmiennoprzecinkowych [double](double.md), wyrażenie ma [double](double.md), lub [bool](bool.md) w porównania relacyjne i porównania dla równości.

- W przypadku nie [double](double.md) wpisz wyrażenie wyrażenie daje w wyniku `float`, lub [bool](bool.md) w porównania relacyjne i porównania dla równości.

Wyrażenie typu zmiennoprzecinkowego może zawierać następujące zestawy wartości:

- Zero dodatnie i ujemne

- Dodatnie i ujemne nieskończoność.

- Wartość nie a liczbą (NaN)

- Ograniczone zbiór wartości wartość różną od zera

Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne zmiennopozycyjna operacje arytmetyczne, dostępne na [IEEE](http://www.ieee.org) witryny sieci Web.

## <a name="example"></a>Przykład

W poniższym przykładzie [int](int.md), [krótki](short.md), a `float` są zawarte w wyrażeniu matematycznym, zapewniając `float` wynik. (Należy pamiętać, że `float` jest aliasem dla <xref:System.Single?displayProperty=nameWithType> typu.) Zwróć uwagę, że ma nie [double](double.md) w wyrażeniu.

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Single>  
- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Rzutowanie i konwersje typów](../../programming-guide/types/casting-and-type-conversions.md)  
- [Słowa kluczowe języka C#](index.md)  
- [Tabela typów całkowitych](integral-types-table.md)  
- [Tabela typów wbudowanych](built-in-types-table.md)  
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)  
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)  