---
title: 'Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0192e12c86b21eb126293bbd220e093b334768b
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324223"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="1c1d1-102">Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych</span><span class="sxs-lookup"><span data-stu-id="1c1d1-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="1c1d1-103">W tym przykładzie pokazano, jak zrównoleglić operacje przy użyciu <xref:System.Threading.Tasks.Parallel.Invoke%2A> w bibliotece zadań równoległych.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="1c1d1-104">Trzy operacje są wykonywane na udostępnione źródło danych.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="1c1d1-105">Ponieważ żadne operacje modyfikuje źródła, mogą być wykonywane równolegle w prosty sposób.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="1c1d1-106">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="1c1d1-107">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="1c1d1-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="1c1d1-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c1d1-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="1c1d1-109">Należy pamiętać, że za pomocą <xref:System.Threading.Tasks.Parallel.Invoke%2A>, po prostu express akcje, które mają być uruchamiane równolegle i środowisko wykonawcze obsługuje wszystkie wątku planowania szczegółów, takich jak automatyczne skalowanie do liczby rdzeni na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="1c1d1-110">W tym przykładzie parallelizes operacji, a nie dane.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="1c1d1-111">Jako alternatywne podejście możesz zrównoleglenia zapytania w LINQ za pomocą PLINQ i uruchamiać je sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="1c1d1-112">Alternatywnie można zrównoleglić danych przy użyciu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="1c1d1-113">Innym rozwiązaniem jest równoległe przetwarzanie zapytań i zadań.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="1c1d1-114">Mimo że wynikowy obciążenie może zmniejszyć wydajność na komputerach hostów stosunkowo niewielką liczbą procesorów, go czy skalowanie znacznie lepsze na komputerach z procesorami wielordzeniowymi, wiele.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="1c1d1-115">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="1c1d1-115">Compile the Code</span></span>

<span data-ttu-id="1c1d1-116">Skopiuj i Wklej cały przykład w projekcie programu Microsoft Visual Studio i naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="1c1d1-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c1d1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c1d1-117">See also</span></span>

- [<span data-ttu-id="1c1d1-118">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="1c1d1-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="1c1d1-119">Instrukcje: anulowanie zadania i jego elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="1c1d1-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="1c1d1-120">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1c1d1-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
