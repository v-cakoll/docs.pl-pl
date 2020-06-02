---
title: 'Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: e44b10b88bef61edcf3f547f56b4020740530e26
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279546"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="d6e94-102">Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania</span><span class="sxs-lookup"><span data-stu-id="d6e94-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="d6e94-103">Jeśli metoda jest blokowana, gdy oczekuje na zasygnalizowanie zdarzenia, nie może sprawdzić wartości tokenu anulowania i odpowiedzieć w odpowiednim czasie.</span><span class="sxs-lookup"><span data-stu-id="d6e94-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="d6e94-104">W pierwszym przykładzie pokazano, jak rozwiązać ten problem podczas pracy ze zdarzeniami, takimi jak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> , które nie obsługują natywnie ujednoliconej platformy anulowania.</span><span class="sxs-lookup"><span data-stu-id="d6e94-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="d6e94-105">Drugi przykład przedstawia bardziej usprawnione podejście, które używa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> , które obsługuje ujednolicone anulowanie.</span><span class="sxs-lookup"><span data-stu-id="d6e94-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6e94-106">Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="d6e94-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="d6e94-107">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="d6e94-107">This error is benign.</span></span> <span data-ttu-id="d6e94-108">Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="d6e94-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="d6e94-109">Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="d6e94-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6e94-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6e94-110">Example</span></span>  
 <span data-ttu-id="d6e94-111">W poniższym przykładzie używa <xref:System.Threading.ManualResetEvent> się, aby zademonstrować, jak odblokować dojścia oczekiwania, które nie obsługują ujednoliconego anulowania.</span><span class="sxs-lookup"><span data-stu-id="d6e94-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="d6e94-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6e94-112">Example</span></span>  
 <span data-ttu-id="d6e94-113">Poniższy przykład używa, <xref:System.Threading.ManualResetEventSlim> Aby zademonstrować, jak odblokować elementy podstawowe koordynacji, które obsługują ujednolicone anulowanie.</span><span class="sxs-lookup"><span data-stu-id="d6e94-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="d6e94-114">Takie samo podejście może być używane z innymi uproszczonymi typami podstawowymi koordynacji, takimi jak <xref:System.Threading.Semaphore> `Slim` i <xref:System.Threading.CountdownEvent> .</span><span class="sxs-lookup"><span data-stu-id="d6e94-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="d6e94-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6e94-115">See also</span></span>

- [<span data-ttu-id="d6e94-116">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="d6e94-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
