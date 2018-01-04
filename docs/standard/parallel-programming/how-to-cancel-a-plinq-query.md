---
title: 'Porady: anulowanie zapytania PLINQ'
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
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5ed3d38cdfd70e7588ba0c4d94816c7105c7cf3e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="aefdb-102">Porady: anulowanie zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="aefdb-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="aefdb-103">W poniższych przykładach pokazano dwa sposoby Anulowanie zapytania PLINQ.</span><span class="sxs-lookup"><span data-stu-id="aefdb-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="aefdb-104">Pierwszym przykładzie pokazano, jak można anulować kwerendę, która składa się przede wszystkim z przechodzenie danych.</span><span class="sxs-lookup"><span data-stu-id="aefdb-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="aefdb-105">Drugim przykładzie pokazano, jak można anulować kwerendę, która zawiera funkcję użytkownika, która jest kosztowna w praktyce.</span><span class="sxs-lookup"><span data-stu-id="aefdb-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aefdb-106">Po włączeniu "Tylko mój kod" programu Visual Studio będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="aefdb-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="aefdb-107">Ten błąd jest niegroźne.</span><span class="sxs-lookup"><span data-stu-id="aefdb-107">This error is benign.</span></span> <span data-ttu-id="aefdb-108">Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="aefdb-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="aefdb-109">Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="aefdb-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="aefdb-110">W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania.</span><span class="sxs-lookup"><span data-stu-id="aefdb-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="aefdb-111">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="aefdb-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aefdb-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="aefdb-112">Example</span></span>  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 <span data-ttu-id="aefdb-113">PLINQ framework nie Przywracanie pojedynczego <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> muszą być obsługiwane w bloku catch oddzielne.</span><span class="sxs-lookup"><span data-stu-id="aefdb-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="aefdb-114">Jeśli co najmniej jeden użytkownik delegatów zgłasza OperationCanceledException(externalCT) (przy użyciu zewnętrznego <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale nie inne wyjątku i zapytania został zdefiniowany jako `AsParallel().WithCancellation(externalCT)`, następnie PLINQ wystawi pojedynczy <xref:System.OperationCanceledException> (externalCT) zamiast <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aefdb-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aefdb-115">Jednak jeśli delegowanie jeden użytkownik zgłasza <xref:System.OperationCanceledException>i delegowanego innego zgłasza innego typu wyjątku, a następnie będzie przeprowadzana zarówno wyjątki <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="aefdb-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>  
  
 <span data-ttu-id="aefdb-116">Ogólne wskazówki dotyczące anulowania jest następujący:</span><span class="sxs-lookup"><span data-stu-id="aefdb-116">The general guidance on cancellation is as follows:</span></span>  
  
1.  <span data-ttu-id="aefdb-117">W przypadku anulowania delegowanie użytkownika powinien informować PLINQ o zewnętrznej <xref:System.Threading.CancellationToken> i zgłosić <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="aefdb-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>  
  
2.  <span data-ttu-id="aefdb-118">Jeśli występuje anulowania, a nie inne wyjątki są zgłaszane, następnie należy powinna obsługiwać <xref:System.OperationCanceledException> zamiast <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="aefdb-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aefdb-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="aefdb-119">Example</span></span>  
 <span data-ttu-id="aefdb-120">Poniższy przykład przedstawia sposób obsługi anulowania, gdy funkcja praktyce kosztowne w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="aefdb-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 <span data-ttu-id="aefdb-121">Podczas obsługi anulowania w kodzie użytkownika, nie trzeba użyć <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> w definicji zapytania.</span><span class="sxs-lookup"><span data-stu-id="aefdb-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="aefdb-122">Jednak zaleca się, że można to zrobić, ponieważ <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nie ma wpływu na wydajność zapytań i umożliwia anulowanie mają być obsługiwane przez operatorów zapytań i kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="aefdb-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>  
  
 <span data-ttu-id="aefdb-123">Aby zapewnić czas reakcji systemu, firma Microsoft zaleca, wyszukaj anulowania wokół raz dla milisekund; Jednak każdy okres maksymalnie 10 milisekund jest uważany za akceptowalne.</span><span class="sxs-lookup"><span data-stu-id="aefdb-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="aefdb-124">Tej częstotliwości nie powinna mieć negatywny wpływ na wydajność kodu.</span><span class="sxs-lookup"><span data-stu-id="aefdb-124">This frequency should not have a negative impact on your code's performance.</span></span>  
  
 <span data-ttu-id="aefdb-125">Jeśli moduł wyliczający zostanie usunięty, na przykład jeśli kod dzieli poza pętli foreach (dla każdej z nich w Visual Basic), która jest iteracja w wynikach zapytania, a następnie zapytanie zostało anulowane, ale nie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="aefdb-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefdb-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aefdb-126">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="aefdb-127">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="aefdb-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="aefdb-128">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="aefdb-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
