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
ms.openlocfilehash: 272f25d62cb63c60209be3bc54dc5e76fb30df54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134230"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="677a1-102">Porady: anulowanie zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="677a1-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="677a1-103">W poniższych przykładach przedstawiono dwa sposoby anulowania kwerendy PLINQ.</span><span class="sxs-lookup"><span data-stu-id="677a1-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="677a1-104">W pierwszym przykładzie pokazano, jak anulować kwerendę, która składa się głównie z przechodzenia danych.</span><span class="sxs-lookup"><span data-stu-id="677a1-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="677a1-105">W drugim przykładzie pokazano, jak anulować kwerendę, która zawiera funkcję użytkownika, która jest obliczeniowo drogie.</span><span class="sxs-lookup"><span data-stu-id="677a1-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="677a1-106">Gdy opcja "Tylko mój kod" jest włączona, program Visual Studio zostanie przerwany w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="677a1-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="677a1-107">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="677a1-107">This error is benign.</span></span> <span data-ttu-id="677a1-108">Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="677a1-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="677a1-109">Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.</span><span class="sxs-lookup"><span data-stu-id="677a1-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="677a1-110">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy.</span><span class="sxs-lookup"><span data-stu-id="677a1-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="677a1-111">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="677a1-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="677a1-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="677a1-112">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="677a1-113">Struktura PLINQ nie toczy <xref:System.OperationCanceledException> się <xref:System.AggregateException?displayProperty=nameWithType>w jeden ; <xref:System.OperationCanceledException> musi być obsługiwany w oddzielnym bloku zaczepu.</span><span class="sxs-lookup"><span data-stu-id="677a1-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="677a1-114">Jeśli jeden lub więcej delegatów użytkownika zgłasza OperationCanceledException(externalCT) (przy <xref:System.Threading.CancellationToken?displayProperty=nameWithType>użyciu zewnętrznego), ale `AsParallel().WithCancellation(externalCT)`nie ma innego wyjątku, <xref:System.OperationCanceledException> a kwerenda została <xref:System.AggregateException?displayProperty=nameWithType>zdefiniowana jako , następnie PLINQ wyda jeden (externalCT) zamiast .</span><span class="sxs-lookup"><span data-stu-id="677a1-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="677a1-115">Jednak jeśli jeden delegat użytkownika <xref:System.OperationCanceledException>zgłasza , a inny delegat zgłasza inny typ wyjątku, <xref:System.AggregateException>a następnie oba wyjątki zostaną zwinięte w .</span><span class="sxs-lookup"><span data-stu-id="677a1-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="677a1-116">Ogólne wytyczne dotyczące anulowania są następujące:</span><span class="sxs-lookup"><span data-stu-id="677a1-116">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="677a1-117">W przypadku wykonywania anulowania delegata użytkownika należy poinformować PLINQ o zewnętrznych <xref:System.Threading.CancellationToken> i wyrzuć <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="677a1-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="677a1-118">Jeśli nastąpi anulowanie i nie zostaną wygenerowane <xref:System.OperationCanceledException> żadne inne <xref:System.AggregateException>wyjątki, należy obsłużyć zamiast .</span><span class="sxs-lookup"><span data-stu-id="677a1-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="677a1-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="677a1-119">Example</span></span>

<span data-ttu-id="677a1-120">W poniższym przykładzie pokazano, jak obsługiwać anulowanie, gdy masz funkcję kosztowną obliczeniowo w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="677a1-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="677a1-121">Podczas obsługi anulowania w kodzie użytkownika, nie <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> trzeba używać w definicji kwerendy.</span><span class="sxs-lookup"><span data-stu-id="677a1-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="677a1-122">Jednak zaleca się, aby to <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> zrobić, ponieważ nie ma wpływu na wydajność kwerendy i umożliwia anulowanie obsługiwane przez operatory zapytań i kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="677a1-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="677a1-123">W celu zapewnienia reakcji systemu, zaleca się sprawdzenie anulowania około raz na milisekundę; jednak każdy okres do 10 milisekund jest uważany za dopuszczalny.</span><span class="sxs-lookup"><span data-stu-id="677a1-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="677a1-124">Ta częstotliwość nie powinna mieć negatywnego wpływu na wydajność kodu.</span><span class="sxs-lookup"><span data-stu-id="677a1-124">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="677a1-125">Gdy wyliczacz jest usuwany, na przykład, gdy kod rozbija się z foreach (For Each in Visual Basic) pętli, która jest iteracji nad wynikami kwerendy, a następnie kwerenda jest anulowana, ale nie wyjątek.</span><span class="sxs-lookup"><span data-stu-id="677a1-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="677a1-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="677a1-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="677a1-127">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="677a1-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="677a1-128">Anulowanie w wątkach zarządzanych</span><span class="sxs-lookup"><span data-stu-id="677a1-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
