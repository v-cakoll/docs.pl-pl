---
title: Typy ogólne i tablice — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703016"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Typy ogólne i tablice (Przewodnik programowania w języku C#)
W C# 2,0 i nowszych tablicach jednowymiarowych, które mają dolną granicę zero, automatycznie implementują <xref:System.Collections.Generic.IList%601>. Dzięki temu można tworzyć metody ogólne, które mogą używać tego samego kodu do iterowania za pomocą tablic i innych typów kolekcji. Ta technika jest szczególnie przydatna w przypadku odczytywania danych w kolekcjach. Interfejs <xref:System.Collections.Generic.IList%601> nie może być używany do dodawania lub usuwania elementów z tablicy. Wyjątek zostanie wygenerowany, jeśli spróbujesz wywołać metodę <xref:System.Collections.Generic.IList%601>, taką jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> w tablicy w tym kontekście.  
  
 Poniższy przykład kodu demonstruje, jak jedna metoda ogólna, która przyjmuje <xref:System.Collections.Generic.IList%601> parametr wejściowy, może wykonać iterację zarówno na liście, jak i w tablicy, w tym przypadku tablicą liczb całkowitych.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Typy ogólne](./index.md)
- [Tablice](../arrays/index.md)
- [Typy ogólne](../../../standard/generics/index.md)
