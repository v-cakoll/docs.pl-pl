---
title: Double — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: f4d6bb4eb698e4afbda6571ba382e828a5f836a4
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424263"
---
# <a name="double-c-reference"></a>double (odwołanie w C#)

`double` — Słowo kluczowe oznacza prosty typ, który przechowuje 64-bitowych wartości zmiennoprzecinkowych. W poniższej tabeli przedstawiono dokładności i przybliżony zakres `double` typu.

|Typ|Przybliżony zakres|Dokładność|Typ architektury .NET|
|----------|-----------------------|---------------|-------------------------|
|`double`|±5.0 x 10<sup>−324</sup> do ±1.7 x 10<sup>308</sup>|około 15 – 17 cyfr|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

Domyślnie, literał liczby rzeczywistej liczbowy po prawej stronie operatora przypisania jest traktowany jako `double`. Jednakże jeśli mają być traktowane jako liczba całkowita z zakresu `double`, Użyj sufiksu d lub D, na przykład:

```csharp
double x = 3D;
```

## <a name="conversions"></a>Konwersje

Możesz mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu. W tym przypadku typów całkowitych są konwertowane do typów zmiennoprzecinkowych. Obliczania wyrażenia odbywa się zgodnie z następującymi zasadami:

- Po spełnieniu jednego z typów zmiennoprzecinkowych `double`, wyrażenie ma `double`, lub [bool](../../../csharp/language-reference/keywords/bool.md) porównania relacyjne i porównania dla równości.

- W przypadku nie `double` typ w wyrażeniu, był oceniany do [float](../../../csharp/language-reference/keywords/float.md), lub [bool](../../../csharp/language-reference/keywords/bool.md) porównania relacyjne i porównania dla równości.

 Wyrażenie typu zmiennoprzecinkowego może zawierać następujące zestawy wartości:

- Zero dodatnie i ujemne.

- Dodatnie i ujemne nieskończoność.

- Wartość nie a liczbą (NaN).

- Ograniczone zbiór wartości wartość różną od zera.

Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne zmiennopozycyjna operacje arytmetyczne, dostępne na [IEEE](https://www.ieee.org) witryny sieci Web.

## <a name="example"></a>Przykład

W poniższym przykładzie [int](../builtin-types/integral-numeric-types.md), [krótki](../../../csharp/language-reference/builtin-types/integral-numeric-types.md), [float](../../../csharp/language-reference/keywords/float.md), a `double` są dodawane, jednocześnie zapewniając `double` wynik.

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md)
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Tabela typów zmiennoprzecinkowych](../../../csharp/language-reference/keywords/floating-point-types-table.md)
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
