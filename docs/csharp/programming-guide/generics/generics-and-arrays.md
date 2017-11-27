---
title: "Typy ogólne i tablice (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94b144075fac44ff749474a5bfa8e81aaadc0a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-arrays-c-programming-guide"></a>Typy ogólne i tablice (Przewodnik programowania w języku C#)
W języku C# 2.0 i nowszych tablice jednowymiarowe, które mają automatycznie dolna granica zero zaimplementować <xref:System.Collections.Generic.IList%601>. Dzięki temu można utworzyć metody ogólne, których można użyć tego samego kodu do iteracji i inne typy kolekcji tablic. Ta technika jest szczególnie przydatna do odczytywania danych w kolekcjach. <xref:System.Collections.Generic.IList%601> Interfejsu nie może służyć do dodawania lub usuwania elementów z tablicy. Zostanie wygenerowany wyjątek przy próbie wywołania <xref:System.Collections.Generic.IList%601> metody, takie jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na tablicy w tym kontekście.  
  
 Poniższy przykład kodu pokazuje sposób pojedynczej metody rodzajowy pobierający <xref:System.Collections.Generic.IList%601> parametru wejściowego można wykonać iterację zarówno lista i tablicy, w tym przypadku tablica liczb całkowitych.  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Typy ogólne](~/docs/standard/generics/index.md)
