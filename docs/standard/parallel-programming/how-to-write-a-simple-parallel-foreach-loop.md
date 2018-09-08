---
title: 'Porady: zapisywanie prostej pętli Parallel.ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03aaae7cd0faa7e7628da2e2e8f622f0967102cf
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205010"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="e1287-102">Porady: zapisywanie prostej pętli Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="e1287-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="e1287-103">W tym przykładzie pokazano, jak używać <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli, aby włączyć równoległość danych przez dowolny <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e1287-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1287-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="e1287-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="e1287-105">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="e1287-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1287-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1287-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="e1287-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli działa jak <xref:System.Threading.Tasks.Parallel.For%2A> pętli.</span><span class="sxs-lookup"><span data-stu-id="e1287-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="e1287-108">Kolekcja źródłowa jest podzielona na partycje, a praca jest zaplanowane na wiele wątków, w zależności od środowiska systemu.</span><span class="sxs-lookup"><span data-stu-id="e1287-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="e1287-109">Więcej procesorów w systemie, tym szybciej parallel — metoda jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="e1287-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="e1287-110">W niektórych kolekcjach źródła pętli sekwencyjnej może być szybciej, w zależności od rozmiaru źródła i rodzaju wykonywanych prac.</span><span class="sxs-lookup"><span data-stu-id="e1287-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="e1287-111">Aby uzyskać więcej informacji o wydajności, zobacz [potencjalne pułapki związane z Równoległością danych i zadań](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="e1287-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="e1287-112">Aby uzyskać więcej informacji na temat pętli równoległych zobacz [porady: zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="e1287-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="e1287-113">Aby użyć <xref:System.Threading.Tasks.Parallel.ForEach%2A> z nieogólna kolekcja, możesz użyć <xref:System.Linq.Enumerable.Cast%2A> metodę rozszerzenia, aby przekonwertować kolekcji do kolekcji ogólnej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e1287-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="e1287-114">Umożliwia także Parallel LINQ (PLINQ) do zrównoleglenia przetwarzania <xref:System.Collections.Generic.IEnumerable%601> źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="e1287-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="e1287-115">PLINQ umożliwia użycie składni zapytań deklaratywne określenie zachowania pętli.</span><span class="sxs-lookup"><span data-stu-id="e1287-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="e1287-116">Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e1287-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1287-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e1287-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="e1287-118">Skopiuj i wklej ten kod do projektu programu Visual Studio 2010 konsoli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1287-118">Copy and paste this code into a Visual Studio 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="e1287-119">Dodaj odwołanie do System.Drawing.dll</span><span class="sxs-lookup"><span data-stu-id="e1287-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="e1287-120">Naciśnij klawisz F5</span><span class="sxs-lookup"><span data-stu-id="e1287-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1287-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1287-121">See also</span></span>

- [<span data-ttu-id="e1287-122">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="e1287-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [<span data-ttu-id="e1287-123">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="e1287-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
- [<span data-ttu-id="e1287-124">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e1287-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
