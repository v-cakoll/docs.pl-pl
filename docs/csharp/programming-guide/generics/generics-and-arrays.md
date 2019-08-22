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
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="128df-102">Typy ogólne i tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="128df-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="128df-103">W C# 2,0 i nowszych tablicach jednowymiarowych, które mają dolną granicę zero, <xref:System.Collections.Generic.IList%601>są implementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="128df-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="128df-104">Dzięki temu można tworzyć metody ogólne, które mogą używać tego samego kodu do iterowania za pomocą tablic i innych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="128df-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="128df-105">Ta technika jest szczególnie przydatna w przypadku odczytywania danych w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="128df-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="128df-106">Nie można użyć interfejsu do dodawania lub usuwania elementów z tablicy. <xref:System.Collections.Generic.IList%601></span><span class="sxs-lookup"><span data-stu-id="128df-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="128df-107">Wyjątek zostanie wygenerowany w przypadku próby wywołania <xref:System.Collections.Generic.IList%601> metody, takiej jak <xref:System.Collections.Generic.IList%601.RemoveAt%2A> w przypadku tablicy w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="128df-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="128df-108">Poniższy przykład kodu demonstruje, jak pojedyncza Metoda ogólna pobierająca <xref:System.Collections.Generic.IList%601> parametr wejściowy może wykonywać iterację zarówno na liście, jak i w tablicy, w tym przypadku tablicą liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="128df-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="128df-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="128df-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="128df-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="128df-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="128df-111">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="128df-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="128df-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="128df-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="128df-113">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="128df-113">Generics</span></span>](../../../standard/generics/index.md)
