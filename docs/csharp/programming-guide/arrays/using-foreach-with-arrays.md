---
title: Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: b858f35167e24390a729769487ce98908a3d349f
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)

[Foreach](../../language-reference/keywords/foreach-in.md) instrukcji umożliwia proste, czystej iterowania po elementach tablicy.

Dla tablice jednowymiarowe `foreach` instrukcji przetwarzania elementów w kolejności rosnącej indeksu z indeksem 0 i kończąc indeksu `Length - 1`:

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

Dla wielowymiarowych tablic elementów jest przesunięta w taki sposób, że indeksy po prawej stronie wymiaru są pierwszy zwiększona, a następnie dalej wymiaru po lewej stronie, i tak dalej do lewej strony:

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

Jednak za pomocą tablice wielowymiarowe przy użyciu zagnieżdżoną [dla](../../language-reference/keywords/for.md) pętli zapewnia większą kontrolę nad w kolejności przetwarzania elementów tablicy.

## <a name="see-also"></a>Zobacz także  
 <xref:System.Array>  
 [Przewodnik programowania w języku C#](../index.md)  
 [Tablice](index.md)  
 [Tablice jednowymiarowe](single-dimensional-arrays.md)  
 [Tablice wielowymiarowe](multidimensional-arrays.md)  
 [Tablice nieregularne](jagged-arrays.md)
