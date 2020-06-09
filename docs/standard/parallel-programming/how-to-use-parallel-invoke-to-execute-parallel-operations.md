---
title: 'Instrukcje: Wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke'
description: Zobacz jak używać metody Parallel. Invoke w bibliotece Task Parallel Library (TPL), która wykonuje operacje równoległe na udostępnionym źródle danych w programie .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 084ade48b1406d23a11eb311739525f35ac973df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596348"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="9022c-103">Instrukcje: Wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke</span><span class="sxs-lookup"><span data-stu-id="9022c-103">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="9022c-104">Ten przykład pokazuje, jak zrównoleglanie operacje przy użyciu <xref:System.Threading.Tasks.Parallel.Invoke%2A> w bibliotece zadań równoległych.</span><span class="sxs-lookup"><span data-stu-id="9022c-104">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="9022c-105">Trzy operacje są wykonywane na udostępnionym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="9022c-105">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="9022c-106">Operacje mogą być wykonywane równolegle w prosty sposób, ponieważ żaden z nich nie modyfikuje źródła.</span><span class="sxs-lookup"><span data-stu-id="9022c-106">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="9022c-107">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL.</span><span class="sxs-lookup"><span data-stu-id="9022c-107">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="9022c-108">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażenia lambda w PLINQ i TPL](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="9022c-108">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="9022c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="9022c-109">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="9022c-110">Za pomocą programu <xref:System.Threading.Tasks.Parallel.Invoke%2A> można po prostu przedstawić, które akcje mają być uruchamiane współbieżnie, a środowisko uruchomieniowe obsługuje wszystkie szczegóły dotyczące planowania wątków, w tym skalowanie automatycznie do liczby rdzeni na komputerze hosta.</span><span class="sxs-lookup"><span data-stu-id="9022c-110">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="9022c-111">Ten przykład parallelizes operacje, a nie dane.</span><span class="sxs-lookup"><span data-stu-id="9022c-111">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="9022c-112">Alternatywnie można zrównoleglanie zapytania LINQ przy użyciu PLINQ i uruchamiać zapytania sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="9022c-112">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="9022c-113">Alternatywnie można zrównoleglanie dane przy użyciu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="9022c-113">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="9022c-114">Kolejną opcją jest zrównoleglanie zarówno zapytania, jak i zadania.</span><span class="sxs-lookup"><span data-stu-id="9022c-114">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="9022c-115">Chociaż wynikowe obciążenie może obniżyć wydajność na komputerach hostów z stosunkowo kilkoma procesorami, lepiej skalować je na komputerach z wieloma procesorami.</span><span class="sxs-lookup"><span data-stu-id="9022c-115">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="9022c-116">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="9022c-116">Compile the Code</span></span>

<span data-ttu-id="9022c-117">Skopiuj i wklej cały przykład do projektu Microsoft Visual Studio i naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="9022c-117">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="9022c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9022c-118">See also</span></span>

- [<span data-ttu-id="9022c-119">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="9022c-119">Parallel Programming</span></span>](index.md)
- [<span data-ttu-id="9022c-120">Instrukcje: Anulowanie zadania i jego elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="9022c-120">How to: Cancel a Task and Its Children</span></span>](how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="9022c-121">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9022c-121">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
