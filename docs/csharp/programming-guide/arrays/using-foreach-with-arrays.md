---
title: "Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
