---
title: Równoległe LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1fe7edffd53023cba6dac1454e620d6e0d7e9513
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210198"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="9148a-102">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9148a-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="9148a-103">Równoległe LINQ (PLINQ) to implementacja przetwarzania równoległego LINQ do obiektów.</span><span class="sxs-lookup"><span data-stu-id="9148a-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="9148a-104">Pełny zestaw LINQ standardowych operatorów zapytań w PLINQ są implementowane jako metody rozszerzenia dla <xref:System.Linq> przestrzeni nazw i ma dodatkowe operatory operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="9148a-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="9148a-105">PLINQ łączy prostotę i czytelności składni LINQ, korzystając z możliwości programowania równoległego.</span><span class="sxs-lookup"><span data-stu-id="9148a-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="9148a-106">Podobnie jak kod przeznaczonego Biblioteka zadań równoległych, zapytania PLINQ skalować w stopień współbieżności oparta na funkcjach komputera-hosta.</span><span class="sxs-lookup"><span data-stu-id="9148a-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="9148a-107">W wielu scenariuszach PLINQ może znacznie zwiększyć szybkość LINQ do zapytań obiekt przy użyciu wszystkich dostępnych rdzeni na komputerze-hoście wydajniej.</span><span class="sxs-lookup"><span data-stu-id="9148a-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="9148a-108">To zwiększenie wydajności zapewnia moc obliczeniową o wysokiej wydajności na pulpit.</span><span class="sxs-lookup"><span data-stu-id="9148a-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9148a-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9148a-109">In This Section</span></span>  
 [<span data-ttu-id="9148a-110">Wprowadzenie do PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="9148a-111">Ogólne informacje o przyspieszeniach w PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="9148a-112">Zachowywanie kolejności w PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="9148a-113">Opcje scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="9148a-114">Instrukcje: tworzenie i wykonywanie prostego zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="9148a-115">Instrukcje: sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="9148a-116">Instrukcje: łączenie równoległych i sekwencyjnych zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="9148a-117">Instrukcje: obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="9148a-118">Instrukcje: anulowanie zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="9148a-119">Instrukcje: pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="9148a-120">Instrukcje: określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="9148a-121">Instrukcje: określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="9148a-122">Instrukcje: iteracja katalogów plików przy użyciu technologii PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="9148a-123">Instrukcje: mierzenie wydajności zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="9148a-124">Próbka danych PLINQ</span><span class="sxs-lookup"><span data-stu-id="9148a-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="9148a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9148a-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="9148a-126">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="9148a-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
- [<span data-ttu-id="9148a-127">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="9148a-127">LINQ (Language-Integrated Query)</span></span>](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
