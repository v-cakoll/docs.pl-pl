---
title: 'Porady: rejestrowanie wywołań zwrotnych żądań anulowania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: 87ba1ab9ac095c733a53f766d00ebb7530a8d9c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137999"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="bd098-102">Porady: rejestrowanie wywołań zwrotnych żądań anulowania</span><span class="sxs-lookup"><span data-stu-id="bd098-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="bd098-103">W poniższym przykładzie pokazano, jak zarejestrować pełnomocnika, który zostanie wywołany, gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość staje się true ze względu <xref:System.Threading.CancellationTokenSource.Cancel%2A> na wywołanie na obiekcie, który utworzył token.</span><span class="sxs-lookup"><span data-stu-id="bd098-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="bd098-104">Ta technika służy do anulowania operacji asynchronicznych, które nie obsługują natywnie ujednoliconej struktury anulowania i dla metod odblokowywania, które mogą czekać na zakończenie operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="bd098-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd098-105">Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="bd098-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="bd098-106">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="bd098-106">This error is benign.</span></span> <span data-ttu-id="bd098-107">Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="bd098-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="bd098-108">Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.</span><span class="sxs-lookup"><span data-stu-id="bd098-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd098-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd098-109">Example</span></span>  
 <span data-ttu-id="bd098-110">W poniższym przykładzie <xref:System.Net.WebClient.CancelAsync%2A> metoda jest zarejestrowana jako metoda, która ma być wywoływana, gdy anulowanie jest wymagane za pośrednictwem tokenu anulowania.</span><span class="sxs-lookup"><span data-stu-id="bd098-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="bd098-111">Jeśli anulowanie zostało już poproszone, gdy wywołanie wywołania odwetowe jest zarejestrowane, wywołanie wywołania wywołania wywołania wywołania jest nadal gwarantowane do wywołania.</span><span class="sxs-lookup"><span data-stu-id="bd098-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="bd098-112">W tym konkretnym <xref:System.Net.WebClient.CancelAsync%2A> przypadku metoda nie zrobi nic, jeśli nie jest w toku żadna operacja asynchroniczna, więc zawsze można bezpiecznie wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="bd098-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd098-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd098-113">See also</span></span>

- [<span data-ttu-id="bd098-114">Anulowanie w wątkach zarządzanych</span><span class="sxs-lookup"><span data-stu-id="bd098-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
