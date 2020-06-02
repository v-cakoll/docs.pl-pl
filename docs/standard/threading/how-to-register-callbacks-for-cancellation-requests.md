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
ms.openlocfilehash: 0482d43925f4f547114119a95909501cbf09eedb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279365"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="d64c8-102">Porady: rejestrowanie wywołań zwrotnych żądań anulowania</span><span class="sxs-lookup"><span data-stu-id="d64c8-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="d64c8-103">Poniższy przykład pokazuje, jak zarejestrować delegata, który zostanie wywołany, gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> Właściwość zostanie prawdziwa, z powodu wywołania do <xref:System.Threading.CancellationTokenSource.Cancel%2A> obiektu, który utworzył token.</span><span class="sxs-lookup"><span data-stu-id="d64c8-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="d64c8-104">Ta technika służy do anulowania operacji asynchronicznych, które nie obsługują natywnie ujednoliconej platformy anulowania oraz dla odblokowania metod, które mogą oczekiwać na zakończenie operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="d64c8-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d64c8-105">Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="d64c8-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="d64c8-106">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="d64c8-106">This error is benign.</span></span> <span data-ttu-id="d64c8-107">Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="d64c8-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="d64c8-108">Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="d64c8-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d64c8-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d64c8-109">Example</span></span>  
 <span data-ttu-id="d64c8-110">W poniższym przykładzie <xref:System.Net.WebClient.CancelAsync%2A> Metoda jest zarejestrowana jako metoda do wywołania w przypadku żądania anulowania za pomocą tokenu anulowania.</span><span class="sxs-lookup"><span data-stu-id="d64c8-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="d64c8-111">Jeśli po zarejestrowaniu wywołania zwrotnego zostało już zgłoszone żądanie anulowania, wywołanie zwrotne jest nadal gwarantowane.</span><span class="sxs-lookup"><span data-stu-id="d64c8-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="d64c8-112">W tym konkretnym przypadku <xref:System.Net.WebClient.CancelAsync%2A> Metoda nie będzie niczego robić, jeśli żadna operacja asynchroniczna nie jest w toku, więc zawsze jest bezpieczna do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="d64c8-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d64c8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d64c8-113">See also</span></span>

- [<span data-ttu-id="d64c8-114">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="d64c8-114">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
