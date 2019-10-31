---
title: Równoległe LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140038"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="6a0e9-102">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="6a0e9-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="6a0e9-103">Równoległe LINQ (PLINQ) to równoległa implementacja LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="6a0e9-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="6a0e9-104">PLINQ implementuje pełny zestaw standardowych operatorów zapytań LINQ jako metody rozszerzenia dla przestrzeni nazw <xref:System.Linq> i ma dodatkowe operatory dla operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="6a0e9-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="6a0e9-105">PLINQ łączy prostotę i czytelność składni LINQ z możliwością programowania równoległego.</span><span class="sxs-lookup"><span data-stu-id="6a0e9-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="6a0e9-106">Podobnie jak kod, który jest przeznaczony dla biblioteki równoległej zadania, PLINQ zapytania skalowanie w poziomie współbieżności w oparciu o możliwości komputera hosta.</span><span class="sxs-lookup"><span data-stu-id="6a0e9-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="6a0e9-107">W wielu scenariuszach PLINQ może znacząco zwiększyć szybkość zapytań LINQ to Objects przy użyciu wszystkich dostępnych rdzeni na komputerze hosta wydajniejszie.</span><span class="sxs-lookup"><span data-stu-id="6a0e9-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="6a0e9-108">Ta zwiększona wydajność zapewnia wysoką wydajność przetwarzania na komputerze stacjonarnym.</span><span class="sxs-lookup"><span data-stu-id="6a0e9-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a0e9-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6a0e9-109">In This Section</span></span>  
 [<span data-ttu-id="6a0e9-110">Wprowadzenie do PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="6a0e9-111">Ogólne informacje o przyspieszeniach w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="6a0e9-112">Zachowywanie kolejności w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="6a0e9-113">Opcje scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="6a0e9-114">Instrukcje: tworzenie i wykonywanie prostego zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="6a0e9-115">Instrukcje: sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="6a0e9-116">Instrukcje: łączenie równoległych i sekwencyjnych zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="6a0e9-117">Instrukcje: obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="6a0e9-118">Instrukcje: anulowanie zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="6a0e9-119">Instrukcje: pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="6a0e9-120">Instrukcje: określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="6a0e9-121">Instrukcje: określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="6a0e9-122">Instrukcje: iteracja katalogów plików przy użyciu technologii PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="6a0e9-123">Instrukcje: mierzenie wydajności zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="6a0e9-124">Próbka danych PLINQ</span><span class="sxs-lookup"><span data-stu-id="6a0e9-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a0e9-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a0e9-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="6a0e9-126">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="6a0e9-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="6a0e9-127">Language-Integrated Query (LINQ) —C#</span><span class="sxs-lookup"><span data-stu-id="6a0e9-127">Language-Integrated Query (LINQ) - C#</span></span>](../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="6a0e9-128">Zapytanie zintegrowane z językiem (LINQ) — Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a0e9-128">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)  
