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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2d61ba254a76235a12ca5dda23fdecb8838ae75
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863585"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="52e2e-102">Porady: rejestrowanie wywołań zwrotnych żądań anulowania</span><span class="sxs-lookup"><span data-stu-id="52e2e-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="52e2e-103">Poniższy przykład pokazuje, jak zarejestrować delegata, która zostanie wywołana, gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość zostanie spełniony ze względu na wywołanie <xref:System.Threading.CancellationTokenSource.Cancel%2A> na obiekt, który utworzył token.</span><span class="sxs-lookup"><span data-stu-id="52e2e-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="52e2e-104">Tej techniki należy używać dla anulowania operacji asynchronicznych, które nie obsługują natywnie w ramach ujednoliconego anulowania, a także dla metod odblokowywania, które może być oczekiwanie na zakończenie operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="52e2e-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52e2e-105">Po włączeniu "Tylko mój kod" Visual Studio, w niektórych przypadkach przerwania w wierszu, który zgłasza wyjątek i wyświetlić komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="52e2e-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="52e2e-106">Ten błąd jest nieszkodliwe.</span><span class="sxs-lookup"><span data-stu-id="52e2e-106">This error is benign.</span></span> <span data-ttu-id="52e2e-107">Naciśnij klawisz F5, aby nadal z niego i wyświetlić zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="52e2e-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="52e2e-108">Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="52e2e-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52e2e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="52e2e-109">Example</span></span>  
 <span data-ttu-id="52e2e-110">W poniższym przykładzie <xref:System.Net.WebClient.CancelAsync%2A> metody jest zarejestrowany jako metoda do wywołania, gdy zażądano anulowania do anulowania.</span><span class="sxs-lookup"><span data-stu-id="52e2e-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="52e2e-111">Jeśli już zażądano anulowania, gdy wywołanie zwrotne jest zarejestrowany, nadal jest gwarantowane można wywołać wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="52e2e-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="52e2e-112">W tym konkretnym przypadku <xref:System.Net.WebClient.CancelAsync%2A> metoda będzie nic nie rób, jeśli nie operacja asynchroniczna jest w toku, dzięki czemu jest zawsze można bezpiecznie wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="52e2e-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e2e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52e2e-113">See also</span></span>

- [<span data-ttu-id="52e2e-114">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="52e2e-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
