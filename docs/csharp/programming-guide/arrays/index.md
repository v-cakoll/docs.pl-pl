---
title: Tablice — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 24c6d54c3fe92ada661e732adec582e87ab62417
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597530"
---
# <a name="arrays-c-programming-guide"></a>Tablice (Przewodnik programowania w języku C#)

Można przechowywać wiele zmiennych tego samego typu w strukturze danych tablicy. Należy zadeklarować tablicę, określając typ jej elementów.  
  
 `type[] arrayName;`  
  
 Poniższy przykład tworzy tablice jednowymiarowe, wielowymiarowe i nieregularne:  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a>Przegląd tablicy

 Tablica ma następujące właściwości:  
  
- Tablica może być Jednowymiarowa, wielowymiarowa lub nieregularna. [](./single-dimensional-arrays.md) [](./multidimensional-arrays.md) [](./jagged-arrays.md)  
  
- Liczba wymiarów i długość każdego wymiaru są ustalane podczas tworzenia wystąpienia tablicy. Nie można zmienić tych wartości w okresie istnienia wystąpienia.  
  
- Wartości domyślne elementów tablicy liczbowej są ustawiane na zero, a elementy odniesienia są ustawione na wartość null.  
  
- Tablica nieregularna jest tablicą tablic, dlatego jej elementy są typami odwołań i są inicjowane do `null`.  
  
- Tablice są indeksowane jako zero: tablica z `n` elementami jest indeksowana `0` z `n-1`do.  
  
- Elementy tablicy mogą być dowolnego typu, łącznie z typem tablicowym.  
  
- Typy tablic są [typami odwołań](../../language-reference/keywords/reference-types.md) pochodzącymi od abstrakcyjnego <xref:System.Array>typu podstawowego. Ponieważ ten typ implementuje <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601>, można użyć iteracji [foreach](../../language-reference/keywords/foreach-in.md) dla wszystkich tablic w C#.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
- [Użycie tablic jako obiektów](./arrays-as-objects.md)  
  
- [Używanie instrukcji foreach z tablicami](./using-foreach-with-arrays.md)  
  
- [Przekazywanie tablic jako argumentów](./passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Kolekcje](../concepts/collections.md)
