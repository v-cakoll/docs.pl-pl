---
title: Tablice — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 258ade63ab7c9008f6c892ed109bf5ea5ab974f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584604"
---
# <a name="arrays-c-programming-guide"></a>Tablice (Przewodnik programowania w języku C#)

W strukturze danych tablicy można przechowywać wiele zmiennych tego samego typu. Można zadeklarować tablicy, określając typ jej elementów.  
  
 `type[] arrayName;`  
  
 Poniższy przykład tworzy tablice jednowymiarowe, wielowymiarowe i nieregularne:  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a>Omówienie macierzy

 Tablica ma następujące właściwości:  
  
- Tablica może być [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) lub [poszarpana](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
- Liczba wymiarów i długość każdego wymiaru są określane podczas tworzenia instancji tabeli. Te wartości nie można zmienić w trakcie okresu istnienia wystąpienia.  
  
- Wartości domyślne elementów tablicy liczbowej są ustawiane na zero, a elementy odniesienia są ustawiane na wartość null.  
  
- Nieregularna tablica jest tablicy tablic, a zatem jej elementy są typami odwołań i są inicjowane na `null`.  
  
- Tablice są indeksowane zero: tablia z `n` elementami jest indeksowana z `0` do `n-1`.  
  
- Elementy tablicy mogą być dowolnego typu, w tym typu tablicowego.  
  
- Typy tablic mają [typy odwołań](../../../csharp/language-reference/keywords/reference-types.md) pochodzące z abstrakcyjnego typy podstawowego <xref:System.Array>. Ponieważ ten typ implementuje <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601>, możesz użyć [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteracji na wszystkich tablicach w C#.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
- [Użycie tablic jako obiektów](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
- [Używanie instrukcji foreach z tablicami](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
- [Przekazywanie tablic jako argumentów](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Kolekcje](../../../csharp/programming-guide/concepts/collections.md)
