---
title: Typy ogólne i tablice - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 145203d259b943bea1f43a9e49db2c7889bf914a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978919"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Typy ogólne i tablice (Przewodnik programowania w języku C#)
W języku C# w wersji 2.0 i nowszych wersjach, tablice jednowymiarowe, które mają automatycznie dolną granicę równą zero zaimplementować <xref:System.Collections.Generic.IList%601>. Pozwala na tworzenie metod ogólnych, które można użyć tego samego kodu do iteracji i inne typy kolekcji tablic. Ta technika jest szczególnie przydatne w przypadku odczytu danych w kolekcjach. <xref:System.Collections.Generic.IList%601> Interfejsu nie może służyć do dodawania lub usuwania elementów z tablicy. Wyjątek zostanie zgłoszony, jeśli zostanie podjęta próba wywołania <xref:System.Collections.Generic.IList%601> metody takie jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> w tablicy, w tym kontekście.  
  
 Poniższy przykład kodu demonstruje, jak pojedynczą ogólny metodę, która przyjmuje <xref:System.Collections.Generic.IList%601> parametr wejściowy można wykonać iterację tablicy i listy w tym przypadku tablicy liczb całkowitych.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Typy ogólne](../../../csharp/programming-guide/generics/index.md)
- [Tablice](../../../csharp/programming-guide/arrays/index.md)
- [Typy ogólne](~/docs/standard/generics/index.md)
