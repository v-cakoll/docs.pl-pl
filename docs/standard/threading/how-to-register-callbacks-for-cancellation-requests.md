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
ms.openlocfilehash: a8df4c73af81580d1b242ce0ede8f8bcb4cad4fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583295"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="7880f-102">Porady: rejestrowanie wywołań zwrotnych żądań anulowania</span><span class="sxs-lookup"><span data-stu-id="7880f-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="7880f-103">Poniższy przykład przedstawia sposób rejestrowania delegata, który będzie wywoływany, gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości jest spełniony wskutek wywołania <xref:System.Threading.CancellationTokenSource.Cancel%2A> dla obiektu, który utworzył token.</span><span class="sxs-lookup"><span data-stu-id="7880f-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="7880f-104">Użyj tej metody dla anulowania operacji asynchronicznych, które nie obsługują natywnie framework ujednoliconego anulowania, a także metod odblokowywania, które może być oczekiwanie na zakończenie operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="7880f-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7880f-105">Po włączeniu "Tylko mój kod" programu Visual Studio w niektórych przypadkach będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="7880f-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="7880f-106">Ten błąd jest niegroźne.</span><span class="sxs-lookup"><span data-stu-id="7880f-106">This error is benign.</span></span> <span data-ttu-id="7880f-107">Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="7880f-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="7880f-108">Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="7880f-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7880f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7880f-109">Example</span></span>  
 <span data-ttu-id="7880f-110">W poniższym przykładzie <xref:System.Net.WebClient.CancelAsync%2A> metody jest zarejestrowany jako metodę do wywołania w przypadku anulowania żądania za pośrednictwem token anulowania.</span><span class="sxs-lookup"><span data-stu-id="7880f-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="7880f-111">Jeśli już zażądano anulowania, gdy wywołanie zwrotne jest zarejestrowany, nadal jest gwarantowane można wywołać metodę wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="7880f-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="7880f-112">W tym przypadku <xref:System.Net.WebClient.CancelAsync%2A> — metoda nie przynosi Jeśli nie asynchroniczne jest operacja w toku, dzięki czemu jest zawsze bezpieczne wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="7880f-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7880f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7880f-113">See Also</span></span>  
 [<span data-ttu-id="7880f-114">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="7880f-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
