---
title: "Porady: nasłuchiwanie żądań anulowania za pomocą sondowania"
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
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56a927e10cb026814302728a72acb2f32223b29b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="c0da0-102">Porady: nasłuchiwanie żądań anulowania za pomocą sondowania</span><span class="sxs-lookup"><span data-stu-id="c0da0-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="c0da0-103">W poniższym przykładzie przedstawiono jeden sposób, aby kod użytkownika można sondować token anulowania w regularnych odstępach czasu, aby zobaczyć, czy z wątku wywołującym zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="c0da0-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="c0da0-104">W tym przykładzie użyto <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu, ale tego samego wzorca dotyczy operacji asynchronicznych utworzone bezpośrednio przez <xref:System.Threading.ThreadPool?displayProperty=nameWithType> typu lub <xref:System.Threading.Thread?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="c0da0-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0da0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0da0-105">Example</span></span>  
 <span data-ttu-id="c0da0-106">Sondowanie wymaga określonego rodzaju pętli lub cykliczne kod, który może odczytywać okresowo wartość typu Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c0da0-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="c0da0-107">Jeśli używasz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu i oczekują na wykonanie zadania w wątku wywołującym, możesz użyć <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody do sprawdzenia właściwości i zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c0da0-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="c0da0-108">Za pomocą tej metody, można zapewnić, że poprawne wyjątku w odpowiedzi na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c0da0-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="c0da0-109">Jeśli używasz <xref:System.Threading.Tasks.Task>, następnie wywołaniem tej metody jest lepszym rozwiązaniem niż ręcznie zgłaszanie <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="c0da0-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="c0da0-110">Jeśli nie masz ma zostać zgłoszony wyjątek, a następnie można po prostu Sprawdź właściwość i zwracany przez metodę, jeśli właściwość jest `true`.</span><span class="sxs-lookup"><span data-stu-id="c0da0-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="c0da0-111">Wywoływanie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> jest bardzo szybkie i nie powodować znaczne obciążenie w pętli.</span><span class="sxs-lookup"><span data-stu-id="c0da0-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="c0da0-112">Jeśli wywołujesz <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, należy jawnie sprawdziła <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości, jeśli masz inne pracy w odpowiedzi na anulowanie oprócz Zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c0da0-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="c0da0-113">W tym przykładzie widać, że kod faktycznie uzyskuje dostęp do właściwości dwa razy: raz w jawny dostęp i ponownie w <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c0da0-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="c0da0-114">Jednak ponieważ act odczytu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości obejmuje tylko jedno pole nietrwałe instrukcji na dostęp do odczytu, double dostępu nie jest istotne z punktu widzenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="c0da0-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="c0da0-115">Zaleca się nadal do wywołania metody, zamiast ręcznie throw <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="c0da0-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0da0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0da0-116">See Also</span></span>  
 [<span data-ttu-id="c0da0-117">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="c0da0-117">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
