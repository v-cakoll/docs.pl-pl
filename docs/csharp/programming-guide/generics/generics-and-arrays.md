---
title: Ogólne i tablice — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703016"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Typy ogólne i tablice (Przewodnik programowania w języku C#)
W języku C# 2.0 i nowszych tablicjednowymiarowych, <xref:System.Collections.Generic.IList%601>które mają dolną granica zero automatycznie implementować . Dzięki temu można utworzyć metody ogólne, które można użyć tego samego kodu do itetencji za pośrednictwem tablic i innych typów kolekcji. Ta technika jest przydatna przede wszystkim do odczytywania danych w kolekcjach. Interfejs <xref:System.Collections.Generic.IList%601> nie może służyć do dodawania lub usuwania elementów z tablicy. Wyjątek zostanie wygenerowany, jeśli spróbujesz wywołać <xref:System.Collections.Generic.IList%601> metodę, taką jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na tablicy w tym kontekście.  
  
 Poniższy przykład kodu pokazuje, jak pojedyncza <xref:System.Collections.Generic.IList%601> metoda ogólna, która przyjmuje parametr wejściowy może iterateć zarówno za pośrednictwem listy i tablicy, w tym przypadku tablicy liczb całkowitych.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania języka C#](../index.md)
- [Typy ogólne](./index.md)
- [Tablice](../arrays/index.md)
- [Typy ogólne](../../../standard/generics/index.md)
