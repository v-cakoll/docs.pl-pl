---
title: Typy ogólne i tablice — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: fee66cf7bd0ab3c051ea67acc323efa02a21a017
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659791"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Typy ogólne i tablice (Przewodnik programowania w języku C#)
W C# 2,0 i nowszych tablicach jednowymiarowych, które mają dolną granicę zero, <xref:System.Collections.Generic.IList%601>są implementowane automatycznie. Dzięki temu można tworzyć metody ogólne, które mogą używać tego samego kodu do iterowania za pomocą tablic i innych typów kolekcji. Ta technika jest szczególnie przydatna w przypadku odczytywania danych w kolekcjach. Nie można użyć interfejsu do dodawania lub usuwania elementów z tablicy. <xref:System.Collections.Generic.IList%601> Wyjątek zostanie wygenerowany w przypadku próby wywołania <xref:System.Collections.Generic.IList%601> metody, takiej jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> w przypadku tablicy w tym kontekście.  
  
 Poniższy przykład kodu demonstruje, jak pojedyncza Metoda ogólna pobierająca <xref:System.Collections.Generic.IList%601> parametr wejściowy może wykonywać iterację zarówno na liście, jak i w tablicy, w tym przypadku tablicą liczb całkowitych.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Typy ogólne](./index.md)
- [Tablice](../arrays/index.md)
- [Typy ogólne](../../../standard/generics/index.md)
