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
ms.openlocfilehash: 665490601cad9ccd7881042aed576b95bbc07115
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139732"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="628d1-102">Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych</span><span class="sxs-lookup"><span data-stu-id="628d1-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="628d1-103">W tym przykładzie pokazano, jak <xref:System.Threading.Tasks.Parallel.Invoke%2A> równoległych operacji przy użyciu w bibliotece równoległej zadania.</span><span class="sxs-lookup"><span data-stu-id="628d1-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="628d1-104">Trzy operacje są wykonywane na udostępnionym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="628d1-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="628d1-105">Ponieważ żadna z operacji modyfikuje źródło, mogą być wykonywane równolegle w prosty sposób.</span><span class="sxs-lookup"><span data-stu-id="628d1-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="628d1-106">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL.</span><span class="sxs-lookup"><span data-stu-id="628d1-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="628d1-107">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="628d1-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="628d1-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="628d1-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="628d1-109">Należy zauważyć, że za pomocą <xref:System.Threading.Tasks.Parallel.Invoke%2A>programu , po prostu wyrazić, które akcje chcesz uruchomić jednocześnie, a czas wykonywania obsługuje wszystkie szczegóły planowania wątków, w tym skalowanie automatycznie do liczby rdzeni na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="628d1-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="628d1-110">W tym przykładzie równoległości operacji, a nie danych.</span><span class="sxs-lookup"><span data-stu-id="628d1-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="628d1-111">Jako alternatywne podejście, można równoległych zapytań LINQ przy użyciu PLINQ i uruchamiać zapytania sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="628d1-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="628d1-112">Alternatywnie można zrównoleglić dane przy użyciu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="628d1-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="628d1-113">Inną opcją jest zrównolegliwość zarówno zapytań, jak i zadań.</span><span class="sxs-lookup"><span data-stu-id="628d1-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="628d1-114">Mimo że wynikające z tego obciążenie może obniżyć wydajność na komputerach hosta z stosunkowo niewielką liczbą procesorów, znacznie lepiej skalowałoby się na komputerach z wieloma procesorami.</span><span class="sxs-lookup"><span data-stu-id="628d1-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="628d1-115">Skompiluj kod</span><span class="sxs-lookup"><span data-stu-id="628d1-115">Compile the Code</span></span>

<span data-ttu-id="628d1-116">Skopiuj i wklej cały przykład do projektu programu Microsoft Visual Studio i naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="628d1-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="628d1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="628d1-117">See also</span></span>

- [<span data-ttu-id="628d1-118">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="628d1-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="628d1-119">Instrukcje: anulowanie zadania i jego elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="628d1-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="628d1-120">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="628d1-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
