---
title: Typy ogólne i tablice (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 6cb205d90d4b6de329a179c5969e2d3b543bfb35
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528503"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="1b700-102">Typy ogólne i tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1b700-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="1b700-103">W języku C# w wersji 2.0 i nowszych wersjach, tablice jednowymiarowe, które mają automatycznie dolną granicę równą zero zaimplementować <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="1b700-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="1b700-104">Pozwala na tworzenie metod ogólnych, które można użyć tego samego kodu do iteracji i inne typy kolekcji tablic.</span><span class="sxs-lookup"><span data-stu-id="1b700-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="1b700-105">Ta technika jest szczególnie przydatne w przypadku odczytu danych w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="1b700-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="1b700-106"><xref:System.Collections.Generic.IList%601> Interfejsu nie może służyć do dodawania lub usuwania elementów z tablicy.</span><span class="sxs-lookup"><span data-stu-id="1b700-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="1b700-107">Wyjątek zostanie zgłoszony, jeśli zostanie podjęta próba wywołania <xref:System.Collections.Generic.IList%601> metody takie jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> w tablicy, w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="1b700-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="1b700-108">Poniższy przykład kodu demonstruje, jak pojedynczą ogólny metodę, która przyjmuje <xref:System.Collections.Generic.IList%601> parametr wejściowy można wykonać iterację tablicy i listy w tym przypadku tablicy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="1b700-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1b700-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b700-109">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="1b700-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1b700-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1b700-111">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="1b700-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
- [<span data-ttu-id="1b700-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="1b700-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="1b700-113">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="1b700-113">Generics</span></span>](~/docs/standard/generics/index.md)
