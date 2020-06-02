---
title: 'Instrukcje: Pisanie niestandardowej funkcji agregowania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 644d6b6f929e040a0fe688c18c774de6f434c4b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290775"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="d2a74-102">Instrukcje: Pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="d2a74-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="d2a74-103">Ten przykład pokazuje, jak używać <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metody do zastosowania niestandardowej funkcji agregacji do sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="d2a74-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d2a74-104">Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie.</span><span class="sxs-lookup"><span data-stu-id="d2a74-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="d2a74-105">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="d2a74-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2a74-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2a74-106">Example</span></span>  
 <span data-ttu-id="d2a74-107">Poniższy przykład oblicza odchylenie standardowe sekwencji liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d2a74-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="d2a74-108">W tym przykładzie użyto przeciążenia standardowego operatora kwerendy agregującej, który jest unikatowy dla PLINQ.</span><span class="sxs-lookup"><span data-stu-id="d2a74-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="d2a74-109">To Przeciążenie pobiera dodatkowy <xref:System.Func%603?displayProperty=nameWithType> jako trzeci parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="d2a74-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="d2a74-110">Ten delegat łączy wyniki ze wszystkich wątków przed wykonaniem obliczenia końcowego na zagregowanych wynikach.</span><span class="sxs-lookup"><span data-stu-id="d2a74-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="d2a74-111">W tym przykładzie dodamy razem kwoty ze wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="d2a74-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="d2a74-112">Należy zauważyć, że gdy treść wyrażenia lambda składa się z pojedynczego wyrażenia, wartość zwracana <xref:System.Func%602?displayProperty=nameWithType> delegata to wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d2a74-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a74-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2a74-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="d2a74-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d2a74-114">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
