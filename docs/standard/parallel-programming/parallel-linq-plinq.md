---
title: "Równoległe LINQ (PLINQ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0028d3d8c30bbc7f0592a4462ca1eeb80c8b1f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="6e0fb-102">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="6e0fb-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="6e0fb-103">Równoległe LINQ (PLINQ) to implementacja równoległe LINQ do obiektów.</span><span class="sxs-lookup"><span data-stu-id="6e0fb-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="6e0fb-104">PLINQ implementuje pełnego zestawu LINQ standardowych operatorów zapytań jako metody rozszerzenia dla <xref:System.Linq> przestrzeni nazw i ma dodatkowe operatory dla operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="6e0fb-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="6e0fb-105">PLINQ łączy prostotę i czytelność składni LINQ dzięki możliwościom Programowanie równoległe.</span><span class="sxs-lookup"><span data-stu-id="6e0fb-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="6e0fb-106">Podobnie jak kod którego element docelowy Biblioteka zadań równoległych, zapytania dotyczące technologii PLINQ skalować stopień współbieżności oparta na funkcjach komputera-hosta.</span><span class="sxs-lookup"><span data-stu-id="6e0fb-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="6e0fb-107">W wielu scenariuszach PLINQ może znacznie zwiększyć szybkość LINQ do obiektów zapytania przy użyciu wszystkie dostępne rdzenie wydajniej na komputerze hosta.</span><span class="sxs-lookup"><span data-stu-id="6e0fb-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="6e0fb-108">To zwiększenie wydajności zapewnia wysoką wydajność mocy obliczeniowej na pulpit.</span><span class="sxs-lookup"><span data-stu-id="6e0fb-108">This increased performance brings high performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e0fb-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6e0fb-109">In This Section</span></span>  
 [<span data-ttu-id="6e0fb-110">Wprowadzenie do PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="6e0fb-111">Informacje o przyspieszeniach w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="6e0fb-112">Zamawianie zachowywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="6e0fb-113">Opcje scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="6e0fb-114">Porady: tworzenie i wykonywanie prostych zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="6e0fb-115">Porady: Sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="6e0fb-116">Porady: łączenie równoległych i sekwencyjnych zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="6e0fb-117">Porady: obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="6e0fb-118">Porady: Anulowanie zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="6e0fb-119">Porady: pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="6e0fb-120">Porady: Określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="6e0fb-121">Porady: Określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="6e0fb-122">Porady: iteracja po katalogach plików z wykorzystaniem technologii PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="6e0fb-123">Porady: mierzenie wydajności zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="6e0fb-124">Próbka danych PLINQ</span><span class="sxs-lookup"><span data-stu-id="6e0fb-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="6e0fb-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e0fb-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="6e0fb-126">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="6e0fb-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="6e0fb-127">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="6e0fb-127">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
