---
title: Tablice — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e31cff94c51c626c4b8f0e08df270c45a9cc1316
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772098"
---
# <a name="arrays-c-programming-guide"></a>Tablice (Przewodnik programowania w języku C#)

Można przechowywać wiele zmiennych tego samego typu w strukturze danych tablicy. Należy zadeklarować tablicę, określając typ jej elementów. Jeśli chcesz, aby tablica była przechowywana elementów dowolnego typu, jako typ można określić `object`. W ujednoliconym systemie typów systemu C#, wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, typy odwołań i typy wartości, dziedziczą bezpośrednio lub pośrednio z <xref:System.Object>.

```csharp
type[] arrayName;
```

## <a name="example"></a>Przykład

Poniższy przykład tworzy tablice jednowymiarowe, wielowymiarowe i nieregularne:

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Przegląd tablicy

Tablica ma następujące właściwości:

- Tablica może być [Jednowymiarowa](single-dimensional-arrays.md), [wielowymiarowa](multidimensional-arrays.md) lub [nieregularna](jagged-arrays.md).
- Liczba wymiarów i długość każdego wymiaru są ustalane podczas tworzenia wystąpienia tablicy. Nie można zmienić tych wartości w okresie istnienia wystąpienia.
- Wartości domyślne elementów tablicy liczbowej są ustawiane na zero, a elementy odniesienia są ustawione na wartość null.
- Tablica nieregularna jest tablicą tablic, dlatego jej elementy są typami odwołań i są inicjowane do `null`.
- Tablice są indeksowane jako zero: tablica z elementami `n` jest indeksowana z `0` do `n-1`.
- Elementy tablicy mogą być dowolnego typu, łącznie z typem tablicowym.
- Typy tablic są [typami odwołań](../../language-reference/keywords/reference-types.md) pochodnymi od abstrakcyjnego typu podstawowego <xref:System.Array>. Ponieważ ten typ implementuje <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601>, można użyć iteracji [foreach](../../language-reference/keywords/foreach-in.md) dla wszystkich tablic w C#.

## <a name="related-sections"></a>Sekcje pokrewne

- [Użycie tablic jako obiektów](arrays-as-objects.md)
- [Używanie instrukcji foreach z tablicami](using-foreach-with-arrays.md)
- [Przekazywanie tablic jako argumentów](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Kolekcje](../concepts/collections.md)
