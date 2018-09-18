---
title: 'Porady: anulowanie zapytania PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5008ede5054e8e6970bcb6f804fa1888244238f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45973095"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="6912e-102">Porady: anulowanie zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="6912e-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="6912e-103">W poniższych przykładach pokazano dwa sposoby Anulowanie zapytania PLINQ.</span><span class="sxs-lookup"><span data-stu-id="6912e-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="6912e-104">Pierwszy przykład pokazuje, jak anulować kwerendę, która składa się przede wszystkim z przechodzenia danych.</span><span class="sxs-lookup"><span data-stu-id="6912e-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="6912e-105">Drugi przykład pokazuje, jak anulować kwerendę, która zawiera funkcję użytkownika, która jest obliczeniowo kosztowne.</span><span class="sxs-lookup"><span data-stu-id="6912e-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6912e-106">Po włączeniu "Tylko mój kod" Visual Studio będzie przerwania w wierszu, który zgłasza wyjątek i wyświetlać komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="6912e-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="6912e-107">Ten błąd jest nieszkodliwe.</span><span class="sxs-lookup"><span data-stu-id="6912e-107">This error is benign.</span></span> <span data-ttu-id="6912e-108">Naciśnij klawisz F5, aby nadal z niego i wyświetlić zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="6912e-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="6912e-109">Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="6912e-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="6912e-110">W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty.</span><span class="sxs-lookup"><span data-stu-id="6912e-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="6912e-111">Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="6912e-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6912e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="6912e-112">Example</span></span>  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 <span data-ttu-id="6912e-113">PLINQ framework nieoperacyjnym pojedynczej <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> muszą być obsługiwane w bloku catch oddzielne.</span><span class="sxs-lookup"><span data-stu-id="6912e-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="6912e-114">Jeśli co najmniej jeden delegatów użytkownika zgłasza OperationCanceledException(externalCT) (przy użyciu zewnętrznego <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale nie innych wyjątków i zapytania została zdefiniowana jako `AsParallel().WithCancellation(externalCT)`, PLINQ wystawi jeden, a następnie <xref:System.OperationCanceledException> (externalCT) zamiast <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6912e-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6912e-115">Jednak jeśli delegowanie jeden użytkownik zgłasza <xref:System.OperationCanceledException>, delegowanego innego zgłasza inny typ wyjątku, a następnie zarówno wyjątki zostanie wycofana do <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="6912e-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>  
  
 <span data-ttu-id="6912e-116">Ogólne wskazówki na temat anulowania jest następująca:</span><span class="sxs-lookup"><span data-stu-id="6912e-116">The general guidance on cancellation is as follows:</span></span>  
  
1.  <span data-ttu-id="6912e-117">Jeśli wykonujesz anulowania pełnomocnika użytkownika informowało PLINQ o zewnętrznej <xref:System.Threading.CancellationToken> i zgłosić <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="6912e-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>  
  
2.  <span data-ttu-id="6912e-118">Jeśli żadne inne wyjątki są zgłaszane następuje anulowanie, następnie należy obsługiwać <xref:System.OperationCanceledException> zamiast <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="6912e-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6912e-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="6912e-119">Example</span></span>  
 <span data-ttu-id="6912e-120">Poniższy przykład przedstawia sposób obsługi anulowania, gdy masz obciążającymi funkcji w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6912e-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 <span data-ttu-id="6912e-121">Podczas obsługi anulowania w kodzie użytkownika, nie trzeba używać <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> w definicji podzapytania.</span><span class="sxs-lookup"><span data-stu-id="6912e-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="6912e-122">Jednak zaleca się, możesz to zrobić, ponieważ <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nie ma wpływu na wydajność zapytań i umożliwia anulowanie, które mają być obsługiwane przez operatorów zapytań, a kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6912e-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>  
  
 <span data-ttu-id="6912e-123">Aby zapewnić czas reakcji systemu, zaleca się sprawdzenie, czy anulowania wokół raz na milisekundę; Jednak każdy okres, maksymalnie 10 milisekund jest uważany za akceptowalne.</span><span class="sxs-lookup"><span data-stu-id="6912e-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="6912e-124">Tę częstotliwość nie powinna mieć negatywny wpływ na wydajność kodu.</span><span class="sxs-lookup"><span data-stu-id="6912e-124">This frequency should not have a negative impact on your code's performance.</span></span>  
  
 <span data-ttu-id="6912e-125">Po usunięciu moduł wyliczający, na przykład gdy kodu przerywa poza pętlę foreach (dla każdego w języku Visual Basic), która jest Iterowanie wyników zapytania, a następnie zapytanie zostało anulowane, ale jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6912e-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6912e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6912e-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="6912e-127">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="6912e-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
- [<span data-ttu-id="6912e-128">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="6912e-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
