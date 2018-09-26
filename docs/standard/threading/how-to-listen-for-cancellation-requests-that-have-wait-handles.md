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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1c8bfea5fc55bafbaa30d3b74edf60b674ef75c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077801"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="05570-102">Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania</span><span class="sxs-lookup"><span data-stu-id="05570-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="05570-103">Jeśli metoda jest zablokowane, ponieważ trwa oczekiwanie na zdarzenie ma być zasygnalizowany, nie mogą sprawdzić wartość tokenu anulowania i reagować w odpowiednim czasie.</span><span class="sxs-lookup"><span data-stu-id="05570-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="05570-104">Pierwszy przykład pokazuje, jak rozwiązać ten problem, podczas pracy ze zdarzeniami takich jak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> , nie obsługują natywnie w ramach ujednoliconego anulowania.</span><span class="sxs-lookup"><span data-stu-id="05570-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="05570-105">Drugi przykład przedstawia podejście usprawnić, który używa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, który obsługuje unified anulowania.</span><span class="sxs-lookup"><span data-stu-id="05570-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05570-106">Po włączeniu "Tylko mój kod" Visual Studio, w niektórych przypadkach przerwania w wierszu, który zgłasza wyjątek i wyświetlić komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="05570-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="05570-107">Ten błąd jest nieszkodliwe.</span><span class="sxs-lookup"><span data-stu-id="05570-107">This error is benign.</span></span> <span data-ttu-id="05570-108">Naciśnij klawisz F5, aby nadal z niego i wyświetlić zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="05570-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="05570-109">Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="05570-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05570-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="05570-110">Example</span></span>  
 <span data-ttu-id="05570-111">W poniższym przykładzie użyto <xref:System.Threading.ManualResetEvent> aby zademonstrować sposób odblokowania uchwytami oczekiwania, które nie obsługują anulowania ujednoliconego.</span><span class="sxs-lookup"><span data-stu-id="05570-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="05570-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="05570-112">Example</span></span>  
 <span data-ttu-id="05570-113">W poniższym przykładzie użyto <xref:System.Threading.ManualResetEventSlim> aby zademonstrować sposób odblokowania koordynacji podstawowych, które obsługują unified anulowania.</span><span class="sxs-lookup"><span data-stu-id="05570-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="05570-114">To samo podejście mogą być używane z innych podstawowych koordynacji uproszczone, takich jak <xref:System.Threading.Semaphore> `Slim` i <xref:System.Threading.CountdownEvent>.</span><span class="sxs-lookup"><span data-stu-id="05570-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="05570-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05570-115">See also</span></span>

- [<span data-ttu-id="05570-116">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="05570-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
