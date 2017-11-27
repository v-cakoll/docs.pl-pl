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
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="52f2d-102">Typy ogólne i tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="52f2d-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="52f2d-103">W języku C# 2.0 i nowszych tablice jednowymiarowe, które mają automatycznie dolna granica zero zaimplementować <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="52f2d-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="52f2d-104">Dzięki temu można utworzyć metody ogólne, których można użyć tego samego kodu do iteracji i inne typy kolekcji tablic.</span><span class="sxs-lookup"><span data-stu-id="52f2d-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="52f2d-105">Ta technika jest szczególnie przydatna do odczytywania danych w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="52f2d-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="52f2d-106"><xref:System.Collections.Generic.IList%601> Interfejsu nie może służyć do dodawania lub usuwania elementów z tablicy.</span><span class="sxs-lookup"><span data-stu-id="52f2d-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="52f2d-107">Zostanie wygenerowany wyjątek przy próbie wywołania <xref:System.Collections.Generic.IList%601> metody, takie jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na tablicy w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="52f2d-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="52f2d-108">Poniższy przykład kodu pokazuje sposób pojedynczej metody rodzajowy pobierający <xref:System.Collections.Generic.IList%601> parametru wejściowego można wykonać iterację zarówno lista i tablicy, w tym przypadku tablica liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="52f2d-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="52f2d-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52f2d-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="52f2d-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="52f2d-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="52f2d-111">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="52f2d-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="52f2d-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="52f2d-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="52f2d-113">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="52f2d-113">Generics</span></span>](~/docs/standard/generics/index.md)
