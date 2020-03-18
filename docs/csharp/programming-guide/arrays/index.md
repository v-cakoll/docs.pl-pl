---
title: Tablice — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715054"
---
# <a name="arrays-c-programming-guide"></a>Tablice (Przewodnik programowania w języku C#)

Wiele zmiennych tego samego typu można przechowywać w strukturze danych tablicowych. Tablica deklaruje, określając typ jej elementów. Jeśli macierz ma przechowywać elementy dowolnego typu, `object` można określić jako jej typ. W ujednoliconym systemie typów Języka C#wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, <xref:System.Object>typy odwołań i typy wartości dziedziczą bezpośrednio lub pośrednio z .

```csharp
type[] arrayName;
```

## <a name="example"></a>Przykład

Poniższy przykład tworzy tablice jednowymiarowe, wielowymiarowe i postrzępione:

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Omówienie tablicy

Tablica ma następujące właściwości:

- Tablica może być [jednowymiarowa,](single-dimensional-arrays.md) [wielowymiarowa](multidimensional-arrays.md) lub [postrzępiona.](jagged-arrays.md)
- Liczba wymiarów i długość każdego wymiaru są ustalane podczas tworzenia wystąpienia tablicy. Tych wartości nie można zmienić w okresie istnienia wystąpienia.
- Wartości domyślne liczbowych elementów tablicy są ustawione na zero, a elementy odwołania są ustawione na null.
- Postrzępiona tablica jest tablicą tablic i dlatego jej elementy `null`są typami odwołań i są inicjowane do .
- Tablice są zerowe: tablica z `n` elementami `0` `n-1`jest indeksowana od do .
- Elementy tablicy mogą być dowolnego typu, w tym typu tablicy.
- Typy tablic są [typami odwołań](../../language-reference/keywords/reference-types.md) <xref:System.Array>wywodzącymi się z abstrakcyjnego typu podstawowego . Ponieważ ten typ <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>implementuje i , można użyć [foreach](../../language-reference/keywords/foreach-in.md) iteracji na wszystkich tablicach w języku C#.

## <a name="related-sections"></a>Sekcje pokrewne

- [Użycie tablic jako obiektów](arrays-as-objects.md)
- [Używanie instrukcji foreach z tablicami](using-foreach-with-arrays.md)
- [Przekazywanie tablic jako argumentów](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Kolekcje](../concepts/collections.md)
