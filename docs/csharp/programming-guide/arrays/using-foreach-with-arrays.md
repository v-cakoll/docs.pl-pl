---
title: Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 8511d9dd3b7155d2f6bca229f264071b54ed173b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)
C# są także [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji. Ta instrukcja oferuje prosty, jasny sposób wykonywania iteracji elementów tablicy lub dowolnej kolekcji, którą można wyliczać. `foreach` Instrukcji przetwarzania elementów w kolejności zwrócony przez typ tablicy lub kolekcji moduł wyliczający, który zazwyczaj znajduje się w elemencie 0th do ostatniego. Na przykład poniższy kod tworzy tablicę `numbers` i iteruje go przy użyciu `foreach` instrukcji:  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 Tej samej metody można też używać do wykonywania iteracji elementów w tablicach wielowymiarowych, na przykład:  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 Jednak za pomocą tablice wielowymiarowe przy użyciu zagnieżdżoną [dla](../../../csharp/language-reference/keywords/for.md) pętli zapewnia większą kontrolę nad elementów tablicy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
