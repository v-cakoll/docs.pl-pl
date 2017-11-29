---
title: "Porady: zapisywanie prostej pętli Parallel.ForEach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16d8cd3c3c01c2f9d83786e78f0eb1c45a38a49b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="64f48-102">Porady: zapisywanie prostej pętli Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="64f48-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="64f48-103">Ten przykład przedstawia sposób użycia <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli, aby włączyć równoległość danych przez żadnego <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych.</span><span class="sxs-lookup"><span data-stu-id="64f48-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64f48-104">Ta dokumentacja używa wyrażenia lambda, aby zdefiniować delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="64f48-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="64f48-105">Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="64f48-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64f48-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="64f48-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="64f48-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli działa jak <xref:System.Threading.Tasks.Parallel.For%2A> pętli.</span><span class="sxs-lookup"><span data-stu-id="64f48-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="64f48-108">Kolekcja źródłowa jest podzielona na partycje i pracy jest zaplanowane na wiele wątków, w zależności od środowiska systemu.</span><span class="sxs-lookup"><span data-stu-id="64f48-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="64f48-109">Więcej procesorów w systemie, tym szybciej równoległych metoda jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="64f48-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="64f48-110">Dla niektórych kolekcji źródłowej loop sekwencyjnych może być szybsze, w zależności od rozmiaru źródła i rodzaj wykonywanej pracy.</span><span class="sxs-lookup"><span data-stu-id="64f48-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="64f48-111">Aby uzyskać więcej informacji o wydajności, zobacz [potencjalne pułapki związane z Równoległością danych i zadań](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="64f48-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="64f48-112">Aby uzyskać więcej informacji na temat pętle równoległe, zobacz [porady: pisanie prostej równoległej pętli for](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="64f48-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="64f48-113">Aby użyć <xref:System.Threading.Tasks.Parallel.ForEach%2A> z kolekcja nierodzajową, możesz użyć <xref:System.Linq.Enumerable.Cast%2A> — metoda rozszerzenia do przekonwertowania kolekcji do kolekcji uniwersalnej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="64f48-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="64f48-114">Umożliwia także równoległe LINQ (PLINQ) do przetwarzania parallelize <xref:System.Collections.Generic.IEnumerable%601> źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="64f48-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="64f48-115">PLINQ pozwala na użycie składni zapytania deklaratywne Express zachowanie pętli.</span><span class="sxs-lookup"><span data-stu-id="64f48-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="64f48-116">Aby uzyskać więcej informacji, zobacz [równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="64f48-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="64f48-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="64f48-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="64f48-118">Skopiuj i wklej go w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="64f48-118">Copy and paste this code into a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="64f48-119">Dodaj odwołanie do System.Drawing.dll</span><span class="sxs-lookup"><span data-stu-id="64f48-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="64f48-120">Naciśnij klawisz F5</span><span class="sxs-lookup"><span data-stu-id="64f48-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f48-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64f48-121">See Also</span></span>  
 [<span data-ttu-id="64f48-122">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="64f48-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="64f48-123">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="64f48-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="64f48-124">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="64f48-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
