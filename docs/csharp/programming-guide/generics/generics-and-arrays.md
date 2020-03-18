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
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="86417-102">Typy ogólne i tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="86417-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="86417-103">W języku C# 2.0 i nowszych tablicjednowymiarowych, <xref:System.Collections.Generic.IList%601>które mają dolną granica zero automatycznie implementować .</span><span class="sxs-lookup"><span data-stu-id="86417-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="86417-104">Dzięki temu można utworzyć metody ogólne, które można użyć tego samego kodu do itetencji za pośrednictwem tablic i innych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="86417-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="86417-105">Ta technika jest przydatna przede wszystkim do odczytywania danych w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="86417-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="86417-106">Interfejs <xref:System.Collections.Generic.IList%601> nie może służyć do dodawania lub usuwania elementów z tablicy.</span><span class="sxs-lookup"><span data-stu-id="86417-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="86417-107">Wyjątek zostanie wygenerowany, jeśli spróbujesz wywołać <xref:System.Collections.Generic.IList%601> metodę, taką jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na tablicy w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="86417-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="86417-108">Poniższy przykład kodu pokazuje, jak pojedyncza <xref:System.Collections.Generic.IList%601> metoda ogólna, która przyjmuje parametr wejściowy może iterateć zarówno za pośrednictwem listy i tablicy, w tym przypadku tablicy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="86417-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="86417-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86417-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="86417-110">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="86417-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="86417-111">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="86417-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="86417-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="86417-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="86417-113">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="86417-113">Generics</span></span>](../../../standard/generics/index.md)
