---
title: Równoległe LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c438170ec48f40e59f8710d4e3820d6e915bed5
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903830"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="21508-102">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="21508-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="21508-103">Równoległe LINQ (PLINQ) to implementacja przetwarzania równoległego LINQ do obiektów.</span><span class="sxs-lookup"><span data-stu-id="21508-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="21508-104">Pełny zestaw LINQ standardowych operatorów zapytań w PLINQ są implementowane jako metody rozszerzenia dla <xref:System.Linq> przestrzeni nazw i ma dodatkowe operatory operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="21508-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="21508-105">PLINQ łączy prostotę i czytelności składni LINQ, korzystając z możliwości programowania równoległego.</span><span class="sxs-lookup"><span data-stu-id="21508-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="21508-106">Podobnie jak kod przeznaczonego Biblioteka zadań równoległych, zapytania PLINQ skalować w stopień współbieżności oparta na funkcjach komputera-hosta.</span><span class="sxs-lookup"><span data-stu-id="21508-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="21508-107">W wielu scenariuszach PLINQ może znacznie zwiększyć szybkość LINQ do zapytań obiekt przy użyciu wszystkich dostępnych rdzeni na komputerze-hoście wydajniej.</span><span class="sxs-lookup"><span data-stu-id="21508-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="21508-108">To zwiększenie wydajności zapewnia moc obliczeniową o wysokiej wydajności na pulpit.</span><span class="sxs-lookup"><span data-stu-id="21508-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21508-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="21508-109">In This Section</span></span>  
 [<span data-ttu-id="21508-110">Wprowadzenie do PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="21508-111">Ogólne informacje o przyspieszeniach w PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="21508-112">Zachowywanie kolejności w PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="21508-113">Opcje scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="21508-114">Instrukcje: Tworzenie i wykonywanie prostych zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="21508-115">Instrukcje: Kontrolka szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="21508-116">Instrukcje: Łączenie równoległych i sekwencyjnych zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="21508-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="21508-117">Instrukcje: Obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="21508-118">Instrukcje: Anulowanie zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="21508-119">Instrukcje: Pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="21508-120">Instrukcje: Określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="21508-121">Instrukcje: Określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="21508-122">Instrukcje: Iteracja katalogów plików przy użyciu PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="21508-123">Instrukcje: Wydajności zapytań PLINQ miary</span><span class="sxs-lookup"><span data-stu-id="21508-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="21508-124">Próbka danych PLINQ</span><span class="sxs-lookup"><span data-stu-id="21508-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="21508-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21508-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="21508-126">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="21508-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="21508-127">Zapytanie o języku zintegrowanym (LINQ) —C#</span><span class="sxs-lookup"><span data-stu-id="21508-127">Language-Integrated Query (LINQ) - C#</span></span>](../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="21508-128">Zapytanie o języku zintegrowanym (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21508-128">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)  
