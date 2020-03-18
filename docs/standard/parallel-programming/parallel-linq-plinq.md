---
title: Równoległe LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140038"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="00384-102">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="00384-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="00384-103">Parallel LINQ (PLINQ) jest równoległą implementacją LINQ do obiektów.</span><span class="sxs-lookup"><span data-stu-id="00384-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="00384-104">PLINQ implementuje pełny zestaw operatorów standardowych zapytań LINQ <xref:System.Linq> jako metody rozszerzenia dla obszaru nazw i ma dodatkowe operatory dla operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="00384-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="00384-105">PLINQ łączy prostotę i czytelność składni LINQ z mocą programowania równoległego.</span><span class="sxs-lookup"><span data-stu-id="00384-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="00384-106">Podobnie jak kod, który jest przeznaczony dla biblioteki równoległej zadania, kwerendy PLINQ są skalowane w stopniu współbieżności na podstawie możliwości komputera-hosta.</span><span class="sxs-lookup"><span data-stu-id="00384-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="00384-107">W wielu scenariuszach PLINQ może znacznie zwiększyć szybkość linq do obiektów zapytań przy użyciu wszystkich dostępnych rdzeni na komputerze hosta bardziej efektywnie.</span><span class="sxs-lookup"><span data-stu-id="00384-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="00384-108">Ta zwiększona wydajność zapewnia wysoką wydajność obliczeniową na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="00384-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00384-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="00384-109">In This Section</span></span>  
 [<span data-ttu-id="00384-110">Wprowadzenie do PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="00384-111">Ogólne informacje o przyspieszeniach w PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="00384-112">Zamawianie zachowywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="00384-113">Opcje scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="00384-114">Instrukcje: tworzenie i wykonywanie prostego zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="00384-115">Porady: sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="00384-116">Porady: łączenie równoległych i sekwencyjnych zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="00384-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="00384-117">Porady: obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="00384-118">Instrukcje: anulowanie zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="00384-119">Instrukcje: pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="00384-120">Instrukcje: określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="00384-121">Instrukcje: określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="00384-122">Instrukcje: iteracja katalogów plików przy użyciu technologii PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="00384-123">Instrukcje: mierzenie wydajności zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="00384-124">Próbka danych PLINQ</span><span class="sxs-lookup"><span data-stu-id="00384-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="00384-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00384-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="00384-126">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="00384-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="00384-127">Zapytanie zintegrowane z językiem (LINQ) — C #</span><span class="sxs-lookup"><span data-stu-id="00384-127">Language-Integrated Query (LINQ) - C#</span></span>](../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="00384-128">Zapytanie zintegrowane z językiem (LINQ) — visual basic</span><span class="sxs-lookup"><span data-stu-id="00384-128">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)  
