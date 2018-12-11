---
title: Używanie instrukcji foreach z tablicami - C# Programming Guide
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: a290cd709dd6491981658f467fa0163011290128
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238471"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Używanie instrukcji foreach z tablicami (C# Programming Guide)

[Foreach](../../language-reference/keywords/foreach-in.md) instrukcja oferuje prosty, jasny sposób iterowania po elementach tablicy.

Aby uzyskać tablice jednowymiarowe `foreach` instrukcji przetwarza elementy w kolejności rosnącej indeksu począwszy od indeksu 0, a kończąc na indeks `Length - 1`:

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

Dla wielowymiarowych tablic elementów jest przesunięta w taki sposób, że indeksy po prawej stronie wymiaru są pierwszy zwiększona, a następnie dalej wymiaru po lewej stronie, i tak dalej, aby po lewej stronie:

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

Jednak przy użyciu tablic wielowymiarowych użycie zagnieżdżonej [dla](../../language-reference/keywords/for.md) pętli daje większą kontrolę nad kolejność, w której ma być przetwarzane elementów tablicy.

## <a name="see-also"></a>Zobacz też

- <xref:System.Array>  
- [Przewodnik programowania w języku C#](../index.md)  
- [Tablice](index.md)  
- [Tablice jednowymiarowe](single-dimensional-arrays.md)  
- [Tablice wielowymiarowe](multidimensional-arrays.md)  
- [Tablice nieregularne](jagged-arrays.md)
