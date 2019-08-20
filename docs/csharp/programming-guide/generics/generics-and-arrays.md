---
title: Typy ogólne i tablice — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f5b82d470f728129fc76851bc2708e20085d5326
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589678"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="8ac78-102">Typy ogólne i tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8ac78-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="8ac78-103">W C# 2,0 i nowszych tablicach jednowymiarowych, które mają dolną granicę zero, <xref:System.Collections.Generic.IList%601>są implementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="8ac78-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="8ac78-104">Dzięki temu można tworzyć metody ogólne, które mogą używać tego samego kodu do iterowania za pomocą tablic i innych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8ac78-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="8ac78-105">Ta technika jest szczególnie przydatna w przypadku odczytywania danych w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="8ac78-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="8ac78-106">Nie można użyć interfejsu do dodawania lub usuwania elementów z tablicy. <xref:System.Collections.Generic.IList%601></span><span class="sxs-lookup"><span data-stu-id="8ac78-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="8ac78-107">Wyjątek zostanie wygenerowany w przypadku próby wywołania <xref:System.Collections.Generic.IList%601> metody, takiej jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> w przypadku tablicy w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="8ac78-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="8ac78-108">Poniższy przykład kodu demonstruje, jak pojedyncza Metoda ogólna pobierająca <xref:System.Collections.Generic.IList%601> parametr wejściowy może wykonywać iterację zarówno na liście, jak i w tablicy, w tym przypadku tablicą liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="8ac78-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="8ac78-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ac78-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="8ac78-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8ac78-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8ac78-111">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="8ac78-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="8ac78-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="8ac78-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="8ac78-113">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="8ac78-113">Generics</span></span>](~/docs/standard/generics/index.md)
