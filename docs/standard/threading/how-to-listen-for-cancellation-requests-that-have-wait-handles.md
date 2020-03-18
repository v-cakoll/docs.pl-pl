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
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137988"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="05f6d-102">Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania</span><span class="sxs-lookup"><span data-stu-id="05f6d-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="05f6d-103">Jeśli metoda jest zablokowana, gdy oczekuje na zdarzenie, które mają być sygnalizowane, nie można sprawdzić wartość tokenu anulowania i odpowiedzieć w odpowiednim czasie.</span><span class="sxs-lookup"><span data-stu-id="05f6d-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="05f6d-104">W pierwszym przykładzie pokazano, jak rozwiązać ten problem <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> podczas pracy ze zdarzeniami, takimi jak które nie obsługują natywnie ujednoliconej struktury anulowania.</span><span class="sxs-lookup"><span data-stu-id="05f6d-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="05f6d-105">Drugi przykład pokazuje bardziej uproszczone <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>podejście, które używa , który obsługuje ujednolicone anulowanie.</span><span class="sxs-lookup"><span data-stu-id="05f6d-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05f6d-106">Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="05f6d-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="05f6d-107">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="05f6d-107">This error is benign.</span></span> <span data-ttu-id="05f6d-108">Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="05f6d-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="05f6d-109">Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.</span><span class="sxs-lookup"><span data-stu-id="05f6d-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05f6d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="05f6d-110">Example</span></span>  
 <span data-ttu-id="05f6d-111">W poniższym <xref:System.Threading.ManualResetEvent> przykładzie użyto do wykazania, jak odblokować uchwyty oczekiwania, które nie obsługują ujednoliconeanulowanie.</span><span class="sxs-lookup"><span data-stu-id="05f6d-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="05f6d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="05f6d-112">Example</span></span>  
 <span data-ttu-id="05f6d-113">W poniższym <xref:System.Threading.ManualResetEventSlim> przykładzie użyto do wykazania, jak odblokować prymitywy koordynacji, które obsługują ujednolicone anulowanie.</span><span class="sxs-lookup"><span data-stu-id="05f6d-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="05f6d-114">To samo podejście może być stosowane z innymi lekkimi prymitywami koordynacyjnymi, takimi jak <xref:System.Threading.Semaphore> `Slim` i <xref:System.Threading.CountdownEvent>.</span><span class="sxs-lookup"><span data-stu-id="05f6d-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="05f6d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05f6d-115">See also</span></span>

- [<span data-ttu-id="05f6d-116">Anulowanie w wątkach zarządzanych</span><span class="sxs-lookup"><span data-stu-id="05f6d-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
