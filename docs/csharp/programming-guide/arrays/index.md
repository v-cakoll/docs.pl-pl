---
title: Tablice (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d395bcb179650fe29ab0918e7f91f3c8b6197b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="arrays-c-programming-guide"></a>Tablice (Przewodnik programowania w języku C#)
W tablicy struktury danych można przechowywać wiele zmiennych tego samego typu. Można zadeklarować tablicy przez określenie typu elementów.  
  
 `type[] arrayName;`  
  
 Poniższe przykłady tworzenia tablice jednowymiarowe wielowymiarowe i nieregularne:  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a>Omówienie tablicy  
 Tablica ma następujące właściwości:  
  
-   Tablica może być [jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) lub [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
-   Liczba wymiarów i długość każdego wymiaru są wyznaczane podczas tworzenia wystąpienia tablicy. Nie można zmienić tych wartości przez cały okres istnienia wystąpienia.  
  
-   Domyślne wartości elementów tablicy liczbowych są ustawione na zero, a elementy odwołań są ustawione na wartość null.  
  
-   Nieregularna tablica jest tablicy tablic, a w związku z tym jej elementy są typy referencyjne i są inicjowane na `null`.  
  
-   Tablice są indeksowane zero: tablica o `n` elementów jest indeksowany z `0` do `n-1`.  
  
-   Elementy tablicy może być dowolnego typu, łącznie z typem tablicy.  
  
-   Typy tablicy są [typy referencyjne](../../../csharp/language-reference/keywords/reference-types.md) pochodzi od typu podstawowego abstrakcyjny <xref:System.Array>. Ponieważ ten typ implementuje <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601>, można użyć [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteracji wszystkich tablic w języku C#.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
-   [Użycie tablic jako obiektów](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [Używanie instrukcji foreach z tablicami](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [Przekazywanie tablic jako argumentów](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [Przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Kolekcje](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Typ kolekcji tablicy](http://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
